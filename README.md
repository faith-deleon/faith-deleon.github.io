# Hosting a Resume in GitHub Pages

### Purpose
This README will describe the practical steps on how to host and format a resume using the following software stack:  
* Markdown
* Markdown editor: VSCode with the Markdown Preview Enhanced extension
* GitHub Pages
* Jekyll  

Each set of instructions will also be related to the general principles of Technical Writing that were outlined in Andrew Etter's book _Modern Technical Writing_.

### Prerequisites
1. Write a resume written using GitHub Flavored Markdown (GFM), which is GitHub's version of the Markdown syntax.
2. Create or login to your GitHub account.
3. Install the following:
    - Visual Studio Code
    - Jekyll

There are links in the ["More Resources"](#more-resources) section to help you set up these prerequisites.

### Instructions
#### Creating your site's repository
1. In the top-left corner of the homepage of GitHub, select the "New" button to create a new repository.   
![Add New Repository](/images/createNewRepo.PNG)  
2. Use the following format for your repository name: [username].github.io.  
![New Repository Form](/images/newRepoForm.PNG)  
Using the image above as an example, the "Repository name" field will have **faith-deleon.github.io**.
3. Set it as a public repository.
4. Complete the repository creation by clicking the "Create Repository" button.

By following the steps above and creating a repository through GitHub, you now have a remote repository for your GitHub pages site. This is where you will be able to store your site's source files, like your resume's Markdown file. One of Andrew Etter's protocols is to use distributed version control so that you can manage a remote repository. This ensures that your repository's files are kept up-to-date.

#### Clone your repository
By cloning your repository, you will be able to have access to your files locally on your own device. VSCode also has a UI for source control which will help us connect to our repository. There, we will be able to add and edit our files. 
1. Open up your repository in GitHub, which should currently have no files.
2. Copy your repository's link. This link should look like: https://github.com/[username]/[username].github.io.
3. In the left toolbar in VSCode, select the third icon from the top. 
4. Select the "Clone Repository" button.  
![VSCode Clone Repo](/images/vscodeCloneRepo.PNG)  
5. A field will appear that says "Provide repository URL or pick a repository source". Paste your GitHub repository link in this field.  
![VSCode Clone Repo Link](/images/vscodeCloneRepoLink.PNG)  
_NOTE: If you are not already logged in to your GitHub account in VSCode, you will be prompted to do so._
6. Choose a location in your local directory where you will place your repository.

You should now be able to open that new location in your local directory using VSCode.

One of Andrew Etter's protocols is to "Help Others Write," which means contribution to your project's files should be encouraged. Another person may have ideas and feedback on how you can improve your code and your documentation. When other people clone your repository, they will be able to suggest changes through pull requests. 

#### Set up Jekyll
1. While your project is open in VSCode, open up the terminal by selecting "Terminal"->"New Terminal" from the menubar. You can also use the shortcut CTRL + SHIFT + `.  
![Open Terminal](/images/openTerminal.PNG)  
2. In the terminal, enter the following command to create your Jekyll site:
    ~~~
    jekyll new --skip-bundle
    ~~~

    This step should have created the following files:  
    ![After Jekyll New](/images/afterJekyllNew.PNG)  

    _NOTE: Make sure you have installed Jekyll and its dependencies._  
3. Open up the Gemfile that was produced in the previous step.
4. Comment out the following line by adding a "#" in front of it:
    ~~~
    gem "jekyll", "~> 4.2.1"
    ~~~
5. Uncomment the line that has "gem "github-pages" and change it to:
    ~~~
    gem "github-pages", "219", group: :jekyll_plugins
    ~~~
    The second parameter "219" is the current dependency version for github-pages. You can find the dependency versions in this [link](https://pages.github.com/versions/).  
    By doing steps 4 and 5, you will be able to use GitHub Pages.
6. Save the changes you've made in the Gemfile.
7. Go back to the terminal and enter the following command:
    ~~~
    bundle install
    ~~~
8. Stage and commit your files. You can do this through the terminal or by using VSCode's UI.
    - **Terminal:**  
        Enter the following commands, separately:
        ~~~
        git add .
        git commit -m "<Commit message>"
        ~~~
    - **VSCode:**  
        1. In the source control tab, select the three dots to view all Git options.  
        ![VSCode Stage and Commit](/images/vscodeStageCommit.png)  
        2. Select "Changes"->"Stage All Changes".
        3. Select "Commit"->"Commit Staged".
        4. Add a helpful commit message describing what you did. 
9. Push your changes. This step can also be done through the terminal or through VSCode.
    - **Terminal:**  
        Enter the following command:
        ~~~
        git push -u origin master
        ~~~
    - **VSCode:**
        1. In the source control tab, select the three dots to view all Git options.  
        ![VSCode Stage and Commit](/images/vscodeStageCommit.png)  
        2. Select "Push".

After these steps, your site will be published at the following link: https://username.github.io/. Replace username with your GitHub username.

In his book, Andrew Etter encourages creating static websites and using static site generators because of how simple the process can be. A static site generator, like Jekyll, combines your Markdown files and your Jekyll template and creates a functional website. It also automatically updates your site when you make changes to your files or template. 

#### Host your resume
1. Open up your site's repository on your browser.
2. Go to the repository's "Settings" tab.
3. Go to the "Pages" section.
4. Under the "Source" section, select the **"/(root)"** folder so that your site is built from the master branch.  
![Source Settings](/images/pagesSettings.png)  
5. When setting up Jekyll, an "index.md" file is automatically added to your files. Click on this file.
6. Click the pencil icon to start editing this file.  
![Edit index.md](/images/editIndex.png)  
7. Replace the contents of this file with your Markdown formatted resume.
8. Scroll to the bottom of the page and click the "Commit changes" button.
9. In the _config.yml file, add the following line so that your Markdown files are rendered as GFM on your GitHub Pages site.
    ~~~
    markdown: GFM
    ~~~

    _NOTE: You are free to delete any settings that you do not need in  the  config.yml file._
10. Repeat step 8 for your _config.yml changes.

_NOTE: There are a lot of files that were automatically created when setting up Jekyll (e.g., about.md, 404.html, posts folder). Feel free to remove these, you will not need them to host your resume._

One of Andrew Etter's principles is to build a website for your documentation rather than having it in PDF format. By creating a site for your resume, you will be able to access it easily and update it instantly. For example, you might want to edit your resume when you get a new job or when you've acquired new skills. 

#### Adding a Jekyll template
1. Open up your site's repository on your browser.
2. Go to the repository's "Settings" tab.
3. Go to the "Pages" section.
4. Under the "Theme Chooser" section, click the "Change theme" button.
5. The previous step should have opened up a new page where you can browse for some themes.
6. Once you have selected a theme you like, click the "Select theme" button to apply it to your site.

_NOTE: There is a link under the ["More Resources"](#more-resources) section where you can view more Jekyll themes._

![](/images/giphy.gif)

### More Resources
- [GitHub Flavored Markdown (GFM) Tutorial](https://github.github.com/gfm/)
- [Modern Technical Writing by Andrew Etter](https://www.amazon.ca/Modern-Technical-Writing-Introduction-Documentation-ebook/dp/B01A2QL9SS)
- [GitHub](https://github.com/)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Jekyll Installation Guide](https://jekyllrb.com/docs/installation/)
- [Jekyll Themes](https://jekyllrb.com/docs/themes/)

### Authors and Acknowledgements
Thanks to my group members Andy Tan, Koye Fatoki, Michael Bathie, and Tuan Le Dinh for their help in reviewing this document. Credits to the author [orderedlist](https://github.com/orderedlist) and other contributors for the Jekyll theme [Minimal Theme](https://github.com/orderedlist/minimal). 

### FAQ
1. Why is Markdown better than a word processor?  

Markdown is more versatile and portable. For example, you can create notes, technical documentation, and websites using Markdown. You can also easily open Markdown files using any application, from Notepad to a specific Markdown editor, like Atom.  

2. Why is my resume not showing up?  

Make sure that you have set up Jekyll for your site and that your resume is in the "index.md" file. You should also make sure that your site is being built on the correct location - see step 4 in the ["Host your resume"](#host-your-resume) instructions. 

It is also good to note that new changes may take a while to show up in your site, so wait a few minutes and then refresh your site. 
