---
layout: project
type: project
image: img/boba.png
title: "Playlists"
date: 2022
published: true
labels:
  - Java
  - GitHub
summary: "An interactive program that simulates the user adding, removing, or saving X amount of songs into a playlist that they can save to a file."
---

An interactive program that simulates the user adding, removing, or saving X amount of songs into a playlist that they can save to a file. This program has at least 5 song objects with valid data and uses three custom methods that work within each other. There are also custom exceptions that catch the user from entering anything out of bounds.

<div class="text-center p-4">
  <img width="200px" src="../img/java1.png" class="img-thumbnail" >
  <img width="200px" src="../img/java2.png" class="img-thumbnail" >
  <img width="200px" src="../img/java3.png" class="img-thumbnail" >
</div>

For this project, I was the lead programmer who was responsible for programming the various capabilities of the mouse.  I started by programming the basics, such as sensor polling and motor actuation using interrupts.  From there, I then programmed the basic PD controls for the motors of the mouse.  The PD control the drive so that the mouse would stay centered while traversing the maze and keep the mouse driving straight.  I also programmed basic algorithms used to solve the maze such as a right wall hugger and a left wall hugger algorithm.  From there I worked on a flood-fill algorithm to help the mouse track where it is in the maze, and to map the route it takes.  We finished with the fastest mouse who finished the maze within our college.

Here is the output code the user is prompted with:

```cpp
Lets listen to some tunes !!
	** Boba **
[
Title: SUNSET BOULEVARD (3: 10) by HOHYUN, 
Title: KISS ME (3: 32) by DPR LIVE, 
Title: Peanut Butter & Tears (3: 44) by DPR IAN, 
Title: airplane thoughts (3: 30) by dhruv, 
Title: War With Heaven (3: 12) by Keshi]
Do you like it? Should I make any changes?
yes
Should I add, or remove a song... or nevermind?
nevermind
Great, I hope you liked it!!
Heres how the playlist looks so far :D!!
[
Title: SUNSET BOULEVARD (3: 10) by HOHYUN, 
Title: KISS ME (3: 32) by DPR LIVE, 
Title: Peanut Butter & Tears (3: 44) by DPR IAN, 
Title: airplane thoughts (3: 30) by dhruv, 
Title: War With Heaven (3: 12) by Keshi]
Did you want to save the playlist so you can listen to it later?
yes
You can save it to a file, type yes or no...
no
You just lost all your songs!
Its okay though, just restart...

Thanks for using my program!! :D

```

You can learn more at the [UH Micromouse News Announcement](https://manoa.hawaii.edu/news/article.php?aId=2857).
