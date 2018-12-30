---
layout: default
title: Hue for Discord
nav_order: 2
has_children: true
permalink: /docs/discord-hue
published: true
---

## Hue for Discord is a Discord.js bot that can control your lights from a Discord server.
The Hue bot is written in Node.js using two main packages:

 * `discord.js`
 * `node-hue-api`
 ___
 ## Configuration - Hue
Firstly, you're going to need to IP Address of you Hue Bridge. This can be done multiple ways, but we'll use the `node-hue-api` JS package here. Create a new JavaScript file in your Node.js project folder and use the following code:

```js
//Import the Hue API
var hue = require("node-hue-api");
//Discovery Function
var displayBridges = (bridge) => {
 	console.log("Hue Bridges Found: " + JSON.stringify(bridge)); 
};
//Function Call Using a Promise
hue.nupnpSearch().then(displayBridges).done();
```
You should receive something resembling the following:
```Hue Bridges Found: [{"id":"001728fffefd1d65","ipaddress":"192.168.1.164"}```
Next, to continue further, we're gonna need a username on the bridge. This is obtained by making a POST request to `IP/api` with a JSON body containing the following:
```json
{"devicetype":"Hue for Discord"}
```
Once again, this can be achieved multiple ways, but we'll be using Node.js again. Here's the code:
```js
//HTTP Request Library
var request = require("request");
//JSON Data to be passed to the bridge
var requestData = {"devicetype":"Hue for Discord"};

//Create URL (be sure to put your own IP address below
var ip = "Input Your Bridge IP Address Here";
var url = ("http://" + ip + "/api");

request({
  	url: url,
  	method: "POST",
  	json: requestData
}, function(error, response, body) {
 
  if (!error && response.statusCode == 200) {
   	console.log(body); 
  } else {
   
    console.log("Error: " + error)
    console.log("Status Code: " + response.statusCode)
    console.log("Status Text: " + response.statusText)
    
  };
  
});
```
Before running the above code, __make sure to press the link button on your Bridge__, otherwise you'll be left with an error similar to this:
```json
[ { error: 
     { type: 101,
       address: '',
       description: 'link button not pressed' } } ]
```
If you did press the link button however, you'll be greeted with this:
```json
[
  {
    "success": {
      "username": "508ed817c37c378e20ab523f25c4b"
    }
  }
]
```
_(sidenote - the username is randomly generated.)_
