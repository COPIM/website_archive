# COPIM's HugoSandbox

Our website is rendered/processed into a static HTML web site by [HUGO](https://gohugo.io/) using the *Markdown files* from this [Git](https://git-scm.com/) repository served to you by [Gitea](https://gitea.io/). *Markdown files* which are rendered into web site pages could be found inside the folder 📁 **content** which is listed right below 📁 **archetypes**, and above 📁 **i18n**, 📁 **public** etc. *Markdown files* have extension **.md**. We **add/edit** *Markdown files* in this repository in order to have **HUGO** process/render/convert it into the regular Web Site people can access. Through that process every *Markdown file* gets transformed into an individual Web/HTML Page.

#### There are two ways to edit existing Markdown files and add a new ones:

#### 1. One could edit the web site by custom setup at https://b.copim.ac.uk/_preview/ which adds the user friendly header which looks like this:

![](static/images/preview_header_small.png)

1. To **edit** the current page one should use the button/link **EDIT_THIS_PAGE**. It brings you straight into the editing page for that page.

2. To **add** a new page under the current folder one should use the button/link **FOLDER/ADD_NEW_PAGE** (where **FOLDER** would expand into either 📁 **about-us** or 📁 **work-pacakges** regarding current URL one is visiting)

3. To **add** a new page or even a new folder one should use the button/link **ADD_NEW_PAGE**. (If you want to add a new folder just type **/** (slash) after the name of a new folder and the input area will automatically let you continue with typing the name of the file to be edited. Yet another thing which is easier if you try it. Just try to type slash **/** after the folder name and it becomes obvious)  

4. To **PUBLISH** one should use the button/link **PUBLISH** which would bring you straight into the editing **PUBLISH.trigger.md** after which commit the web site will be published.


####  2. One could edit the web site by using this Gitea instance (https://a.copim.ac.uk/WebSite/HugoSandbox) where you just read this **README.md** file.

1. To **edit** *Markdown files* you should get inside the 📁 **content** folder where you will find two folders 📁 **about-us** and 📁 **work-packages**. All the individual *Markdown files* are saved/accessible there.

2. To **edit** a particular *Markdown file* in this repository one should click on the 🖉 (pen) in the top right corner of the Gitea toolbar which appears after you open the Gitea web page of that *Markdown file* ![](static/images/edit_page.png)

    - It is very important to always have a **header** at the top of the Markdown file which starts with three dashes ( --- ); is then followed by **title** and/or **date** lines carrying the obvious value of the **title** and/or the **date** of the markdown file. Sometimes you could find **weight** which is used by the web site **menus** and the Markdown file (or a web page of our web site after being commited and/or published) with lower number will apear above the one with higher number. Usually you make the top of the **menu** with **weight: 10** and the rest with 20, 30, 40... So if you ever add the new page you could easily make it in between (e.g. 25, 35, 45..) without changing anything else. Here is one of the examples from 📁 **content/about-us/\_index.md**:  
![](static/images/front_matter.png)


3. To **add** a new *Markdown file* one should click the button **[New File]** in the folder where one wants the new *Markdown file* (at the moment these are 📁 **content/about-us** and 📁 **content/work-packages**)

    - Every **new** *Markdown file* should have **.md** extension as the part of its name. For example: **ResearchReport.md**.
    - Every **new** *Markdown file* has to have **header** at the top. The first line should start with three dashes ( **---** ), the second line should have a **title** (for example: **title: "Research Report 2021"**), **date**, **weight** should follow and before the actual content **header** should end again with three dashes ( **--** ).

4. To **upload** images one should click the button **[Upload File]** and upload the image inside the folders 📁 **static/images**. Once inside the 📁 **static/images** there are bunch of already uploaded images. Important to note is that if you are uploading an image, make sure the file name doesn't contain spaces " " but instead has **underscores** or is one word: team_photo.jpg, teamphoto.jpg or TeamPhoto.jpg for example.

5. To **PUBLISH** the web site with the all of the latest changes one should **edit** the file **PUBLISH.trigger.md**. It is listed in the root of this repository. Once there **PUBLISH.trigger.md** should have the 🖉 (pen) in the top right corner of the Gitea page toolbar just like every other page in the repository. Published version of the web site is here: https://b.copim.ac.uk/

6. After you get familiar with the workflow you migh also try the *trick* to *quickly* **PUBLISH** the web site by adding **!publish!** as a part of the commit message just like shown in this screenshot:

![](static/images/commit_publish_small.png)


#### NOTE: https://b.copim.ac.uk/_preview/ will show the changes after every commit/change. PUBLISH should be triggered after we are happy with the changes because that's the web site supposed to be public.

---

*If anything went wrong those two files could help few people not scared of reading logs :)*

- https://b.copim.ac.uk/last-commit-log.txt
- https://b.copim.ac.uk/_preview/last-commit-log.txt

[^1]: **Header** is called [Front Matter](https://gohugo.io/content-management/front-matter/) in HUGO's documentation.