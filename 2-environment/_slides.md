!SLIDE  fullscreen middle
![](medium.png)
# the medium is the `msg`

!SLIDE
#hey hubot...
    @@@ coffeescript
    module.exports = (robot) ->
      robot.respond /what time is it/i, (msg) ->
        msg.send "Game time."
      robot.respond /what time is it\!/i, (msg) ->
        msg.send "GAME TIME!!"
        
!SLIDE
#WOAH! i thought this was a javascript meetup?

!SLIDE

## coffeescript

    @@@ coffeescript
    module.exports = (robot) ->
      robot.respond /what time is it/i, (msg) ->
        msg.send "Game time."
<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>
<br/><br/><br/><br/><br/><br/><br/><br/>
        
!SLIDE

## coffeescript

    @@@ coffeescript
    module.exports = (robot) ->
      robot.respond /what time is it/i, (msg) ->
        msg.send "Game time."

## is basically javascript

    @@@ javascript
    module.exports = function(robot){
      robot.respond(/what time is it/i, function(msg){
        msg.send("Game time.")
        });
    }

!SLIDE
#one second regex review

    @@@ coffeescript
      robot.respond /crank ?it/i, (msg) ->
        #zeroth match is entire string matched
        dosomething()
        
      robot.respond /(queue ?up|pandora ?me) (.+)/i, (msg) ->
        #second match not first
        dosomethingWith(msg.match[2])
        
      robot.respond /vol \+?(\-?\d+)/i, (msg) ->
        dosomethignWithInt(msg,parseInt(msg.match[1]))

!SLIDE
#`respond` vs `hear`
    @@@ coffeescript
    module.exports = (robot) ->
      robot.respond /want to hang out/i, (msg) ->
        msg.send 'NO!'

    module.exports = (robot) ->
      robot.hear /disassemble/i, (msg) ->
        msg.send 'NO DISASSEMBLE!'

!SLIDE
# useful `hear`

    @@@ coffeescript
    # Allow Hubot to show what's lurking behind a CloudApp link.
    robot.hear /(https?:\/\/cl.ly\/[A-Za-z0-9]+)(\/[^\/]+)?/i, (msg) ->
      #get direct link
      

!SLIDE
#adapter variables
    @@@ coffeescript
    #from hipchat adapter
    bot.onMessage (channel, from, message) ->
      author = (self.userForName from) or {}
      author.name = from unless author.name
      author.reply_to = channel
      author.room = self.roomNameFromJid(channel)
      hubot_msg = message.replace(mention, "#{self.robot.name}: ")
      self.receive new Robot.TextMessage(author, hubot_msg)

##check out [your adapter](https://github.com/hipchat/hubot-hipchat/blob/master/src/hipchat.coffee)

    @@@ coffeescript  
    class Robot.Message
      constructor: (@user, @done = false) ->
    class Robot.TextMessage extends Robot.Message
      constructor: (@user, @text) ->
        super @user
    #the messsage gets attached to the *msg*, therefore we have
    "#{msg.message.user.name} and #{msg.message.user.room}"


!SLIDE
#adapter variable examples
    @@@ coffeescript
    robot.respond /say something boring/i, (msg) ->
      m=msg.message
      msg.send "well #{m.user.name}, you told me" +
               "to '#{m.text}' in #{m.user.room} room"

    robot.hear /looser/i, (msg) ->
      m=msg.message
      msg.send "@#{m.user.name} only loosers call people loosers"

!SLIDE
#images get linked in

    @@@ coffeescript
    robot.respond /.*(sproc|sql|stored proc).*/i, (msg) ->
        msg.send "http://imgs.xkcd.com/comics/exploits_of_a_mom.png"

!SLIDE
# convenient random method
    @@@ coffeescript
    ackbars = [
      "http://dayofthejedi.com/wp-content/uploads/2011/03/171.jpg",
      "http://dayofthejedi.com/wp-content/uploads/2011/03/152.jpg",
      "http://farm6.staticflickr.com/5250/5216539895_09f963f448_z.jpg"
    ]

    robot.respond /\(?t(ra|ar)p\)?/i, (msg) ->
      msg.send msg.random ackbars
