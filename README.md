

<!DOCTYPE html>
<html>
<head>
<title> Debugging Nightmare </title>
<style>
body {
background-color: aqua;
font-family: Arial, sans-serif;
margin:0px;
padding:0px;
}
h1{
color:blue;
font-size:30px;
text-align:center;
}
.container{
width:80%;
margin:auto;
border:2px solid black;
padding:20px;
background-color:lightblue;
border-radius:20%;
align-items: centre ;
justify-content: centre ;
}
button:hover{
  background-color: Lightgreen;
  color:black;
}
button{
padding:10px 20px;
margin:5px;
cursor:pointer;
background-color: green;
color:white;
border:none;
border-radius:10%;
}
#output{
margin-top:20px;
font-size:18px;
color:red;
}
.hidden{
display:none;
}
</style>
</head>
<body>
<h1> Messy Debugging Playground </h1>
<div class="container">
<p id="intro">Welcome to the debugging test zone</p>
<button onclick="startGame()">Start</button>
<button onclick="toggleMessage()">Toggle Message</button>
<button onclick="checkLogic()">Check Logic</button>
<button onclick="resetAll()">Reset</button>
<div id="output"></div>
</div>

<script>
// Messy JavaScript with only functions, objects, booleans, logical operators

var gameState = {
    started:false,
    attempts:0,
    player:{name:"ROG", active:true, score:0},
    settings:{mode:"easy", sound:true, debug:false}
};

function startGame(){
    if(!gameState.started && gameState.player.active && gameState.settings.sound===true)
    {
        gameState.started=true;
        gameState.attempts=gameState.attempts++;
        document.getElementById("output").innerHTML="Game Started for "+gameState.player.name;
    }
     else if (gameState.started===true && !gameState.settings.debug)
     {
        document.getElementById("output").innerHTML="Already started!";
    }
     else {
        document.getElementById("output").innerHTML="Conditions failed!";
    }
}
 var msgObj={visible:true, text:"Hidden message appears"};
function toggleMessage(){
    if(msgObj.visible && gameState.player.active || !gameState.settings.sound)
    {
        document.getElementById("output").innerHTML=msgObj.text;
        msgObj.visible=false;
    } 
    else if(!msgObj.visible && gameState.settings.debug===false)
    {
        document.getElementById("output").innerHTML="Message is hidden now";
    } else {
        document.getElementById("output").innerHTML="Toggle failed";
    }
}
var logicObj={a:true, b:false, c:true}; 
 function checkLogic(){
if (logicObj.a && !logicObj.b || (logicObj.c && gameState.started))
    {
        document.getElementById("output").innerHTML="Logic Passed!";
        gameState.player.score=gameState.player.score++;
    }
     else if((!logicObj.a && logicObj.b) || !gameState.player.active)
     {
        document.getElementById("output").innerHTML="Logic Failed!";
    } 
    else {
        document.getElementById("output").innerHTML="Logic Confused!";
    }
}

function resetAll(){
    gameState.started=false;
    gameState.attempts=0;
    gameState.player.score=0;
    gameState.settings.sound=true;
    gameState.settings.debug=false;
    if(!gameState.started && gameState.settings.sound && !gameState.settings.debug){
        document.getElementById("output").innerHTML="Reset complete!";
    } else {
        document.getElementById("output").innerHTML="Reset error!";
    }
}
</script>
</body>
</html>
