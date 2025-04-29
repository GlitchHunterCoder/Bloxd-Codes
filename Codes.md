# Codes

This is a collection of codes which i have either made or found, all placed here,
they are split into 3 parts
- Code Blocks, codes which only needs a code block
- World Code, codes which live in world code, and may also need code blocks to function
- Board Code, uses of `press to ...` signs to make codes
in each of these, they will have a title and code attached, each code is unrelated to another unless stated otherwise



## Code Blocks
### Meta Readers
#### Book metadata
```js
myStr = api.getStandardChestItems([thisPos[0],thisPos[1]+1,thisPos[2]]);

console.log(toString(myStr[0]))
```
#### Better Book Reader
```js
pageindex=0
chestslot=0
p = api.getMoonstoneChestItemSlot(myId, chestslot)
p2 = p.attributes
p3 = p2.customAttributes 
p4 = p3.pages
p5 = p4[pageindex]
console.log(p5)
```
#### Book Reader + KeyWord Replacer \(credits to `aits`\)
```js
systemowner = "Aits/undefined"
version = "1.p3"
pnotes = "Added revamp of IsleBox to now use books, added RichWrite environment for user-friendly and useful writing"
tillconway = "As of writing the code for 1.p3, 84 more people must join the official isleos server until Conways Game of Life will be added (zero if arthur adds getBlockRect)"
year = Math.round(api.now() / 31557600000 + 1970)
month = Math.round(api.now() / 2629800000 / year*12)-1
months = ["January", "February", "March", "April", "June", "July", "August", "September", "October", "November", "December"]
pageindex=0
q = "getMoonstoneChest"
q += "ItemSlot"
p = api[q](myId, 0)
p2 = p.attributes
p3 = p2.customAttributes 
p4 = p3.pages
p5 = p4[pageindex]
aq = "getEnt"
aq += "ityName"
temptext = p5
step0 = p5.replace(/@ats/gi, "COMMANDS: remove pipes for functionality\n@|ats: returns all ats\n@|year: returns current year\n@|month: returns current month\n@|owner: returns the owner of the system (likely undefined)\n@|whoami: returns current user\n@|version: returns system version\n@|notes: returns latest patch notes\n@|tillcon: gives the number of players to join the isleos server until Conways game of Life will be added without getBlockRect")
step1 = step0.replace(/@year/gi, year)
step2 = step1.replace(/@month/gi, months[month-1])
step3 = step2.replace(/@owner/gi, systemowner)
step4 = step3.replace(/@whoami/gi, api[aq](myId))
step5 = step4.replace(/@version/gi, version)
step6 = step5.replace(/@notes/gi, pnotes)
step7 = step6.replace(/@tillcon/gi, tillconway)
```
#### Book to One Line Converter (minified)
```js
eval((Book=$=>{var e,a=api.getStandardChestItems([thisPos[0],thisPos[1]+1,thisPos[2]])[$],r=Object.values(a),t=Object.values(r[2]),t=t[0],l=Object.values(t),s="";for(let v=0;v<10;v++){var u=l[0][v],u=u.replace(/\n/g,"");""!=u&&(s+=u)}return a=0,r=0,t=0,l=0,u=0,s})(0));
```
#### Different Block Meta Types
```js
console.log(api.getMetaInfo("temp"))
console.log(api.getHeldItem(myId))
console.log(api.getEmptyChunk())
console.log(api.getChunk([0,0,0]))
```
#### Book Writer
```js
console.log(api.getMoonstoneChestItemSlot(myId,0))

console.log({"customAttributes":{"pages":["","","","","","","","","",""],"author":"FISHING-SIM-SERVER"},"customDisplayName":"SaveData"})

api.setMoonstoneChestItemSlot(myId, 0, "Book", 1, {"customAttributes":{"pages":["","","","","","","","","",""],"author":""},"customDisplayName":"SaveData","customDescription":"DO NOT REMOVE OR MOVE"})
```
#### Book Evaluator
```js
p = api.getStandardChestItems([thisPos[0],thisPos[1]+1,thisPos[2]])[0]

p2 = p.attributes
p3 = p2.customAttributes 
p4 = p3.pages
p5 = ""
for(let i = 0;i<10;i++){
  p5 += p4[i]
}
eval(p5)
```
### Ban Machines Code Block
#### Book Banner
```js
var a = api.getStandardChestItems([thisPos[0],thisPos[1]+1,thisPos[2]])[0];
var b = Object.values(a)
var b1 = b[2]
var c = Object.values(b1)
var c = c[0]
var d = Object.values(c)
var d = d[0][0]
a = 0
b = 0
c = 0
e = d.replace(/\n/g, "")

f = 2 * 999999999999999999999999999999999999999999999999999
api.forceRespawn(api.getPlayerId(e), [f, 0, 0])
```
### Global
Global variables are variables which can be referenced by different code blocks
#### Global Variable Example \(2 codes\)
```js
test="testing"
```
and
```js
console.log(test)
```
this isnt anything new, what is new is this...
#### Global Lists \(String Elements only, Outdated Method\)
initialise \(execute once at start of server session\)
```js
List = [1,2,3];
ListStore=String(List)
```
Execute
```js
//getter
var List = ListStore.split(",")

//Code involving List

//sender
ListStore=String(List)
```
It works because its triggered, it stores the list as a string, and so packaging a list as a variable, to send off.

