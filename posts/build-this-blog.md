.. title: Build this blog.
.. date: 2019-01-09
.. tags: nikola, python, github, blog
.. type: text

# Why Nikola, why Python?
Good question, relatively simple answer. Both Python and Nikola are the easiest tools you can 
use when creating a simple and static blog. The exception being the application of Ruby and 
Jekyll when using github pages. That being said, and as much as I do enjoy Ruby, I prefer to 
keep my languages and frameworks consistent professionally and personally. The added benefit of 
Github Pages being able to host static content at no cost (and also not having to maintain a 
server) seal the deal on this setup for me. 

## What do I need?
Im going to make the assumption you are running a Linux machine. If you are not, you have other 
things you should be addressing before you worry about creating a blog. If you are, then you'll 
need to get these packages: ```nikola ghp-import2 python-markdown git```. These packages are 
available in most distro repositories, as well as through pip. The common practice when working 
on projects such as this is to also get ```virtualenv``` and install your libraries/software in 
the virtual environment, but a development VM or your base OS will be fine as well. 

## Set up your Github repository.
This is straightforward for anyone who has used github before. If not, there are tutorials on 
Github showing you how to set up your "Github Pages" (username.github.io). Dont worry about 
initializing the repo, the readme, or ignore file. We will do that in the next step. All you 
need to do is create the repository.

## Hold my beer.
In the next ~7min you're going to have a functioning blog on Github. Its so easy you're going 
to wonder why you havent done it before. So easy in fact, I'm going to give the instructions in 
a numbered list.

1. Use Nikola to iniate the blog (which creates a directory). This will populate the folder 
with all the framework you need to get started.
```nikola init <username>.github.io```
2. Change into the new folder and initialize it as a github repository.
```git init .```
```git remote add origin git@github.com:<user>/<repository>.git```
3. Open ```conf.py``` in your editor of choice (which is vim, right?). Make sure the options 
you gave when initializing nikola are correct, and make sure your github settings are as 
follows:
<pre>```GITHUB_SOURCE_BRANCH = 'src'
GITHUB_DEPLOY_BRANCH = 'master'
GITHUB_REMOTE_NAME = 'origin'
GITHUB_COMMIT_SOURCE = True```</pre>
4. Create the ```.gitignore``` file and populate it with ```cache .doit.db __pycache__ 
output```
5. Create a test post with ```nikola new_post -e```. This will open your text editor of choice 
(vim, right?) and pre-populate it with the necessary data. Enter whatever text you wish, make 
sure its saved in the ```posts/``` directory, and save it.
6. Build your site with ```nikola build``` and correct any errors.

## WITNESS ME!
If you followed the previous steps correctly we can prop up a nikola test server, view our 
results, and when satisfied push it to Github.
```nikola serve --browser```
This will run a local server and open your default browser to your blog's landing page. Viola! 
Hit CTRL+C to shut down the server.
Now, when you're ready to go live simply use Nikola's built in tool ```nikola github_deploy``` 
to send it off to Github. You will be prompted for your username/password if not token'ed up.

# Enjoy
P.S. - You can download themes with ```nikola theme -i <theme>``` and use them by adding them 
in your ```conf.py```
