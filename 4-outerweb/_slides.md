!SLIDE fullscreen middle
![](internet.jpg)
#doing interesting things

!SLIDE
#GET POST PUT DEL HEAD

 * `msg` has  [scoped-http-client](https://github.com/technoweenie/node-scoped-http-client) attached as `http`
 
## this means it's super duper easy to make web requests

!SLIDE
#get with a query string

    @@@ coffeescript
    robot.respond /(image|img)( me)? (.*)/i, (msg) ->
      imageMe msg, msg.match[3], (url) ->
        msg.send url
        
    imageMe = (msg, query, cb) ->
      msg.http('http://ajax.googleapis.com/ajax/services/search/images')
        .query(v: "1.0", rsz: '8', q: query, safe: 'active')
        .get() (err, res, body) ->
          images = JSON.parse(body)
          images = images.responseData.results
          if images.length > 0
            image  = msg.random images
            cb "#{image.unescapedUrl}#.png"

!SLIDE
#you can set headers and go nuts
    @@@ coffeescript
    _cmd = (msg,what,cb) ->
      data=
        "id":1,
        "method":"slim.request",
        "params":[process.env.SQUEEZE_BOX_PLAYER_ID,what]
      json=JSON.stringify(data)
      _login msg, (cookie) ->
        msg.http("http://mysqueezebox.com/jsonrpc.js")
          .header("content-type","application/json")
          .header("content-length",json.length)
          .header("cookie", cookie)
          .post(json) (err,res,body) ->
            cb(err,res,body) if cb?

!SLIDE
# pro-tip: understand it's callback driven
    @@@ coffeescript
    robot.respond /(image|img)( me)? (.*)/i, (msg) ->
      imageMe msg, msg.match[3], (url) ->
        msg.send url
    
    imageMe = (msg, query, cb) ->
      msg.http('http://ajax.googleapis.com/ajax/services/search/images')
        .query(v: "1.0", rsz: '8', q: query, safe: 'active')
        .get() (err, res, body) ->
          images = JSON.parse(body)
          images = images.responseData.results
          if images.length > 0
            image  = msg.random images
            cb "#{image.unescapedUrl}#.png"

!SLIDE

# you can save stuff
![](disk.jpg)

!SLIDE
# it's goes into the `brain.data`

    @@@ coffeescript
    robot.respond /add station (.*) (.*)/i, (msg) ->
      msg.send "ok, i'll add #{msg.match[1]} w/ url #{msg.match[2]}"
      robot.brain.data.stations ?={}
      robot.brain.data.stations[msg.match[1]]=msg.match[2]
      
!SLIDE
# and get it back

    @@@ coffeescript
    robot.respond /play (.*)/i, (msg) ->
      robot.brain.data.stations ?={}
      url = robot.brain.data.stations[msg.match[1]]
      if url
        _cmd msg, ['playlist','play',url,msg.match[1]]
        msg.send "playing #{msg.match[1]}"
      else
        msg.send "don't know #{msg.match[1]}"

    robot.respond /stations/i, (msg) ->
      robot.brain.data.stations ?={}
      for station, url of robot.brain.data.stations
        msg.send "#{station} #{url}"
