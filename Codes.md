# Codes

This is a collection of codes which i have either made or found, all placed here,
they are split into 3 parts
- Code Blocks, codes which only needs a code block
- World Code, codes which live in world code, and may also need code blocks to function
- Board Code, uses of `press to ...` signs to make codes
in each of these, they will have a title and code attached, each code is unrelated to another unless stated otherwise
if i dont know who made the code \(credits to ____\) will be left

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
#### Book Banner \(Credit to aits for idea\)
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
#### Book Executer Special \(Credit to ____, idk who it was\) \(3 codes\)
Book Data Getter
```js
api.broadcastMessage("Admin "+api.getEntityName(myId)+" is trying to execute "+
"some code", {color:"#ff0000"});
let p=api.getPlayerTargetInfo(myId).position
let x,y,z,_break;
for(x=-1;x<=1;x++)for(y=-1;y<=1;y++)for(z=-1;z<=1;z++){
if(_break)break;
let np=[p[0]+x,p[1]+y,p[2]+z];
if(api.getBlock(np[0],np[1],np[2])=="Chest"){
let item=api.getStandardChestItems(np)[0];
if(item==null || item.name!="Book"){
api.sendMessage(myId,"No book found in chest. Got more than one chest nearby?")
_break=true;
break;
}
if(item.attributes.customAttributes.author!=api.getEntityName(myId)){
throw "Operation Aborted because you are not the author of the book";
}
current_code=item.attributes.customAttributes.pages;
current_admin=myId;
current_confirm=false;
current_running=true;
api.sendMessage(myId,"perform further operations")
_break=true;
break;
}
}
if(!_break){
api.sendMessage(myId,"No chest found. Are you using press to execute?")
}
```
Page Selector
```js
function pageNum(id) {
id++;
if(id==1)return "1st";
if(id==2)return "2nd";
if(id==3)return "3rd";
return id+"th";
}
try{
current_admin;current_code;current_confirm;current_running;
if(!current_running)throw null;
}catch{
api.sendMessage(myId, "no code is being executed rn");
throw "Operation Aborted because there is nothing to see"
}
api.sendMessage(myId, "viewing "+api.getEntityName(current_admin)+"'s code")
let pageId=api.getSelectedInventorySlotI(myId);
api.sendMessage(myId, "viewing "+pageNum(pageId)+" page");
api.log([current_code[pageId]]);
```
Code Executer
```js
function pageNum(id) {
id++;
if(id==1)return "1st";
if(id==2)return "2nd";
if(id==3)return "3rd";
return id+"th";
}
try{
current_admin;current_code;current_confirm;current_running;
if(!current_running)throw null;
}catch{
api.sendMessage(myId, "no code is being executed rn");
throw "Operation Aborted because there is no code to run"
}
if(current_admin!=myId) {
api.sendMessage(myId, "You are not the admin trying to execute code");
throw "Operation Aborted because you are not the one who wrote the code";
}
//current_running=false
api.broadcastMessage("Admin "+api.getEntityName(myId)+" is executing "+
"some code", {color:"#ff0000"});
current_code.forEach(function(ele,i){
try{eval(ele)}catch(e){throw "Error executing "+pageNum(i)+" page:"+e;}
})
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
### TopRightHelper
#### Data Getter \(Credit to `Binary`\)
```js
const playerIds = api.getPlayerIds();
const numPlayers = api.getNumPlayers();
const heldItem = JSON.stringify(api.getHeldItem(myId));
const standingBlocks = api.getBlockTypesPlayerStandingOn(myId).join(', ');

const entityNames = playerIds.map(id => {
    const name = api.getEntityName(id);
    const position = api.getPosition(id).map(coord => parseInt(coord));
    const mobileStatus = api.isMobile(id) ? "[Mobile]" : "[PC]";
    return `${name} (${id}) ${position.join(' ')} ${mobileStatus}`;
}).join('  _____  ');

api.sendTopRightHelper(myId, "star", `Coded by Binary _______________________________________________________ <<<<<---Player Ids--->>>>>  Your ID: ${myId} _____ All IDs: ${playerIds.join(', ')} ______________________________________________________ <<<<<---Blocks/Items--->>>>> Standing on: ${standingBlocks} _____ Held item/block: ${heldItem} ________________________________________________________ <<<<<---Player-Info--->>>>> Num of players: ${numPlayers} _____ Player name, id, position, mobile/pc: ${entityNames} ______________________________________________________`, {
    duration: 10,
    width: 500,
    height: 500,
    color: "#33c7d8",
    iconSizeMult: 5,
    textAndIconColor: "#FFFFFF",
    fontSize: "10px"
}); 
```
#### Complex Helper \(Credit to ____\)
```js
// Display "Hi" message on the right side of the screen
function displayHiMessage(playerId) {
  // Configuration for the message display
  const messageConfig = {
    duration: 5,        // Display for 5 seconds
    width: 100,         // Width of the message box
    height: 50,         // Height of the message box
    color: "#3366FF",   // Background color
    iconSizeMult: 1,    // Icon size multiplier
    textAndIconColor: "#FFFFFF", // Text color
    fontSize: "18px"    // Font size
  };

  // Display the message to the player
  api.sendTopRightHelper(
    playerId,           // Player's entity ID
    "info",             // Icon to display (use what's available in your game)
    "Hi",               // Message text
    messageConfig       // Display configuration
  );
}

// This function can be called directly by your game's event system
function onPlayerJoin(playerId) {
  // Set player health to max
  api.setHealth(playerId, 100);

  // Display welcome message
  displayHiMessage(playerId);
}

// Direct implementation for when a player enters the game
// This assumes myId is defined in your game environment
api.setHealth(myId, 100);
displayHiMessage(myId);
```
### Custom Styling
#### Super Rank Styling
```js
api.broadcastMessage([{str:"[⚡Super] ", style:{color:"Yellow", fontWeight:"0", fontSize:"14px", fontStyle:"", opacity:1}},{str:"GlitchHunter: ", style:{color:"Red", fontWeight:"0", fontSize:"14px", fontStyle:"", opacity:1}},{str:"hi", style:{color:"White", fontWeight:"0", fontSize:"14px", fontStyle:"", opacity:1}}])
```
#### Big Text
```js
api.broadcastMessage([{str:"Sub", style:{color:"White", fontWeight:"0", fontSize:"100px", fontStyle:"", opacity:1}}])
```
#### Styling Code \(Credit to ____\)
```js
function styTxt(text) {
    let fn_ = styTxt
    if (!fn_.tags_) {
        fn_.tags_ = {
            c: "color",
            w: "fontWeight",
            st: "fontStyle",
            s: "fontSize",
            o: ["opacity", Number],
        }
        fn_.resetTag_ = "r"
        fn_.regex_ = new RegExp(`(\\\\<)|<(${Object.keys(fn_.tags_).join("|")}|${fn_.resetTag_})(?: *)([^>]+)?>`, "g")
    }

    if (text == "") return [""]
    const res = [], currStyle = new Map()
    let currText = "", lastI = 0

    for (let { index, 0: full, 1: escape, 2: tag, 3: value } of [...text.matchAll(fn_.regex_), { index: text.length }]) {
        currText += text.slice(lastI, index)
        lastI = index + (full?.length ?? 0)

        if (escape) {
            currText += "<"
            continue
        }

        if (currText) {
            res.push(currStyle.size ? { str: currText, style: Object.fromEntries(currStyle) } : currText)
            currText = ""
        }

        if (index == text.length)
            continue

        if (tag == fn_.resetTag_) {
            currStyle.clear()
        } else {
            let prop = fn_.tags_[tag], parser
            if (Array.isArray(prop))
                [prop, parser] = prop
            if (value)
                currStyle.set(prop, parser?.(value) ?? value)
            else
                currStyle.delete(prop)
        }
    }
    return res
}

// Styled Text Display
api.sendMessage(myId, styTxt("hello <c red><w bold>Red,bold <w>not bold <c#00F>blue <st italic>Italic<w 100>Thin <w900><s 30px>Big<o 0.2>Fad<cyellow>ed<r>Reset all\\<c red>escaped"))

//Styled Text Raw Formatted
console.log(styTxt("hello <c red><w bold>Red,bold <w>not bold <c#00F>blue <st italic>Italic<w 100>Thin <w900><s 30px>Big<o 0.2>Fad<cyellow>ed<r>Reset all\\<c red>escaped"))

//Styled Text Raw
console.log("hello <c red><w bold>Red,bold <w>not bold <c#00F>blue <st italic>Italic<w 100>Thin <w900><s 30px>Big<o 0.2>Fad<cyellow>ed<r>Reset all\\<c red>escaped")
```
### Ray Casting
#### Ray Casting
```js
onPlayerClick = (pid,alt) => {
heldItem=api.getHeldItem(pid)["name"]
if(heldItem=="Wood Axe") {
cdir = api.getPlayerFacingInfo(pid)["dir"];
cpos = api.getPlayerFacingInfo(pid)["camPos"];
found=false
for (let i = 0; ((i < 100)&&(found==false)); i++) {
block = api.raycastForBlock(cpos, cdir)
if(!(block==null)){
block = block["adjacent"]
found = true
block[0]+=0.5
block[2]+=0.5
api.setPosition(pid,block)
}
cpos=[cpos[0]+(cdir[0]*5),cpos[1]+(cdir[1]*5),cpos[2]+(cdir[2]*5)]
}  
}
}
```
#### Laser
```js
onPlayerUsedThrowable = (id, item, itemId) => {
    if (item !== "Arrow") return;
    /*laser variables, can be replaced in the code with constants if you want to remove these*/
    const amount = 8; //laser length
    const spreadDist = 2 //distants between each particle 
    const logRayResults = false // set to true if you want to log the entities found, in chat
    const beamStrength = 70 // set the damage of the beam
    const beamTexture = "bubble" // set the texture of the beam
    /* laser code */
    let facing = api.getPlayerFacingInfo(id).dir;
    let pos = api.getPosition(id);
    
    api.broadcastSound("cannonFire3", 1, 5, {
        playerIdOrPos: id
        , maxHearDist: 15
    });
    for (let i = 0; i < amount; i++) {
        
        const magnitude = Math.sqrt(
            facing[0] ** 2 + facing[1] ** 2 + facing[2] ** 2
        );
        const normalized = [
    facing[0] / magnitude
    , facing[1] / magnitude
    , facing[2] / magnitude
];
        
        
        api.playParticleEffect({
            dir2: [0, 0, 0]
            , dir1: [facing[0], facing[0], facing[2]]
            , pos1: [pos[0] += ((i + spreadDist) * facing[0]), pos[1] += ((i + spreadDist) * facing[1]), pos[2] += ((i + spreadDist) * facing[2])]
            , pos2: [pos[0] += ((i + spreadDist) * facing[0]), pos[1] += ((i + spreadDist) * facing[1]), pos[2] += ((i + spreadDist) * facing[2])]
            , texture: beamTexture
            , minLifeTime: 0.05 + (i / 100)
            , maxLifeTime: 0.05 + (i / 100)
            , minEmitPower: 2
            , maxEmitPower: 2
            , minSize: 0.5
            , maxSize: 3 - (i / 10)
            , manualEmitCount: 10
            , gravity: [0, -2, 0]
            , colorGradients: [
                {
                    timeFraction: 0
                    , minColor: [255, 81, 0, 1]
                    , maxColor: [253, 3, 3, 1],
                    //rgb(255, 81, 0)
        }
    , ]
            , velocityGradients: [
                {
                    timeFraction: 0
                    , factor: 1
                    , factor2: 1
        , }
    , ]
            , blendMode: 1
        , });
        
        let xyz = [
    pos[0] + normalized[0] * i
    , pos[1] + normalized[1] * i
    , pos[2] + normalized[2] * i
];
        
        /*collision detection, size varries based on spread distance, change that if you dont like it */
        let hit = api.getEntitiesInRect([xyz[0] - spreadDist, xyz[1] - 2, xyz[2] - spreadDist], [xyz[0] + spreadDist, xyz[1] + 2, xyz[2] + spreadDist]);
        if (logRayResults) api.log("ray results:", hit);
        //applies damage
        for (let target of hit) {
            if (target !== id) {
                api.attemptApplyDamage({
                    eId: id
                    , hitEId: target
                    , attemptedDmgAmt: beamStrength
                    , withItem: "Red Ceramic"
                    , attackDir: facing
                    , showCritParticles: true
                    , reduceVerticalKbVelocity: false
                });
            }
        }
    }
};
```
### Illegal Blocks / Item Getter 
#### Block Placer \(Mostly, Unloaded Doesnt Work\)
Intialiser
```js
i=2
```
Iterator
```js
while(true){
api.setBlockRect([40,25,i],[40,25,i],api.blockIdToBlockName(i));
i+=1
}
```
#### Item \(Mostly, Unloaded Doesnt Work\)
Intialiser
```js
b=2
```
Iterator
```js
while(true){
  c=""+b
  api.editItemCraftingRecipes(myId,c,[{requires:[{items:["2"],amt:null}],produces:null,station:"Potion Table"}])
  b+=1
}
```
## World Code
### Simple
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
### Mods
#### Gravity
```js
let gravityId = new Set()
let lastParticleTime = 0
let downdraftCooldown = {}

onPlayerJoin = (playerId) => {
  api.giveItem(playerId, "Iron Spade", 1, { customDisplayName: "Downdraft" })
}

onPlayerClick = (playerId, x, y, z, face, itemName) => {
  let held = api.getHeldItem(playerId)
  if (
    held &&
    held.name === "Iron Spade" &&
    held.attributes?.customDisplayName === "Downdraft"
  ) {
    let now = api.now()
    if (downdraftCooldown[playerId] && now - downdraftCooldown[playerId] < 1000) {
      return
    }
    let wasFloating = gravityId.has(playerId)
    downdraftCooldown[playerId] = now
    api.applyImpulse(playerId, 0, -15, 0)
    if (wasFloating) {
      api.playSound(playerId, "glass3", 1, 1, { playerIdOrPos: playerId })
    }
    gravityId.delete(playerId)
  }
}

onPlayerAltAction = (playerId) => {
  let held = api.getHeldItem(playerId)
  if (
    held &&
    held.name === "Iron Spade" &&
    held.attributes?.customDisplayName === "Downdraft"
  ) {
    return
  }
  if (gravityId.has(playerId)) {
    gravityId.delete(playerId)
    api.playSound(playerId, "glass2", 1, 1, { playerIdOrPos: playerId })
  } else {
    gravityId.add(playerId)
    api.playSound(playerId, "sweep6", 1, 1, { playerIdOrPos: playerId })
  }
}

tick = () => {
  let now = api.now()
  for (let playerId of api.getPlayerIds()) {
    if (gravityId.has(playerId)) {
      api.applyImpulse(playerId, 0, 2.2, 0)
      if (now - lastParticleTime >= 100) {
        let pos = api.getPosition(playerId)
        let x = pos[0]
        let y = pos[1] + 1
        let z = pos[2]
        api.playParticleEffect({
          dir1: [-0.3, -0.3, -0.3],
          dir2: [0.3, 0.3, 0.3],
          pos1: [x - 0.5, y, z - 0.5],
          pos2: [x + 0.5, y + 1, z + 0.5],
          texture: "critical_hit",
          minLifeTime: 0.2,
          maxLifeTime: 0.5,
          minEmitPower: 1.2,
          maxEmitPower: 2,
          minSize: 0.2,
          maxSize: 0.35,
          manualEmitCount: 10,
          gravity: [0, -10, 0],
          colorGradients: [
            { timeFraction: 0, minColor: [0, 100, 255, 1], maxColor: [0, 255, 255, 1] }
          ],
          velocityGradients: [
            { timeFraction: 0, factor: 1, factor2: 1 }
          ],
          blendMode: 1
        })
      }
    }
  }
  if (now - lastParticleTime >= 100) {
    lastParticleTime = now
  }
}
```
#### Random Movement
```js
// Initial position of the "Finish Block" (replace "TNT" with any valid block name if needed)
let finishBlockPos = [0, 1, 0];

// List of possible directions to move (left, right, forward, back)
const directions = [
    [-1, 0, 0], // left
    [1, 0, 0],  // right
    [0, 0, -1], // forward
    [0, 0, 1]   // back
];

// Define the movement magnitude multiplier
const movementMagnitude = 1;

// List of possible block names to randomly place as a trail
const blockTypes = [
    "White Concrete"
];

