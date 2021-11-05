This documentation provides details on Copim's website at [https://copim.ac.uk](https://copim.ac.uk/). The website is managed through a Gitea repository and generated as a site by Hugo static site generator. These services are all hosted on Copim's virtual server at copimres01.coventry.ac.uk.

**Server admin:**

Simon Bowie (Open-Source Software Developer) - ad7588@coventry.ac.uk

# gitella

The gitella Docker Compose container contains the website and associated services served via the nextcloud-web container. This container uses a custom build from a Dockerfile in /home/ac9573/docker-setup/nextcloud/gitella.

gitella contains the tools that generate the site on the gitellaweb volume to be served by the nextcloud-web container.

Gitea and Hugo are both located in the gitellarepo volume mounted to the gitella container at /root/gitea

The container starts Gitea as an entrypoint by running:

```
/root/gitea/gitea web
```

After restarting the server on 2021-09-08, Simon found that the site could no longer communicate with the themify-icon font files to retrieve icons. This was resolved by editing the www.copim.ac.uk site in the Nginx configuration to allow Access-Control-Allow-Origin for font files in the location stanza.

```
    location / { 
            root /var/www/gitella;

            if ($request_filename ~* ^.*?/([^/]*?)$)
            {
                set $filename $1; 
            }

            if ($filename ~* ^.*?\.(eot)|(ttf)|(woff)$){
                add_header Access-Control-Allow-Origin *;
            }
    }
```

# Gitea

