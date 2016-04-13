This repository contains the source files of the website for the German book API-Design. The website is based on:

* [Jekyll](http://jekyllrb.com) that transforms Markdown into static websites
* [Lanyon](https://github.com/poole/lanyon) that is a theme built on top of Poole

# Instructions

    $ jekyll build // Build static websites
    $ jekyll serve // Run locally (Change the baseurl to '' in the config file.)
    
    $ git add -f _site && git commit -m "foo bar"
    $ git subtree push --prefix _site origin gh-pages