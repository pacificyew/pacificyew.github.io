---
layout: post
title: EDCI 336 - Website Construction
categories: [content, demo]
published: true

---
<img src="/assets/jekyllreflection/jekyll.png" align="right" width="330px"/>
This website is no longer in its infancy. This post outlines the process by which I created this blog.

### Homebrew

I don't really have much coding experience. Most of my data crunching was done in MATLAB in my undergrad. I had a course in Fortran, but those skills dont really translate to useful languages that are actually used today. The most useful thing i learned was navigating my computer using bash. Creating and deleting files, editing documents, and writing programs from the command line.<img src="/assets/jekyllreflection/homebrew.png" align="right" width="230px"/>UNIX based computers do this with a "terminal" program, Windows computers have DOS and whatever they call their command line. This is basically where my knowledge ended before this program. Anyone who is looking at this post for advice, look elsewhere; I basically just banged my head against it for a couple months.[^1]

Homebrew is a free open-source package manager that operates from command line on UNIX-based operating systems. It was created in 2009. I used Homebrew to install jekyll and its dependancies as well as other useful software that I didnt know existed before this. Homebrew installs into ``/usr/local`` by default. Hit ``Cmd + Shift + .`` to see otherwise hidden folders in Finder. Dont delete any of them for no reason though, apple hid them for a reason. Running
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
in Terminal will install Homebrew. The [Homebrew webiste](https://brew.sh/) contains analytics data, programs, changelogs etc. Homebrew was necessary for installing Jekyll which is the main compiler for the website. After all the programs necessary for jekyll were installed, I haven't really used Homebrew much.

### Jekyll[^2]

Jekyll is a program that compiles websites. It is written in Ruby by Github founder Tom Preston-Werner. A host of volunteers maintains the software, and its most stable release was 4.2.0 in 2020. Detailed instructions for its installation are on [their website](https://jekyllrb.com/docs/). If you are running the latest operating systems of MacOS, I think it will probably work as advertised. For the rest of us stuck in late 2015, Jekyll only works with a particular version of Ruby installed (>2.5.0). Newer versions for whatever reason dont like being installed. I had issues with OpenSSH not being the right version. I don't honestly remember what I did to get everything to install properly but forums are your friend. People with actual modern computers probably won't have the issues I did since

>"Jekyll requires Ruby v2.5.0 or higher. macOS Big Sur 11.x ships with Ruby 2.6.3. Check your Ruby version using ruby -v."

I mostly followed the instructions on the [Jekyll website](https://jekyllrb.com/docs/installation/macos/) for the installation. Once set up, define a folder that you want to permanently be the website folder, then hit 

```
$ gem install bundler jekyll
$ jekyll name-of-new-website
$ cd name-of-new-website
$ bundle exec jekyll serve
```
The last line here hosts the website locally and updates every time you make a change to it. You can turn off your internet and work on it remotely. To view it in your browser go to `localhost:4000`.

### Github

Now there needs to be some way to host the website. [Github pages](https://pages.github.com/) does this for free as long as you can keep your website to under 1 gb. Github is also open-source software. I have no idea where they get money from but it doesn't seem to be advertising. Get a Github account and then install git and any other dependancies you might need using Homebrew. What you need to do is clone a folder on your computer to a repository on Github. To get a nice URL for your website like `github-username.github.io`, create a repository of the same name. Go to the `pages` section of settings for that repo, and enable Github Pages.
<br>

![fsdf](/assets/jekyllreflection/github.png)
<br>
Ok, now there needs to be an easy way of updating the repo straight from your computer where you edit it. You do this by cloning a folder to your repo in terminal. Get the URL of the desired repo by hitting the `code` button on it page on Github, then in terminal
```
$ cd /where-you-want-site
$ git clone URL-from-Github name-of-website-folder
```
Then drag and drop the contents of the other website folder into this new one. If permissions are set correctly for you to push straight onto the main branch of the repo then you can submit changes by hitting
```
$ cd /where-you-want-site
$ git add -A
$ git commit -m "desciption of any changes made"
$ git push
```
Wait 30 minutes, and Github will be hosting your website at `https://github-username.github.io`

The other thing I did to get a jump start on the blog is to populate my empty website with one of the templates listed on [http://jekyllthemes.org/](http://jekyllthemes.org/). I used [Forever Jekyll](https://github.com/forever-jekyll/forever-jekyll) as stated in the footer of this website, but this theme has its issues. I've definitely had to tailor it to my liking. To populate a repo, you can copy-paste the contents or fork it.

### Troubleshooting

Most of the personalization I did to the website I 've been doing by trial and error. I'll make a couple changes to the `_includes` html files and see what it does. I managed to add the [Trees of BC](https://pacificyew.github.io/TreesofBC) navigation header which works when I host the website locally but now when I let Github Pages compile it. 

This brings me to the main troubleshooting point which is that Github Pages doesn't do everything that you might want it to. It only hosts static sites, and any plugins you might want to add probably won't work. If found this out the hard way by creating some really nice maps for my tree project which ended up not working because they required a plugin called leaflet. A complete list of dependancy versions for jekyll compatible with Pages is [found here](https://pages.github.com/versions/). To remedy the problem with the maps, I found that you could really easily make google maps with markers and then link them to a website page as such:
```
<iframe 
  width="720"
  height="500"
  frameborder="0" style="border:0"
  src="https://www.google.com/maps/d/embed?mid=1StAOnbgdOCSCagiKEdqfr10P4phAsUqK">
</iframe>
```

This brings me to another point. Posts for jekyll are written in Markdown which is, for my purposes at least, a simplified version of html. You can take snippets of html (most of which I find by trolling forums) and put them straight into your markdown blog post. For the same of demonstration, an identical post to this one is also posted on the blog. This way, you can see which symbols do what. This post is a good example because I integrate some pictures, manipulate the text alignment, add hyperlinks and mess around with the text a bit.

### Plans for the Future

I want to really personalize this blog because I'm going to use it for a long time. If the [Trees of BC](https://pacificyew.github.io/TreesofBC) wasn't 404'ed, the information I've compiled during my tree project would be visible there. Its actually all written, I just can't figure out why Pages doesn't like it. I want a whole other page of posts to be listed on this page with a post for each variety of tree. Having one static website host two separate blogs is quite difficult and I won't get to it any time soon, but I think it would work really well.

I also want to spice up the visuals a bit. Right now everything is white and boring. I would love cool patterns down the margins on the sides or maybe pictures in the background.

[^1]: Vítor Galvão, Mike McQuaid, Synoli. (2019). "Homebrew Logo".
[^2]: Tom Preston-Werner. (2020). "Jekyll Logo". CC BY 4.0
