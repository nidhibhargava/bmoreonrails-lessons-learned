!SLIDE bullets
# intermission: gotchas
![](trap.jpg)

!SLIDE bullets
#whitespace

    @@@ coffeescript
    # this is a code example of incompatible whitespace

<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>
<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>

    @@@ coffeescript
    # watch your tabs: use spaces (soft-tabs)
!SLIDE bullets
#package.json
    @@@ javascript
    {
        "name": "localup hubot",
        ...
        "dependencies": {
            "hubot-hipchat": "1.0.3",
            "hubot": "2.1.3",
            "hubot-scripts": "2.0.6",
            "soupselect": "0.2.0",
        }
    }
## this is your brain on drugs


!SLIDE
#hubot versions: 2.1.3 != 2.1.4
##and hipchat adapter no like 2.1.4


!SLIDE
#hubot versions: 2.1.3 != 2.1.4
##and hipchat adapter no like 2.1.4

    @@@ javascript
    dependencies": {
      "hubot-hipchat": ">= 1.0.3",
      "hubot": ">= 2.0.1", //but apparently not 2.1.4 :-/
      ...
    }
