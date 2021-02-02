# Commands for Nightbot and Streamelements to get CSGO elo, last matches and last stats from faceit 
Commands for the Nightbot and Streamelements chat bots to get CSGO elo, last matches and last stats, from faceit platform. Intended to use on stream chats like Twitch ones.


## How to

If Nightbot or Streamelements is already present in your chat room, you just have to **copy the desired command line and paste into your channel chat**.

Before pasting the command line review if the command has the name you want (!elo, !last, !stats) you can change it by whatever you want (!csgoelo, !lastmatches, !laststats).

**Replace YOUR_FACEIT_USER with your faceit user id. Watch out, the faceit user Id is case sensitive**, copy it from faceit.

#### This command already exists on my chat

You need to delete the previous command; in Nightbot this would be `!delcom !elo` (to remove the !elo command) and in Streamelements it would be `!command del !elo`.

## Examples for Nightbot

*Elo command (command: !elo)*

`!addcom -cd=5 !elo $(eval const api = $(urlfetch json http://api.faceit.myhosting.info:81/?n=YOUR_FACEIT_USER); if (api.error) {api.message;} else { '$(user), my elo is '+ api.elo +' (Lvl: '+ api.level +')' })`

*Last games report (command: !last)*

`!addcom -cd=5 !last $(eval const api = $(urlfetch json http://api.faceit.myhosting.info:81/?n=YOUR_FACEIT_USER); if (api.error) {api.message;} else { '$(user) my last matches -> ' + api.report; })`

*Last game stats (command: !stats)*

`!addcom -cd=5 !stats $(eval const api = $(urlfetch json http://api.faceit.myhosting.info:81/?n=YOUR_FACEIT_USER); if (api.error) {api.message;} else { '$(user) my last match stats -> ' + api.last_match })`

## Examples for Streamelements

*Elo command (command: !elo)*

`!command add !elo ${user} my elo is $(urlfetch http://api.faceit.myhosting.info:81/?n=YOUR_FACEIT_USER&f=plain&l=en&o=elo)`

*Last games report (command: !last)*

`!command add !last ${user} these are my last matches $(urlfetch http://api.faceit.myhosting.info:81/?n=YOUR_FACEIT_USER&f=plain&l=en&o=report)`

*Last game stats (command: !stats)*

`!command add !stats ${user} stats from my last match $(urlfetch http://api.faceit.myhosting.info:81/?n=YOUR_FACEIT_USER&f=plain&l=en&o=stats)`




## Examples to get data from any faceit user in your chat (eg: !elo s1mple), for Nightbot

*Elo command (usage: !checkelo s1mple)*

`!addcom -cd=5 !checkelo $(eval const api = $(urlfetch json http://api.faceit.myhosting.info:81/?n=$(touser)); if (api.error) {api.message;} else { '$(user), $(touser) elo is '+ api.elo +' (Lvl: '+ api.level +')' })`

*Last games report (usage: !checklast s1mple)*

`!addcom -cd=5 !checklast $(eval const api = $(urlfetch json http://api.faceit.myhosting.info:81/?n=$(touser)); if (api.error) {api.message;} else { '$(user) last $(touser) matches -> ' + api.report; })`

*Last game stats (usage: !checkstats s1mple)*

`!addcom -cd=5 !checkstats $(eval const api = $(urlfetch json http://api.faceit.myhosting.info:81/?n=$(touser)); if (api.error) {api.message;} else { '$(user) last $(touser) match stats -> ' + api.last_match })`


## Other commands requested by users

*Full data*

`!command add !stats ${user} stats from my last match $(eval const api = $(urlfetch json http://api.faceit.myhosting.info:81/?n=YOUR_FACEIT_USER); if (api.error) {api.message;} else { '$(user) --> Lvl '+ api.level +': '+ api.elo +' << '+ api.report +' << '+ api.trend +' << Last game stats: ' + api.last_match })`


## Language

I've included translations for some language, to get it translated add "l=YOUR_LANGUAGE_CODE&" in the url.

*URL should look like this*

`http://api.faceit.myhosting.info:81/?l=YOUR_LANGUAGE_CODE&n=YOUR_FACEIT_USER&f=plain&o=stats)`

Available languages are, at this moment: es (for spanish), en (for english), no (for norwegian)

## More info and support

https://community.nightdev.com/t/customapi-faceit-last-games-matches-api/28513
