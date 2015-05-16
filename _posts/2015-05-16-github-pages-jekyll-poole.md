---
layout: post
title: Github Pages, Jekyll, Poole
---

Two years have rolled by without a post to my [blog](http://scriptogr.am/richie) at [Scriptogram](http://scriptogr.am/). Scriptogram is (was !) fun. The ease of use (markdown & dropbox) & the minimalism hooks you to it. Its not easy getting away from scriptogram - I dont want to and will not kill it. But the urge to experiment has been too much and here I come - with a lot of skepticism & fear.

The desire to take the Github leap was inspired by these posts;

- [https://pages.github.com/](https://pages.github.com/)
- [http://24ways.org/2013/get-started-with-github-pages/](http://24ways.org/2013/get-started-with-github-pages/)
- [http://jekyllrb.com/docs/quickstart/](http://jekyllrb.com/docs/quickstart/)

### 15th May 2015
I spend hours breaking my head trying to come to terms with the dependencies. Ruby.. aaargh ... 1 am ... I'm off to bed.

### 16th May 2015

Pray. Take a deep breath. Plunge.

Install the following -

1. Ruby Installer http://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.1.6.exe
2. Development Kit - http://dl.bintray.com/oneclick/rubyinstaller/DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe

From git bash type `gem install jekyll`

And then we run into ...



    Fetching: fast-stemmer-1.0.2.gem (100%)
    ERROR:  Error installing jekyll:
    The 'fast-stemmer' native gem requires installed build tools.

    Please update your PATH to include build tools or download the DevKit
    from 'http://rubyinstaller.org/downloads' and follow the instructions
    at 'http://github.com/oneclick/rubyinstaller/wiki/Development-Kit'

So I add "C:/DevKit" to the PATH.

But same message again.

Okay I missed this. Should have done these before trying to install Jekyll;

1. `cd C:DevKit`
2. `ruby dk.rb init`


`[INFO] found RubyInstaller v1.9.3 at C:/Ruby193`
`[INFO] found RubyInstaller v2.1.6 at C:/Ruby21`
    
`Initialization complete! Please review and modify the auto-generated`
`'config.yml' file to ensure it contains the root directories to all`
`of the installed Rubies you want enhanced by the DevKit.``

Okay.. now run

    ruby dk.rb install

But now we run into ..

    [ERROR] Unable to find RubyGems in site_ruby or core Ruby. Please
    install RubyGems and rerun 'ruby dk.rb install'.


[https://github.com/rubygems/rubygems/issues/630](https://github.com/rubygems/rubygems/issues/630) saves me.

[afffsdd](https://github.com/afffsdd) 's casual remark - *"But when I remove - C:/jruby-1.7.4 it goes along without a hitch,"* - saves the day. 

So, `C:/Ruby193` in the config.yml file must be the problem.

Remove that entry.

Now run `ruby dk.rb install` 

    [INFO] Updating convenience notice gem override for 'C:/Ruby21'
    [INFO] Installing 'C:/Ruby21/lib/ruby/site_ruby/devkit.rb'



Now lets try `gem install jekyll`

Yesssss !!!!!! Woohoo !!!


Now I go through the Jekyll docs to set up the blog. Uh oh ... A huge lump in my throat. Its back to some loafing around in google and then you come across a precious jewel called **poole**. Poole saves you the trouble of doing the blog setup from scratch. 

- [How I Created a Beautiful and Minimal Blog Using Jekyll, Github Pages, and poole](http://joshualande.com/jekyll-github-pages-poole/)
- [Poole](http://demo.getpoole.com/)

I download the repo as a zipped file from [github - poole](https://github.com/poole/poole) and copy the files to my github.io repo.

Fingers crossed ...

    $ jekyll serve
    Configuration file: d:/richie-blog/richielionell.github.io/_config.yml
    Source: d:/richie-blog/richielionell.github.io
       Destination: d:/richie-blog/richielionell.github.io/_site
      Generating...
    done.

Brilliant !!!

Time to transfer my posts from Scriptogram and launch http://richielionell.github.io/

