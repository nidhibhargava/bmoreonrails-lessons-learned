!SLIDE
![](hubot.png)
# Hubot @ baltimore.js
## [j.mp/hubot](http://j.mp/hubot)
## [hubot-bjs.heroku.com](http://haii-hubot.heroku.com/)

!SLIDE bullets full-page
# Haiiiii!
## i'm [@kylefritz](http://twitter.com/kylefritz)
## go here: [http://j.mp/hubot](http://j.mp/hubot)

!SLIDE fullscreen middle
![](how-works.png)

!SLIDE bullets
#You'll need

 * [node.js](http://nodejs.org/)
 * [heroku toolbelt](https://toolbelt.heroku.com/)
 * [hubot template](https://github.com/github/hubot/downloads)

## OMG this is easy now

!SLIDE
# Try it locally

    $ cd your-robot 
    $ npm install
	# will spit & curse
    $ bin/hubot
	# more spitting & cursing
	# press enter!
	Hubot> hubot image me kittens

!SLIDE
#get it live

  1. [choose an adapter](https://github.com/github/hubot/wiki)
  1. turn your template into a git repo
  1. create *cedar stack* heroku app
  1. push hubot & configure variables with `heroku config:add SETTING=value`
  1. verify your heroku account (cc-req'd) and add redis
  1. start the worker with `heroku ps:scale app=1`

!SLIDE
#for deploy details

 1. check the [wiki](https://github.com/github/hubot/wiki/Deploying-Hubot-onto-Heroku)
 1. if you have the heroku toolbelt, skip to *creating git repo*

## hit me on [twitter](http://twitter.com/kylefritz) for more help

!SLIDE
#fun part:
#make hubot yours

!SLIDE bullets
#community scripts

 * shop at [hubot-scripts](http://github.com/github/hubot-scripts)

## be sure it's in the [release](https://github.com/github/hubot-scripts/tags) you pick

!SLIDE
# `hubot-scripts.json`

    [
    "ambush.coffee",
    "cloudapp.coffee",
    "coin.coffee",
    "gemwhois.coffee",
    ...
    ]

!SLIDE bullets
#write your own 
## (very easy)
 * copy an existing script into your `scripts` folder
 * modify & test locally