tick = () => {
    // Randomly select a direction
    const randomDirectionIndex = Math.floor(Math.random() * directions.length);
    const direction = directions[randomDirectionIndex];

    // Calculate the new position by multiplying the direction by the movement magnitude
    const newX = finishBlockPos[0] + direction[0] * movementMagnitude;
    const newY = finishBlockPos[1]; // Keep the Y the same to move on the ground
    const newZ = finishBlockPos[2] + direction[2] * movementMagnitude;

    // Check if the new position is in a loaded chunk
    if (api.isBlockInLoadedChunk(newX, newY, newZ)) {
        // Randomly select a block type for the trail
        const randomBlockIndex = Math.floor(Math.random() * blockTypes.length);
        const randomBlock = blockTypes[randomBlockIndex];

        // Place the randomly selected block at the old position
        api.setBlock(finishBlockPos[0], finishBlockPos[1], finishBlockPos[2], randomBlock);

        // Set the new position to "TNT" or any other valid block name
        api.setBlock(newX, newY, newZ, "Finish Block");

        // Update the finishBlockPos to the new position
        finishBlockPos = [newX, newY, newZ];
    }
};
```
### PvP Codes
#### Amputation Code \(Credit to `MrChestplate`\) \(NO CREDIT TO HIS LICENSE HE PUT IN CODE, see other for license\)
```js
//License has been moved to the Wall Of Shame
dicss=["TorsoNode", "HeadMesh", "ArmRightMesh", "ArmLeftMesh","LegLeftMesh", "LegRightMesh"]
scl={}
s=4
function onPlayerDamagingOtherPlayer(
    attackingPlayer,
    damagedPlayer,
    damageDealt,
    withItem,
    bodyPartHit,
    damagerDbId,
){
	iddx=api.getSelectedInventorySlotI(attackingPlayer)
	itm = api.getItemSlot(attackingPlayer,iddx)
	if (itm.attributes.customDescription === "Attack to amputate other players!"){
		
		if (bodyPartHit==="Torso"){
			bodyPartHit="TorsoNode"
		}else{
			bodyPartHit+="Mesh"
			scl[damagedPlayer][bodyPartHit]=[0,0,0]
			api.scalePlayerMeshNodes(damagedPlayer, scl[damagedPlayer])
		}
		
		
		api.applyHealthChange(damagedPlayer, damageDealt)
	}
}
function onPlayerJoin(id){
	scl[id]={}
	for (const dic of dicss){
		scl[id][dic]=[1,1,1]
	}
	api.scalePlayerMeshNodes(id, scl[id])
	api.setItemSlot(id, 0, "Artisan Shears", null, {customDescription: "Attack to amputate other players!", customDisplayName:"Amputation Shear"})
}
```
#### Crystal PvP \(Credit to `MrChestplate`\) \(NO CREDIT TO HIS OBSCURIFICATION see other for original Code ,Mostly Taken Out\)
```js
sos = "cannonFire2";
anchors = {};
function p3(khiyon, chryel, ellody) {
  api.playParticleEffect({dir1: [-1, -1, -1], dir2: [1, 1, 1], pos1: [khiyon - 1, chryel, ellody - 1], pos2: [khiyon + 1, chryel + 1, ellody + 1], texture: "glint", minLifeTime: 0.5, maxLifeTime: 1, minEmitPower: 2, maxEmitPower: 2, minSize: 0.25, maxSize: 0.5, manualEmitCount: 100, gravity: [0, 0, 0], colorGradients: [{timeFraction: 0, minColor: [0, 255, 0, 1], maxColor: [0, 150, 0, 1]}], velocityGradients: [{timeFraction: 0, factor: 1, factor2: 1}], blendMode: 1});
  api.playParticleEffect({dir1: [-1, -1, -1], dir2: [1, 1, 1], pos1: [khiyon - 1, chryel, ellody - 1], pos2: [khiyon + 1, chryel + 1, ellody + 1], texture: "glint", minLifeTime: 0.5, maxLifeTime: 1, minEmitPower: 2, maxEmitPower: 2, minSize: 0.25, maxSize: 0.5, manualEmitCount: 100, gravity: [0, 0, 0], colorGradients: [{timeFraction: 0, minColor: [255, 255, 0, 1], maxColor: [255, 255, 0, 1]}], velocityGradients: [{timeFraction: 0, factor: 1, factor2: 1}], blendMode: 1});
}
tasks = [];
function tick() {
  if (tasks.length > 0) {
    for (i = 0; i < tasks.length; i++) {
      task = tasks[i];
      if (task[0] === 0) {
        coord1 = task[1];
        coord2 = task[2];
        explode(coord1, coord2);
      }
      tasks.splice(i, 1);
    }
  }
}
function explode(jaleesia, taquia) {
  for (x = jaleesia[0]; x < taquia[0]; x++) {
    for (y = jaleesia[1]; y < taquia[1]; y++) {
      for (z = jaleesia[2]; z < taquia[2]; z++) {
        curBlock = api.getBlock(x, y, z);
        if (curBlock !== "Obsidian" && curBlock !== "Bedrock") {
          api.setBlock(x, y, z, "Air");
        }
      }
    }
  }
}
function onPlayerClick(hannha, heleyna) {
  slotidx = api.getSelectedInventorySlotI(hannha);
  itm = api.getItemSlot(hannha, slotidx);
  if (itm !== null) {
    if (itm.attributes.customDisplayName === "Extra Life" && heleyna && !api.getEffects(hannha).includes("Extra Life")) {
      api.applyEffect(hannha, "Extra Life", null, {displayName: "Extra Life", icon: "Gold Spade"});
      api.setItemSlot(hannha, slotidx, "Gold Spade", 0);
    }
  }
  target = api.getPlayerTargetInfo(hannha);
  if (target) {
    blockpos = target.position;
    slotidx = api.getSelectedInventorySlotI(hannha);
    itm = api.getItemSlot(hannha, slotidx);
    if (heleyna) {
      if (target.blockID === 125 && itm.name === "Golden Decoration") {
        api.setBlock(target.position[0], target.position[1], target.position[2], "Dim Lamp On");
      }
    } else {
      if (target.blockID === 124 && itm.name !== "Golden Decoration") {
        anchors[target.position] = 0;
        coord1 = [blockpos[0] - 4, blockpos[1] - 4, blockpos[2] - 4];
        coord2 = [blockpos[0] + 4, blockpos[1] + 5, blockpos[2] + 4];
        api.playSound(hannha, sos, 0.5, 1);
        enties = api.getEntitiesInRect(coord1, coord2);
        damage = 125;
        prot = 0.6;
        for (i = 0; i < enties.length; i++) {
          id1 = enties[i];
          posid1 = api.getPosition(id1);
          if ((api.getPlayerIds().includes(id1) || api.getMobIds().includes(id1)) && api.isAlive(id1)) {
            dist = Math.sqrt(Math.pow(blockpos[0] + 0.5 - posid1[0], 2) + Math.pow(blockpos[1] + 0.5 - posid1[1], 2) + Math.pow(blockpos[2] + 0.5 - posid1[2], 2));
            api.playSound(id1, sos, 0.5, 1);
            force = api.calcExplosionForce(id1, 1, 0.3, 5, [blockpos[0] + 0.5, blockpos[1] + 0.5, blockpos[2] + 0.5], true).force;
            slotidx = api.getSelectedInventorySlotI(id1);
            itm = api.getItemSlot(id1, slotidx);
            if (api.getHealth(id1) - Math.round((-20 * dist + 130) * (1 - prot)) > 5 && !(api.getEffects(id1).includes("Extra Life") || itm.attributes.displayName === "Extra Life")) {
              api.applyHealthChange(id1, -Math.round((-20 * dist + 130) * (1 - prot)), hannha);
            } else if ((api.getEffects(id1).includes("Extra Life") || itm && itm.attributes.displayName === "Extra Life") && api.getHealth(id1) - Math.round((-20 * dist + 130) * (1 - prot)) < 5) {
              poser = api.getPosition(id1);
              if (itm && itm.attributes.displayName === "Extra Life") {
                api.setItemSlot(id1, slotidx, "Gold Spade", 0);
              }
              api.setHealth(id1, 10);
              api.applyEffect(id1, "Health Regen", 4e4, {inbuiltLevel: 2});
              api.setShieldAmount(id1, 20);
              api.playSound(id1, "cashRegister", 1, 1);
              api.removeEffect(id1, "Extra Life");
              p3(poser[0], poser[1], poser[2]);
            } else {
              api.applyHealthChange(id1, -Math.round((-20 * dist + 130) * (1 - prot)), {lifeformId: hannha, withItem: "Dim Lamp On"});
            }
            api.applyImpulse(id1, force[0], force[1], force[2]);
          }
        }
        tasks.push([0, coord1, coord2]);
      } else {
        if (target.blockID === 1004) {
          blockUnder = api.getBlock(blockpos[0], blockpos[1] - 1, blockpos[2]);
          if (blockUnder === "Obsidian") {
            api.setBlock(blockpos[0], blockpos[1], blockpos[2], "Air");
            coords1 = [blockpos[0] - 6, blockpos[1] + 1, blockpos[2] - 6];
            coords2 = [blockpos[0] + 7, blockpos[1] + 7, blockpos[2] + 7];
            coord1 = [blockpos[0] - 4, blockpos[1], blockpos[2] - 4];
            coord2 = [blockpos[0] + 4, blockpos[1] + 4, blockpos[2] + 4];
            enties = api.getEntitiesInRect(coords1, coords2);
            damage = 50;
            prot = 0.6;
            rng = Math.floor(Math.random() * 100) + 1;
            api.playSound(hannha, sos, 0.5, 1);
            for (i = 0; i < enties.length; i++) {
              id1 = enties[i];
              if ((api.getPlayerIds().includes(id1) || api.getMobIds().includes(id1)) && api.isAlive(id1)) {
                api.playSound(id1, sos, 0.5, 1);
                force = api.calcExplosionForce(id1, 1, 0.3, 20, [blockpos[0] + 0.5, blockpos[1], blockpos[2] + 0.5], true).force;
                slotidx = api.getSelectedInventorySlotI(id1);
                itm = api.getItemSlot(id1, slotidx);
                if (api.getHealth(id1) - Math.round(damage * (1 - prot)) > 5 && !(api.getEffects(id1).includes("Extra Life") || itm.attributes.displayName === "Extra Life")) {
                  api.applyHealthChange(id1, -Math.round(damage * (1 - prot)), {lifeformId: hannha, withItem: "Bouncy Purple Bomb"});
                } else if ((api.getEffects(id1).includes("Extra Life") || itm && itm.attributes.displayName === "Extra Life") && api.getHealth(id1) - Math.round(damage * (1 - prot)) < 5) {
                  poser = api.getPosition(id1);
                  api.setHealth(id1, 10);
                  api.applyEffect(id1, "Health Regen", 4e4, {inbuiltLevel: 2});
                  api.setShieldAmount(id1, 20);
                  api.playSound(id1, "cashRegister", 1, 1);
                  api.removeEffect(id1, "Extra Life");
                  p3(poser[0], poser[1], poser[2]);
                } else {
                  api.applyHealthChange(id1, -Math.round(damage * (1 - prot)), hannha);
                }
                api.applyImpulse(id1, force[0] * (rng / 50), force[1] * (rng / 50), force[2] * (rng / 50));
              }
            }
            explode(coord1, coord2);
          }
        }
      }
    }
  }
}
function onPlayerDamagingOtherPlayer(wendra, camillah, raymer) {
  if ((api.getEffects(camillah).includes("Extra Life") || itm && itm.attributes.displayName === "Extra Life") && api.getHealth(camillah) - raymer < 5) {
    poser = api.getPosition(camillah);
    if (itm && itm.attributes.displayName === "Extra Life") {
      api.setItemSlot(camillah, slotidx, "Gold Spade", 0);
    }
    api.setHealth(camillah, 10);
    api.applyEffect(camillah, "Health Regen", 4e4, {inbuiltLevel: 2});
    api.setShieldAmount(camillah, 20);
    api.playSound(camillah, "cashRegister", 1, 1);
    api.removeEffect(camillah, "Extra Life");
    p3(poser[0], poser[1], poser[2]);
  }
}
function onPlayerChangeBlock(tunny, quantavious, chellsee, ajwan, mansoor, madelein, alithea, chrishana) {
  if (mansoor === "Air" && madelein === "Bouncy Bomb Block") {
    blockUnder = api.getBlock(quantavious, chellsee - 1, ajwan);
    if (blockUnder !== "Obsidian") {
      api.setBlock(quantavious, chellsee, ajwan, mansoor);
    }
  }
  if (mansoor.includes("Dim Lamp") && madelein === "Air") {
    api.setBlock(quantavious, chellsee, ajwan, mansoor);
  }
  if (madelein.includes("Dim Lamp")) {
    anchors[[quantavious, chellsee, ajwan]] = 0;
  }
  if (madelein === "Golden Decoration") {
    posers = [[1, 0, 0], [0, 1, 0], [0, 0, 1], [-1, 0, 0], [0, -1, 0], [0, 0, -1]];
    for (i = 0; i < posers.length; i++) {
      p = posers[i];
      if (api.getBlock([quantavious + p[0], chellsee + p[1], ajwan + p[2]]) === "Dim Lamp On") {
        api.setBlock(quantavious, chellsee, ajwan, "Air");
      }
    }
  }
  if (mansoor === "Bouncy Bomb Block" && madelein === "Air") {
    blockpos = [quantavious, chellsee, ajwan];
    blockUnder = api.getBlock(blockpos[0], blockpos[1] - 1, blockpos[2]);
    if (blockUnder === "Obsidian") {
      coords1 = [blockpos[0] - 6, blockpos[1] + 1, blockpos[2] - 6];
      coords2 = [blockpos[0] + 7, blockpos[1] + 7, blockpos[2] + 7];
      coord1 = [blockpos[0] - 4, blockpos[1], blockpos[2] - 4];
      coord2 = [blockpos[0] + 4, blockpos[1] + 4, blockpos[2] + 4];
      enties = api.getEntitiesInRect(coords1, coords2);
      damage = 50;
      prot = 0.6;
      rng = Math.floor(Math.random() * 100) + 1;
      api.playSound(tunny, sos, 0.5, 1);
      for (i = 0; i < enties.length; i++) {
        id1 = enties[i];
        if ((api.getPlayerIds().includes(id1) || api.getMobIds().includes(id1)) && api.isAlive(id1)) {
          api.playSound(id1, sos, 0.5, 1);
          force = api.calcExplosionForce(id1, 1, 0.3, 20, [blockpos[0] + 0.5, blockpos[1], blockpos[2] + 0.5], true).force;
          slotidx = api.getSelectedInventorySlotI(id1);
          itm = api.getItemSlot(id1, slotidx);
          if (api.getHealth(id1) - Math.round(damage * (1 - prot)) > 5 && !(api.getEffects(id1).includes("Extra Life") || itm.attributes.displayName === "Extra Life")) {
            api.applyHealthChange(id1, -Math.round(damage * (1 - prot)), tunny);
          } else if ((api.getEffects(id1).includes("Extra Life") || itm && itm.attributes.displayName === "Extra Life") && api.getHealth(id1) - Math.round(damage * (1 - prot)) < 5) {
            poser = api.getPosition(id1);
            if (itm && itm.attributes.displayName === "Extra Life") {
              api.setItemSlot(id1, slotidx, "Gold Spade", 0);
            }
            api.setHealth(id1, 10);
            api.applyEffect(id1, "Health Regen", 4e4, {inbuiltLevel: 2});
            api.setShieldAmount(id1, 20);
            api.playSound(id1, "cashRegister", 1, 1);
            api.removeEffect(id1, "Extra Life");
            p3(poser[0], poser[1], poser[2]);
          } else {
            api.applyHealthChange(id1, -Math.round(damage * (1 - prot)), tunny);
          }
          api.applyImpulse(id1, force[0] * (rng / 50), force[1] * (rng / 50), force[2] * (rng / 50));
        }
      }
      for (quantavious = coord1[0]; quantavious < coord2[0]; quantavious++) {
        for (chellsee = coord1[1]; chellsee < coord2[1]; chellsee++) {
          for (ajwan = coord1[2]; ajwan < coord2[2]; ajwan++) {
            curBlock = api.getBlock(quantavious, chellsee, ajwan);
            if (curBlock !== "Obsidian" && curBlock !== "Bedrock") {
              api.setBlock(quantavious, chellsee, ajwan, "Air");
            }
          }
        }
      }
    }
  }
}
function onPlayerJoin(shamair) {
  if (api.getPlayerIds().length > 15 && api.getEntityName(shamair) !== "MrChestplate") {
    api.kickPlayer(shamair, "Lobby is Full! Max player count: 10.");
  }
  api.setWalkThroughType(shamair, "Bouncy Bomb Block");
  api.setItemSlot(shamair, 0, "Diamond Sword", null);
  api.setItemSlot(shamair, 1, "Obsidian", 999);
  api.setItemSlot(shamair, 2, "Bouncy Bomb Block", 999, {customDisplayName: "End Crystal", customDescription: "Try Placing it on obsidian and breaking it."});
  api.setItemSlot(shamair, 3, "Cobweb", 999);
  api.setItemSlot(shamair, 4, "Moonstone Orb", 999);
  api.setItemSlot(shamair, 5, "Bread", 999);
  api.setItemSlot(shamair, 6, "Dim Lamp Off", 999, {customDisplayName: "Respawn Anchor", customDescription: "Use Glowstone to charge it."});
  api.setItemSlot(shamair, 7, "Golden Decoration", 999, {customDisplayName: "Glowstone", customDescription: "Charges Respawn Anchor."});
  api.setItemSlot(shamair, 8, "Stone Bow", 1);
  api.setItemSlot(shamair, 10, "Arrow", 999);
  api.setItemSlot(shamair, 9, "Moonstone Pickaxe", 999);
  api.giveItem(shamair, "Gold Spade", 40, {customDisplayName: "Extra Life", customDescription: "With a Twist!"});
  api.setItemSlot(shamair, 46, "Diamond Helmet", null);
  api.setItemSlot(shamair, 47, "Diamond Chestplate", null);
  api.setItemSlot(shamair, 48, "Diamond Gauntlets", null);
  api.setItemSlot(shamair, 49, "Diamond Leggings", null);
  api.setItemSlot(shamair, 50, "Diamond Boots", null);
  api.applyEffect(shamair, "Haste", null, {inbuiltLevel: 5});
  api.sendTopRightHelper(shamair, "info-circle", "Subscribe to @Javeline 947! Tutorial on Youtube!", {duration: 10, width: 500, height: 300, color: "red", textAndIconColor: "red"});
  api.setCantChangeBlockRect(shamair, [14, -20, -19], [-24, 55, 29]);
}
```
### Persistent World Code
#### For Loop Persistent \(World Code + Code Block\)
World Code
```js
cmd=null  //used to make variables at start
i=null  //variable
i1=null  //variable clone, aka the magic way it works
function tick(){
  if(cmd==null){
    start=0  //if no command is running, allow new command to be set
  }
  if(cmd=="for"){
    if(start==0){  //initialisation code, runs only once at start
      i=1  //equivilant of i=1 in for loop
      start=1
    }
    i1=i  //tests code with clone, if it fails, it will try again from this point
    //for loop, start----------------------------------------------------------------
      api.broadcastMessage(String(i1), { color: "red" })  //message number
      if(i1==1000){  //equivilant of i<=1000 in for loop
        cmd=null  //ends code
        ThisErrorIsFineIgnoreErrorMessage  //undefined variable, to cause an error
      }
      i1+=1  //equivilant of i++ in for loop
    //for loop, end----------------------------------------------------------------
    i=i1  //magic, if all the code above executed without interruptions, allow to move to next step
  }
}
```
Code Block
```js
if(start==0){  //if no persistent code is running, allow new code to be set
  cmd="for"
}
```
### Utilitys
#### World Edit World Code \( + Code Block \)
World Code
```js
/* WORLDEDIT WORLD CODE */
let spos = {};
let epos = {};
onPlayerClick = (pId, alt) => {
  let heldItem = api.getHeldItem(pId);
  if ( && heldItem?.name == "Moonstone Axe" && heldItem?.attributes.customDisplayName == "WorldEdit Tool" && heldItem?.attributes.customDescription == "Set EZ WorldEdit Positions") {
    if (alt == true) {
      if (!spos[pId]) {
        spos[pId] = api.getPosition(pId);
        api.log("Starting Position set: " + spos[pId]);
      } else {
        epos[pId] = api.getPosition(pId);
        api.log("Ending Position set: "
          epos[pId]);
      }
    } else {
      delete spos[pId];
      delete epos[pId];
      api.log("Cleared Position Variables");
    }
  }
}
onPlayerChat = (pId, msg) => {
  if (spos[pId] != null && epos[pId] != null && msg.substring(0, 3) == ":f ") {
    let block = msg.substring(3, msg.length);
    api.setBlockRect(spos[pId], epos[pId], block);
    delete spos[pId];
    delete epos[pId];
  }
}
onPlayerLeave = (pId) => {
  if (spos[pId] != null && epos[pId] != null) {
    /* Delete Position Data on Exit */
    delete spos[pId];
    delete epos[pId];
  }
}
```
Code Block to get World Edit Axe
```js
 api.giveItem(myId, "Moonstone Axe", 1, {customDisplayName: "WorldEdit Tool", customDescription: "Set EZ WorldEdit Positions"});
```
#### Helpful Axes
- Wood Axe-tp anywhere u look (up to 150 blocks distance)
- Stone Axe-tp 1 block in the direction u look (use to go thru blocks)
- Iron Axe-Travel Fast in the direction you look
- Gold Axe-Travel Even Faster in the direction you look
- Diamond Axe-Stop In Place (reset velocity)
- Moonstone Axe-Sums up all features
  - Crouch+Alt-Travel Fast at a decent pace
  - Crouch+Normal-Stop In Place
  - Stand+Alt-tp 1 block in the direction u look
  - Stand+Normal-Tp anywhere you look
```js
onPlayerClick = (e, $) => {
  if ("Iron Axe" == (heldItem = api.getHeldItem(e).name) && (cdir = api.getPlayerFacingInfo(e).dir, api.setVelocity(e, 30 * cdir[0], 30 * cdir[1], 30 * cdir[2])), "Diamond Axe" == heldItem && api.setVelocity(e, 0, 0, 0), "Gold Axe" == heldItem && (cdir = api.getPlayerFacingInfo(e).dir, api.setVelocity(e, 100 * cdir[0], 100 * cdir[1], 100 * cdir[2])), "Wood Axe" == heldItem) {
    cdir = api.getPlayerFacingInfo(e).dir, cpos = api.getPlayerFacingInfo(e).camPos, found = !1;
    for (let o = 0; o < 30 && !1 == found; o++) null != (block = api.raycastForBlock(cpos, cdir)) && (block = block.adjacent, found = !0, block[0] += .5, block[2] += .5, api.setPosition(e, block)), cpos = [cpos[0] + 5 * cdir[0], cpos[1] + 5 * cdir[1], cpos[2] + 5 * cdir[2]]
  }
  if ("Stone Axe" == heldItem && (cdir = api.getPlayerFacingInfo(e).dir, cpos = [(cpos = api.getPosition(e))[0] + 1 * cdir[0], cpos[1], cpos[2] + 1 * cdir[2]], Math.abs(cdir[1]) > .9 && (cpos[1] += 1.001 * cdir[1]), api.setPosition(e, cpos)), "Moonstone Axe" == heldItem) {
    if (crouch = api.isPlayerCrouching(e), cdir = api.getPlayerFacingInfo(e).dir, cpos = api.getPlayerFacingInfo(e).camPos, crouch) $ ? api.setVelocity(e, 50 * cdir[0], 50 * cdir[1], 50 * cdir[2]) : api.setVelocity(e, 0, 0, 0);
    else if ($) cdir = api.getPlayerFacingInfo(e).dir, cpos = [(cpos = api.getPosition(e))[0] + 1 * cdir[0], cpos[1], cpos[2] + 1 * cdir[2]], Math.abs(cdir[1]) > .9 && (cpos[1] += 1.001 * cdir[1]), api.setPosition(e, cpos);
    else {
      found = !1;
      for (let t = 0; t < 30 && !1 == found; t++) null != (block = api.raycastForBlock(cpos, cdir)) && (block = block.adjacent, found = !0, block[0] += .5, block[2] += .5, api.setPosition(e, block)), cpos = [cpos[0] + 5 * cdir[0], cpos[1] + 5 * cdir[1], cpos[2] + 5 * cdir[2]]
    }
  }
};
```
#### setTimeOut World Code \( + Code Block Usage\)
World Code \(Minified\)
```js
let ordinary_tick_function,do_next_tick_queue=new Set,timed_functions_queue=[];function tick(t){if("function"==typeof ordinary_tick_function&&ordinary_tick_function(t),do_next_tick_queue.forEach((t=>{"function"==typeof t&&t(),do_next_tick_queue.delete(t)})),timed_functions_queue.length&&timed_functions_queue[0][0]<api.now()){try{timed_functions_queue[0][1]()}catch{}timed_functions_queue=timed_functions_queue.slice(1)}}do_this_next_tick=t=>{"function"==typeof t&&do_next_tick_queue.add(t)},setTimeOut=(t,e)=>{let n=Date.now()+e;"function"==typeof t&&(timed_functions_queue.push([n,t]),timed_functions_queue.sort((([t],[e])=>t-e)))};
```
Code Block Usage
- to delay the execution of a function, use setTimeOut(NOTE that the O is uppercase):
```js
setTimeOut(()=>{
  console.log("this message will be shown after 2 seconds")
}, 2*1000)//number of milliseconds to wait
```
- to perform an action immediately next tick, use do_this_next_tick
```js
do_this_next_tick(
()=>console.log("this message is immediately displayed")
)
```
- to use the ordinary tick function, assign a value to ordinary_tick_function
```js
ordinary_tick_function=()=>{
console.log("this message will be shown once every tick")
}
```
### Rendering
#### Music \( World Code + Code Block \)
World Code
```js
const REF_PITCH = 144.73;

function calcFreq(midiNote) {
    return Math.pow(2, (midiNote - 69) / 12) * 440;
}

function calcRate(midiNote) {
    return calcFreq(midiNote) / REF_PITCH;
}

let notesPlaying = [];

function playSong(playerId, song) {
    notesPlaying = notesPlaying.concat(song
        .map(note => ({
            ...note
            , playerId
        })));
}

tick = (dt) => {
    notesPlaying = notesPlaying.map(note => ({
        ...note
        , time: note.time - dt / 1000
    }));
    let stopIdx = undefined;
    
    for (let i = 0; i < notesPlaying.length; i++) {
        const note = notesPlaying[i];
        if (note.time < 0) {
            api.playSound(note.playerId, "pickUp", note.velocity, calcRate(note.midi));
        } else {
            stopIdx = i;
            break;
        }
    }
    
    stopIdx ??= notesPlaying.length;
    
    notesPlaying = notesPlaying.slice(stopIdx);
}
```
Code Block \("Rickroll Midi File Example"\)
```js
const song = [{"midi":60,"time":0.06979166666666667,"velocity":0.5748031496062992},{"midi":62,"time":0.196875,"velocity":0.6614173228346457},{"midi":65,"time":0.325,"velocity":0.6850393700787402},{"midi":62,"time":0.453125,"velocity":0.7244094488188977},{"midi":74,"time":0.5916666666666667,"velocity":0.2992125984251969},{"midi":69,"time":0.5916666666666667,"velocity":0.5118110236220472},{"midi":62,"time":0.5916666666666667,"velocity":0.47244094488188976},{"midi":46,"time":0.5916666666666667,"velocity":0.5905511811023622},{"midi":65,"time":0.6041666666666666,"velocity":0.4409448818897638},{"midi":69,"time":0.9864583333333333,"velocity":0.5275590551181102},{"midi":65,"time":0.9864583333333333,"velocity":0.4409448818897638},{"midi":62,"time":0.9864583333333333,"velocity":0.48031496062992124},{"midi":50,"time":0.9864583333333333,"velocity":0.3228346456692913},{"midi":46,"time":0.9864583333333333,"velocity":0.6220472440944882},{"midi":60,"time":1.38125,"velocity":0.3700787401574803},{"midi":64,"time":1.3927083333333334,"velocity":0.4566929133858268},{"midi":48,"time":1.3927083333333334,"velocity":0.5275590551181102},{"midi":36,"time":1.4052083333333334,"velocity":0.5118110236220472},{"midi":60,"time":2.160416666666667,"velocity":0.6062992125984252},{"midi":62,"time":2.3,"velocity":0.6141732283464567},{"midi":65,"time":2.428125,"velocity":0.6535433070866141},{"midi":62,"time":2.566666666666667,"velocity":0.6220472440944882},{"midi":64,"time":2.6947916666666667,"velocity":0.4251968503937008},{"midi":60,"time":2.6947916666666667,"velocity":0.5511811023622047},{"midi":67,"time":2.70625,"velocity":0.3858267716535433},{"midi":45,"time":2.7760416666666665,"velocity":0.5433070866141733},{"midi":67,"time":3.089583333333333,"velocity":0.44881889763779526},{"midi":64,"time":3.089583333333333,"velocity":0.4881889763779528},{"midi":45,"time":3.089583333333333,"velocity":0.4645669291338583},{"midi":60,"time":3.1010416666666667,"velocity":0.5984251968503937},{"midi":38,"time":3.484375,"velocity":0.5433070866141733},{"midi":65,"time":3.495833333333333,"velocity":0.4881889763779528},{"midi":64,"time":3.890625,"velocity":0.5590551181102362},{"midi":50,"time":3.902083333333333,"velocity":0.4015748031496063},{"midi":62,"time":4.008333333333334,"velocity":0.3543307086614173},{"midi":60,"time":4.275,"velocity":0.6220472440944882},{"midi":62,"time":4.403125,"velocity":0.6377952755905512},{"midi":65,"time":4.530208333333333,"velocity":0.6456692913385826},{"midi":65,"time":4.797916666666667,"velocity":0.41732283464566927},{"midi":62,"time":4.797916666666667,"velocity":0.4330708661417323},{"midi":58,"time":4.809375,"velocity":0.5275590551181102},{"midi":50,"time":4.809375,"velocity":0.3779527559055118},{"midi":43,"time":4.809375,"velocity":0.5511811023622047},{"midi":31,"time":5.192708333333333,"velocity":0.3700787401574803},{"midi":67,"time":5.319791666666666,"velocity":0.6456692913385826},{"midi":36,"time":5.586458333333334,"velocity":0.4409448818897638},{"midi":64,"time":5.598958333333333,"velocity":0.5275590551181102},{"midi":60,"time":5.598958333333333,"velocity":0.3937007874015748},{"midi":48,"time":5.598958333333333,"velocity":0.5826771653543307},{"midi":62,"time":5.983333333333333,"velocity":0.5984251968503937},{"midi":60,"time":6.110416666666667,"velocity":0.5196850393700787},{"midi":48,"time":6.110416666666667,"velocity":0.5826771653543307},{"midi":72,"time":6.378125,"velocity":0.3464566929133858},{"midi":48,"time":6.378125,"velocity":0.7637795275590551},{"midi":60,"time":6.644791666666666,"velocity":0.6299212598425197},{"midi":48,"time":6.65625,"velocity":0.6929133858267716},{"midi":45,"time":6.9,"velocity":0.6377952755905512},{"midi":67,"time":6.911458333333333,"velocity":0.3543307086614173},{"midi":60,"time":6.911458333333333,"velocity":0.5748031496062992},{"midi":57,"time":6.911458333333333,"velocity":0.3858267716535433},{"midi":52,"time":6.911458333333333,"velocity":0.6062992125984252},{"midi":48,"time":6.911458333333333,"velocity":0.49606299212598426},{"midi":38,"time":7.434375,"velocity":0.6535433070866141},{"midi":65,"time":7.445833333333334,"velocity":0.49606299212598426},{"midi":50,"time":7.445833333333334,"velocity":0.3779527559055118},{"midi":60,"time":8.480208333333334,"velocity":0.6141732283464567},{"midi":62,"time":8.619791666666666,"velocity":0.6456692913385826},{"midi":65,"time":8.747916666666667,"velocity":0.6692913385826772},{"midi":62,"time":8.875,"velocity":0.7165354330708661},{"midi":69,"time":9.014583333333333,"velocity":0.5196850393700787},{"midi":62,"time":9.014583333333333,"velocity":0.47244094488188976},{"midi":46,"time":9.014583333333333,"velocity":0.5826771653543307},{"midi":65,"time":9.026041666666666,"velocity":0.4409448818897638},{"midi":69,"time":9.409375,"velocity":0.5354330708661418},{"midi":62,"time":9.409375,"velocity":0.4566929133858268},{"midi":46,"time":9.409375,"velocity":0.5905511811023622},{"midi":65,"time":9.420833333333333,"velocity":0.47244094488188976},{"midi":60,"time":9.804166666666667,"velocity":0.33858267716535434},{"midi":48,"time":9.804166666666667,"velocity":0.5118110236220472},{"midi":64,"time":9.815625,"velocity":0.4645669291338583},{"midi":36,"time":9.815625,"velocity":0.48031496062992124},{"midi":60,"time":10.583333333333334,"velocity":0.6062992125984252},{"midi":62,"time":10.722916666666666,"velocity":0.6141732283464567},{"midi":65,"time":10.85,"velocity":0.6456692913385826},{"midi":62,"time":10.989583333333334,"velocity":0.6220472440944882},{"midi":60,"time":11.116666666666667,"velocity":0.5511811023622047},{"midi":45,"time":11.186458333333333,"velocity":0.5748031496062992},{"midi":33,"time":11.233333333333333,"velocity":0.4015748031496063},{"midi":64,"time":11.651041666666666,"velocity":0.44881889763779526},{"midi":45,"time":11.651041666666666,"velocity":0.7007874015748031},{"midi":38,"time":11.90625,"velocity":0.5826771653543307},{"midi":65,"time":11.91875,"velocity":0.5748031496062992},{"midi":45,"time":11.91875,"velocity":0.4015748031496063},{"midi":64,"time":12.303125,"velocity":0.5984251968503937},{"midi":50,"time":12.360416666666667,"velocity":0.4094488188976378},{"midi":62,"time":12.430208333333333,"velocity":0.4094488188976378},{"midi":60,"time":12.697916666666666,"velocity":0.6141732283464567},{"midi":62,"time":12.825,"velocity":0.6220472440944882},{"midi":65,"time":12.953125,"velocity":0.6614173228346457},{"midi":62,"time":13.091666666666667,"velocity":0.7086614173228346},{"midi":65,"time":13.23125,"velocity":0.4251968503937008},{"midi":62,"time":13.23125,"velocity":0.4330708661417323},{"midi":50,"time":13.23125,"velocity":0.3937007874015748},{"midi":43,"time":13.23125,"velocity":0.5590551181102362},{"midi":58,"time":13.242708333333333,"velocity":0.5275590551181102},{"midi":31,"time":13.544791666666667,"velocity":0.3937007874015748},{"midi":67,"time":13.754166666666666,"velocity":0.6456692913385826},{"midi":36,"time":13.998958333333333,"velocity":0.4330708661417323},{"midi":64,"time":14.010416666666666,"velocity":0.5196850393700787},{"midi":60,"time":14.010416666666666,"velocity":0.3937007874015748},{"midi":48,"time":14.010416666666666,"velocity":0.5748031496062992},{"midi":62,"time":14.405208333333333,"velocity":0.5984251968503937},{"midi":60,"time":14.533333333333333,"velocity":0.5275590551181102},{"midi":48,"time":14.544791666666667,"velocity":0.5748031496062992},{"midi":48,"time":14.811458333333333,"velocity":0.7637795275590551},{"midi":72,"time":14.811458333333333,"velocity":0.3779527559055118},{"midi":60,"time":15.066666666666666,"velocity":0.6299212598425197},{"midi":48,"time":15.066666666666666,"velocity":0.6850393700787402},{"midi":45,"time":15.322916666666666,"velocity":0.6377952755905512},{"midi":57,"time":15.334375,"velocity":0.3858267716535433},{"midi":52,"time":15.334375,"velocity":0.6220472440944882},{"midi":67,"time":15.345833333333333,"velocity":0.3543307086614173},{"midi":60,"time":15.345833333333333,"velocity":0.5669291338582677},{"midi":48,"time":15.345833333333333,"velocity":0.5039370078740157},{"midi":50,"time":15.85625,"velocity":0.3858267716535433},{"midi":65,"time":15.867708333333333,"velocity":0.4645669291338583},{"midi":38,"time":15.927083333333334,"velocity":0.6456692913385826}];

