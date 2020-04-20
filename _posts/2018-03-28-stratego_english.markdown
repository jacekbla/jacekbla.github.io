---
layout: post_english
title:  "Stratego"
date:   2018-03-28 23:12:50 +0100
featured-img: minmax
categories: [eng]
---
## Project goal
The main goal of the project was to implement the "Stratego" game engine and to analyze algorithms for solving logic games. 
The application was built with the help of external **Qt** libraries.  
The game is about taking subsequent fields on the board. During his move, the player chooses the free field he wants to occupy, if the selected field creates at least one line with other occupied fields (from one edge of the board to another), consisting of at least 3 fields, then receives a number of points equal to the number of fields that make all lines passing through the occupied field are connected. Players take alternating moves. Some game variants award points only for fields previously occupied by one player or one point for each line, regardless of length. Board sizes can be changed in options menu.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/stratego/stratego.jpg)

## Basic algorithms for solving games

### min-max
Min-max is an algorithm used to minimize the possible loss in the worst case scenario and maximize the minimum profit. Originally formulated for two-player zero-sum game theory, covering both cases where players make alternative moves as well as those in which they make moves simultaneously. It has also been extended to more complex games and to make general decisions in the presence of uncertainty.

### alpha-beta
Alpha-beta pruning is a search algorithm that aims to reduce the number of nodes that are evaluated by the min-max algorithm in the search tree. This algorithm is commonly used in two-player computer games.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/stratego/menu.jpg)


## Heuristics

#### Game state heuristics
Three heuristics were used to assess the game status:
- standard - colors (who occupied the node) do not matter, points are awarded for a full edge-to-edge line. The number of points is the same as the length of the line.
- colored - colors matter, points awarded for a full edge-to-edge line. The number of points is equal to the number of nodes of the player's color in the line.
- one per line - regardless of the colors and length, player gets 1 point after finishing a line.

#### Heuristics of node order selection
Two heuristics of node order selection have been implemented:
- standard - the nodes are selected one after the other
- random - the nodes are selected in random order  

[GitHub](https://github.com/jacekbla/si3)