when another code block is triggered, it gets the packaged list variable, and unpacks it back to a list to use

\(This was made when lists couldnt be Global, That has now changed\)

## World Code
#### Timer \(1000 seconds\)
```js
a=Date.now()
function tick(dt){
  if(Date.now()-a>1000){
    a=Date.now()
    //code
  }
}
```
## Board Code

## Other
### Metadata
#### Schematic Metadata
```json
a="illegals>&æWþþ{"persisted":{"chestStr":"[{\"name\":\"Apple block\",\"amount\":999,\"attributes\":{\"customAttributes\":{\"pages\":[\"\",\"\",\"\",\"\",\"\",\"\",\"\",\"\",\"\",\"\"],\"author\":\"nightops\",\"changeTime\":1738808482237},\"customDescription\":\"by nightowl\",\"customDisplayName\":\"dTomato blockd\"}},{\"name\":\"Compass\",\"amount\":null,\"attributes\":{\"customAttributes\":{\"target\":[928,null,null]},\"customDescription\":\"points to (928, NaN, NaN)\"}},{\"name\":\"Compass\",\"amount\":null,\"attributes\":{\"customAttributes\":{\"target\":[null,null,null]},\"customDescription\":\"points to (NaN, NaN, NaN)\"}},{\"name\":\"Double barrel\",\"amount\":null,\"attributes\":{\"customAttributes\":{\"shotsLeft\":9000000000}}},{\"name\":\"AK-47\",\"amount\":null,\"attributes\":{\"customAttributes\":{\"shotsLeft\":-1}}},{\"name\":\"AWp\",\"amount\":null,\"attributes\":{\"customAttributes\":{\"shotsLeft\":99}}},{\"name\":\"Minigun\",\"amount\":null,\"attributes\":{\"customAttributes\":{\"shotsLeft\":9000000000}}},{\"name\":\"book\",\"amount\":null,\"attrTittes\":{\"customAttributes\":{\"pages\":[\"gvdj\",\"\",\"\",\"\",\"\",\"\",\"\",\"\",\"\",\"\"],\"author\":\"Turtl3\",\"changeTime\":1738259561292},\"customDescription\":\"by Arthur\",\"customDisplayName\":\"Title\"}},null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null]"}}"
```
another
```json
{"persisted":{"shared":{"text":"api.setItemSlot(myId, api.getSelectedInventorySlotI(myId), \"Code block\", 1, attributes?: ItemAttributes, tellClient = true)","uncensoredText":"api.setItemSlot(myId, api.getSelectedInventorySlotI(myId), \"Code block\", 1, attributes?: ItemAttributes, tellClient = true)","textSize":0},"author":"_eu8VhYXV7hM8u41oGGZG","builder":"_eu8VhYXV7hM8u41oGGZG"}}
```

