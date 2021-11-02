## Hosting a Resume in GitHub Pages

### Purpose
This README will describe the practical steps on how to host and format a resume using the following software stack:  
* Markdown
* Markdown editor: VSCode with the Markdown Preview Enhanced extension
* GitHub Pages
* Jekyll  

Each step will also be related to the general principles of Technical Writing that were outlined in Andrew Etter's book _Modern Technical Writing_.

### Prerequisites
1. Write a resume written using GitHub Flavored Markdown (GFM), which is GitHub's version of the Markdown syntax.
2. Create or login to your GitHub account.
3. Install the following:
    - Visual Studio Code
    - Jekyll

There are resources in the "More Resources" section to help you set up these prerequisites.

### Instructions
#### Creating your site's repository
By creating a new repository, you will have a place where you can store your site's source files. This is where your resume's Markdown file will be.  
1. In the top-left corner of the homepage of GitHub, select the "New" button to create a new repository. 
![Add New Repository](/images/createNewRepo.PNG)
2. Use the following format for your repository name: [username].github.io. 
![New Repository Form](/images/newRepoForm.PNG)
Using the image above as an example, the "Repository name" field will have **faith-deleon.github.io**.
3. Set it as a public repository.
4. Complete the repository creation by clicking the "Create Repository" button.

#### Clone your repository
By cloning your repository, you will be able to have access to your files locally on your own device. VSCode also has UI for source control which will help us connect to our repository. There, we will be able to add and edit our files.  
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

#### Set up Jekyll
1. While your project is open in VSCode, open up the terminal by selecting "Terminal"->"New Terminal" from the menubar. You can also use the shortcut CTRL + `.
![Open Terminal](/images/openTerminal.PNG)
2. In the terminal, enter the following command to create your Jekyll site:
    ~~~
    jekyll new --skip-bundle
    ~~~
    _NOTE: Make sure you have installed Jekyll and its dependencies._  
    This step should have created the following files:
    ![After Jekyll New](/images/afterJekyllNew.PNG)
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
        Enter the following commands separately:
        ~~~
        git add .
        git commit -m "<Commit message>"
        ~~~
    - **VSCode:**
        1. In the source control tab, select the three dots to view all Git options.
        ![VSCode Stage and Commit](/images/vscodeStageCommit.PNG)
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
        ![VSCode Stage and Commit](/images/vscodeStageCommit.PNG)
        2. Select "Push".

After these steps, your site will be published at the following link: https://username.github.io/. Replace username with your GitHub username.

#### Host your resume
1. Open up the repository for your site on your browser.
2. Go to the repository's "Settings" tab.
3. Go to the "Pages" section.
4. In the "Source" section, select the "/(root)" folder so that your site is built from the master branch.
![Source Settings](/images/pagesSettings.PNG)
5. When setting up Jekyll, an "index.md" file is automatically added to your files.
6. Click the pencil icon to start editing this file.
![Edit index.md](/images/editIndex.PNG)
7. Replace the contents of this file with your Markdown formatted resume.
8. Scroll to the bottom of the page and click the "Commit changes" button.
9. In the _config.yml file, add the following line so that your Markdown files are rendered as GFM on your GitHub Pages site.
    ~~~
    markdown: GFM
    ~~~

    _NOTE: You are free to delete any settings that you do not need in  the  config.yml file._
10. Repeat step 8 for your _config.yml changes.

_NOTE: There are a lot of files that were automatically created when setting up Jekyll (e.g., about.md, 404.html, posts folder). Feel free to remove these, you will not need them to host your resume._

### More Resources
- [GitHub Flavored Markdown (GFM) Tutorial](https://github.github.com/gfm/)
- [Modern Technical Writing by Andrew Etter](https://www.amazon.ca/Modern-Technical-Writing-Introduction-Documentation-ebook/dp/B01A2QL9SS)
- [GitHub](https://github.com/)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Jekyll Installation Guide](https://jekyllrb.com/docs/installation/)
- [Jekyll Themes](https://jekyllrb.com/docs/themes/)

### Authors and Acknowledgements
- [Minimal Theme by orderdedlist](https://github.com/orderedlist/minimal)

### FAQs
1. Why is Markdown better than a word processor?
Markdown is more versatile and portable. For example, you can create notes, technical documentation, and websites by using Markdown. You can also easily open Markdown files using any application, from Notepad to a specific Markdown editor, like Atom.
2. Why is my resume not showing up?
Make sure that you have set up Jekyll for your site and that your resume is in the "index.md" file. You should also make sure that your site is being built on the correct location - see step 4 in the "Host your resume" instructions.