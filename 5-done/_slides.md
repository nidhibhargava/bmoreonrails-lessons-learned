!SLIDE bullets
#Including help with [tomdoc](http://tomdoc.org/)

    @@@ coffeescript
    # Allows Hubot to speak many languages.
    #
    # speak me <phrase> - Detects the language 'phrase' is written in, then
    #                     sends back a spoken version of that phrase in its native
    #                     language.

!SLIDE bullets
#serving web requests

    @@@ coffeescript
    module.exports = (robot) ->
      robot.router.get "/hubot/version", (req, res) ->
        res.end robot.version

## [connect](https://github.com/senchalabs/connect) is on your side

!SLIDE bullets
# not quite working yet

 * introduced in 2.1.4
 * doesn't seem to play well with hipchat's adapter

## example would be to serve what localup is listening to

!SLIDE bullets

 * some interesting community scripts
     * ambush = remembers stuff, finds users
     * cloudapp = replaces drops w/ direct links
     * coin = flip
     * conversation = good idea, bad implementation
     * keep-alive = pings heroku apps
     * squeezebox (that's mine! not in a release yet)
     
!SLIDE

# Biiiii!
## i'm [@kylefritz](http://twitter.com/kylefritz) also on [github](http://github.com/kylefritz)
## i work at [localup](http://localup.com)
## you can copy off [our hubot](http://github.com/localup/robot)
     
