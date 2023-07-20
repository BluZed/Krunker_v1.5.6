<div align="center">
  	<p align="center">
		<a><img src="https://krunker.io/img/krunker_logo_0.png" width="600"></a>
  	</p>
</div>

# Krunker v1.5.6 - Offline

>**Note: I do not own this, the credit goes to the Krunker Developer Team & related people who made / contributed to the game and if they want this or any part of this removed, I'm willing to do so, without any strings attached.**
>

Yeah this is exactly what the title says. 
This is Krunker, version 1.5.6 released on August 19, 2019, which is just the version in which the commando class was added in game. I made it so that you can play that version of the game, right now, by downloading this and following the instructions properly. However, there are some major drawbacks.
1) Multiplayer **does not** work. Support for multiplayer may be added in future.
2) Only 5 Maps: Burg, Littletown, Old Kanji, Subzero and Sandstorm exist in-game.
3) You currently **cannot** load custom maps. This also may be added in future updates. You can probably load mods if made correctly for this version of the game, though this hasn't been tested.
4) Community mods, Community maps, Online servers will show nothing.
5) **Last and a very important point: Logins will not work and please do not try to login to your account for security reasons.** Just for fun, the name that displays in the leaderboard when you play the game is Sidney ;)
<div align="center">
  	<p>
		<a><img src="https://media.discordapp.net/attachments/1100782582678954107/1129665343632187543/snap.png" width="600" height="300"></a>
		<br><br><br>
		<a href="https://discord.com/channels/448194623580667916/534719260497543169/612941468763684864"><img src="https://media.discordapp.net/attachments/1100782582678954107/1129644608830308402/image.png" width="600" height="250"></a>
  	</p>
</div>
^ Click the image above to go the message in Krunker Bunker discord.
<div><br></div>
This is solely made for the purpose of revisiting og krunker by players who used to play the game or for people who are just curious.
A heads up, slidehopping was a bit different back then ;)
<div><br></div>


### Important: Keybinds
- **F4 = Cycle between the maps**
- **F11 = Toggle Fullscreen**
- **F9 = Open Inspect Element**
- **Escape = Exit pointer lock**

# Usage
[Node.js (nodejs.org)](https://nodejs.org/en) must be installed on your PC. 
This has been tested to work as intended on [Node.js v18.16.1](https://nodejs.org/download/release/v18.16.1/)
Please install Node.js before attempting any of the steps below.

You need a video tutorial? Here ya go: [Link to Youtube Video](https://www.youtube.com/watch?v=aPvZdDX10IQ)

1) Download the Source Code as a [Zip](https://github.com/BluZed/Krunker_v1.5.6/archive/refs/heads/main.zip) or via git.
2) Open Terminal and ```cd``` into the folder containing the source code.
3) Run ```npm i```  to install dependencies and after that completes,
4) Run ```npm start``` to start game.

> Note: Step 1 and Step 3 only need to be run once. You can start from Step 2 and then do Step 4 once you have done all of them once in the correct order, to start the game again.
> During Step 2, remember that the correct folder which should be your current working directory is the one which has the package.json file.


*Happy Gaming!*
# Some Extra Customizations 
> The following text is irrelevant for people who don't know javascript so no point in reading allat and also a prerequisite knowledge of Node.js & Electron would be nice to have, to properly understand how the code works.

Hmm, so you want to change the way the game works? or you want to help me with the server logic? Well, Pull Requests are always welcome!
I'll give you a headstart. 

- Game Code: `main/krunkerio/js/game.D28pq.js` 
- Server Code (though doesn't do much):`main/gameserver.js`
- Game assets folder: `main/krunkerio`
- Electron app files: `main/main.js` `main/preload.js`

It would be awesome if someone figured out the server part of the code since that would help with enabling multiplayer, and also I'd be willing to help in doing so. (I just couldn't figure that out myself) Also to edit these files I'd recommend using a good IDE, I personally prefer [Visual Studio Code](https://code.visualstudio.com/) but it's totally upto you. 

You may notice there are two `game.D28pq.js` files in there, out of which one of them starts with `___UNTOUCHED___game.D28pq`, well the name speaks for itself and it is the unedited game.js file but if you plug it in it won't work due to some bug in receiving packets from server (this bug was around line `80555` in the edited `game.D28pq.js` file) and if it works, you still won't be able to spawn in because the game expects the server to tell it that you can spawn in and also along with some more data which I could not figure out. 

What I did as a workaround was enable single player mode by editing the part where the game checks if you are testing some map and voila! you can spawn in. These lines would be around line no. `82503` and `85378` in the edited `game.D28pq.js` file. I mostly commented out the part which i had to remove from the file to make it obvious that it was edited. 

Line `80696` exposes the Game variable to the global window variable, and makes it available as `window.game`. It can be used in the electron `main/preload.js` file.

Game server code at `main/gameserver.js` is completely made my me and can be improved. All it does is make the game think its connected to a server and also it manages the game time & the map which is loaded in game. It is also the next step to achieving multiplayer and all the packet labels that would be relevant here are around line `85552` in the edited `game.D28pq.js` file.

Currently I haven't added any code into the game source file that connects the game to the locally hosted websocket, I make the game forcefully connect only to `ws://localhost:8080/` by hooking the global websocket class and this part of the code is available in the electron `main/preload.js` file.

My Discord is `bluzed` (no discrim tag),  feel free to dm me.

I wish you good luck with your code!

<br><p align=center>***</p>
