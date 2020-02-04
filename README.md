# COPIM's HugoSandbox

Our website is rendered/processed into a static HTML web site by [HUGO](https://gohugo.io/) using the Markdown files from this repository served to you by [Gitea](https://gitea.io/). Markdown files which are rendered into web site pages could be found inside the folder 📁 **content** which is listed right below 📁 **archetypes**, and above 📁 **i18n**, 📁 **public** etc. Markdown files have extension **.md**. 

#### There are two ways to edit existing pages and add new pages:

1.  One could edit the web site by using **this** Gitea instance (https://a.copim.ac.uk/WebSite/HugoSandbox) where you read this README.md file. To **Edit pages** you should get inside the 📁 **content** folder where you will find two folders 📁 **about-us** and 📁 **work-packages**. All the individual pages are available there.
    1. To **edit** the page one should click on the 🖉 (pen) in the top right corner of the page toolbar
        - It is very important to always have a **header** at the top of the markdown file which starts with three dashes ( --- ); is then followed by **title** and **date** lines carrying the obvious value of the **title** and the **date** of the page. After you click on  the 🖉 icon and get into the **editing** area for any of the Markdown files inside 📁 **content** it will become quite obvious.
    2. To **add** a new page one should click the button **[New File]** in the folder where one wants the new page (at the moment these are 📁 **about-us** and 📁 **work-packages**
        - It is very important to always have a **header** at the top of the Markdown file which starts with three dashes ( --- ); is then followed by **title** and **date** lines carrying the obvious value of the **title** and the **date** of the markdown file.
    3. To **upload** images one should click the button **[Upload File]** and upload the image inside the folders 📁 **static/images**. Once inside the 📁 **static/images** there are bunch of already uploaded images. Important to note is that if you are uploading an image, make sure the file name doesn't contain spaces " " but instead has **underscores** or is one word: team_photo.jpg, teamphoto.jpg or TeamPhoto.jpg for example.
    4. To **PUBLISH** the web site with the all of the latest changes one should **edit** the file **PUBLISH.trigger.md**. It is listed in the root of the repository half the page above this very text. The 🖉 (pen) in the top right corner of the page toolbar is there as for every other page in the repository.
        - published version of the web site is here: https://b.copim.ac.uk/
     5. One could also *quickly* **PUBLISH** the web site by adding **!publish!** as a commit message like here: ![](static/images/commit_publish_small.png)


2. One could edit the web site by custom setup at https://b.copim.ac.uk/_preview/ which adds the user friendl header which looks like this:

![](static/images/preview_header_small.png)
  1. To **edit** the current page one should use the button/link **EDIT_THIS_PAGE**. It brings you straight into the editing page for that page.
  2. To **add** a new page under the current folder one should use the button/link **FOLDER/ADD_NEW_PAGE** (where **FOLDER** would expand into either 📁 **about-us** or 📁 **work-pacakges** regarding current URL one is visiting)
  3. To **add** a new page or even a new folder one should use the button/link **ADD_NEW_PAGE**. (If you want to add a new folder just type **/** (slash) after the name of a new folder and the input area will automatically let you continue with typing the name of the file to be edited. Yet another thing which is easier if you try it. Just try to type slash **/** after the folder name and it becomes obvious)  
  4. To **PUBLISH** one should use the button/link **PUBLISH** which would bring you straight into the editing **PUBLISH.trigger.md** after which commit the web site will be published.

#### https://b.copim.ac.uk/_preview/ will show the changes after every commit/change. PUBLISH should be triggered after we are happy with the changes because that's the web site supposed to be public.

---

*If anything went wrong those two files could help few people not scared of reading logs :)*

- https://b.copim.ac.uk/last-commit-log.txt
- https://b.copim.ac.uk/_preview/last-commit-log.txt
