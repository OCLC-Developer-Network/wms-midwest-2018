# A Beginner's Guide to Working with WorldShare APIs
## WMS Midwest Meeting 2018 - API Workshop
### Tutorial Part 2 - Setting Up Your Project & Version Control

1. We're going to use git to control versioning of our code, and host our code repositories on GitHub. First, create an empty repository on [github.com](https://github.com/) for your code.
	1. Click "New repository"
	2. Title your repository "wms-midwest-2018"
	3. Check the box next to "Initialize this repository with a README"
	4. Click "Create repository"
2. In a terminal window, change into the following directory:
```bash
$ cd /your-bitnami-installation-directory/apache2/htdocs
```
3. Enter this command to clone the repository you just created, substituting your GitHub username for `your-github-username`:
```bash
$ git clone https://github.com/your-github-username/wms-midwest-2018.git
```
4. You should now have a subdirectory called `wms-midwest-2018` with an empty README.md file in it.
```bash
$ cd wms-midwest-2018/
$ ls
README.md
```
5. Next, we're going to run a quick test to make sure you can make updates to your repository.
	1. Open README.md in your text editor.
	2. Make a change - any change - and save it.
	3. Back in your terminal window, run this command:
	```bash
	$ git status
	```
	You should see output like this:
	```bash
	On branch master
	Your branch is up-to-date with 'origin/master'.
	Changes not staged for commit:
	  (use "git add <file>..." to update what will be committed)
	  (use "git checkout -- <file>..." to discard changes in working directory)
		modified:   README.md
	no changes added to commit (use "git add" and/or "git commit -a")
	```
	4. Now, stage the changes to commit to your repository:
	```bash
	$ git add --all
	```
	5. Commit the changes:
	```bash
	$ git commit -m "a message about your commit"
	```
	6. Push the changes to your repository:
	```bash
	$ git push origin master
	```
	7. In your browser, head back to your GitHub repository at https://github.com/your-github-username/wms-midwest-2018, and you should see the changes you just made to your README file.

**[on to Part 3](tutorial-03.md)**

**[back to Part 1](tutorial-01.md)**