playSong(myId, song);
```
Extra
[Midi To Code Converter](https://tonejs.github.io/Midi/)
## Board Code

## Other
### Bloxd Internal Code
#### Translation Document \(Credit to ____\)
```json
{    "general": {        "submit": "Submit",        "resume": "Resume",        "create": "Create",        "play": "Play",        "copy": "Copy",        "copied": "Copied",        "playerJoined": "{{name}} joined",        "playerLeft": "{{name}} left",        "go": "Go",        "set": "Set",        "delete": "Delete",        "request": "Request",        "damaged": "damaged",        "joined": "joined",        "attacked": "attacked",        "teleport": "Teleport",        "head": "Head",        "body": "Body",        "legs": "Legs",        "selected": "Selected",        "invite": "Invite",        "disband": "Disband",        "select": "Select",        "no": "No",        "default": "Default",        "global": "Global",        "team": "Team",        "join": "Join",        "full": "Full",        "player": "Player",        "players": "Players",        "cantBuildHere": "Can't build here",        "respawn": "Respawn",        "add": "Add",        "remove": "Remove",        "get": "Get",        "error": "Error",        "cancel": "Cancel",        "continue": "Continue",        "customize": "Customize",        "apply": "Apply",        "choose": "Choose",        "install": "Install",        "accept": "Accept",        "decline": "Decline",        "cape": "Cape",        "nameColour": "Name Colour",        "name": "Name",        "ok": "OK",        "hide": "Hide",        "explore": "Explore",        "timeLeft": "{{time}} left",        "getItNow": "Get It Now!",        "yes": "Yes"    },    "settingsMenu": {        "language": "Language",        "exitGame": "Exit Game",        "exitFullscreen": "Exit Fullscreen",        "general": "General",        "graphics": "Graphics",        "controls": "Controls",        "horizontalChunkLoadDistance": "Horizontal Chunk Load Distance",        "chunkLoadDistanceInfo": "Higher values let you see further, but can cause lag. Decrease if fps is low.",        "verticalChunkLoadDistance": "Vertical Chunk Load Distance",        "musicVolume": "Music Volume",        "soundEffectsVolume": "Sound Effects Volume",        "disableFullscreenMode": "Disable Fullscreen Mode",        "showCoordinates": "Show Coordinates",        "showChunkCoordinates": "Show Chunk Coordinates",        "showFps": "Show FPS",        "disableBunnyHopping": "Disable Bunny Hopping",        "showChat": "Show Chat",        "texturePack": "Texture Pack",        "disableBlockTextureAtlas": "Disable Block Texture Atlas",        "disableBlockTextureAtlasInfo": "Disable if all blocks show as black. Disabling may increase fps. \n\nRequires page refresh to take effect. Texture packs will not work when disabled.",        "texturePackInfo": "Clear for default. Requires page refresh to take effect. Example: {{texturePackUrl}}",        "fieldOfView": "Field Of View",        "useTouchControls": "Use Touch Controls",        "crouchToggle": "Crouch Toggle",        "crouchToggleInfo": "Turn off to only crouch when button is held.",        "touchscreenSensitivity": "Touch Screen Sensitivity",        "mouseSensitivity": "Mouse Sensitivity",        "inviteLink": "Invite Link",        "disableViewBobbing": "Disable View Bobbing",        "disableViewBobbingInfo": "Disable Bobbing animation for player when they are walking or running",        "disableCameraShakeOnDamage": "Disable Camera Shake On Damage",        "customTextureWarning": "Customizing texture packs may break the game",        "reloadPagePopupTitle": "Reload Page",        "reloadPagePopupSubtitle": "You will need to reload page to apply your changes",        "reloadPagePopupConfirm": "Reload",        "loseChangesTitle": "Lose Changes",        "loseChangesSubtitle": "You will lose the changes to your custom texture pack if you select a different texture pack",        "viewDocumentation": "View documentation",        "showFog": "Show Fog",        "fogChunkDistance": "Fog Chunk Distance",        "fogChunkDistanceInfo": "Fog Chunk Distance should be less or equal than Horizontal Chunk Load Distance to be visible",        "keyBindings": "Key Bindings",        "secondAgo": "{{second}} second ago",        "secondsAgo": "{{seconds}} seconds ago",        "minuteAgo": "{{minute}} minute ago",        "minutesAgo": "{{minutes}} minutes ago",        "hourAgo": "{{hour}} hour ago",        "hoursAgo": "{{hours}} hours ago",        "dayAgo": "{{day}} day ago",        "daysAgo": "{{days}} days ago",        "getSuperRankAdditionalDays": "Get {{days}} additional days for {{price}} {{currency}}"    },    "controls": {        "moveForward": "Move Forward",        "moveBackward": "Move Backward",        "moveLeft": "Move Left",        "moveRight": "Move Right",        "run": "Run",        "primaryAction": "Primary Action",        "openInventory/Craft": "Open Inventory / Craft",        "secondaryAction": "Secondary Action",        "dropItem": "Drop Item",        "jump": "Jump",        "crouch": "Crouch",        "pickBlock": "Pick Block (creative)",        "zoom": "Zoom",        "leftClick": "Left Click",        "rightClick": "Right Click",        "middleMouseButton": "Middle Mouse Button",        "shift": "Shift",        "control": "Control",        "backslash": "Backslash",        "space": "Space",        "capsLock": "CapsLock",        "altLeftClick": "Alt+Left Click",        "tab": "Tab",        "shiftLeft": "Left Shift",        "shiftRight": "Right Shift",        "controlLeft": "Left Control",        "controlRight": "Right Control",        "resetBindings": "Reset Bindings",        "sharedBindingsWarning": "This action shares bindings with other actions:",        "mustHaveAtLeastOneBinding": "Must have at least one binding",        "enterNewBinding": "Enter new binding",        "keyIsReserved": "The key you entered is reserved",        "clickToEnterNewBinding": "Click to enter new binding",        "hotBarSlotNumber": "Hotbar slot {{number}}",        "specialAction1": "Special Action 1",        "specialAction2": "Special Action 2",        "reloadGun": "Reload Gun",        "openLobbyLeaderboard": "Open Lobby Leaderboard",        "openCharacterCustomization": "Open Character Customization",        "openSettings": "Open Settings",        "openInviteLink": "Open Invite Link",        "openTasksAndLeaderboard": "Open Tasks And Leaderboard",        "openShop": "Open Shop",        "swapCameraZoom": "Swap Camera Zoom"    },    "homePage": {        "playingAs": "Playing As",        "partnersAndCredits": "Partners And Credits",        "credits": "Credits",        "quickPlay": "Quick Play",        "rejoinLobbyNumber": "Rejoin Lobby {{number}}",        "joinLobbyName": "Join Lobby Name",        "joinLobbyNameInfo": "Join a specific lobby",        "rejoinLobbyNumberInfo": "Join the last lobby you were in.\nInventories and worlds are saved per lobby.",        "quickPlayInfo": "Join a lobby with many players",        "browse": "Browse",        "browseInfo": "View a list of open worlds lobbies",        "createLobby": "Create",        "createLobbyInfo": "Create a lobby",        "enterName": "Enter Name",        "changeNameMinLengthError": "Name must be {{length}} or more characters",        "changeNameMaxLengthError": "Name must be {{length}} or less characters",        "createTitleLobby": "Create {{name}} Lobby",        "playTitle": "Play {{name}}",        "lobbyName": "Lobby Name",        "lobbyNameMustBeNumber": "Name must be number",        "worldsNameCannotBeNumber": "Worlds name cannot be number",        "loadingGame": "Loading Game...",        "recentlyPlayedLobbies": "Recently Played Lobbies",        "joinWorldsLobby": "Join Worlds Lobby",        "discordPlayInfo": "Play with the Discord users in your channel!",        "joinDiscordLobby": "Join Discord World",        "bloxdIngameRules": "Bloxd Rules",        "privacyPolicy": "Bloxd Privacy Policy",        "gameIsUpdating": "Game is updating...",        "signedInWith": "Signed in with: {{authProvider}} ({{accountInfo}})",        "newMapBadge": "NEW MAP",        "account": "Account",        "info": "Info",        "popularBadge": "POPULAR",        "updatedBadge": "UPDATED",        "newBadge": "NEW",        "skipAdPopupTitle": "Skip AD?",        "skipAdPopupSubtitle": "AD not showing? Click the button below to skip.",        "skipAdPopupConfirmText": "Skip",        "skipAdPopupConfirmTooltip": "Click here to skip this AD screen!",        "limitedTimeGameBadge": "LIMITED TIME",        "whatsNew": "What's New",        "updateLog": "Update Log",        "discordNamePopupTitle": "Bloxd Username",        "discordNamePopupConfirmTooltip": "We'll try to find a name that matches your Discord name",        "discordNamePopupCancelText": "Random name",        "discordNamePopupCancelTooltip": "We'll give you a random name",        "termsOfService": "Terms of Service",        "orInstallOnPc": "Or Install on PC",        "mobileAndPwaPrompt": "Play on any mobile device by scanning the QR code!",        "pwaPrompt": "Install Bloxd as an app on your device!",        "reloadPopupTitle": "Restart Required",        "reloadPopupSubtitle": "Bloxd needs to restart. Please exit the activity and rejoin.",        "reloadPopupConfirmText": "Exit",        "reloadPopupConfirmTooltip": "Exit the activity",        "playerCraftedBadge": "PLAYER CRAFTED",        "getSuperRank": "Get Super Rank",        "giftSuperRank": "Gift Super Rank",        "getSuperRankDays": "Get {{days}} days for {{price}} {{currency}}",        "giftSuperRankDays": "Gift {{days}} days for {{price}} {{currency}}",        "getSuperRankPitch": "Get perks and help support the development of Bloxd!",        "giftSuperRankPitch": "Send a gift to grant perks and help support the development of Bloxd!",        "buyForYourself": "Buy for yourself",        "sendGiftInstead": "Send a gift instead",        "superRank": "Super Rank",        "logInToGetSuperRank": "Log in to get Super Rank",        "rotateScreen": "Rotate Screen",        "scrollScreen": "Scroll Screen",        "enterBloxd": "Enter Bloxd",        "customLobbies": "Custom Lobbies",        "ownedLobbies": "Owned Lobbies",        "renewSuperRank": "Renew Super Rank",        "unlockWithSuperRank": "Unlock with Super Rank",        "favouriteLobbies": "Favourite Lobbies"    },    "auth": {        "progressUpdateMessage": "Progress updated\nLog out to continue with previous progress.",        "signOut": "Sign Out",        "login": "Login",        "loginFailed": "{{authProvider}} Login Failed",        "sessionExpired": "Your {{authProvider}} session has expired. Please log in again."    },    "loadingPage": {        "findingLobby": "Finding Lobby",        "joiningLobby": "Joining Lobby",        "loadingGame": "Loading Game",        "loadingPlayerInfo": "Loading Player Info",        "loadingWorld": "Loading World",        "standBy": "Stand by...",        "humanOrIronWatermelon": "Human or Iron Watermelon?? 🤔",        "loadingAssets": "Loading Assets"    },    "classicGame": {        "loseItemsIfLogOutTip": "You will lose your items if you log out when less than 80hp and hit within the previous 6 seconds.",        "protectLandWithProtectorsTip": "Protect your land and chests with protectors - craft them from diamonds",        "findProtectorPositionTip": "Want to move a protector? Find its position by typing the \"/protectors\" command. Then break it",        "protectorWillDisappearTip": "Watch out! Your protectors will disappear if you're away for more than 30 days",        "buildCloseToSpawnResetTip": "If you build within 192 blocks of spawn your building will be reset every few hours. Build outside this range to keep your building.",        "obtainTallGrassTip": "Obtain Tall Grass by breaking it with shears",        "helpCommandTip": "There are commands you can use to do useful things. Type \"/help\" in chat to see them",        "logInToSaveProgressTip": "If your browser's cookies are wiped, you lose your progress. Browsers sometimes do this by themselves. Log in to permanently save your progress",        "obtainWaterFromCactusTip": "Obtain water from a Fat Cactus with a bucket",        "playerCombatLogged": "{{name}} combat logged and was killed.",        "exitingBlockResetArea": "Exiting area within which blocks are reset",        "enteringBlockResetArea": "Entering area within which blocks are reset",        "cannotBuildThisHigh": "You cannot build this high in {{gameName}}!",        "blocksNearSpawnAreReset": "Careful! Blocks within 200 blocks of spawn are reset every few hours. Build things you want to keep outside this area.",        "saplingsAreLimited": "Saplings are limited. Wait to use more.",        "lostTeleportInvulnerabilityTip": "Lost teleport invulnerability",        "cantAttackCloseToSpawn": "Can't attack this close to spawn",        "playerSpawnedLessThan5sAgo": "Player spawned less than 5s ago",        "playerHasTeleportInvulnerabilityForTime": "Player has teleport invulnerability for {{time}}s",        "switchToPeaceful": "Would you like to switch to Peaceful?",        "spawnIsJustSpawn": "/spawn is just \"/spawn\"",        "blocksNearSpawnWillResetInTime": "Blocks near lobby spawn will be reset in {{time}}.",        "blocksNearSpawnDoNotResetInPrivate": "Blocks near spawn do not reset in private lobbies.",        "canOnlyUseCommandInWorlds": "Can only use this command in a worlds lobby",        "youAreNotLobbyOwner": "You are not the owner of this lobby",        "defaultGamemodeCommand": "This sets the gamemode of all players who haven't had their gamemode set with /gamemode [gamemode] [playerName?]",        "defautGamemodeValidGamemodes": "The only valid gamemodes are \"survival\" \"creative\" \"peaceful\" \"survivaladventure\" \"peacefuladventure\" \"spectator\". Format: /defaultgamemode [gamemode]",        "keepInventoryIsSetToValue": "Keep Inventory is now set to {{value}}",        "gamemodeValidGamemodes": "The only valid gamemodes are \"survival\" \"creative\" \"peaceful\" \"survivaladventure\" \"peacefuladventure\" \"spectator\". Format: /gamemode [gamemode] [playerName?]",        "cantFindPlayerWithName": "Can't find player with name {{name}} :(",        "setSpawnIsJustSetSpawn": "/setspawn is just \"/setspawn\"",        "setSpawnCommand": "Set spawn point to your current position",        "toggleCommand": "Usage: '/toggle hardcore' '/toggle homes'.",        "itemIsDisabledInCreative": "{{name}} is disabled in creative",        "teleportedToSpawn": "Teleported to lobby spawn",        "resettingBlocksNearSpawn": "Resetting blocks near lobby spawn.",        "freshJoinSpawnUpdated": "Fresh join spawn updated.",        "teleportToLobbySpawn": "Teleport to lobby spawn",        "utilities": "Utilities",        "lobbySpawn": "Lobby Spawn",        "freshLand": "Fresh Land",        "freshLandDescription": "Teleport to a random location to build uninterrupted",        "defaultGamemodeIsNowGamemode": "Default gamemode is now {{name}}",        "yourGamemodeIsNowGamemode": "Your gamemode is now {{name}}",        "setGamemodeOfPlayerToGamemode": "Set the gamemode of {{player}} to {{gamemode}}",        "cannotActionIfActionWithinTime": "Cannot {{action1}} if {{action2}} within the last {{time1}} seconds. {{time2}} seconds remaining.",        "cannotActionWhileDead": "Cannot {{action}} while dead.",        "receivedTimeTeleportInvulnerability": "Received {{time}}s teleport invulnerability.",        "teleportedTimeAgoNoTeleportInvulnerability": "Teleported {{time}}s ago, no teleport invulnerability.",        "cantChangeHere": "Can't change here",        "cantChangeWhileInGamemode": "Can't change while in {{gamemode}} mode",        "teleportedToFreshLand": "Teleported to Fresh Land",        "factionsWorldBorderTip": "IMPORTANT: On the 1st of July 2024, the Factions world border will be set 10k blocks from spawn, and you won't be able to use your personal home anymore. Make sure to move your base inside the safe zone, and replace your personal home with a faction home before then!",        "playerJoinedLessThan15sAgo": "Player joined less than 15s ago",        "spawnIsDisabled": "Teleporting to lobby spawn has been disabled by the lobby owner.",        "cantAttackCloseToFactionsOutpost": "Can't attack this close to the {{factionsOutpostName}}",        "pvpDisabledInFactionsOutpost": "PvP is disabled in the {{factionsOutpostName}}",        "mustBeInDefaultFactionToTpToFactionsOutpost": "You must be in the {{defaultFactionName}} to teleport to the {{factionsOutpostName}}",        "sandMineResetReminder": "The sand mine will reset in {{minutes}} minutes!",        "woodMillResetReminder": "The wood mill will reset in {{minutes}} minutes!",        "timeUntilFactionsCampsReset": "{{defaultFactionName}} camps will reset in {{time}}",        "factionsCampsReset": "{{defaultFactionName}} camps have been reset. They will reset again in {{days}} days time.",        "cantOpenChestWhileInGamemode": "Can't open loot chest while in {{gamemode}} mode",        "chiliPeppersGrowFasterOnSand": "Chili Pepper plants grow faster on Sand and Red Sand",        "tryGrowingChiliPeppersNearLava": "Try growing Chili Peppers near Lava..."    },    "homeCommand": {        "teleportToAHome": "Teleport to a home",        "setAHome": "Set a home",        "homeName": "Home Name",        "maxHomes": "Max Homes",        "deleteAHome": "Delete a home",        "teleportedToHome": "Teleported to home {{home}}",        "setYourDefaultHome": "Set your default home. Visit it with \"/home\"",        "setHome": "Set home \"{{home}}\". Visit it with \"/home {{home}}\"",        "deletedHome": "Deleted home \"{{home}}\""    },    "teleportCommand": {        "tpRequestDescription": "Request to teleport to player. Player accepts by typing \"/tpaccept\" in chat"    },    "tribe": {        "manageTribe": "Manage Tribe",        "createTribe": "Create Tribe",        "tribeName": "Tribe Name",        "enterAName": "Enter a name",        "nameTooLong": "Name too long, must be 16 characters or less",        "nameContainsProfanity": "Name contains profanity",        "tribeNameAlreadyExists": "A tribe with that name already exists",        "tribeNameCreatedByPlayer": "Tribe {{tribe}} has been created by {{player}}",        "createdTribe": "Created tribe {{tribe}}",        "setTribeHome": "Set Tribe Home",        "setTribeHomeAtCurrentPosition": "Set tribe home at your current position",        "invitePlayer": "Invite Player",        "invitePlayerToTribe": "Invite a player to the tribe",        "maxNumberOfPlayersInTribe": "Max number of players in tribe is 30",        "invitedPlayerToJoin": "Invited {{player}} to join",        "playerHasInvitedYouToJoinTribe": "{{player}} has invited you to join {{tribe}}",        "playerHasJoinedTribe": "{{player}} has joined the tribe",        "playerDeclinedInvite": "{{player}} declined the invite",        "tribeProtector": "Tribe Protector",        "protectYourTribe": "Protect your tribe!",        "disbandTribe": "Disband Tribe",        "disbandTribeDescription": "Disband the tribe. The tribe will cease to exist.",        "tribeHasBeenDisbandedByPlayer": "Tribe {{tribe}} has been disbanded by {{player}}",        "tribeHasBeenDisbanded": "Tribe {{tribe}} has been disbanded"    },    "item": {        "woodPickaxe": "Wood Pickaxe",        "stonePickaxe": "Stone Pickaxe",        "ironPickaxe": "Iron Pickaxe",        "goldPickaxe": "Gold Pickaxe",        "diamondPickaxe": "Diamond Pickaxe",        "moonstonePickaxe": "Moonstone Pickaxe",        "woodAxe": "Wood Axe",        "stoneAxe": "Stone Axe",        "ironAxe": "Iron Axe",        "goldAxe": "Gold Axe",        "diamondAxe": "Diamond Axe",        "moonstoneAxe": "Moonstone Axe",        "woodSpade": "Wood Spade",        "stoneSpade": "Stone Spade",        "ironSpade": "Iron Spade",        "goldSpade": "Gold Spade",        "diamondSpade": "Diamond Spade",        "woodSword": "Wood Sword",        "stoneSword": "Stone Sword",        "ironSword": "Iron Sword",        "goldSword": "Gold Sword",        "diamondSword": "Diamond Sword",        "woodHoe": "Wood Hoe",        "stoneHoe": "Stone Hoe",        "ironHoe": "Iron Hoe",        "goldHoe": "Gold Hoe",        "diamondHoe": "Diamond Hoe",        "woodHelmet": "Wood Helmet",        "ironHelmet": "Iron Helmet",        "goldHelmet": "Gold Helmet",        "diamondHelmet": "Diamond Helmet",        "woodChestplate": "Wood Chestplate",        "ironChestplate": "Iron Chestplate",        "goldChestplate": "Gold Chestplate",        "diamondChestplate": "Diamond Chestplate",        "woodLeggings": "Wood Leggings",        "ironLeggings": "Iron Leggings",        "goldLeggings": "Gold Leggings",        "diamondLeggings": "Diamond Leggings",        "woodBoots": "Wood Boots",        "ironBoots": "Iron Boots",        "goldBoots": "Gold Boots",        "diamondBoots": "Diamond Boots",        "woodGauntlets": "Wood Gauntlets",        "ironGauntlets": "Iron Gauntlets",        "goldGauntlets": "Gold Gauntlets",        "diamondGauntlets": "Diamond Gauntlets",        "whiteWoodHelmet": "White Wood Helmet",        "orangeWoodHelmet": "Orange Wood Helmet",        "magentaWoodHelmet": "Magenta Wood Helmet",        "lightBlueWoodHelmet": "Light Blue Wood Helmet",        "yellowWoodHelmet": "Yellow Wood Helmet",        "limeWoodHelmet": "Lime Wood Helmet",        "pinkWoodHelmet": "Pink Wood Helmet",        "grayWoodHelmet": "Gray Wood Helmet",        "lightGrayWoodHelmet": "Light Gray Wood Helmet",        "cyanWoodHelmet": "Cyan Wood Helmet",        "purpleWoodHelmet": "Purple Wood Helmet",        "blueWoodHelmet": "Blue Wood Helmet",        "brownWoodHelmet": "Brown Wood Helmet",        "greenWoodHelmet": "Green Wood Helmet",        "redWoodHelmet": "Red Wood Helmet",        "blackWoodHelmet": "Black Wood Helmet",        "whiteWoodChestplate": "White Wood Chestplate",        "orangeWoodChestplate": "Orange Wood Chestplate",        "magentaWoodChestplate": "Magenta Wood Chestplate",        "lightBlueWoodChestplate": "Light Blue Wood Chestplate",        "yellowWoodChestplate": "Yellow Wood Chestplate",        "limeWoodChestplate": "Lime Wood Chestplate",        "pinkWoodChestplate": "Pink Wood Chestplate",        "grayWoodChestplate": "Gray Wood Chestplate",        "lightGrayWoodChestplate": "Light Gray Wood Chestplate",        "cyanWoodChestplate": "Cyan Wood Chestplate",        "purpleWoodChestplate": "Purple Wood Chestplate",        "blueWoodChestplate": "Blue Wood Chestplate",        "brownWoodChestplate": "Brown Wood Chestplate",        "greenWoodChestplate": "Green Wood Chestplate",        "redWoodChestplate": "Red Wood Chestplate",        "blackWoodChestplate": "Black Wood Chestplate",        "whiteWoodLeggings": "White Wood Leggings",        "orangeWoodLeggings": "Orange Wood Leggings",        "magentaWoodLeggings": "Magenta Wood Leggings",        "lightBlueWoodLeggings": "Light Blue Wood Leggings",        "yellowWoodLeggings": "Yellow Wood Leggings",        "limeWoodLeggings": "Lime Wood Leggings",        "pinkWoodLeggings": "Pink Wood Leggings",        "grayWoodLeggings": "Gray Wood Leggings",        "lightGrayWoodLeggings": "Light Gray Wood Leggings",        "cyanWoodLeggings": "Cyan Wood Leggings",        "purpleWoodLeggings": "Purple Wood Leggings",        "blueWoodLeggings": "Blue Wood Leggings",        "brownWoodLeggings": "Brown Wood Leggings",        "greenWoodLeggings": "Green Wood Leggings",        "redWoodLeggings": "Red Wood Leggings",        "blackWoodLeggings": "Black Wood Leggings",        "whiteWoodBoots": "White Wood Boots",        "orangeWoodBoots": "Orange Wood Boots",        "magentaWoodBoots": "Magenta Wood Boots",        "lightBlueWoodBoots": "Light Blue Wood Boots",        "yellowWoodBoots": "Yellow Wood Boots",        "limeWoodBoots": "Lime Wood Boots",        "pinkWoodBoots": "Pink Wood Boots",        "grayWoodBoots": "Gray Wood Boots",        "lightGrayWoodBoots": "Light Gray Wood Boots",        "cyanWoodBoots": "Cyan Wood Boots",        "purpleWoodBoots": "Purple Wood Boots",        "blueWoodBoots": "Blue Wood Boots",        "brownWoodBoots": "Brown Wood Boots",        "greenWoodBoots": "Green Wood Boots",        "redWoodBoots": "Red Wood Boots",        "blackWoodBoots": "Black Wood Boots",        "whiteWoodGauntlets": "White Wood Gauntlets",        "orangeWoodGauntlets": "Orange Wood Gauntlets",        "magentaWoodGauntlets": "Magenta Wood Gauntlets",        "lightBlueWoodGauntlets": "Light Blue Wood Gauntlets",        "yellowWoodGauntlets": "Yellow Wood Gauntlets",        "limeWoodGauntlets": "Lime Wood Gauntlets",        "pinkWoodGauntlets": "Pink Wood Gauntlets",        "grayWoodGauntlets": "Gray Wood Gauntlets",        "lightGrayWoodGauntlets": "Light Gray Wood Gauntlets",        "cyanWoodGauntlets": "Cyan Wood Gauntlets",        "purpleWoodGauntlets": "Purple Wood Gauntlets",        "blueWoodGauntlets": "Blue Wood Gauntlets",        "brownWoodGauntlets": "Brown Wood Gauntlets",        "greenWoodGauntlets": "Green Wood Gauntlets",        "redWoodGauntlets": "Red Wood Gauntlets",        "blackWoodGauntlets": "Black Wood Gauntlets",        "shears": "Shears",        "stick": "Stick",        "coal": "Coal",        "ironBar": "Iron Bar",        "goldBar": "Gold Bar",        "diamond": "Diamond",        "moonstone": "Moonstone",        "bowl": "Bowl",        "bowlOfCranberries": "Bowl Of Cranberries",        "mushroomSoup": "Mushroom Soup",        "cotton": "Cotton",        "bucket": "Bucket",        "waterBucket": "Water Bucket",        "boat": "Boat",        "snowball": "Snowball",        "pebble": "Pebble",        "reinforcedPebble": "Reinforced Pebble",        "ball": "Ball",        "reinforcedBall": "Reinforced Ball",        "moonstoneOrb": "Moonstone Orb",        "fireball": "Fireball",        "iceball": "Iceball",        "woodBow": "Wood Bow",        "stoneBow": "Stone Bow",        "ironBow": "Iron Bow",        "goldBow": "Gold Bow",        "diamondBow": "Diamond Bow",        "woodCrossbow": "Wood Crossbow",        "stoneCrossbow": "Stone Crossbow",        "ironCrossbow": "Iron Crossbow",        "goldCrossbow": "Gold Crossbow",        "diamondCrossbow": "Diamond Crossbow",        "woodCrossbowCharged": "Wood Crossbow Charged",        "stoneCrossbowCharged": "Stone Crossbow Charged",        "ironCrossbowCharged": "Iron Crossbow Charged",        "goldCrossbowCharged": "Gold Crossbow Charged",        "diamondCrossbowCharged": "Diamond Crossbow Charged",        "arrow": "Arrow",        "compass": "Compass",        "bread": "Bread",        "bowlOfRice": "Bowl of Rice",        "apple": "Apple",        "plum": "Plum",        "coconut": "Coconut",        "crackedCoconut": "Cracked Coconut",        "pear": "Pear",        "watermelonSlice": "Watermelon Slice",        "goldWatermelonSlice": "Gold Watermelon Slice",        "melonSlice": "Melon Slice",        "goldMelonSlice": "Gold Melon Slice",        "pumpkinPie": "Pumpkin Pie",        "nameTag": "Name Tag",        "book": "Book",        "emptyBottle": "Empty Bottle",        "waterBottle": "Water Bottle",        "slownessPotion": "Slowness Potion",        "slownessPotionII": "Slowness Potion II",        "splashSlownessPotion": "Splash Slowness Potion",        "splashSlownessPotionII": "Splash Slowness Potion II",        "arrowOfSlowness": "Arrow of Slowness",        "poisonPotion": "Poison Potion",        "poisonPotionII": "Poison Potion II",        "splashPoisonPotion": "Splash Poison Potion",        "splashPoisonPotionII": "Splash Poison Potion II",        "arrowOfPoison": "Arrow of Poison",        "weaknessPotion": "Weakness Potion",        "weaknessPotionII": "Weakness Potion II",        "splashWeaknessPotion": "Splash Weakness Potion",        "splashWeaknessPotionII": "Splash Weakness Potion II",        "arrowOfWeakness": "Arrow of Weakness",        "instantDamagePotion": "Instant Damage Potion",        "instantDamagePotionII": "Instant Damage Potion II",        "splashInstantDamagePotion": "Splash Instant Damage Potion",        "splashInstantDamagePotionII": "Splash Instant Damage Potion II",        "arrowOfInstantDamage": "Arrow of Instant Damage",        "milkPotion": "Milk Potion",        "arrowOfMilk": "Arrow of Milk",        "speedPotion": "Speed Potion",        "speedPotionII": "Speed Potion II",        "splashSpeedPotion": "Splash Speed Potion",        "splashSpeedPotionII": "Splash Speed Potion II",        "arrowOfSpeed": "Arrow of Speed",        "defensePotion": "Defense Potion",        "defensePotionII": "Defense Potion II",        "splashDefensePotion": "Splash Defense Potion",        "splashDefensePotionII": "Splash Defense Potion II",        "arrowOfDefense": "Arrow of Defense",        "strengthPotion": "Strength Potion",        "strengthPotionII": "Strength Potion II",        "splashStrengthPotion": "Splash Strength Potion",        "splashStrengthPotionII": "Splash Strength Potion II",        "arrowOfStrength": "Arrow of Strength",        "invisibilityPotion": "Invisibility Potion",        "splashInvisibilityPotion": "Splash Invisibility Potion",        "arrowOfInvisibility": "Arrow of Invisibility",        "jumpPotion": "Jump Potion",        "jumpPotionII": "Jump Potion II",        "splashJumpPotion": "Splash Jump Potion",        "splashJumpPotionII": "Splash Jump Potion II",        "arrowOfJumping": "Arrow of Jumping",        "knockbackPotion": "Knockback Potion",        "splashKnockbackPotion": "Splash Knockback Potion",        "splashKnockbackPotionII": "Splash Knockback Potion II",        "arrowOfKnockback": "Arrow of Knockback",        "regenerationPotion": "Regeneration Potion",        "regenerationPotionII": "Regeneration Potion II",        "splashRegenerationPotion": "Splash Regeneration Potion",        "splashRegenerationPotionII": "Splash Regeneration Potion II",        "arrowOfRegeneration": "Arrow of Regeneration",        "instantHealingPotion": "Instant Healing Potion",        "instantHealingPotionII": "Instant Healing Potion II",        "splashInstantHealingPotion": "Splash Instant Healing Potion",        "splashInstantHealingPotionII": "Splash Instant Healing Potion II",        "arrowOfInstantHealing": "Arrow of Instant Healing",        "hastePotion": "Haste Potion",        "hastePotionII": "Haste Potion II",        "splashHastePotion": "Splash Haste Potion",        "splashHastePotionII": "Splash Haste Potion II",        "arrowOfHaste": "Arrow of Haste",        "dirt": "Dirt",        "messyDirt": "Messy Dirt",        "grassBlock": "Grass Block",        "sand": "Sand",        "clay": "Clay",        "gravel": "Gravel",        "snow": "Snow",        "mapleLog": "Maple Log",        "pineLog": "Pine Log",        "plumLog": "Plum Log",        "cedarLog": "Cedar Log",        "aspenLog": "Aspen Log",        "elmLog": "Elm Log",        "mapleWoodPlanks": "Maple Wood Planks",        "aspenWoodPlanks": "Aspen Wood Planks",        "plumWoodPlanks": "Plum Wood Planks",        "elmWoodPlanks": "Elm Wood Planks",        "pineWoodPlanks": "Pine Wood Planks",        "cedarWoodPlanks": "Cedar Wood Planks",        "barklessMapleLog": "Barkless Maple Log",        "barklessAspenLog": "Barkless Aspen Log",        "barklessPlumLog": "Barkless Plum Log",        "barklessElmLog": "Barkless Elm Log",        "barklessPineLog": "Barkless Pine Log",        "barklessCedarLog": "Barkless Cedar Log",        "stone": "Stone",        "messyStone": "Messy Stone",        "smoothStone": "Smooth Stone",        "diorite": "Diorite",        "smoothDiorite": "Smooth Diorite",        "andesite": "Andesite",        "smoothAndesite": "Smooth Andesite",        "granite": "Granite",        "smoothGranite": "Smooth Granite",        "sandstone": "Sandstone",        "yellowstone": "Yellowstone",        "coalOre": "Coal Ore",        "ironOre": "Iron Ore",        "goldOre": "Gold Ore",        "lapisLazuliOre": "Lapis Lazuli Ore",        "emeraldOre": "Emerald Ore",        "diamondOre": "Diamond Ore",        "blockOfCoal": "Block of Coal",        "blockOfIron": "Block of Iron",        "blockOfGold": "Block of Gold",        "blockOfLapisLazuli": "Block of Lapis Lazuli",        "blockOfEmerald": "Block of Emerald",        "whiteWool": "White Wool",        "orangeWool": "Orange Wool",        "magentaWool": "Magenta Wool",        "lightBlueWool": "Light Blue Wool",        "yellowWool": "Yellow Wool",        "limeWool": "Lime Wool",        "pinkWool": "Pink Wool",        "grayWool": "Gray Wool",        "lightGrayWool": "Light Gray Wool",        "cyanWool": "Cyan Wool",        "purpleWool": "Purple Wool",        "blueWool": "Blue Wool",        "brownWool": "Brown Wool",        "greenWool": "Green Wool",        "redWool": "Red Wool",        "blackWool": "Black Wool",        "bakedClay": "Baked Clay",        "whiteBakedClay": "White Baked Clay",        "orangeBakedClay": "Orange Baked Clay",        "magentaBakedClay": "Magenta Baked Clay",        "lightBlueBakedClay": "Light Blue Baked Clay",        "yellowBakedClay": "Yellow Baked Clay",        "limeBakedClay": "Lime Baked Clay",        "pinkBakedClay": "Pink Baked Clay",        "grayBakedClay": "Gray Baked Clay",        "lightGrayBakedClay": "Light Gray Baked Clay",        "cyanBakedClay": "Cyan Baked Clay",        "purpleBakedClay": "Purple Baked Clay",        "blueBakedClay": "Blue Baked Clay",        "brownBakedClay": "Brown Baked Clay",        "greenBakedClay": "Green Baked Clay",        "redBakedClay": "Red Baked Clay",        "blackBakedClay": "Black Baked Clay",        "grayConcrete": "Gray Concrete",        "lightGrayConcrete": "Light Gray Concrete",        "blackConcrete": "Black Concrete",        "blueConcrete": "Blue Concrete",        "brownConcrete": "Brown Concrete",        "cyanConcrete": "Cyan Concrete",        "lightBlueConcrete": "Light Blue Concrete",        "limeConcrete": "Lime Concrete",        "magentaConcrete": "Magenta Concrete",        "orangeConcrete": "Orange Concrete",        "pinkConcrete": "Pink Concrete",        "purpleConcrete": "Purple Concrete",        "redConcrete": "Red Concrete",        "whiteConcrete": "White Concrete",        "greenConcrete": "Green Concrete",        "yellowConcrete": "Yellow Concrete",        "pineLeaves": "Pine Leaves",        "aspenLeaves": "Aspen Leaves",        "mapleLeaves": "Maple Leaves",        "elmLeaves": "Elm Leaves",        "watermelon": "Watermelon",        "glass": "Glass",        "blackGlass": "Black Glass",        "blueGlass": "Blue Glass",        "brownGlass": "Brown Glass",        "cyanGlass": "Cyan Glass",        "grayGlass": "Gray Glass",        "lightGrayGlass": "Light Gray Glass",        "greenGlass": "Green Glass",        "lightBlueGlass": "Light Blue Glass",        "limeGlass": "Lime Glass",        "magentaGlass": "Magenta Glass",        "orangeGlass": "Orange Glass",        "pinkGlass": "Pink Glass",        "purpleGlass": "Purple Glass",        "redGlass": "Red Glass",        "whiteGlass": "White Glass",        "yellowGlass": "Yellow Glass",        "water": "Water",        "bricks": "Bricks",        "stoneBricks": "Stone Bricks",        "darkRedBrick": "Dark Red Brick",        "darkRedStone": "Dark Red Stone",        "blockOfQuartz": "Block of Quartz",        "chiseledBlockOfQuartz": "Chiseled Block of Quartz",        "engravedStone": "Engraved Stone",        "mossyStoneBricks": "Mossy Stone Bricks",        "crackedStoneBricks": "Cracked Stone Bricks",        "smoothSandstone": "Smooth Sandstone",        "engravedSandstone": "Engraved Sandstone",        "ice": "Ice",        "obsidian": "Obsidian",        "hayBale": "Hay Bale",        "sponge": "Sponge",        "beacon": "Beacon",        "goldenDecoration": "Golden Decoration",        "moonstoneExplosive": "Moonstone Explosive",        "bedrock": "Bedrock",        "smoothDoubleStoneSlab": "Smooth Double Stone Slab",        "cactus": "Cactus",        "grass": "Grass",        "dandelion": "Dandelion",        "poppy": "Poppy",        "redTulip": "Red Tulip",        "pinkTulip": "Pink Tulip",        "whiteTulip": "White Tulip",        "orangeTulip": "Orange Tulip",        "daisy": "Daisy",        "bluebell": "Bluebell",        "forget-Me-Not": "Forget-me-not",        "allium": "Allium",        "azureBluet": "Azure Bluet",        "lilyOfTheValley": "Lily of the Valley",        "witherRose": "Wither Rose",        "furnace": "Furnace",        "workbench": "Workbench",        "blockOfDiamond": "Block of Diamond",        "mapleDoor": "Maple Door",        "mapleTrapdoor": "Maple Trapdoor",        "aspenSapling": "Aspen Sapling",        "mapleSapling": "Maple Sapling",        "elmSapling": "Elm Sapling",        "plumSapling": "Plum Sapling",        "pineSapling": "Pine Sapling",        "cedarSapling": "Cedar Sapling",        "chest": "Chest",        "protector": "Protector",        "fatCactus": "Fat Cactus",        "dryFatCactus": "Dry Fat Cactus",        "ladder": "Maple Ladder",        "vines": "Vines",        "ironLadder": "Iron Ladder",        "whitePlanks": "White Planks",        "orangePlanks": "Orange Planks",        "magentaPlanks": "Magenta Planks",        "lightBluePlanks": "Light Blue Planks",        "yellowPlanks": "Yellow Planks",        "limePlanks": "Lime Planks",        "pinkPlanks": "Pink Planks",        "grayPlanks": "Gray Planks",        "lightGrayPlanks": "Light Gray Planks",        "cyanPlanks": "Cyan Planks",        "purplePlanks": "Purple Planks",        "bluePlanks": "Blue Planks",        "brownPlanks": "Brown Planks",        "greenPlanks": "Green Planks",        "redPlanks": "Red Planks",        "blackPlanks": "Black Planks",        "artisanBench": "Artisan Bench",        "whiteCeramic": "White Ceramic",        "orangeCeramic": "Orange Ceramic",        "magentaCeramic": "Magenta Ceramic",        "lightBlueCeramic": "Light Blue Ceramic",        "yellowCeramic": "Yellow Ceramic",        "limeCeramic": "Lime Ceramic",        "pinkCeramic": "Pink Ceramic",        "grayCeramic": "Gray Ceramic",        "lightGrayCeramic": "Light Gray Ceramic",        "cyanCeramic": "Cyan Ceramic",        "purpleCeramic": "Purple Ceramic",        "blueCeramic": "Blue Ceramic",        "brownCeramic": "Brown Ceramic",        "greenCeramic": "Green Ceramic",        "redCeramic": "Red Ceramic",        "blackCeramic": "Black Ceramic",        "wheatSeeds": "Wheat Seeds",        "wheat": "Wheat",        "tilledSoil": "Tilled Soil",        "breadBlock": "Bread Block",        "mossyMessyStone": "Mossy Messy Stone",        "whiteBed": "White Bed",        "orangeBed": "Orange Bed",        "magentaBed": "Magenta Bed",        "lightBlueBed": "Light Blue Bed",        "yellowBed": "Yellow Bed",        "limeBed": "Lime Bed",        "pinkBed": "Pink Bed",        "grayBed": "Gray Bed",        "lightGrayBed": "Light Gray Bed",        "cyanBed": "Cyan Bed",        "purpleBed": "Purple Bed",        "blueBed": "Blue Bed",        "brownBed": "Brown Bed",        "greenBed": "Green Bed",        "redBed": "Red Bed",        "blackBed": "Black Bed",        "appleBlock": "Apple Block",        "moonstoneOre": "Moonstone Ore",        "moonstoneChest": "Moonstone Chest",        "blockOfMoonstone": "Block of Moonstone",        "magma": "Magma",        "uselessSoil": "Useless Soil",        "markedSandstone": "Marked Sandstone",        "redSandstone": "Red Sandstone",        "smoothRedSandstone": "Smooth Red Sandstone",        "engravedRedSandstone": "Engraved Red Sandstone",        "markedRedSandstone": "Marked Red Sandstone",        "greenStone": "Green Stone",        "greenBricks": "Green Bricks",        "darkGreenBricks": "Dark Green Bricks",        "sandstoneBricks": "Sandstone Bricks",        "engravedDiorite": "Engraved Diorite",        "dioriteBricks": "Diorite Bricks",        "engravedAndesite": "Engraved Andesite",        "andesiteBricks": "Andesite Bricks",        "engravedGranite": "Engraved Granite",        "graniteBricks": "Granite Bricks",        "iceBricks": "Ice Bricks",        "plumLeaves": "Plum Leaves",        "cedarLeaves": "Cedar Leaves",        "palmLeaves": "Palm Leaves",        "palmLog": "Palm Log",        "palmWoodPlanks": "Palm Wood Planks",        "palmSapling": "Palm Sapling",        "pineDoor": "Pine Door",        "plumDoor": "Plum Door",        "cedarDoor": "Cedar Door",        "aspenDoor": "Aspen Door",        "elmDoor": "Elm Door",        "palmDoor": "Palm Door",        "pineTrapdoor": "Pine Trapdoor",        "plumTrapdoor": "Plum Trapdoor",        "cedarTrapdoor": "Cedar Trapdoor",        "aspenTrapdoor": "Aspen Trapdoor",        "elmTrapdoor": "Elm Trapdoor",        "palmTrapdoor": "Palm Trapdoor",        "redSand": "Red Sand",        "redSandstoneBricks": "Red Sandstone Bricks",        "rockyDirt": "Rocky Dirt",        "autumnMapleLeaves": "Autumn Maple Leaves",        "fallenMapleLeaves": "Fallen Maple Leaves",        "mapleSlab": "Maple Slab",        "pineSlab": "Pine Slab",        "plumSlab": "Plum Slab",        "cedarSlab": "Cedar Slab",        "aspenSlab": "Aspen Slab",        "elmSlab": "Elm Slab",        "palmSlab": "Palm Slab",        "dirtSlab": "Dirt Slab",        "grassSlab": "Grass Slab",        "messyStoneSlab": "Messy Stone Slab",        "stoneSlab": "Stone Slab",        "smoothStoneSlab": "Smooth Stone Slab",        "engravedStoneSlab": "Engraved Stone Slab",        "stoneBricksSlab": "Stone Bricks Slab",        "mossyStoneSlab": "Mossy Stone Slab",        "mossyStoneBricksSlab": "Mossy Stone Bricks Slab",        "andesiteSlab": "Andesite Slab",        "smoothAndesiteSlab": "Smooth Andesite Slab",        "engravedAndesiteSlab": "Engraved Andesite Slab",        "andesiteBricksSlab": "Andesite Bricks Slab",        "dioriteSlab": "Diorite Slab",        "smoothDioriteSlab": "Smooth Diorite Slab",        "engravedDioriteSlab": "Engraved Diorite Slab",        "dioriteBricksSlab": "Diorite Bricks Slab",        "graniteSlab": "Granite Slab",        "smoothGraniteSlab": "Smooth Granite Slab",        "engravedGraniteSlab": "Engraved Granite Slab",        "graniteBricksSlab": "Granite Bricks Slab",        "sandstoneSlab": "Sandstone Slab",        "smoothSandstoneSlab": "Smooth Sandstone Slab",        "engravedSandstoneSlab": "Engraved Sandstone Slab",        "markedSandstoneSlab": "Marked Sandstone Slab",        "sandstoneBricksSlab": "Sandstone Bricks Slab",        "redSandstoneSlab": "Red Sandstone Slab",        "smoothRedSandstoneSlab": "Smooth Red Sandstone Slab",        "engravedRedSandstoneSlab": "Engraved Red Sandstone Slab",        "markedRedSandstoneSlab": "Marked Red Sandstone Slab",        "redSandstoneBricksSlab": "Red Sandstone Bricks Slab",        "bricksSlab": "Bricks Slab",        "iceBricksSlab": "Ice Bricks Slab",        "plumBlock": "Plum Block",        "coconutBlock": "Coconut Block",        "pearLog": "Pear Log",        "pearWoodPlanks": "Pear Wood Planks",        "pearLeaves": "Pear Leaves",        "pearDoor": "Pear Door",        "pearTrapdoor": "Pear Trapdoor",        "pearSapling": "Pear Sapling",        "pearSlab": "Pear Slab",        "pearBlock": "Pear Block",        "compressedMessyStone": "Compressed Messy Stone",        "extraCompressedMessyStone": "Extra Compressed Messy Stone",        "superCompressedMessyStone": "Super Compressed Messy Stone",        "hyperCompressedMessyStone": "Hyper Compressed Messy Stone",        "ultraCompressedMessyStone": "Ultra Compressed Messy Stone",        "megaCompressedMessyStone": "Mega Compressed Messy Stone",        "board": "Board",        "net": "Net",        "cobweb": "Cobweb",        "brownMushroomBlock": "Brown Mushroom Block",        "redMushroomBlock": "Red Mushroom Block",        "mushroomStem": "Mushroom Stem",        "fireballBlock": "Fireball Block",        "iceballBlock": "Iceball Block",        "watermelonSeeds": "Watermelon Seeds",        "pumpkinSeeds": "Pumpkin Seeds",        "pumpkin": "Pumpkin",        "carvedPumpkin": "Carved Pumpkin",        "jackO'Lantern": "Jack o'Lantern",        "melonSeeds": "Melon Seeds",        "melon": "Melon",        "ironWatermelon": "Iron Watermelon",        "patternedBlackGlass": "Patterned Black Glass",        "patternedBlueGlass": "Patterned Blue Glass",        "patternedBrownGlass": "Patterned Brown Glass",        "patternedCyanGlass": "Patterned Cyan Glass",        "patternedGrayGlass": "Patterned Gray Glass",        "patternedLightGrayGlass": "Patterned Light Gray Glass",        "patternedGreenGlass": "Patterned Green Glass",        "patternedLightBlueGlass": "Patterned Light Blue Glass",        "patternedLimeGlass": "Patterned Lime Glass",        "patternedMagentaGlass": "Patterned Magenta Glass",        "patternedOrangeGlass": "Patterned Orange Glass",        "patternedPinkGlass": "Patterned Pink Glass",        "patternedPurpleGlass": "Patterned Purple Glass",        "patternedRedGlass": "Patterned Red Glass",        "patternedWhiteGlass": "Patterned White Glass",        "patternedYellowGlass": "Patterned Yellow Glass",        "potionTable": "Potion Table",        "pineLadder": "Pine Ladder",        "plumLadder": "Plum Ladder",        "cedarLadder": "Cedar Ladder",        "aspenLadder": "Aspen Ladder",        "elmLadder": "Elm Ladder",        "palmLadder": "Palm Ladder",        "pearLadder": "Pear Ladder",        "blackCarpet": "Black Carpet",        "blueCarpet": "Blue Carpet",        "brownCarpet": "Brown Carpet",        "cyanCarpet": "Cyan Carpet",        "grayCarpet": "Gray Carpet",        "lightGrayCarpet": "Light Gray Carpet",        "greenCarpet": "Green Carpet",        "lightBlueCarpet": "Light Blue Carpet",        "limeCarpet": "Lime Carpet",        "magentaCarpet": "Magenta Carpet",        "orangeCarpet": "Orange Carpet",        "pinkCarpet": "Pink Carpet",        "purpleCarpet": "Purple Carpet",        "redCarpet": "Red Carpet",        "whiteCarpet": "White Carpet",        "yellowCarpet": "Yellow Carpet",        "bookshelf": "Bookshelf",        "mailbox": "Mailbox",        "rice": "Rice",        "cranberries": "Cranberries",        "redMushroom": "Red Mushroom",        "brownMushroom": "Brown Mushroom",        "cottonSeeds": "Cotton Seeds",        "tribeProtector": "Tribe Protector",        "tallGrass": "Tall Grass",        "attachedWatermelonStem": "Attached Watermelon Stem",        "attachedPumpkinStem": "Attached Pumpking Stem",        "attachedMelonStem": "Attached Melon Stem",        "pickaxeDescription": "Mines stone",        "moonstonePickaxeDescription": "Stones drop their exact block",        "axeDescription": "Chops wood",        "spadeDescription": "Digs dirt",        "swordDescription": "Does damage",        "hoeDescription": "Cuts leaves and tills soil",        "stickDescription": "Deals increased knockback",        "bowlOfCranberriesDescription": "Eat to increase mining speed",        "throwableItemDescription": "Throw at players to do damage",        "ballDescription": "A bouncy ball.\nDoes wood actually bounce this much? idk",        "reinforcedBallDescription": "Flies further than a normal ball",        "moonstoneOrbDescription": "Throw to teleport to the landing location",        "fireballDescription": "Launch fireball for BOOM",        "iceballDescription": "Freezes players on explosion",        "bowDescription": "Shoots arrows",        "compassDescription": "Points to (0, 0, 0)",        "foodDescription": "Eat to restore health",        "plumDescription": "Temporarily gain increased damage",        "coconutDescription": "Throw on the ground to break into a cracked coconut",        "crackedCoconutDescription": "Temporarily gain increased speed",        "pearDescription": "Temporarily receive reduced damage",        "watermelonSliceDescription": "Eat to get a jump boost",        "melonSliceDescription": "Eat to become invisible",        "pumpkinPieDescription": "Temporarily gain increased damage",        "nameTagDescription": "Rename items",        "bookDescription": "Write down your thoughts...",        "emptyBottleDescription": "This has potential...",        "waterBottleDescription": "Mmm room temp water",        "slownessPotionDescription": "Slows you down",        "splashSlownessPotionDescription": "Slow other players down",        "poisonPotionDescription": "Drink me...",        "splashPoisonPotionDescription": "Poison anyone who stands in your way!",        "weaknessPotionDescription": "Makes you take more damage when attacked",        "splashWeaknessPotionDescription": "Make others take more damage when attacked",        "instantDamagePotionDescription": "Instantly damage yourself",        "splashInstantDamagePotionDescription": "Deal instant damage to other players",        "milkPotionDescription": "Removes all potion effects",        "speedPotionDescription": "Gotta go fast",        "splashSpeedPotionDescription": "Launch speed buffs at your friends (or enemies?)",        "defensePotionDescription": "Temporarily receive reduced damage",        "splashDefensePotionDescription": "Launch defense buffs at your friends (or enemies?)",        "strengthPotionDescription": "Temporarily gain increased damage",        "splashStrengthPotionDescription": "Launch attack buffs at your friends (or enemies?)",        "invisibilityPotionDescription": "Temporarily become invisible",        "splashInvisibilityPotionDescription": "Launch invisibility buffs at your friends (or enemies?)",        "jumpPotionDescription": "Temporarily jump higher",        "splashJumpPotionDescription": "Launch jump boosts at your friends (or enemies?)",        "knockbackPotionDescription": "Applies force",        "splashKnockbackPotionDescription": "Force people to leave you alone!",        "regenerationPotionDescription": "Temporarily increases health regeneration",        "splashRegenerationPotionDescription": "Increase health regen of your friends (or enemies?)",        "instantHealingPotionDescription": "Temporarily increases health regeneration",        "splashInstantHealingPotionDescription": "Increase health regen of your friends (or enemies?)",        "hastePotionDescription": "Temporarily increases mining speed",        "splashHastePotionDescription": "Increase mining speed of your friends (or enemies?)",        "coalOreDescription": "Decorative. Obtained using Moonstone Pickaxe",        "diamondOreDescription": "Decorative. Obtained using Moonstone Pickaxe",        "moonstoneExplosiveDescription": "Goes boom!",        "furnaceDescription": "Turn ores into crafting items",        "workbenchDescription": "Create advanced items",        "protectorDescription": "Prevents other players from changing blocks and opening chests in the placed chunk",        "artisanBenchDescription": "Create decorative blocks",        "wheatSeedsDescription": "Plant to grow wheat",        "moonstoneOreDescription": "Decorative. Obtained using Moonstone Pickaxe",        "moonstoneChestDescription": "Access the same items from any moonstone chest",        "netDescription": "Slows players inside",        "cobwebDescription": "Slows players inside",        "watermelonSeedsDescription": "Plant a stem that grows watermelons",        "pumpkinSeedsDescription": "Plant a stem that grows pumpkins",        "melonSeedsDescription": "Plant a stem that grows melons",        "potionTableDescription": "Make tasty potions!",        "mailboxDescription": "Let other players leave you notes",        "riceDescription": "Plant to grow rice",        "cranberriesDescription": "Plant to grow a cranberry bush",        "cottonSeedsDescription": "Plant to grow a cotton plant",        "tribeProtectorDescription": "Prevents other tribes from changing blocks and opening chests in the placed chunk",        "emptyBookshelfDescription": "Empty bookshelf",        "splashMilkPotion": "Splash Milk Potion",        "woodHangGlider": "Wood Hang Glider",        "ironHangGlider": "Iron Hang Glider",        "goldHangGlider": "Gold Hang Glider",        "diamondHangGlider": "Diamond Hang Glider",        "goldCoin": "Gold Coin",        "barklessPalmLog": "Barkless Palm Log",        "barklessPearLog": "Barkless Pear Log",        "rpg": "RPG",        "superRpg": "Super RPG",        "rpgDescription": "Fire rocket for BOOM",        "superRpgDescription": "Fire rocket for massive BOOM",        "whiteConcreteSlab": "White Concrete Slab",        "orangeConcreteSlab": "Orange Concrete Slab",        "magentaConcreteSlab": "Magenta Concrete Slab",        "lightBlueConcreteSlab": "Light Blue Concrete Slab",        "yellowConcreteSlab": "Yellow Concrete Slab",        "limeConcreteSlab": "Lime Concrete Slab",        "pinkConcreteSlab": "Pink Concrete Slab",        "grayConcreteSlab": "Gray Concrete Slab",        "lightGrayConcreteSlab": "Light Gray Concrete Slab",        "cyanConcreteSlab": "Cyan Concrete Slab",        "purpleConcreteSlab": "Purple Concrete Slab",        "blueConcreteSlab": "Blue Concrete Slab",        "brownConcreteSlab": "Brown Concrete Slab",        "greenConcreteSlab": "Green Concrete Slab",        "redConcreteSlab": "Red Concrete Slab",        "blackConcreteSlab": "Black Concrete Slab",        "grenadeLauncher": "Grenade Launcher",        "grenadeLauncherDescription": "Use bouncing grenades to cause explosions",        "barklessCherryLog": "Barkless Cherry Log",        "cherryWoodPlanks": "Cherry Wood Planks",        "cherryLog": "Cherry Log",        "cherryLeaves": "Cherry Leaves",        "fallenCherryLeaves": "Fallen Cherry Leaves",        "cherryDoor": "Cherry Door",        "cherryTrapdoor": "Cherry Trapdoor",        "cherrySapling": "Cherry Sapling",        "cherrySlab": "Cherry Slab",        "cherryLadder": "Cherry Ladder",        "cherryBlock": "Cherry Block",        "cherry": "Cherry",        "cherryDescription": "Temporarily increases health regeneration",        "bouncyBomb": "Bouncy Bomb",        "bouncyBombDescription": "BOUNCE 'n' BOOM",        "updraft": "Updraft",        "updraftDescription": "Dash upwards!",        "snowdash": "Snowdash",        "snowdashDescription": "Dash forwards!",        "floorCreator": "Floor Creator",        "floorCreatorDescription": "Create a floor of gold underneath you!",        "chaosPotion": "Chaos Potion",        "chaosPotionDescription": "Gives one random positive and negative effect.",        "moonstoneRemoteExplosive": "Moonstone Remote Explosive",        "moonstoneRemoteExplosiveDescription": "Throw an explosive and detonate it from afar!",        "moonstoneRemote": "Moonstone Remote",        "moonstoneRemoteDescription": "Detonate your bomb from afar!",        "spikesDescription": "Walk over these to receive damage. Trap your enemies with ease!",        "woodSpikes": "Wood Spikes",        "stoneSpikes": "Stone Spikes",        "ironSpikes": "Iron Spikes",        "goldSpikes": "Gold Spikes",        "diamondSpikes": "Diamond Spikes",        "killSpikes": "Kill Spikes",        "killSpikesDescription": "Megaspikes. Players who touch these will instantly die!",        "corn": "Corn",        "cornBlock": "Corn Block",        "cornDescription": "Eat to gain a shield",        "cornSeeds": "Corn Seeds",        "cornSeedsDescription": "Plant to grow corn",        "shieldPotion": "Shield Potion",        "shieldPotionII": "Shield Potion II",        "shieldPotionDescription": "Gives you a shield",        "splashShieldPotion": "Splash Shield Potion",        "splashShieldPotionII": "Splash Shield Potion II",        "splashShieldPotionDescription": "Gives other players a shield",        "arrowOfShield": "Arrow of Shield",        "iceBridge": "Ice Bridge",        "iceBridgeDescription": "Create a bridge of melting ice",        "redBalloon": "Red Balloon",        "yellowBalloon": "Yellow Balloon",        "whiteBalloon": "White Balloon",        "purpleBalloon": "Purple Balloon",        "pinkBalloon": "Pink Balloon",        "orangeBalloon": "Orange Balloon",        "magentaBalloon": "Magenta Balloon",        "limeBalloon": "Lime Balloon",        "lightGrayBalloon": "Light Gray Balloon",        "lightBlueBalloon": "Light Blue Balloon",        "greenBalloon": "Green Balloon",        "cyanBalloon": "Cyan Balloon",        "brownBalloon": "Brown Balloon",        "blueBalloon": "Blue Balloon",        "blackBalloon": "Black Balloon",        "cornbread": "Cornbread",        "cornbreadDescription": "Eat to regain health and gain shield",        "balloonDescription": "Go up high and fall down slowly",        "redPopupTower": "Red Popup Tower",        "yellowPopupTower": "Yellow Popup Tower",        "whitePopupTower": "White Popup Tower",        "purplePopupTower": "Purple Popup Tower",        "pinkPopupTower": "Pink Popup Tower",        "orangePopupTower": "Orange Popup Tower",        "magentaPopupTower": "Magenta Popup Tower",        "limePopupTower": "Lime Popup Tower",        "lightGrayPopupTower": "Light Gray Popup Tower",        "lightBluePopupTower": "Light Blue Popup Tower",        "greenPopupTower": "Green Popup Tower",        "grayPopupTower": "Gray Popup Tower",        "cyanPopupTower": "Cyan Popup Tower",        "brownPopupTower": "Brown Popup Tower",        "bluePopupTower": "Blue Popup Tower",        "blackPopupTower": "Black Popup Tower",        "popupTowerDescription": "Pop up a tower to defend yourself",        "rawPorkchop": "Raw Porkchop",        "cookedPorkchop": "Cooked Porkchop",        "rawMeatDescription": "Cook and eat to gain health (or eat RAW for a nasty surprise...)",        "yellowPaintballGun": "Yellow Paintball Gun",        "whitePaintballGun": "White Paintball Gun",        "redPaintballGun": "Red Paintball Gun",        "purplePaintballGun": "Purple Paintball Gun",        "pinkPaintballGun": "Pink Paintball Gun",        "orangePaintballGun": "Orange Paintball Gun",        "magentaPaintballGun": "Magenta Paintball Gun",        "limePaintballGun": "Lime Paintball Gun",        "lightGrayPaintballGun": "Light Gray Paintball Gun",        "lightBluePaintballGun": "Light Blue Paintball Gun",        "greenPaintballGun": "Green Paintball Gun",        "grayPaintballGun": "Gray Paintball Gun",        "cyanPaintballGun": "Cyan Paintball Gun",        "brownPaintballGun": "Brown Paintball Gun",        "bluePaintballGun": "Blue Paintball Gun",        "blackPaintballGun": "Black Paintball Gun",        "rawBeef": "Raw Beef",        "steak": "Steak",        "yellowPaintBow": "Yellow Paint Bow",        "whitePaintBow": "White Paint Bow",        "redPaintBow": "Red Paint Bow",        "purplePaintBow": "Purple Paint Bow",        "pinkPaintBow": "Pink Paint Bow",        "orangePaintBow": "Orange Paint Bow",        "magentaPaintBow": "Magenta Paint Bow",        "limePaintBow": "Lime Paint Bow",        "lightGrayPaintBow": "Light Gray Paint Bow",        "lightBluePaintBow": "Light Blue Paint Bow",        "greenPaintBow": "Green Paint Bow",        "grayPaintBow": "Gray Paint Bow",        "cyanPaintBow": "Cyan Paint Bow",        "brownPaintBow": "Brown Paint Bow",        "bluePaintBow": "Blue Paint Bow",        "blackPaintBow": "Black Paint Bow",        "yellowHeavyPaintballGun": "Yellow Heavy Paintball Gun",        "whiteHeavyPaintballGun": "White Heavy Paintball Gun",        "redHeavyPaintballGun": "Red Heavy Paintball Gun",        "purpleHeavyPaintballGun": "Purple Heavy Paintball Gun",        "pinkHeavyPaintballGun": "Pink Heavy Paintball Gun",        "orangeHeavyPaintballGun": "Orange Heavy Paintball Gun",        "magentaHeavyPaintballGun": "Magenta Heavy Paintball Gun",        "limeHeavyPaintballGun": "Lime Heavy Paintball Gun",        "lightGrayHeavyPaintballGun": "Light Gray Heavy Paintball Gun",        "lightBlueHeavyPaintballGun": "Light Blue Heavy Paintball Gun",        "greenHeavyPaintballGun": "Green Heavy Paintball Gun",        "grayHeavyPaintballGun": "Gray Heavy Paintball Gun",        "cyanHeavyPaintballGun": "Cyan Heavy Paintball Gun",        "brownHeavyPaintballGun": "Brown Heavy Paintball Gun",        "blueHeavyPaintballGun": "Blue Heavy Paintball Gun",        "blackHeavyPaintballGun": "Black Heavy Paintball Gun",        "yellowPaintballExplosive": "Yellow Paintball Explosive",        "whitePaintballExplosive": "White Paintball Explosive",        "redPaintballExplosive": "Red Paintball Explosive",        "purplePaintballExplosive": "Purple Paintball Explosive",        "pinkPaintballExplosive": "Pink Paintball Explosive",        "orangePaintballExplosive": "Orange Paintball Explosive",        "magentaPaintballExplosive": "Magenta Paintball Explosive",        "limePaintballExplosive": "Lime Paintball Explosive",        "lightGrayPaintballExplosive": "Light Gray Paintball Explosive",        "lightBluePaintballExplosive": "Light Blue Paintball Explosive",        "greenPaintballExplosive": "Green Paintball Explosive",        "grayPaintballExplosive": "Gray Paintball Explosive",        "cyanPaintballExplosive": "Cyan Paintball Explosive",        "brownPaintballExplosive": "Brown Paintball Explosive",        "bluePaintballExplosive": "Blue Paintball Explosive",        "blackPaintballExplosive": "Black Paintball Explosive",        "yellowSeekingPaintballExplosive": "Yellow Seeking Paintball Explosive",        "whiteSeekingPaintballExplosive": "White Seeking Paintball Explosive",        "redSeekingPaintballExplosive": "Red Seeking Paintball Explosive",        "purpleSeekingPaintballExplosive": "Purple Seeking Paintball Explosive",        "pinkSeekingPaintballExplosive": "Pink Seeking Paintball Explosive",        "orangeSeekingPaintballExplosive": "Orange Seeking Paintball Explosive",        "magentaSeekingPaintballExplosive": "Magenta Seeking Paintball Explosive",        "limeSeekingPaintballExplosive": "Lime Seeking Paintball Explosive",        "lightGraySeekingPaintballExplosive": "Light Gray Seeking Paintball Explosive",        "lightBlueSeekingPaintballExplosive": "Light Blue Seeking Paintball Explosive",        "greenSeekingPaintballExplosive": "Green Seeking Paintball Explosive",        "graySeekingPaintballExplosive": "Gray Seeking Paintball Explosive",        "cyanSeekingPaintballExplosive": "Cyan Seeking Paintball Explosive",        "brownSeekingPaintballExplosive": "Brown Seeking Paintball Explosive",        "blueSeekingPaintballExplosive": "Blue Seeking Paintball Explosive",        "blackSeekingPaintballExplosive": "Black Seeking Paintball Explosive",        "yellowQuickPaintballExplosive": "Yellow Quick Paintball Explosive",        "whiteQuickPaintballExplosive": "White Quick Paintball Explosive",        "redQuickPaintballExplosive": "Red Quick Paintball Explosive",        "purpleQuickPaintballExplosive": "Purple Quick Paintball Explosive",        "pinkQuickPaintballExplosive": "Pink Quick Paintball Explosive",        "orangeQuickPaintballExplosive": "Orange Quick Paintball Explosive",        "magentaQuickPaintballExplosive": "Magenta Quick Paintball Explosive",        "limeQuickPaintballExplosive": "Lime Quick Paintball Explosive",        "lightGrayQuickPaintballExplosive": "Light Gray Quick Paintball Explosive",        "lightBlueQuickPaintballExplosive": "Light Blue Quick Paintball Explosive",        "greenQuickPaintballExplosive": "Green Quick Paintball Explosive",        "grayQuickPaintballExplosive": "Gray Quick Paintball Explosive",        "cyanQuickPaintballExplosive": "Cyan Quick Paintball Explosive",        "brownQuickPaintballExplosive": "Brown Quick Paintball Explosive",        "blueQuickPaintballExplosive": "Blue Quick Paintball Explosive",        "blackQuickPaintballExplosive": "Black Quick Paintball Explosive",        "yellowStickPaintballExplosive": "Yellow Stick Paintball Explosive",        "whiteStickPaintballExplosive": "White Stick Paintball Explosive",        "redStickPaintballExplosive": "Red Stick Paintball Explosive",        "purpleStickPaintballExplosive": "Purple Stick Paintball Explosive",        "pinkStickPaintballExplosive": "Pink Stick Paintball Explosive",        "orangeStickPaintballExplosive": "Orange Stick Paintball Explosive",        "magentaStickPaintballExplosive": "Magenta Stick Paintball Explosive",        "limeStickPaintballExplosive": "Lime Stick Paintball Explosive",        "lightGrayStickPaintballExplosive": "Light Gray Stick Paintball Explosive",        "lightBlueStickPaintballExplosive": "Light Blue Stick Paintball Explosive",        "greenStickPaintballExplosive": "Green Stick Paintball Explosive",        "grayStickPaintballExplosive": "Gray Stick Paintball Explosive",        "cyanStickPaintballExplosive": "Cyan Stick Paintball Explosive",        "brownStickPaintballExplosive": "Brown Stick Paintball Explosive",        "blueStickPaintballExplosive": "Blue Stick Paintball Explosive",        "blackStickPaintballExplosive": "Black Stick Paintball Explosive",        "pigSpawnOrb": "Pig Spawn Orb",        "cowSpawnOrb": "Cow Spawn Orb",        "pigSpawnOrbDescription": "Throw to spawn a Pig at the landing location",        "cowSpawnOrbDescription": "Throw to spawn a Cow at the landing location",        "rawMutton": "Raw Mutton",        "cookedMutton": "Cooked Mutton",        "sheepSpawnOrb": "Sheep Spawn Orb",        "sheepSpawnOrbDescription": "Throw to spawn a Sheep at the landing location",        "moonstoneAxeDescription": "Cuts down entire tree trunks",        "timedSpikeBomb": "Timed Spike Bomb",        "timedSpikeBombDescription": "Plant the Spike on the given sites.",        "lava": "Lava",        "lavaBucket": "Lava Bucket",        "obsidianBoat": "Obsidian Boat",        "obsidianBoatDescription": "Use me to sail in Lava!",        "fatBrownMushroom": "Fat Brown Mushroom",        "fatRedMushroom": "Fat Red Mushroom",        "fatMushroomDescription": "A bouncy block.\nDo mushrooms actually bounce this much? idk",        "chiliPepperBlock": "Chili Pepper Block",        "chiliPepperSeeds": "Chili Pepper Seeds",        "chiliPepperSeedsDescription": "Plant to grow chili peppers",        "chiliPepper": "Chili Pepper",        "chiliPepperDescription": "Eat to gain heat resistance",        "heatResistancePotion": "Heat Resistance Potion",        "heatResistancePotionDescription": "Gives you heat resistance",        "splashHeatResistancePotion": "Splash Heat Resistance Potion",        "splashHeatResistancePotionDescription": "Gives other players heat resistance",        "arrowOfHeatResistance": "Arrow of Heat Resistance",        "codeBlock": "Code Block",        "toxinBall": "Toxin Ball",        "toxinBallDescription": "Shoot at players to poison them!"    },    "game": {        "survival": "Survival",        "survivalDescription": "Kill people (and do other things maybe) in a persistent open world",        "creative": "Creative",        "creativeDescription": "Infinite blocks & flying in a persistent open world. Go build!",        "worlds": "Worlds",        "worldsDescription": "Create your own world",        "bloxdHop": "Bloxd Hop",        "bloxdHopDescription": "Jump your way through varied parkour maps",        "cubeWarfare": "Cube Warfare",        "cubeWarfareDescription": "Shoot your enemies and obtain cool powerups",        "evilTower": "Evil Tower",        "evilTowerDescription": "Climb your way to the top of a randomly generated tower with absolutely no checkpoints",        "doodleCube": "Doodle Cube",        "doodleCubeDescription": "Build competitions with varied themes",        "oneBlock": "One Block",        "oneBlockDescription": "Start on a single block and build your island",        "skyWars": "Skywars",        "skyWarsDescription": "Fight to the death in the sky!",        "plots": "Plots",        "plotsDescription": "Build on your own plot of private land",        "pirates": "Pirates",        "piratesDescription": "Destroy your enemy's ship to win!",        "greenville": "Greenville",        "greenvilleDescription": "Build and upgrade your plot. Work for a living",        "bedwars": "Bedwars",        "bedwarsDuos": "Duos",        "bedwars4v4v4v4": "Squads",        "bedwarsDuosDescription": "Destroy your enemies beds to win! Play in teams of 2",        "bedwars4v4v4v4Description": "Destroy your enemies beds to win! Play in teams of 4",        "murderMystery": "Murder Mystery",        "murderMysteryDescription": "Play as an innocent, detective or murderer!",        "hideAndSeek": "Hide and Seek",        "hideAndSeekDescription": "Hide as a block. Don't get caught!",        "infection": "Infection",        "infectionDescription": "Play as a Human trying to escape, or a Zombie trying to hunt them down!",        "peaceful": "Peaceful",        "peacefulDescription": "Mine, build, and explore in a persistent open world",        "worldsOpenWorldRecommended": "Open World (recommended)",        "factions": "Factions",        "factionsDescription": "Create, join, raid and trade with factions in a persistent open world",        "bedwarsSolos": "Solos",        "bedwarsSolosDescription": "Destroy your enemies beds to win! Play without teammates",        "luckyTowers": "Lucky Towers",        "rocketObby": "Rocket Obby",        "rocketSpleef": "Rocket Spleef",        "bingo": "Bingo",        "paintball": "Paintball",        "bridge": "Bridge",        "bridgeDescription": "Jump into the other team's hole to win!",        "2d_classic": "One Block Wide",        "2dClassicDescription": "All you ever wanted. Survival but now in one less dimension.",        "bedwarsTrios": "Trios",        "bedwarsTriosDescription": "Destroy your enemies beds to win! Play in teams of 3",        "openWorld": "Open World",        "sandbox": "Sandbox"    },    "skywarsGame": {        "archer": "Archer",        "builder": "Builder",        "disco": "Disco",        "energix": "Energix",        "healer": "Healer",        "lumberjack": "Lumberjack",        "miner": "Miner",        "newbie": "Newbie",        "scout": "Scout",        "tank": "Tank",        "warrior": "Warrior",        "baseballer": "Baseballer",        "engineer": "Engineer",        "farmer": "Farmer",        "frog": "Frog",        "ghost": "Ghost",        "knight": "Knight",        "pharaoh": "Pharaoh",        "poisoner": "Poisoner",        "sniper": "Sniper",        "snowman": "Snowman",        "catapult": "Catapult",        "model": "Model",        "salmon": "Salmon",        "slug": "Slug",        "troll": "Troll",        "bomber": "Bomber",        "guardian": "Guardian",        "wraith": "Wraith",        "defaultDescription": "Start with nothing...",        "archerDescription": "Start with a bow and arrows!",        "builderDescription": "Start with wood and stone blocks!",        "discoDescription": "Disco time!",        "energixDescription": "Super strength magic!",        "healerDescription": "Health and safety first <3",        "lumberjackDescription": "Start with logs and an axe!",        "minerDescription": "Start with stone and a pickaxe!",        "newbieDescription": "Get going quick!",        "scoutDescription": "Start with some tasty snacks!",        "tankDescription": "Start with wooden armour!",        "warriorDescription": "Start with a sword!",        "baseballerDescription": "Time to join the major league!",        "engineerDescription": "Make your enemies go BOOM!",        "farmerDescription": "Time to farm some kills!",        "frogDescription": "Ribbit ribbit",        "ghostDescription": "Spooky",        "knightDescription": "Slay your enemies with a golden sword!",        "pharaohDescription": "Rule the world with emerald blocks!",        "poisonerDescription": "Start with splash poison potions.",        "sniperDescription": "Snipe away with splash damage potions :)",        "snowmanDescription": "Everything you need for a snowball fight!",        "catapultDescription": "Knock your enemies off the map!",        "modelDescription": "Shuffle up your wardrobe!",        "salmonDescription": "Become a fish and swim upstream!",        "slugDescription": "Slow n steady wins the race",        "trollDescription": "Trolls!? In my skywars!? It's more likely than you think...",        "bomberDescription": "Make your enemies go BOOM (but faster)!",        "guardianDescription": "Become a benevolent protector of the universe",        "wraithDescription": "Weaken your foes!",        "selectKitFailureMessage": "You cannot select kits whilst in a game!",        "maniac": "Maniac",        "blacksmith": "Blacksmith",        "bridger": "Bridger",        "arrowhead": "Arrowhead",        "leech": "Leech",        "resistance": "Resistance",        "rusher": "Rusher",        "luckyPick": "Lucky Pick",        "baker": "Baker",        "robbery": "Robbery",        "frost": "Frost",        "inferno": "Inferno",        "greenThumb": "Green Thumb",        "greenThumbDescription": "Quickly grow seeds and saplings",        "maniacDescription": "Gain {{number}} second(s) of increased damage after kills",        "blacksmithDescription": "{{number}}% chance to instantly smelt mined ores",        "bridgerDescription": "{{number}}% chance to recover placed blocks",        "arrowheadDescription": "{{number}}% chance to immediately recover fired arrows",        "leechDescription": "Gain {{number}} health after each kill",        "resistanceDescription": "Gain {{number}} seconds of damage reduction when the game starts",        "rusherDescription": "Gain {{number}} seconds of speed when the game starts",        "luckyPickDescription": "{{number}}% chance of getting an extra ore when mining",        "bakerDescription": "{{number}}% chance of getting bread after each kill",        "robberyDescription": "{{number}}% chance of making a player drop their held item when you hit them with your fist",        "frostDescription": "{{number}}% chance of slowing a player down when you hit them with an arrow",        "infernoDescription": "{{number}}% chance of getting a fireball after each kill",        "winMessage": "YOU WON!!! +20 GOLD!!",        "otherPlayerWinMessage": "{{name}} WON!!!",        "compassReceivedMessage": "Compass received. Use it to track down remaining players",        "compassMessage": "Compass given to all alive players.",        "selectPerkMessage": "You have selected the {{name}} perk!",        "cantSelectPerkMessage": "You cannot change perks whilst in a game!",        "goldForKill": "+{{number}} gold for killing {{name}}",        "killedText": "You were killed by {{name}} :(",        "chestsReplenished": "Chests replenished.",        "compassDisplayName": "Nearest Alive Player",        "compassDescription": "Points to nearest alive player"    },    "kitShop": {        "boughtKitMessage": "You bought:",        "kitSelected": "Selected:",        "kitSelectedInShop": "{{name}} starter kit selected. Open the shop to select a different kit!",        "alreadyOwnedKit": "Already owned:",        "received": "Received:",        "gemsAmount": "{{number}} gems!",        "common": "Common",        "rare": "Rare",        "epic": "Epic",        "legendary": "Legendary",        "mysteryKit": "Mystery Kit",        "kit": "Kit",        "mysteryKitDescription": "Unlock a mystery kit!",        "loot": "Loot"    },    "sessionBasedGame": {        "needMoreThanOneTeam": "Need more than one team to start the game.",        "playersRemaining": "{{number}} players remaining.",        "killNotification": "{{name}} was killed by {{name2}}.",        "playerDied": "{{name}} died.",        "stayInLobby": "Stay in lobby",        "startingIn": "Starting in:",        "spectator": "Spectator",        "chooseTeam": "Choose Team",        "joinTeam": "Join {{name}} Team",        "teamFull": "Team is full.",        "lobbyOverfull": "Lobby Overfull",        "lobbyOverfullDescription": "Lobby is overfull. You will be able to play once players leave.",        "gameStartInSeconds": "Game starting in {{number}} seconds.",        "startingGame": "Starting game.",        "lobbyFullStartInSeconds": "Lobby full, starting game in {{number}} seconds.",        "mapChanged": "Map changed to {{name}}.",        "startingNewGameInSeconds": "Starting new game in {{number}} seconds.",        "spectate": "Spectate",        "cantChangeBlocksWhileSpectating": "Can't change blocks while spectating",        "goldOnGgMessage": "+{{gold}} gold for saying gg!",        "chooseColour": "Choose Colour",        "joinColour": "Select {{name}} Colour",        "colourFull": "Colour is full.",        "mapVoted": "{{map}} won the vote, selected by {{player}}.",        "votedForMap": "Successfully voted for {{map}}."    },    "perksPlugin": {        "maxed": "Maxed"    },    "stats": {        "kills": "Kills",        "wins": "Wins",        "gamesPlayed": "Games Played",        "games": "Games"    },    "plotsGame": {        "addPlayerToPlot": "Add Player to Plot {{number}}",        "addPlayerToPlotDescription": "Grant a player access to your plot",        "playerCanNowAccessPlot": "{{name}} can now access your plot",        "removePlayerFromPlot": "Remove Player from Plot {{number}}",        "removePlayerFromPlotDescription": "Revoke a player's access to your plot",        "playerCanNoLongerAccessPlot": "{{name}} can no longer access your plot",        "goToOwnedPlot": "Go To Owned Plot",        "goToOwnedPlotDescription": "Go to a plot you own",        "teleportedToYourPlotNum": "Teleported to your plot #{{number}}",        "getNewPlot": "Get New Plot ({{number}}/{{maxPlotNum}})",        "getNewPlotDescription": "Get a new plot to build on",        "boughtNewPlot": "You have a new plot (#{{number}})",        "goToSharedPlot": "Go To Shared Plot",        "goToSharedPlotDescription": "Go to a plot you have been granted access to",        "teleportedToOtherPlayerPlot": "Teleported to {{name}}'s plot (#{{number}})",        "tpToPlot": "Tp To Plot",        "tpToPlotDescription": "Tp to any plot in the world using the plot coords",        "plot": "Plot:",        "plotOwner": "Owner:",        "cannotSpawnMobInPlotOwnedByOtherPlayer": "Cannot spawn mob in plot owned by other player."    },    "infectionGame": {        "nextSectionUnlocked": "Next section unlocked!",        "humansHaveUnlockedNextSection": "The humans have unlocked the next section!",        "human": "Human",        "zombie": "Zombie",        "humanDescription": "Follow the arrows and get through the obstacles before the zombies infect you!",        "zombieDescription": "Kill all the humans before they escape! Happy hunting!",        "youAreTheLastHuman": "You are the last human!",        "tapScreenToPay": "Tap screen to pay",        "pressFToPay": "Press f to pay",        "tapScreenToBuyGun": "Tap screen to buy {{gun}}",        "pressFToBuyGun": "Press f to buy {{gun}}",        "humansWin": "Humans win!",        "zombiesWin": "Zombies win!",        "humanTeamWinAward": "You escaped the Zombies!",        "zombieTeamWinAward": "You stopped the Humans from escaping!",        "firstKillAward": "First kill",        "finalKillAward": "Final kill",        "finalHumanAward": "You were the last Human alive",        "finalThreeHumanAward": "You were one of the last three Humans alive",        "firstZombieAward": "You were one of the first Zombies"    },    "worldBorderPlugin": {        "nearWorldBorderWarning": "You are near the world border (>{{radius}}).",        "teleportedBackWarning": "You will be teleported back if you go outside the border.",        "firstTimeJoinWarning": "Since you were last online, a world border has been added (>{{radius}}).",        "gracePeriodWarning": "You have {{gracePeriod}} mins to move your stuff into the safe zone."    },    "oneblockGame": {        "welcomeMessage": "Welcome!",        "skillNotReadyYet": "Skill is not ready yet!",        "minSkillLvlNotification": "You need to be level {{minSkillLevel}} to use this skill!",        "skillExpGain": "+{{skill}} Level exp",        "skillLevelGain": "+{{skill}} Level {{level}}",        "event": "EVENT",        "place": "place",        "theFastest": "the fastest",        "unscramble": "unscramble",        "type": "Type",        "typed": "typed",        "unscrambled": "unscrambled",        "placed": "placed",        "theFastestIn": "the fastest in\n",        "owner": "Owner",        "phase": "Phase",        "nextPhase": "Next Phase",        "blocks": "Blocks",        "newPhase": "New Phase",        "lucky": "Lucky",        "skill": "Skill",        "active": "Active",        "ready": "Ready",        "mining": "Mining",        "digging": "Digging",        "chopping": "Chopping",        "phaseForest": "Forest",        "phasePlains": "Plains",        "phaseJungle": "Jungle",        "phaseUnderground": "Underground",        "phaseWinter": "Winter",        "phaseRainbow": "Rainbow",        "phaseOcean": "Ocean",        "phaseSwamp": "Swamp",        "phaseDungeon": "Dungeon",        "phaseDesert": "Desert",        "phaseVolcano": "Volcano",        "phasePlenty": "Plenty",        "phaseDesolation": "Desolation",        "phaseMoon": "Moon",        "cannotChangePhase": "Cannot change phase until unlocking all phases",        "changedPhase": "Changed Phase!",        "locked": "Locked",        "islandPhases": "Island Phases",        "skills": "Skills",        "islandConfig": "Island Config",        "playerIslands": "Player Islands",        "minSkill": "Reach level 10 to unlock Skill",        "miningSkillName": "Super Mining",        "miningSkillDescription": "Break 3x faster and get 3x drops",        "duration": "Duration",        "rightClickToActivate": "Right click to activate",        "diggingSkillName": "Super Digging",        "diggingSkillDescription": "Break dirt blocks instantly",        "choppingSkillName": "Mega Chop",        "choppingSkillDescription": "Break trees with one chop!",        "renameIsland": "Rename Island",        "renameIslandDescription": "Change your island name",        "change": "Change",        "nameTooLong": "Name is too long!",        "setIslandNameMsg": "Set island name to {{islandName}}",        "nameTooShort": "Name is too short!",        "allowEdit": "Allow Edit",        "allowEditDescription": "Allow edit access to your island",        "allowEditWarning": "WARNING: This will allow anyone to take your blocks. Use at your own risk.",        "allowEditClickMsg": "Allow edit toggled!",        "prohibitEdit": "Prohibit Edit",        "prohibitEditDescription": "Remove edit access to your island",        "teleported": "Teleported!",        "reachPortalBeforeTeleport": "Reach your portal before using teleport!",        "island": "Island",        "totalBlocksMined": "Total blocks mined",        "doubleDropChance": "Double drop chance",        "playerIsland": "{{player}}'s Island"    },    "greenvilleGame": {        "welcomeMessage": "Welcome!",        "teleportedHome": "Teleported home!",        "recentActionText": "You can't do that right now!",        "joinHelperMessage": "Press B to choose your starting house. Take the portal to the town square to earn gold!",        "isleOfGrove": "Isle of Grove",        "prohibitedArea": "This area cannot be visited yet!",        "mood": "Mood",        "energy": "Energy",        "restLevel": "Rest Level",        "jobs": "Jobs",        "market": "Market",        "demolition": "Demolition",        "mining": "Mining",        "woodcutting": "Woodcutting",        "farming": "Farming",        "totalLevel": "Total Level",        "redWoolDescription": "Used to eliminate players in Parkour Mode",        "yellowWoolDescription": "Used to set checkpoints in Parkour Mode",        "lightBlueWoolDescription": "Used to set start block in Parkour Mode",        "orangeWoolDescription": "Used to set end block in Parkour Mode",        "flowerPackDescription": "Gives two random sets of three flowers",        "woolPackDescription": "Gives two random sets of five wool blocks",        "arenaWelcomeMesage": "Welcome to the Arena! Battle other players here",        "arenaRewardMessage": "Eliminated {{opponent}}! You have {{eliminationCount}} eliminations. Rewarded {{goldReward}} gold.",        "demolitionWelcomeMessage": "Welcome to demolition! Help destroy blocks and earn money. You have been equipped with a booster to jump more, try it!",        "demolitionPowerBoost": "POWER BOOST!",        "rewardMessage": "Great job, earned {{goldEarned}} gold!",        "rewardMessageWithExp": "Great job, earned {{goldEarned}} gold and {{expEarned}} exp!",        "demolitionAdvice": "Break more blocks! Remember you can multi-jump!",        "demolitionBigRewardMessage": "Demolished building, earned {{goldEarned}} gold",        "demolitionBigRewardMessageWithExp": "Demolished building, earned {{goldEarned}} gold and {{expEarned}} exp",        "demolitionPower": "Power",        "demolitionPoints": "Points",        "shopAdvice": "You can sell items you collect on the shop!",        "marketWelcomeMessage": "Welcome to the market! Help customers and earn gold. Find some {{block}}!",        "marketNewBlock": "Now find some {{block}}!",        "marketEarningPower": "Earning Power",        "marketMoneyBoost": "MONEY BOOST!",        "lowMoodMessage": "Mood is low! Getting decreased earnings. Rest at a bed to increase mood.",        "miningWelcomeMessage": "Welcome to Mining! Mine blocks and return them to the camp to earn riches!",        "miningInsideMineMessage": "You must be inside the mine!",        "miningMineralTooAdvanced": "The mineral is too advanced to mine, level up first!",        "miningBackpackFull": "Backpack full, get to the surface to sell!",        "miningStuckKeyboard": "Stuck? Press F to teleport up!",        "miningStuckMobile": "Stuck? Press the 'Up' button to teleport up!",        "miningDepth": "Depth",        "miningValue": "Value",        "miningBackpack": "Backpack",        "miningMineCollapsed": "The mine collapsed! New treasure awaits",        "spleefWelcome": "Welcome to Spleef! Make all other players fall to win. 2 players needed for game to start",        "spleefPlayerWonGame": "{{player}} won the game!",        "spleefYouWon": "You won! Earned {{goldEarned}} gold",        "spleefEliminatedPlayer": "You eliminated {{player}}! Earned {{goldEarned}} gold",        "spleefEliminations": "Eliminations",        "spleefWins": "Wins",        "spleefGameStartCounter": "Game starting in {{seconds}}",        "townSquare": "Town Square",        "arena": "Arena",        "mapleWoods": "Maple Woods",        "wheatFields": "Wheat Fields",        "haybaleValley": "Haybale Valley",        "aspenForest": "Aspen Forest",        "fastTravelDescription": "Travel to {{location}}",        "fastTravelBoughtMessage": "Traveled to {{location}}!",        "plotWoodenHouse": "Wooden House",        "plotMedievalHouse": "Medieval House",        "plotHobbitHole": "Hobbit Hole",        "plotEmptyPlot": "Empty Plot",        "plotStarterParkourPlot": "Starter Parkour Plot",        "plotModernHouse": "Modern House",        "plotModernHouse2": "Modern House 2",        "plotPvPArena": "PvP Arena",        "plotJapaneseHouse": "Japanese House",        "plotModernHouse3": "Modern House 3",        "plotGatedWoodenHouse": "Gated Wooden House",        "plotCountryHouse": "Country House",        "plotGreenMushroomHouse": "Green Mushroom House",        "plotRedMushroom": "Red Mushroom",        "plotCastle": "Castle",        "plotTreehouse": "Treehouse",        "plotParkourBase": "Parkour Base",        "plotEmptyPlot2": "Empty Plot 2",        "plotEmptyPlot3": "Empty Plot 3",        "unlockHouse": "Unlock {{houseName}}.",        "onHouseBought": "{{houseName}} unlocked.",        "houseChangeDescription": "Change your home to {{houseName}}",        "houseOnChange": "House Changed to {{houseName}}",        "locked": "Locked",        "travel": "Travel",        "onBuyMessage": "{{name}} bought!",        "unlockedFastTravel": "Unlocked fast travel for {{location}}!",        "bedDescription": "Bed level {{level}}\nResting increases earnings\nBetter bed level = more earnings",        "homeHostParty": "Host PARTY!",        "homeHostPartyBuyText": "Host!",        "homeHostPartyDescription": "Invite everyone to your house",        "homeHostPartyClickMessage": "Invited everyone to your house!",        "homeRenameHouse": "Rename House",        "homeRenameHouseDescription": "Change your house name",        "homeRenameHouseClickMessage": "Change",        "homeAllowEntry": "Allow Entry",        "homeAllowEntryDescription": "Toggle access to your home",        "homePvP": "Player Fighting",        "homePvPDescription": "Enable player vs player combat in your home",        "homeParkour": "Parkour",        "homeParkourDescription": "Enable parkour blocks in your home",        "homeCannotPlaceBed": "Cannot place a bed in plot border",        "homeAvoidRedWool": "Avoid the red wool!",        "homeParkourStuck": "Stuck? Type {{command}} to leave the house",        "homePlayerCompletedParkour": "{{player}} completed parkour in {{time}} seconds!",        "homeParkourModeOn": "Parkour mode is on! Red wool eliminates you and yellow wool activates checkpoints",        "homeNotAllowedEntry": "You are not allowed to enter {{player}}'s house",        "nameTooLong": "Name too long!",        "homeNameChange": "Set house name to {{houseName}}",        "homeInvitePlayersTimer": "You can invite players in {{time}} seconds!",        "homePartyJoinRequest": "{{player}} is hosting a party! Join?",        "homeMustUnlockSetting": "Must unlock {{settingName}} from shop first!",        "homeNotInAHouse": "You are not in a house",        "homeTeleportedOut": "Teleported out!",        "owner": "Owner",        "homeVisitorsAllowed": "Visitors allowed",        "homeTimer": "Timer",        "homePlayerNotRecognised": "Player name not recognised",        "homePlayersHouse": "{{player}}'s House",        "homeParkourCheckpointSaved": "Checkpoint saved",        "prohibitEdit": "Prohibit Edit",        "prohibitEditDescription": "Remove edit access to your house",        "prohibitEditOnBought": "Allow edit toggled!",        "prohibitEditRemove": "Removed {{player}} from your plot editors list.",        "prohibitEditYouWereRemoved": "You have been removed from {{player}}'s plot editors list.",        "enteringZone": "Entering {{zoneName}} zone",        "home": "Home",        "luck": "Luck",        "fastTravel": "Fast Travel",        "houses": "Houses",        "buy": "Buy",        "sell": "Sell",        "houseConfig": "House Config",        "packs": "Packs"    },    "greenvilleGamer": {        "homePlayerWhitelisted": "Player added to whitelist!"    },    "piratesGame": {        "default": "Default",        "engineer": "Engineer",        "juggernaut": "Juggernaut",        "keeper": "Keeper",        "leaper": "Leaper",        "navigator": "Navigator",        "plunderer": "Plunderer",        "swashbuckler": "Swashbuckler",        "bomber": "Bomber",        "boxer": "Boxer",        "cannoneer": "Cannoneer",        "medic": "Medic",        "pegleg": "Pegleg",        "rafter": "Rafter",        "scout": "Scout",        "captain": "Captain",        "drunkard": "Drunkard",        "firebreather": "Firebreather",        "ghost": "Ghost",        "hawk": "Hawk",        "hitman": "Hitman",        "admiral": "Admiral",        "portalmaster": "Portalmaster",        "raven": "Raven",        "scoundrel": "Scoundrel",        "maniac": "Maniac",        "maniacDescription": "Gain {{number}} second(s) of increased damage after kills",        "bridger": "Bridger",        "bridgerDescription": "{{number}}% chance to recover placed blocks",        "arrowhead": "Arrowhead",        "arrowheadDescription": "{{number}}% chance to immediately recover fired arrows",        "leech": "Leech",        "leechDescription": "Gain {{number}} health after each kill",        "resistance": "Resistance",        "resistanceDescription": "Gain {{number}} seconds of damage reduction when the game starts",        "rusher": "Rusher",        "rusherDescription": "Gain {{number}} seconds of speed when the game starts",        "baker": "Baker",        "bakerDescription": "{{number}}% chance of getting bread after each kill",        "frost": "Frost",        "frostDescription": "{{number}}% chance of slowing a player down when you hit them with an arrow",        "inferno": "Inferno",        "infernoDescription": "{{number}}% chance of getting a fireball after each kill",        "selectKitFailureMessage": "You cannot select kits whilst in a game!",        "defaultDescription": "Just a dirty scrub...",        "engineerDescription": "Get a pick, an axe and Granite Bricks!",        "juggernautDescription": "Be an absolute UNIT",        "keeperDescription": "Keep your inventory on death!",        "leaperDescription": "Get a Jump Potion!",        "navigatorDescription": "Find enemy spawns!",        "plundererDescription": "Place a chest and it'll fill with loot!",        "sniperDescription": "No-scope fools with a Diamond Bow and extra arrows!",        "sniper": "Sniper",        "swashbucklerDescription": "Place Cobwebs and Ladders!",        "bomberDescription": "Fire in the hole!",        "boxerDescription": "Slow and deal more damage with your fists!",        "cannoneerDescription": "Fire 2 cannon balls at once when using cannons!",        "medicDescription": "Heal your wounded hearties!",        "peglegDescription": "Knock foes back with a hefty peg leg!",        "rafterDescription": "Use boats to ride the waves!",        "scoutDescription": "Double jump!",        "captainDescription": "Rally your comrades! Nearby allies will get some Damage Reduction...",        "drunkardDescription": "Swig rum and toss Rakija cocktails!",        "firebreatherDescription": "Get a bunch more fireballs!",        "ghostDescription": "Teleport! But only for a limited time...",        "hawkDescription": "Soar through the air and hunt your prey!",        "hitmanDescription": "Get an Iron Crossbow and Poison Arrows!",        "admiralDescription": "Request an artillery strike!",        "portalmasterDescription": "Open portals for your allies!",        "ravenDescription": "Triple jump and bomb your enemies with splash potions!",        "scoundrelDescription": "Turn invisible and backstab your enemies!",        "gamesPlayed": "Games Played:",        "wins": "Wins:",        "startMessage": "Ahoy! Destroy the enemy's spawn blocks to win!",        "cannonMessage": "Click {{team}} Glass to fire cannons!",        "lootMessage": "LOOT has been refilled!!!",        "artilleryBeacon": "Artillery Beacon",        "artilleryBeaconDescription": "Place to request an artillery strike!",        "winMessage": "{{team}} TEAM WINS!",        "goldOnWinMessage": "You get {{gold}} gold!!!",        "goldOnFinalKillMessage": "+{{gold}} gold for killing {{playerName}}",        "cowardsCurseMessage": "Return to the fight or perish, coward...",        "raftersSeaSicknessMessage": "Get to land or drown!",        "spawnsLeft": "{{spawnCount}} Spawns Left",        "playersLeft": "{{playerCount}} Players Left",        "playerLeft": "{{playerCount}} Player Left",        "cowardCannotHealMessage": "A coward cannot heal...",        "compassDisplayNameNearestPlayer": "Nearest Player - {{targetName}} ({{targetTeam}})",        "compassDisplayNameNearestSpawn": "Nearest Spawn ({{targetTeam}})",        "defeat": "Defeat!",        "victory": "Victory!",        "compassDisplayNameTeamEliminated": "The {{team}} team has been eliminated!",        "\ncompassDisplayNameTeamsEliminated": "The {{firstTeams}} and {{lastTeam}} team has been eliminated!",        "cantFireEnemyCannonMessage": "You can't fire an enemy cannon!",        "cannonReloadingMessage": "Cannon reloading!",        "cantDestroyFriendlyCannonMessage": "You can't destroy a friendly cannon!",        "cantDestroyFriendlySpawnBlockMessage": "You can't destroy a friendly spawn block!",        "cantDestroySpawnBlockWhilstInvisibleMessage": "You can't destroy spawn blocks whilst invisible!",        "enemyCannonBrokenMessage": "Enemy cannon broken! It will reload soon...",        "cantDestroyReloadingCannonMessage": "You can't destroy a reloading cannon!",        "cantBuildOnTopOfSpawnBlockMessage": "You cannot build on top of a spawn block!",        "tooCloseToPortalKeystoneMessage": "Too close to existing Portal Keystone!",        "tooCloseToSpawnBlockMessage": "Too close to spawn block!",        "portalOpenedMessage": "{{playerName}} has opened a portal!",        "portalDestroyedMessage": "Your Portal Keystone has been destroyed!",        "cantCraft": "Pirates can't craft a:",        "plunderersChestMessage": "This is a plunderer's chest!",        "cantDestroyFriendlyArtilleryBeaconMessage": "You can't destroy a friendly artillery beacon!",        "artilleryBeaconOnCooldownMessage": "Artillery beacon is on cooldown!",        "requestingArtilleryMessage": "{{playerName}} is requesting artillery!",        "artilleryBeaconDestroyedMessage": "{{playerName}}'s artillery beacon has been destroyed!",        "artilleryStrikeIncomingMessage": "{{playerName}}'s artillery strike is INCOMING!",        "boxingGloves": "Boxing Gloves",        "boxingGlovesDescription": "Use me to deal bonus damage and slow your enemies!",        "lootChest": "Loot Chest",        "lootChestDescription": "Place me and I'll fill with loot!",        "pegLeg": "Peg Leg",        "rum": "Rum",        "rumDescription": "Gives Strength and Slowness",        "rakija": "Rakija Cocktail",        "rakijaDescription": "Deals damage and knocks back",        "hauntingOrb": "Haunting Orb",        "hauntingOrbDescription": "Teleport to the landing location! But only for a limited time...",        "hawksGlider": "Hawk's Glider",        "portalKeystone": "Portal Keystone",        "portalKeystoneDescription": "Place two to create a portal!",        "scoundrelPotionDescription": "Backstabs while invisible deal bonus damage!",        "goldOnSpawnBlockBreakMessage": "+{{gold}} gold for breaking a spawn!",        "noSpawnBlocksLeftMessage": "The {{team}} team has no spawn blocks left!",        "yourTeamHasNoSpawnBlocksLeftMessage": "YOUR TEAM has no spawn blocks left!",        "noSpawnBlocksLeftWithCompassMessage": "Use your Compass to hunt them down...",        "teamEliminatedMessage": "The {{team}} team has been ELIMINATED!",        "boxersDaze": "Boxer's Daze",        "lootChestCooldown": "Loot Chest Cooldown",        "raftersSeaSickness": "Rafter's Sea Sickness",        "raftersSeaSicknessImmunity": "Rafter's Sea Sickness Immunity",        "scoutsWeakness": "Scout's Weakness",        "captainsDefense": "Captain's Defense",        "captainsSpeed": "Captain's Speed",        "firebreathersRegeneration": "Firebreather's Regeneration",        "ghostsInvisibility": "Ghost's Invisibility",        "ghostsRegeneration": "Ghost's Regeneration",        "hitmansPoison": "Hitman's Poison",        "artilleryCooldown": "Artillery Cooldown",        "portalCooldown": "Portal Cooldown",        "ravensWeakness": "Raven's Weakness",        "cowardsCurse": "Coward's Curse",        "ghostHaunting": "Haunting...",        "spawnPointBrokenMessage": "{{team}} team spawn broken by:"    },    "mmGame": {        "survivalReward": "Survival Reward: +{{goldEarned}} gold",        "pickupMoonstone": "Picked up a moonstone! +{{goldEarned}} gold",        "survivedGame": "Survived the game! +{{goldEarned}} gold",        "winAsMurderer": "Won as murderer! +{{goldEarned}} gold",        "killMurderer": "Killed the Murderer! +{{goldEarned}} gold",        "killInnocentAsMurderer": "Killed an Innocent! +{{goldEarned}} gold",        "killDetectiveAsMurderer": "Killed the detective! +{{goldEarned}} gold",        "saidGG": "Said gg! +{{goldEarned}} gold",        "murdererGettingWeapon": "The murderer gets their weapon in",        "youNeedMoonstone": "You need {{amount}} {{moonstone}} to do that!",        "dailyQuestComplete": "You completed the Daily Quest \"{{questName}}\"!",        "weeklyQuestComplete": "You completed the Weekly Quest \"{{questName}}\"!",        "givingGun": "Giving gun in {{seconds}} seconds!",        "givingSword": "Giving sword in {{seconds}} seconds!",        "killedAPlayer": "Killed a player!",        "youDied": "YOU DIED!",        "murdererStabbedYou": "The murderer stabbed you!",        "murdererShotYou": "The murderer shot you!",        "murdererKilledYou": "The murderer killed you!",        "innocentShotYou": "Another innocent player shot you!",        "detectiveShotYou": "The detective shot you!",        "youWin": "YOU WIN",        "murdererWin": "You killed all innocents!",        "youLose": "YOU LOSE",        "murdererKilledAllInnocents": "The murderer killed all innocents!",        "revealMurderer": "{{playerName}} was the murderer!",        "murdererStopped": "The Murderer has been stopped!",        "detective": "Detective",        "murderer": "Murderer",        "winner": "Winner",        "dead": "(dead)",        "kills": "({{killCount}} kills)",        "youAreTheDetective": "YOU ARE THE DETECTIVE",        "goal": "GOAL",        "detectiveGoal": "Find and kill the murderer!",        "youAreInnocent": "YOU ARE INNOCENT",        "innocentGoal": "Stay alive as long as possible!",        "youAreTheMurderer": "YOU ARE THE MURDERER",        "murdererGoal": "Kill all players!",        "detectiveKilled": "The detective has been killed!",        "gunDropped": "The gun has been dropped! ({{location}})",        "role": "Role",        "innocentsLeft": "Innocents Left",        "timeLeft": "Time Left",        "innocent": "Innocent",        "players": "Players",        "totalKills": "Total Kills",        "totalWins": "Total Wins",        "winsAsDetective": "Wins as Detective",        "winsAsMurderer": "Wins as Murderer",        "needMoreThanOnePlayer": "Need more than one player to start the game",        "startingGame": "Starting game",        "killedMurdererText": "{{murdererName}} was the murderer! ({{murdererKills}} kills)\n{{murdererKiller}} killed the murderer!",        "gunHasBeenPickedUp": "The gun has been picked up!",        "weaponGivenToMurderer": "Weapon given! Kill all players!",        "weaponGivenToDetective": "Gun Given! It has a 5 second cooldown. Shoot the murderer to win, but die if you kill an innocent.",        "gameStartingInNSeconds": "Game starting in {{seconds}} seconds",        "gun": "Gun",        "dropped": "Dropped",        "alive": "Alive",        "mapChanged": "Map Changed to {{mapName}}",        "pickUpToObtainGun": "Pick up {{matAmount}} {{mat}} to obtain a gun!",        "playersCaps": "PLAYERS",        "murdererCaps": "MURDERER",        "poisonedWater": "The water is poisoned! You take damage",        "enteredRing": "Entered ring! +{{amount}} {{matName}}",        "dinoReveal": "The dino is pleased and reveals the detective: {{playerName}}",        "dinoRevealDead": "The dino is pleased and reveals the detective is dead!",        "dinoRevealMurderer": "The dino is pleased and reveals the murderer: {{playerName}}",        "dinoRevealMurdererDead": "The dino is pleased and reveals the murderer is dead!",        "dinoGrantGun": "You have been granted a gun!",        "dinoGrantThreeGuns": "The dino is pleased and grants you guns to punish your enemies",        "dinoGrantSevenGuns": "The dino is very pleased and grants you his arsenal",        "dinoCurseSlow": "The dino is displeased and curses you with slowness",        "dinoGrantSpam": "THE DINO HAS CURSED YOU WITH SPAM",        "dinoCurseJump": "The dino is displeased and curses you with no jumping",        "ringInformation": "Jump into gold and diamond rings to earn {{matName}}!",        "redTulipKN": "The intense red color could signify anger or revenge, marking a vendetta that the killer is fulfilling through their crimes.",        "dandelionKN": "Symbolizing resilience, the dandelion could represent the killer's ability to thrive in adversity, or their belief in a new beginning after every killing.",        "pinkTulipKN": "This might symbolize an innocent love or affection, perhaps pointing to the killer's twisted perception of their relationship with the victim.",        "whiteTulipKN": "The color white often symbolizes forgiveness or redemption. The killer might leave this flower to show remorse or to seek forgiveness for their actions, however misguided that sentiment might be.",        "aspenSaplingKN": "The aspen tree is known for trembling leaves, which might symbolize fear or trepidation. The killer may see themselves as instilling fear in others or be driven by their own deep-seated fears.",        "elmSaplingKN": "Elm trees are often associated with wisdom and communication. The killer could see their actions as delivering a profound message or a wisdom that others fail to comprehend.",        "mossyMessyStoneKN": "The overgrown and disorderly aspect of this stone might hint at something neglected or a crime long-planned.",        "diamondOreKN": "Symbolic of the victim being valuable or precious, or that they had something the killer wanted. Could hint at a motive of greed or envy.",        "iceBricksKN": "Ice can symbolize coldness, both in terms of a cold-blooded killer and in terms of the victim being 'frozen out' or isolated.",        "coalKN": "An item usually associated with punishment or judgment, perhaps left behind to symbolize the killer's perceived justice.",        "vinesKN": "Possibly symbolizing the killer's reach, spreading like vines and impossible to escape.",        "blackBedKN": "This could represent the eternal sleep that the killer has sentenced the victim to.",        "redSandstoneKN": "This could symbolize the blood spilled and the desert-like emptiness left behind.",        "glassKN": "Perhaps symbolizing the fragility of life, or a hint that the killer sees through people.",        "engravedStoneKN": "This could include cryptic symbols or messages, leading investigators on a chase to decode the killer's next move.",        "hyperCompressedMessyStoneKN": "The intense pressure used to create this stone could symbolize the stress or force that drives the killer.",        "cactusKN": "The prickly and unforgiving nature of a cactus could symbolize the killer's personality or approach to their victims.",        "protectorKN": "A very ironic item to leave at a murder scene, this could suggest a warped sense of justice on the part of the killer, or perhaps a desire to taunt law enforcement or other 'protectors'",        "magmaKN": "This hot and dangerous substance could represent the killer's anger or intensity.",        "cobwebKN": "A cobweb might signify the killer's ability to ensnare victims, possibly relating to a theme of manipulation or deceit.",        "common": "Common",        "uncommon": "Uncommon",        "rare": "Rare",        "epic": "Epic",        "legendary": "Legendary",        "openCrateForCosmetic": "Open a crate for a random cosmetic!",        "killNoteChanged": "Kill Note Changed to {{name}}!",        "lastWordsDescription": "In case the murderer gets you, drop a message with your last words for everyone to read!",        "lastWordChanged": "Last Word changed to {{name}}!",        "inProgress": "In progress",        "claim": "Claim",        "claimed": "Claimed",        "questClaimed": "Quest Claimed!",        "open": "Open",        "unlockedCosmetic": "Unlocked {{category}}: {{name}}!",        "alreadyOwnCosmetic": "Already owned, received {{moneyToGive}} gold instead.",        "onCosmeticBought": "{{name}} bought!",        "cheapSword": "Cheap Sword",        "stake": "Stake",        "scythe": "Scythe",        "openCrate": "Open Crate",        "slayerQuest": "Slayer",        "moonstoneHunterQuest": "Moonstone Hunter",        "victoryQuest": "Victory",        "masterSlayerQuest": "Master Slayer",        "extremeVictoryQuest": "Extreme Victory",        "quests": "Quests",        "weapons": "Weapons",        "killNotes": "Kill Notes",        "lastWords": "Last Words",        "cosmeticCrates": "Cosmetic Crates",        "noneLW": "None",        "angryLW": "ANGRY",        "dontCareLW": "Don't Care",        "frustratedLW": "Frustrated",        "adviceGuruLW": "Advice Guru",        "sportsmanshipLW": "Sportsmanship",        "encouragementLW": "Encouragement",        "condescendingLW": "Condescending",        "protipsLW": "Protips",        "sarcasticLW": "Sarcastic",        "gravesLW": "Graves",        "dramaticLW": "Dramatic",        "meowLW": "Meow",        "crybabyLW": "cRyBAbY",        "vengefulLW": "Vengeful",        "flamboyantLW": "Flamboyant",        "bizarreLW": "Bizarre",        "emojiTrajedyLW": "Emoji Tragedy",        "gamerLingoLW": "Gamer Lingo",        "humorousLW": "Humorous",        "existentialLW": "Existential",        "progress": "Progress",        "reward": "Reward",        "notDropped": "Not Dropped",        "default": "Default",        "startingIn": "Starting in",        "spectating": "Spectating"    },    "socialBar": {        "onHomePage": "On Home Page",        "playingGameMode": "Playing {{gameMode}} in Lobby {{lobbyName}}",        "requests": "Requests",        "offline": "Offline",        "addFriend": "Add Friend",        "enterPlayerName": "Enter Player Name",        "sendFriendRequest": "Send Friend Request",        "friends": "Friends",        "removeFriend": "Remove Friend",        "playerNotFound": "{{playerName}} not found",        "playerIsAlreadyYourFriend": "{{playerName}} is already your friend",        "playerHasTooManyFriends": "{{playerName}} has too many friends",        "youHaveTooManyFriends": "You have too many friends",        "playerHasTooManyFriendRequests": "{{playerName}} has too many friend requests",        "cantJoinFriend": "Can't Join Friend",        "limitReached": "Limit Reached",        "partyCode": "Party Code",        "leaveParty": "Leave Party",        "copyPartyCode": "Copy Party Code",        "waitingForPartyLeader": "Waiting for Party leader",        "joinParty": "Join Party",        "createParty": "Create Party",        "partyLeaderIsInControl": "{{player}} is in control of the Party",        "youAreBanned": "You are banned"    },    "doodle": {        "defaultDescription": "The default floor.",        "woodDescription": "A nice wooden floor.",        "mineDescription": "A cave-inspired floor.",        "riverDescription": "A river floor.",        "beachDescription": "A beach floor.",        "defaultWallsDescription": "Stone walls.",        "woodWallsDescription": "Wooden walls.",        "grassWallsDescription": "Grassy walls.",        "yellowWallsDescription": "Yellow walls.",        "orangeWallsDescription": "Orange walls.",        "pinkWallsDescription": "Pink walls.",        "purpleWallsDescription": "Purple walls.",        "blueWallsDescription": "Blue walls.",        "redWallsDescription": "Red walls.",        "whiteWallsDescription": "White walls.",        "blackWallsDescription": "Black walls."    },    "mobSpawnerPlugin": {        "couldNotSpawnPig": "Couldn't spawn Pig",        "couldNotSpawnCow": "Couldn't spawn Cow",        "mobsDisabledInGame": "Mobs are disabled in this game.",        "mobsSpawningTooQuickly": "You are spawning mobs too quickly!",        "tooManyMobsInLobby": "Too many mobs in the lobby.",        "tooManyMobsNearby": "Too many mobs nearby.",        "couldNotSpawnSheep": "Couldn't spawn Sheep"    },    "enablePointerLockNotification": {        "title": "Bloxd is blocked from using your mouse",        "step1": "Click the page permission icon in your browser's address bar",        "step2": "Enable \"Mouse lock and use\"",        "step3": "Message us on Discord if you still have issues"    },    "explosives": {        "explosivesAreLimited": "Explosives are limited. Wait to use more."    }}
```
### Metadata
#### Schematic Metadata
```json
a="illegals>&æWþþ{"persisted":{"chestStr":"[{\"name\":\"Apple block\",\"amount\":999,\"attributes\":{\"customAttributes\":{\"pages\":[\"\",\"\",\"\",\"\",\"\",\"\",\"\",\"\",\"\",\"\"],\"author\":\"nightops\",\"changeTime\":1738808482237},\"customDescription\":\"by nightowl\",\"customDisplayName\":\"dTomato blockd\"}},{\"name\":\"Compass\",\"amount\":null,\"attributes\":{\"customAttributes\":{\"target\":[928,null,null]},\"customDescription\":\"points to (928, NaN, NaN)\"}},{\"name\":\"Compass\",\"amount\":null,\"attributes\":{\"customAttributes\":{\"target\":[null,null,null]},\"customDescription\":\"points to (NaN, NaN, NaN)\"}},{\"name\":\"Double barrel\",\"amount\":null,\"attributes\":{\"customAttributes\":{\"shotsLeft\":9000000000}}},{\"name\":\"AK-47\",\"amount\":null,\"attributes\":{\"customAttributes\":{\"shotsLeft\":-1}}},{\"name\":\"AWp\",\"amount\":null,\"attributes\":{\"customAttributes\":{\"shotsLeft\":99}}},{\"name\":\"Minigun\",\"amount\":null,\"attributes\":{\"customAttributes\":{\"shotsLeft\":9000000000}}},{\"name\":\"book\",\"amount\":null,\"attrTittes\":{\"customAttributes\":{\"pages\":[\"gvdj\",\"\",\"\",\"\",\"\",\"\",\"\",\"\",\"\",\"\"],\"author\":\"Turtl3\",\"changeTime\":1738259561292},\"customDescription\":\"by Arthur\",\"customDisplayName\":\"Title\"}},null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null]"}}"
```
another
```json
{"persisted":{"shared":{"text":"api.setItemSlot(myId, api.getSelectedInventorySlotI(myId), \"Code block\", 1, attributes?: ItemAttributes, tellClient = true)","uncensoredText":"api.setItemSlot(myId, api.getSelectedInventorySlotI(myId), \"Code block\", 1, attributes?: ItemAttributes, tellClient = true)","textSize":0},"author":"_eu8VhYXV7hM8u41oGGZG","builder":"_eu8VhYXV7hM8u41oGGZG"}}
```
### Wall Of Shame for Poor Code Etiquette
#### License for MrChestplate Code, \(Was Taken Out\)
```js
/*Explicit Citation Attribution License (ECAL) Version 1.0
Copyright (c) [2025] [MrChestplate]

1. Definitions

a. Work: The copyrighted content or intellectual property to which this license applies.

b. Licensor: The original creator and owner of the Work.

c. Licensee: Any individual or entity receiving rights under this license.

d. Copy: Any reproduction of the Work, in whole or in part, in any form or medium.

2. Grant of Rights

Subject to the terms and conditions of this license,a the Licensor hereby grants the Licensee a non-exclusive, worldwide, royalty-free license to use, reproduce, distribute, and publicly display the Work, as well as create derivative works (if permitted by the underlying rights of the Work), provided that every copy or substantial portion distributed includes the explicit citation or credit as specified in Section 3.

3. Attribution and Citation Requirements

a. Any reproduction, distribution, or public display of the Work—whether in its original form or in derivative works—must include a clear and conspicuous citation or credit to the Licensor IN GAME. The required citation should include:

The name of the Licensor (i.e., the original author or copyright holder);

The title of the Work;

A reference to this license (i.e., “Licensed under the Explicit Citation Attribution License (ECAL) Version 1.0”);

The year of first publication (if applicable).

b. The default citation format is as follows (this may be modified only with the Licensor's explicit written consent):

> “© [Year] [Licensor’s Name]. Title of the Work. Licensed under the Explicit Citation Attribution License (ECAL) Version 1.0.”

c. Any variation from or omission of the required citation constitutes a breach of this license.

4. Prohibited Uses Without Attribution

The Licensee is expressly prohibited from copying, reproducing, distributing, publicly displaying, or otherwise using the Work—whether in whole or in part—without the inclusion of the explicit citation or credit as detailed above. Any such unauthorized use shall be deemed a violation of this license and may result in immediate termination of the rights granted herein.

5. Termination

a. This license and the rights granted herein are effective until terminated.

b. If the Licensee fails to comply with any of the terms or conditions of this license, or if the Licensee engages in any unauthorized use of the Work, this license shall immediately terminate, and the Licensee must cease all use of the Work.

c. Upon termination, the Licensee shall remove any copies of the Work from distribution and refrain from further use.

6. No Additional Rights

This license does not grant the Licensee any rights beyond those explicitly set forth herein. All rights not expressly granted are reserved by the Licensor.

7. Disclaimer of Warranty

THE WORK IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE WARRANTIES OF GAMING, IN-GAME VIOLENCE FOR A PARTICULAR PURPOSE, AND NON-INFRINGEMENT. IN NO EVENT SHALL THE LICENSOR BE LIABLE FOR ANY CLAIM, DAMAGES, OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT, OR OTHERWISE, ARISING FROM, OUT OF, OR IN CONNECTION WITH THE WORK OR THIS LICENSE.

8. Governing Law

This license shall be governed by and construed in accordance with the laws of the jurisdiction in which the Licensor resides.

By using, copying, distributing, or modifying the Work, you acknowledge that you have read, understood, and agree to be bound by the terms and conditions of this Explicit Citation Attribution License (ECAL) Version 1.0.*/
```
#### Obscurification \( Was Taken Out \)
```js
var _0x1ab779=_0x7735;(function(_0x1bea7e,_0x59a4eb){var _0x51bc91=_0x7735,_0x3c24ab=_0x1bea7e();while(!![]){try{var _0x152697=-parseInt(_0x51bc91(0x37))/0x1+parseInt(_0x51bc91(0x3))/0x2+-parseInt(_0x51bc91(0x4f))/0x3*(parseInt(_0x51bc91(0x38))/0x4)+parseInt(_0x51bc91(0x2b))/0x5*(-parseInt(_0x51bc91(0x15))/0x6)+parseInt(_0x51bc91(0x7))/0x7*(-parseInt(_0x51bc91(0x35))/0x8)+-parseInt(_0x51bc91(0x3e))/0x9+parseInt(_0x51bc91(0xb))/0xa*(parseInt(_0x51bc91(0x20))/0xb);if(_0x152697===_0x59a4eb)break;else _0x3c24ab['push'](_0x3c24ab['shift']());}catch(_0x527153){_0x3c24ab['push'](_0x3c24ab['shift']());}}}(_0x59d7,0x6965b),sos=_0x1ab779(0x17),anchors={});function p3(_0x2a7ebd,_0x461a2b,_0x2c2a70){var _0x3703f4=_0x7735;api[_0x3703f4(0x2c)]({'dir1':[-0x1,-0x1,-0x1],'dir2':[0x1,0x1,0x1],'pos1':[_0x2a7ebd-0x1,_0x461a2b,_0x2c2a70-0x1],'pos2':[_0x2a7ebd+0x1,_0x461a2b+0x1,_0x2c2a70+0x1],'texture':_0x3703f4(0x48),'minLifeTime':0.5,'maxLifeTime':0x1,'minEmitPower':0x2,'maxEmitPower':0x2,'minSize':0.25,'maxSize':0.5,'manualEmitCount':0x64,'gravity':[0x0,0x0,0x0],'colorGradients':[{'timeFraction':0x0,'minColor':[0x0,0xff,0x0,0x1],'maxColor':[0x0,0x96,0x0,0x1]}],'velocityGradients':[{'timeFraction':0x0,'factor':0x1,'factor2':0x1}],'blendMode':0x1}),api[_0x3703f4(0x2c)]({'dir1':[-0x1,-0x1,-0x1],'dir2':[0x1,0x1,0x1],'pos1':[_0x2a7ebd-0x1,_0x461a2b,_0x2c2a70-0x1],'pos2':[_0x2a7ebd+0x1,_0x461a2b+0x1,_0x2c2a70+0x1],'texture':_0x3703f4(0x48),'minLifeTime':0.5,'maxLifeTime':0x1,'minEmitPower':0x2,'maxEmitPower':0x2,'minSize':0.25,'maxSize':0.5,'manualEmitCount':0x64,'gravity':[0x0,0x0,0x0],'colorGradients':[{'timeFraction':0x0,'minColor':[0xff,0xff,0x0,0x1],'maxColor':[0xff,0xff,0x0,0x1]}],'velocityGradients':[{'timeFraction':0x0,'factor':0x1,'factor2':0x1}],'blendMode':0x1});}tasks=[];function tick(){var _0x19bbaf=_0x7735;if(tasks[_0x19bbaf(0x2d)]>0x0)for(i=0x0;i<tasks[_0x19bbaf(0x2d)];i++){task=tasks[i],task[0x0]===0x0&&(coord1=task[0x1],coord2=task[0x2],explode(coord1,coord2)),tasks['splice'](i,0x1);}}function explode(_0x3d241f,_0x2d9165){var _0x3cf2d6=_0x7735;for(x=_0x3d241f[0x0];x<_0x2d9165[0x0];x++){for(y=_0x3d241f[0x1];y<_0x2d9165[0x1];y++){for(z=_0x3d241f[0x2];z<_0x2d9165[0x2];z++){curBlock=api[_0x3cf2d6(0x4c)](x,y,z),curBlock!=='Obsidian'&&curBlock!==_0x3cf2d6(0x4a)&&api[_0x3cf2d6(0x3d)](x,y,z,'Air');}}}}function calcDim(_0x1fe9d2){return-0x14*_0x1fe9d2+0x82;}function onPlayerClick(_0x1444f4,_0x15019c){var _0x35d992=_0x7735;slotidx=api[_0x35d992(0x26)](_0x1444f4),itm=api[_0x35d992(0x2a)](_0x1444f4,slotidx);itm!==null&&(itm[_0x35d992(0x3f)]['customDisplayName']===_0x35d992(0x49)&&_0x15019c&&!api[_0x35d992(0x24)](_0x1444f4)[_0x35d992(0x53)](_0x35d992(0x49))&&(api[_0x35d992(0x4d)](_0x1444f4,_0x35d992(0x49),null,{'displayName':_0x35d992(0x49),'icon':_0x35d992(0x9)}),api[_0x35d992(0x21)](_0x1444f4,slotidx,_0x35d992(0x9),0x0)));target=api[_0x35d992(0xa)](_0x1444f4);if(target){blockpos=target[_0x35d992(0x47)],slotidx=api[_0x35d992(0x26)](_0x1444f4),itm=api[_0x35d992(0x2a)](_0x1444f4,slotidx);if(_0x15019c)target[_0x35d992(0x1b)]===0x7d&&itm[_0x35d992(0x43)]==='Golden\x20Decoration'&&api[_0x35d992(0x3d)](target[_0x35d992(0x47)][0x0],target[_0x35d992(0x47)][0x1],target[_0x35d992(0x47)][0x2],_0x35d992(0x29));else{if(target[_0x35d992(0x1b)]===0x7c&&itm[_0x35d992(0x43)]!==_0x35d992(0x31)){anchors[target[_0x35d992(0x47)]]=0x0,coord1=[blockpos[0x0]-0x4,blockpos[0x1]-0x4,blockpos[0x2]-0x4],coord2=[blockpos[0x0]+0x4,blockpos[0x1]+0x5,blockpos[0x2]+0x4],api[_0x35d992(0x3b)](_0x1444f4,sos,0.5,0x1),enties=api[_0x35d992(0x54)](coord1,coord2),damage=0x7d,prot=0.6;for(i=0x0;i<enties[_0x35d992(0x2d)];i++){id1=enties[i],posid1=api['getPosition'](id1);if(isPlayer(id1)&&api[_0x35d992(0x32)](id1)){dist=Math[_0x35d992(0x13)](Math[_0x35d992(0x46)](blockpos[0x0]+0.5-posid1[0x0],0x2)+Math[_0x35d992(0x46)](blockpos[0x1]+0.5-posid1[0x1],0x2)+Math[_0x35d992(0x46)](blockpos[0x2]+0.5-posid1[0x2],0x2)),api[_0x35d992(0x3b)](id1,sos,0.5,0x1),force=api[_0x35d992(0x1c)](id1,0x1,0.3,0x5,[blockpos[0x0]+0.5,blockpos[0x1]+0.5,blockpos[0x2]+0.5],!![])[_0x35d992(0xd)],slotidx=api[_0x35d992(0x26)](id1),itm=api['getItemSlot'](id1,slotidx);if(api[_0x35d992(0xc)](id1)-Math[_0x35d992(0x42)](calcDim(dist)*(0x1-prot))>0x5&&!(api[_0x35d992(0x24)](id1)[_0x35d992(0x53)](_0x35d992(0x49))||itm[_0x35d992(0x3f)][_0x35d992(0x1e)]===_0x35d992(0x49)))api[_0x35d992(0x50)](id1,-Math[_0x35d992(0x42)](calcDim(dist)*(0x1-prot)),_0x1444f4);else(api[_0x35d992(0x24)](id1)[_0x35d992(0x53)](_0x35d992(0x49))||itm&&itm[_0x35d992(0x3f)]['displayName']===_0x35d992(0x49))&&api['getHealth'](id1)-Math[_0x35d992(0x42)](calcDim(dist)*(0x1-prot))<0x5?(poser=api[_0x35d992(0x11)](id1),itm&&itm[_0x35d992(0x3f)]['displayName']===_0x35d992(0x49)&&api[_0x35d992(0x21)](id1,slotidx,_0x35d992(0x9),0x0),api[_0x35d992(0x51)](id1,0xa),api[_0x35d992(0x4d)](id1,'Health\x20Regen',0x9c40,{'inbuiltLevel':0x2}),api[_0x35d992(0x28)](id1,0x14),api[_0x35d992(0x3b)](id1,_0x35d992(0x1a),0x1,0x1),api[_0x35d992(0x25)](id1,_0x35d992(0x49)),p3(poser[0x0],poser[0x1],poser[0x2])):api[_0x35d992(0x50)](id1,-Math[_0x35d992(0x42)](calcDim(dist)*(0x1-prot)),{'lifeformId':_0x1444f4,'withItem':_0x35d992(0x29)});api[_0x35d992(0x6)](id1,force[0x0],force[0x1],force[0x2]);}}tasks['push']([0x0,coord1,coord2]);}else{if(target[_0x35d992(0x1b)]===0x3ec){blockUnder=api[_0x35d992(0x4c)](blockpos[0x0],blockpos[0x1]-0x1,blockpos[0x2]);if(blockUnder===_0x35d992(0x52)){api['setBlock'](blockpos[0x0],blockpos[0x1],blockpos[0x2],_0x35d992(0x14)),coords1=[blockpos[0x0]-0x6,blockpos[0x1]+0x1,blockpos[0x2]-0x6],coords2=[blockpos[0x0]+0x7,blockpos[0x1]+0x7,blockpos[0x2]+0x7],coord1=[blockpos[0x0]-0x4,blockpos[0x1],blockpos[0x2]-0x4],coord2=[blockpos[0x0]+0x4,blockpos[0x1]+0x4,blockpos[0x2]+0x4],enties=api[_0x35d992(0x54)](coords1,coords2),damage=0x32,prot=0.6,rng=Math['floor'](Math['random']()*0x64)+0x1,api[_0x35d992(0x3b)](_0x1444f4,sos,0.5,0x1);for(i=0x0;i<enties[_0x35d992(0x2d)];i++){id1=enties[i];if(isPlayer(id1)&&api[_0x35d992(0x32)](id1)){api[_0x35d992(0x3b)](id1,sos,0.5,0x1),force=api[_0x35d992(0x1c)](id1,0x1,0.3,0x14,[blockpos[0x0]+0.5,blockpos[0x1],blockpos[0x2]+0.5],!![])[_0x35d992(0xd)],slotidx=api['getSelectedInventorySlotI'](id1),itm=api[_0x35d992(0x2a)](id1,slotidx);if(api[_0x35d992(0xc)](id1)-Math[_0x35d992(0x42)](damage*(0x1-prot))>0x5&&!(api[_0x35d992(0x24)](id1)['includes'](_0x35d992(0x49))||itm[_0x35d992(0x3f)][_0x35d992(0x1e)]===_0x35d992(0x49)))api[_0x35d992(0x50)](id1,-Math[_0x35d992(0x42)](damage*(0x1-prot)),{'lifeformId':_0x1444f4,'withItem':_0x35d992(0x30)});else(api[_0x35d992(0x24)](id1)[_0x35d992(0x53)](_0x35d992(0x49))||itm&&itm[_0x35d992(0x3f)][_0x35d992(0x1e)]===_0x35d992(0x49))&&api[_0x35d992(0xc)](id1)-Math[_0x35d992(0x42)](damage*(0x1-prot))<0x5?(poser=api[_0x35d992(0x11)](id1),api[_0x35d992(0x51)](id1,0xa),api[_0x35d992(0x4d)](id1,_0x35d992(0x40),0x9c40,{'inbuiltLevel':0x2}),api['setShieldAmount'](id1,0x14),api[_0x35d992(0x3b)](id1,'cashRegister',0x1,0x1),api[_0x35d992(0x25)](id1,_0x35d992(0x49)),p3(poser[0x0],poser[0x1],poser[0x2])):api[_0x35d992(0x50)](id1,-Math[_0x35d992(0x42)](damage*(0x1-prot)),_0x1444f4);api[_0x35d992(0x6)](id1,force[0x0]*(rng/0x32),force[0x1]*(rng/0x32),force[0x2]*(rng/0x32));}}explode(coord1,coord2);}}}}}}function isPlayer(_0x2854a6){var _0x4488c7=_0x7735;return api[_0x4488c7(0x2e)]()[_0x4488c7(0x53)](_0x2854a6)||api[_0x4488c7(0x45)]()[_0x4488c7(0x53)](_0x2854a6);}function onPlayerDamagingOtherPlayer(_0x2107fb,_0x3baedb,_0x3225f2){var _0x284ba3=_0x7735;(api[_0x284ba3(0x24)](_0x3baedb)[_0x284ba3(0x53)](_0x284ba3(0x49))||itm&&itm[_0x284ba3(0x3f)][_0x284ba3(0x1e)]===_0x284ba3(0x49))&&api[_0x284ba3(0xc)](_0x3baedb)-_0x3225f2<0x5&&(poser=api[_0x284ba3(0x11)](_0x3baedb),itm&&itm[_0x284ba3(0x3f)]['displayName']===_0x284ba3(0x49)&&api[_0x284ba3(0x21)](_0x3baedb,slotidx,_0x284ba3(0x9),0x0),api[_0x284ba3(0x51)](_0x3baedb,0xa),api[_0x284ba3(0x4d)](_0x3baedb,_0x284ba3(0x40),0x9c40,{'inbuiltLevel':0x2}),api[_0x284ba3(0x28)](_0x3baedb,0x14),api[_0x284ba3(0x3b)](_0x3baedb,_0x284ba3(0x1a),0x1,0x1),api[_0x284ba3(0x25)](_0x3baedb,_0x284ba3(0x49)),p3(poser[0x0],poser[0x1],poser[0x2]));}function onPlayerChangeBlock(_0x16c818,_0x5bf510,_0x9adcdd,_0x3ea6e7,_0x1628d5,_0xe1a78,_0x538cdf,_0x5a7221){var _0x1e8156=_0x7735;_0x1628d5==='Air'&&_0xe1a78===_0x1e8156(0x44)&&(blockUnder=api[_0x1e8156(0x4c)](_0x5bf510,_0x9adcdd-0x1,_0x3ea6e7),blockUnder!==_0x1e8156(0x52)&&api['setBlock'](_0x5bf510,_0x9adcdd,_0x3ea6e7,_0x1628d5));_0x1628d5[_0x1e8156(0x53)](_0x1e8156(0x23))&&_0xe1a78===_0x1e8156(0x14)&&api[_0x1e8156(0x3d)](_0x5bf510,_0x9adcdd,_0x3ea6e7,_0x1628d5);_0xe1a78[_0x1e8156(0x53)](_0x1e8156(0x23))&&(anchors[[_0x5bf510,_0x9adcdd,_0x3ea6e7]]=0x0);if(_0xe1a78===_0x1e8156(0x31)){posers=[[0x1,0x0,0x0],[0x0,0x1,0x0],[0x0,0x0,0x1],[-0x1,0x0,0x0],[0x0,-0x1,0x0],[0x0,0x0,-0x1]];for(i=0x0;i<posers[_0x1e8156(0x2d)];i++){p=posers[i],api[_0x1e8156(0x4c)]([_0x5bf510+p[0x0],_0x9adcdd+p[0x1],_0x3ea6e7+p[0x2]])==='Dim\x20Lamp\x20On'&&api['setBlock'](_0x5bf510,_0x9adcdd,_0x3ea6e7,_0x1e8156(0x14));}}if(_0x1628d5==='Bouncy\x20Bomb\x20Block'&&_0xe1a78===_0x1e8156(0x14)){blockpos=[_0x5bf510,_0x9adcdd,_0x3ea6e7],blockUnder=api[_0x1e8156(0x4c)](blockpos[0x0],blockpos[0x1]-0x1,blockpos[0x2]);if(blockUnder===_0x1e8156(0x52)){coords1=[blockpos[0x0]-0x6,blockpos[0x1]+0x1,blockpos[0x2]-0x6],coords2=[blockpos[0x0]+0x7,blockpos[0x1]+0x7,blockpos[0x2]+0x7],coord1=[blockpos[0x0]-0x4,blockpos[0x1],blockpos[0x2]-0x4],coord2=[blockpos[0x0]+0x4,blockpos[0x1]+0x4,blockpos[0x2]+0x4],enties=api[_0x1e8156(0x54)](coords1,coords2),damage=0x32,prot=0.6,rng=Math[_0x1e8156(0x2f)](Math[_0x1e8156(0x1f)]()*0x64)+0x1,api['playSound'](_0x16c818,sos,0.5,0x1);for(i=0x0;i<enties['length'];i++){id1=enties[i];if(isPlayer(id1)&&api[_0x1e8156(0x32)](id1)){api['playSound'](id1,sos,0.5,0x1),force=api[_0x1e8156(0x1c)](id1,0x1,0.3,0x14,[blockpos[0x0]+0.5,blockpos[0x1],blockpos[0x2]+0.5],!![])['force'],slotidx=api[_0x1e8156(0x26)](id1),itm=api[_0x1e8156(0x2a)](id1,slotidx);if(api[_0x1e8156(0xc)](id1)-Math[_0x1e8156(0x42)](damage*(0x1-prot))>0x5&&!(api['getEffects'](id1)[_0x1e8156(0x53)](_0x1e8156(0x49))||itm[_0x1e8156(0x3f)][_0x1e8156(0x1e)]===_0x1e8156(0x49)))api['applyHealthChange'](id1,-Math[_0x1e8156(0x42)](damage*(0x1-prot)),_0x16c818);else(api[_0x1e8156(0x24)](id1)[_0x1e8156(0x53)](_0x1e8156(0x49))||itm&&itm['attributes'][_0x1e8156(0x1e)]==='Extra\x20Life')&&api[_0x1e8156(0xc)](id1)-Math[_0x1e8156(0x42)](damage*(0x1-prot))<0x5?(poser=api['getPosition'](id1),itm&&itm[_0x1e8156(0x3f)]['displayName']===_0x1e8156(0x49)&&api[_0x1e8156(0x21)](id1,slotidx,'Gold\x20Spade',0x0),api[_0x1e8156(0x51)](id1,0xa),api[_0x1e8156(0x4d)](id1,_0x1e8156(0x40),0x9c40,{'inbuiltLevel':0x2}),api['setShieldAmount'](id1,0x14),api[_0x1e8156(0x3b)](id1,_0x1e8156(0x1a),0x1,0x1),api['removeEffect'](id1,_0x1e8156(0x49)),p3(poser[0x0],poser[0x1],poser[0x2])):api['applyHealthChange'](id1,-Math[_0x1e8156(0x42)](damage*(0x1-prot)),_0x16c818);api['applyImpulse'](id1,force[0x0]*(rng/0x32),force[0x1]*(rng/0x32),force[0x2]*(rng/0x32));}}for(_0x5bf510=coord1[0x0];_0x5bf510<coord2[0x0];_0x5bf510++){for(_0x9adcdd=coord1[0x1];_0x9adcdd<coord2[0x1];_0x9adcdd++){for(_0x3ea6e7=coord1[0x2];_0x3ea6e7<coord2[0x2];_0x3ea6e7++){curBlock=api[_0x1e8156(0x4c)](_0x5bf510,_0x9adcdd,_0x3ea6e7),curBlock!=='Obsidian'&&curBlock!==_0x1e8156(0x4a)&&api['setBlock'](_0x5bf510,_0x9adcdd,_0x3ea6e7,_0x1e8156(0x14));}}}}}}function _0x59d7(){var _0x39765c=['info-circle','playSound','setWalkThroughType','setBlock','6614766TKFcfu','attributes','Health\x20Regen','Diamond\x20Chestplate','round','name','Bouncy\x20Bomb\x20Block','getMobIds','pow','position','glint','Extra\x20Life','Bedrock','setCantChangeBlockRect','getBlock','applyEffect','End\x20Crystal','109866OhrqyA','applyHealthChange','setHealth','Obsidian','includes','getEntitiesInRect','Diamond\x20Sword','Bread','Glowstone','Diamond\x20Boots','1283020wjyjiu','Moonstone\x20Pickaxe','red','applyImpulse','7XryQWF','Arrow','Gold\x20Spade','getPlayerTargetInfo','20758810QwbptD','getHealth','force','Lobby\x20is\x20Full!\x20Max\x20player\x20count:\x2010.','Use\x20Glowstone\x20to\x20charge\x20it.','Try\x20Placing\x20it\x20on\x20obsidian\x20and\x20breaking\x20it.','getPosition','Diamond\x20Helmet','sqrt','Air','847446XvrNXi','getEntityName','cannonFire2','Charges\x20Respawn\x20Anchor.','Diamond\x20Gauntlets','cashRegister','blockID','calcExplosionForce','Cobweb','displayName','random','11gVGsna','setItemSlot','sendTopRightHelper','Dim\x20Lamp','getEffects','removeEffect','getSelectedInventorySlotI','MrChestplate','setShieldAmount','Dim\x20Lamp\x20On','getItemSlot','5xdjIcD','playParticleEffect','length','getPlayerIds','floor','Bouncy\x20Purple\x20Bomb','Golden\x20Decoration','isAlive','Haste','Respawn\x20Anchor','6042664cjuPmo','Subscribe\x20to\x20@Javeline\x20947!\x20Tutorial\x20on\x20Youtube!','141428xthuYO','56KzPxeN','Dim\x20Lamp\x20Off'];_0x59d7=function(){return _0x39765c;};return _0x59d7();}function _0x7735(_0x436af7,_0x59d7c4){var _0x7735c6=_0x59d7();return _0x7735=function(_0xcce612,_0x18d63d){_0xcce612=_0xcce612-0x0;var _0x42cde9=_0x7735c6[_0xcce612];return _0x42cde9;},_0x7735(_0x436af7,_0x59d7c4);}function onPlayerJoin(_0x4c450a){var _0xbde8d3=_0x7735;api[_0xbde8d3(0x2e)]()['length']>0xf&&api[_0xbde8d3(0x16)](_0x4c450a)!==_0xbde8d3(0x27)&&api['kickPlayer'](_0x4c450a,_0xbde8d3(0xe)),api[_0xbde8d3(0x3c)](_0x4c450a,'Bouncy\x20Bomb\x20Block'),api[_0xbde8d3(0x21)](_0x4c450a,0x0,_0xbde8d3(0x55),null),api[_0xbde8d3(0x21)](_0x4c450a,0x1,'Obsidian',0x3e7),api[_0xbde8d3(0x21)](_0x4c450a,0x2,_0xbde8d3(0x44),0x3e7,{'customDisplayName':_0xbde8d3(0x4e),'customDescription':_0xbde8d3(0x10)}),api[_0xbde8d3(0x21)](_0x4c450a,0x3,_0xbde8d3(0x1d),0x3e7),api[_0xbde8d3(0x21)](_0x4c450a,0x4,'Moonstone\x20Orb',0x3e7),api[_0xbde8d3(0x21)](_0x4c450a,0x5,_0xbde8d3(0x0),0x3e7),api[_0xbde8d3(0x21)](_0x4c450a,0x6,_0xbde8d3(0x39),0x3e7,{'customDisplayName':_0xbde8d3(0x34),'customDescription':_0xbde8d3(0xf)}),api[_0xbde8d3(0x21)](_0x4c450a,0x7,_0xbde8d3(0x31),0x3e7,{'customDisplayName':_0xbde8d3(0x1),'customDescription':_0xbde8d3(0x18)}),api[_0xbde8d3(0x21)](_0x4c450a,0x8,'Stone\x20Bow',0x1),api[_0xbde8d3(0x21)](_0x4c450a,0xa,_0xbde8d3(0x8),0x3e7),api['setItemSlot'](_0x4c450a,0x9,_0xbde8d3(0x4),0x3e7),api['giveItem'](_0x4c450a,_0xbde8d3(0x9),0x28,{'customDisplayName':_0xbde8d3(0x49),'customDescription':'With\x20a\x20Twist!'}),api['setItemSlot'](_0x4c450a,0x2e,_0xbde8d3(0x12),null),api[_0xbde8d3(0x21)](_0x4c450a,0x2f,_0xbde8d3(0x41),null),api[_0xbde8d3(0x21)](_0x4c450a,0x30,_0xbde8d3(0x19),null),api[_0xbde8d3(0x21)](_0x4c450a,0x31,'Diamond\x20Leggings',null),api[_0xbde8d3(0x21)](_0x4c450a,0x32,_0xbde8d3(0x2),null),api[_0xbde8d3(0x4d)](_0x4c450a,_0xbde8d3(0x33),null,{'inbuiltLevel':0x5}),api[_0xbde8d3(0x22)](_0x4c450a,_0xbde8d3(0x3a),_0xbde8d3(0x36),{'duration':0xa,'width':0x1f4,'height':0x12c,'color':_0xbde8d3(0x5),'textAndIconColor':'red'}),api[_0xbde8d3(0x4b)](_0x4c450a,[0xe,-0x14,-0x13],[-0x18,0x37,0x1d]);}
```

