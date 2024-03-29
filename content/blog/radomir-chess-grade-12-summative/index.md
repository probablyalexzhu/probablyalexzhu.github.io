---
title: "Radomir Chess: Grade 12 Summative"
tags: [projects, java, swing, networking]
date: 2022-01-30
showDate: true
showWordCount: true
showReadingTime: true

# summary: "Hi! My name is Alex Zhu."
showSummary: true
showAuthor: true
showTableOfContents: false
showComments: true
showPagination: true
invertPagination: true
showTaxonomies: true

draft: false
---
This is the Readme file from our Grade 12 summative project. You can view the repository here: https://github.com/Edison-Du/Radomir-Chess.

![Radomir Chess Logo and Name.](thumb.png "Radomir Chess Logo and Name.")


## Overview

Radomir Chess is our ambitious Lichess/Chess.com-like chess application that runs purely on Java Swing. It features networking for many simultaneous multiplayer lobbies, a sophisticated and efficient chess engine, and an excellent UI complete with a login system. Our chess application is named after our computer science teacher, who will be marking this summative project.

We have packed Radomir Chess with features for a truly fun and functional chess application, but there are potential rooms for improvement. Mainly, implementing a chess clock could help create more timely matches, and an elo system could raise the stakes of the already exciting games.

## How to Install

Do the following:
* download and unzip the repository

For local use:
* run one instance of Application.java found in the server folder
* run as many instance of Application.java found in the client server as desired
* make sure that the IP address in client > config > Consts.java is 127.0.0.1

For online use:
* run as many instance of Application.java found in the client server as desired
* make sure that the IP address in client > config > Consts.java is the IP address of the server being run on a VM (the IP can be found in file)
* this will only work while the VM is being run, which cannot be guaranteed as this is a school project not meant for permanent hosting.

## How to Use

The Swing interface is intuitive. Use the left navigation bar to navigate between pages. The landing page will allow you to enter a chess match.
* To create a game (public or private), press Create Game. To join a public game, you can find it in the Browse Games page or type in a game code in the Join Game page. Private games can only be joined by entering the lobby code on the Join Game page. To play against our bot, click Play Bot.
  * In the chess match, drag the pieces to make move. On the right bar, you can chat with your opponent and offer a takeback, draw, or resign.
* In Settings, you can customize your game experience from 18 custom chess board themes, 5 custom chess piece sets, and 11 possible move colours. You can also toggle on/off move sounds and possible moves.
* The About Page tells you about Radomir Chess.
* In Login, you can register or login an account, which will let you display a custom username and save your custom settings.
* Quit closes the application (but why would you ever want to do that?). If you ever want to return to the landing page, just press Play on the left navigation bar.

## Images

![image](https://user-images.githubusercontent.com/87958079/150737376-771f29b6-59cb-4439-a55e-71469d5501b5.png)
![image](https://user-images.githubusercontent.com/87958079/150737504-71346c03-2e8d-4e9c-873f-97fc086a4393.png)

## Credits

This application was built by Team JPANEL, which incredibly, is an acronym for the team's developers Jeffrey X, Peter G, Alex Z, Nicholas C, Edison D, and Leo G.

Thanks to Jeffrey for his expertise in UI implementation. Thanks to Peter for his work on the chess engine and the account system. Thanks to Alex for his networking and chess game UI/UX contributions. Thanks to Nicholas for his handling of game lobbies and UI design. Thanks to Edison for designing the overall client/server system, leading the project and lending a hand to everyone. And Thanks to Leo for his crafting of the chess engine and game logic.

Credit to Lichess and Chess.com, from which much inspiration and assets for features and graphics were sourced.

**We hope that you enjoy Radomir Chess!**