---
layout: post_english
title:  "Tetrises"
date:   2020-01-26 23:12:50 +0100
featured-img: tetris
categories: [eng]
---
## Sprint
During studies, many projects aimed to familiarize students with new technologies. As part of two such courses, I decided to implement the Tetris game. One of them is based on the **.NET** - **C#** and **WPF** environment, the other is based on **Python** and **PyGame**.
Both applications deal with the ***Sprint*** Tetris variant. This mode is to clear a certain number of lines as soon as possible. The most popular is Sprint 40L, which basically mean player needs to lay 40 lines as quickly as possible.

## Python
Less complex, the application consists of only one screen. Settings can only be adjusted via constants in code. The game allows basic controls, such as moving and rotating the block in both directions or immediately lowering the block all the way to the bottom. The interface informs the user about the number of lines done and the time of the game.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/tetris/python.jpg)

[BitBucket](https://bitbucket.org/jacekbla/python_tetris)

## .NET
An application is very similar to the Python equivalent, but supports several additional functionalities. First of all, it contains the main menu and access to several different screens. Among them, the user can change game options and check best results.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/tetris/menu.jpg)

The game itself also includes several helpful functions:
- Hold - a kind of storage, that allows you to replace the current block with the one currently in the storage box.
- Ghost tetromino - the bottom position of the current block is displayed.
- Statistics window - after the game is over the game presents statistics and allows you to save them.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/tetris/stats.jpg)

As part of the classes you had to connect the application with a database, so the results of games are saved in a very simple database.

[BitBucket](https://bitbucket.org/jacekbla/tetris)