Gitea 1.10.2 (<https://gitea.io/en-us/>) runs at <https://a.copim.ac.uk/> with a large amount of user-facing documentation for maintaining and changing the website at <https://a.copim.ac.uk/WebSite/HugoSandbox/src/branch/master/README.md>

The site is generated from files maintained in the WebSite/HugoSandbox repository.

The Gitea configuration file is located at /root/gitea/custom/conf/app.ini in the gitellarepo volume. Possible configuration file changes are documented at <https://docs.gitea.io/en-us/config-cheat-sheet/>

Gitea data (non-repository data) is stored in /root/gitea/data.

Gitea runs off a sqlite3 database at /root/gitea/data/gitea.db.

Gitea command line documentation is available at <https://docs.gitea.io/en-us/command-line/> and can be run on the Docker container using:

```
sudo docker exec -it gitella /root/gitea/gitea [INSERT COMMAND HERE]
```

# Hugo

Hugo 0.63.2-934EE21F (<https://gohugo.io/>) static site generator renders / processes the Markdown files in the WebSite/HugoSandbox repository into a static website served through Nginx to <https://copim.ac.uk/>.

Hugo renders the Markdown files into the website files in the gitellaweb volume at /var/www/html which gets mounted on to the nextcloud-web container at /var/www/gitella.

Hugo command line documentation is available at <https://gohugo.io/getting-started/usage/> and can be run on the Docker container using:

```
sudo docker exec -it gitella /root/gitea/hugo [INSERT COMMAND HERE]
```

The Hugo config file is documented at <https://gohugo.io/getting-started/configuration/> and is kept in the WebSite/HugoSandbox repository itself in config.toml: <https://a.copim.ac.uk/WebSite/HugoSandbox/src/branch/master/config.toml>

Hugo is triggered by Gitea through git hooks in the HugoSandbox repository at <https://a.copim.ac.uk/WebSite/HugoSandbox/settings/hooks/git> (on the server as /var/lib/docker/volumes/nextcloud_gitellarepo/_data/repositories/website/hugosandbox.git/hooks). The post-receive Bash script is most important and consists of: 

```
#!/bin/bash

set -e

WEBSITE=/var/www/html/
[ -d $WEBSITE ] || mkdir -p $WEBSITE

WEBSITEPREVIEW=/var/www/html/_preview/
[ -d $WEBSITEPREVIEW ] || mkdir -p $WEBSITEPREVIEW

GIT_URL="https://a.copim.ac.uk/WebSite/HugoSandbox"
HUGO_PREVIEW_URL="https://www.copim.ac.uk/_preview/"

GIT_PATH="git"
HUGO_PATH="/root/gitea/hugo"

BRK="krb"
SAVEIFS=$IFS

TMP_WEBSITE=/tmp/website$RANDOM
TMP_WEBSITEPREVIEW=/tmp/websitepreview$RANDOM

d=`date`
CWD=`pwd`

while read oldrev newrev ref
do
	refs=`$GIT_PATH diff-tree --no-commit-id --name-only $ref`
	IFS=$'\n'
	r=($refs)

	for (( i=0; i<${#r[@]}; i++ ))
	do
		if [ ${r[$i]} = "PUBLISH.trigger.md" ]; then
			cd $CWD
			$GIT_PATH clone . $TMP_WEBSITE
			cd $TMP_WEBSITE
			[ -d $WEBSITE ] || mkdir -p $WEBSITE

                        if [ -d $WEBSITE ]
	                  then
			    rm -rf ${WEBSITE}*
                        fi

			$HUGO_PATH -d $WEBSITE > ${TMP_WEBSITE}/last-commit-log.txt
			printf "\n>> $d\n>> `date`" >> ${TMP_WEBSITE}/last-commit-log.txt
			mv ${TMP_WEBSITE}/last-commit-log.txt $WEBSITE
			cd /tmp/

                        if [ -d $TMP_WEBSITE ]
	                  then
			    rm -rf $TMP_WEBSITE
                        fi
			
			BRK="brk"
			break
		fi
	done

	if [ $BRK = "brk" ]; then
		break
	fi
	
	cd $CWD
	refs=`$GIT_PATH show --format="%s" -s`
	IFS=$' '
	r=($refs)
	for (( i=0; i<${#r[@]}; i++ ))
	do
		if [ ${r[$i]} = "!publish!" ]; then
			$GIT_PATH clone . $TMP_WEBSITE
			cd $TMP_WEBSITE

			[ -d $WEBSITE ] || mkdir -p $WEBSITE

                        if [ -d $WEBSITE ]
	                  then
			    rm -rf ${WEBSITE}*
                        fi

			$HUGO_PATH -d $WEBSITE > ${TMP_WEBSITE}/last-commit-log.txt
			printf "\n>> $d\n>> `date`" >> ${TMP_WEBSITE}/last-commit-log.txt
			mv $TMP_WEBSITE/last-commit-log.txt $WEBSITE
			cd /tmp/

			if [ -d $TMP_WEBSITE ]; then
				rm -rf $TMP_WEBSITE
			fi

			break
		fi
	done
done

cd $CWD
$GIT_PATH clone . $TMP_WEBSITEPREVIEW
cd $TMP_WEBSITEPREVIEW

[ -d $WEBSITEPREVIEW ] || mkdir -p $WEBSITEPREVIEW

mkdir data
echo 'edit = true' > data/myvars.toml
echo 'giturl="'${GIT_URL}'"' >> data/myvars.toml

if [ -d $WEBSITEPREVIEW ]
  then
    rm -rf $WEBSITEPREVIEW
fi


$HUGO_PATH -b $HUGO_PREVIEW_URL -d $WEBSITEPREVIEW > ${TMP_WEBSITEPREVIEW}/last-commit-log.txt
printf "\n>> $d\n>> `date`" >> ${TMP_WEBSITEPREVIEW}/last-commit-log.txt
mv ${TMP_WEBSITEPREVIEW}/last-commit-log.txt $WEBSITEPREVIEW

if [ -d $TMP_WEBSITEPREVIEW ]
  then
    rm -rf $TMP_WEBSITEPREVIEW
fi

IFS=$SAVEIFS
```

## copim.ac.uk

The website uses a heavily customised version of the theme 'dot' in the themes directory. This theme is available at <https://gethugothemes.com/products/hugo-documentation-theme/>