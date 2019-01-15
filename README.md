[![Build Status](https://travis-ci.org/UMM-CSci-3601-F17/iteration-3-raymond-shayler.svg?branch=style-like-shayler)](https://travis-ci.org/UMM-CSci-3601-F17/iteration-3-raymond-shayler)

<!-- TOC depthFrom:1 depthTo:5 withLinks:1 updateOnSave:1 orderedList:0 -->
## Table of Contents
- [Welcome](#welcome)
- [Concept and Gameplay](#concept-and-gameplay)
- [Features](#features)
- [Technologies](#technologies)
- [Gradle Tasks](#gradle-tasks)


<!-- /TOC -->

## Welcome
Thank you for your interest in the SAGE project. SAGE is an educational and customizable 
game that is designed for teachers to help students learn new vocabulary words. This particular
version of SAGE is targeted for elementary aged students.

## Concept and Gameplay

![Screenshot](gameplay.png)

SAGE is played with one or more players. These players can take turns at having 
different roles during the game. One player is shown a word on a card that is 
displayed on the screen of a device. Their goal is to correctly identify what 
that word means. The other players will judge whether or not 
the guesser has correctly identified the meaning of the word. Players who are 
guessing can also receive hints. These hints come in four different
varieties: synonyms, antonyms, general senses, and example usages (SAGE). 
Synonyms and antonyms are pretty self explanatory, whereas a general sense 
provides a basic description of the word, and an example uses the word in a 
sentence. Four hints can be shown per card, one of each type, and will appear 
in a random order. If a player can guess what a word means without using any hints, 
they will receive five points. Each time a hint is used, a point will be subtracted 
from the score they will receive from that card.

## Features

Teachers are able to login using google authentication to access customization tools, whereas students can simply begin playing without these options being visible. Players can choose a deck to play with, the number of players there will be in a game, and a color which will represent the player whose turn it is. During the game, players can press a hint or got it button, or skip ahead to another card. A peek button which will display all of the hints on a card can be pressed to help the judgers, which will not affect the guessers score. At the end of a game, a results dialog will pop up which will indicate the scores of each of the players.
 
From the homepage and playpage, a help page which explains the rules of the game as well as some of the customization tools is available.
 
There is a deck page which displays all of the decks in the system and allows for the creation of new decks. Individual deck names can be clicked on from this screen which will take you to a page that displays all of the cards within that deck and will allow additional cards to be added to it. Deck names can be edited from this page, and decks themselves can also be deleted.
 
There is also a card list page which displays the words of every card in the system across all decks and a menu for selecting, adding, deleting cards, and a dropdown for selecting decks. If a card is clicked on and no button is selected, the full content of that card will appear on the screen in a dialog. If the select button is pressed, when cards are pressed they will light up blue to indicate that they have been selected. Once a deck is selected, the add and delete buttons are available to press. When either are pressed, the selected cards are added or deleted from the selected deck, and a dialog will pop up that shows the changes that have been made and will allow a user to see those changes if they desire. Selected cards can be wiped by pressing the cancel button. Cards can also be permanently removed from the system from this screen by pressing the trash icons inside of the full view of a card. 

![Screenshot](card-list.png)


## Technologies

The front end technologies of SAGE primarily consist of HTML, CSS, and Typescript 
which are used in conjunction with an Angular4 framework. The front end angular components
can be found in client/src/app path.  Because typescript is being used, we recommend ignoring messages that may ask to compile the code into javascript as it will cause numerous errors. We have also incorporated various Material Design and Covalent styling modules into our components. There are angular jasmine and karma unit tests included with each of our components, along with protractor and selenium webdriver end to end tests located in the e2e directory. With regards to the backend,
we have used a java spark server that interacts with a MongoDB database. It is tested with Java unit 
testing. We have a REST API that is located in the /server/src/main/java/umm3601/Server.java
path. We are also using both yarn and npm as package managers. Travis CI is currently being used
our continuous integration service. Gradle is used to manage launching
various local tasks, which are described in the next section.

## Gradle Tasks

* `runAllTests` runs both the server tests and the clients tests once.
* `runClientTests` runs the client tests once.
* `runClientTestsAndWatch` runs the client tests every time that the code changes after a save.
* `runClientTestsWithCoverage` runs the client tests and deposits code coverage statistics into a new directory within `client` called `coverage`. In there you will find an `index.html`. Right click on `index.html` and select `Open in Browser` with your browser of choice. For Chrome users, you can drag and drop index.html onto chrome and it will open it.  
* `runE2ETest` runs end to end test for the client side. NOTE: Two Gradle tasks _must_ be run before you can run the e2e tests. 
The server (`run`) needs to be on for this test to work, and test data
must have been seeded into the database before running this task. We also recommend that the database be cleared and then re-seeded prior to each run of these tests. Certain tests may fail randomly up to half of the time they are run.
* `run` will run the server (which is available at ``localhost:4567``)
* `build` will build the application but not run anything.
* `runClient` task will build and run the client side of the application (available at ``localhost:9000``)
* `clearMongoDB` will clear the database of all local data.
* `seedMongoDB` will populate the database with the data provided in the cards.seed.json and decks.seed.json files.

Please note that a `useAuth` property within the `config.json` file detailed by the SETUP documentation should be set
to false prior to running tests.
