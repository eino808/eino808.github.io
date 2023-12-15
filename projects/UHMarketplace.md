---
layout: project
type: project
image: img/play.png
title: "Playlist"
date: 2023
published: true
labels:
  - Java
  - GitHub
summary: "A makeshift playlist project that I developed for ICS 111"
---

This interactive program serves as a simulation allowing users to add, remove, or save a specified number of songs (X amount) to a playlist, which can be stored in a file. 

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

```

Within this program, you'll find a collection of no less than five song objects, each containing valid data. To make these operations smoother, the program uses a set of three personalized methods that work together in harmony. Moreover, the custom exceptions help catch any input errors from users that might be out of the valid range. While it may not rival the features of platforms like Spotify, the program emulates the experience of managing and organizing songs within a playlist.

```java

public class SongException extends Exception {
   
   private String message = "";
    public SongException() {
    }
    public String getMessage() {
      return this.message;
    }
    public void setMessage(String newMessage) {
      this.message = newMessage;
    }
}

```
```java

public class Song {
   
   private String title = "";
   private String artist = "";
   private int min = 0;
   private int sec = 0;

   public Song (String title, String artist, int min, int sec) throws Exception {
      this.setTitle(title);
      this.artist = artist;
      this.min = min;
      this.sec = sec;
   }
   
   public String getTitle() {
      return this.title;
   }
   
   public String getArtist() {
      return this.artist;
   }
   
   public int getMin() {
      return this.min;
   }
   
   public int getSec() {
      return this.sec;
   }
    
   public void setTitle(String newTitle) throws Exception {
      if (newTitle.length() > 1) {
         this.title = newTitle;
      }
      else {
         SongException se = new SongException();   
         se.setMessage("\t\t***ERROR ERROR ERROR*** " + "\n\t" + newTitle + " \tis not valid.");
         throw se; 
      }
   }
   
   public void setArtist(String newArtist) throws Exception {
      if (newArtist.length() > 1) {
         this.artist = newArtist;
      }
      else {
         SongException se = new SongException();   
         se.setMessage("\t\t***ERROR ERROR ERROR*** " + "\n\t" + newArtist + " \tis not valid.");
         throw se; 
      }
   }

   public void setMin(int newMin) throws Exception {
      if (newMin > 0 && newMin  < 60) {
         this.min = newMin;
      }
      else {
         SongException se = new SongException();   
         se.setMessage("\t\t***ERROR ERROR ERROR*** " + "\n\t" + newMin + " \tis not valid.");
         throw se; 
      }
   }

   public void setSec(int newSec) throws Exception {
      if (newSec > 0 || newSec < 60) {
         this.sec = newSec;
      }
      else {
         SongException se = new SongException();   
         se.setMessage("\t\t***ERROR ERROR ERROR*** " + "\n\t" + newSec + " \tis not valid.");
         throw se; 
      }
   }
   
   public String toString() {
      String output = ""; 
      output += "\nTitle: " + this.title + " (" + this.min + ": " + this.sec + ") " + "by " + this.artist;
      return output;
   }
}

```
Above, are snippets of the custom exception, and the class designed for modeling the song object.

