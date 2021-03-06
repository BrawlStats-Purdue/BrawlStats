![Logo-min](https://user-images.githubusercontent.com/22580992/79498091-c3177c00-7ff6-11ea-9396-c70632cb44bb.png)

## Table of Contents

1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
1. [Schema](#Schema)

## Overview

### Description

A simple app that tracks the statistics of a user who plays the BrawlStar Game

### App Evaluation

- **Category:** Game
- **Mobile:** iOS
- **Story:** BrawlStars is a mobile game that is played by millions around the world, there is currently no way to view BrawlStars stats through a mobile app. This app will show a users personal stats and other users stats as well.
- **Market:** BrawlStars players
- **Habit:** Active player will constantly check for their stats
- **Scope:** All players

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

- Show User Stats
- Trophy Graph
- Show Global Stats: Top Users and Top Clubs
- Search other people's stat

**Optional Nice-to-have Stories**

- Club stats
- Club member changes over time

### 2. Screen Archetypes

- Profile
  - Show User Stats
  - Trophy Graph
- Search (Search User Tag)
  - Login
- Stream
  - Search other people's stat

### 3. Navigation

**Tab Navigation** (Tab to Screen)

- Personal Stats
- Search
- Global Rankings

**Flow Navigation** (Screen to Screen)

- Personal Stat
- Search
  => User Stats
  => Personal Stats
- Global Stats
  => User Stats

## Wireframes

<img src="https://imgur.com/8QAaVzP.png" width=600>

## Design Development

### Final Logo

![Logo](https://user-images.githubusercontent.com/22580992/79077922-c0edae80-7cd2-11ea-9701-ffd1bd85e6f2.png)

## Development Screenshots

### Profile Page with Design
![dark](https://user-images.githubusercontent.com/22580992/80891265-edbd3200-8c90-11ea-86ec-d68a581c94de.png)

### No Design Search Page (and search page with recent searches)

<img width="230" alt="Screen Shot 2020-04-01 at 6 19 47 PM" src="https://user-images.githubusercontent.com/22580992/78513401-563fee80-7779-11ea-934c-959eb4937042.png">
<img width="230" alt="Search Page with previous search results" src="https://i.imgur.com/ge9lZpj.png">

### Personal Stat Page
<img width="230" alt="Screen Shot 2020-04-01 at 6 19 47 PM" src="https://imgur.com/l5SA2bM.png">

The image on the right is the final update for functionality on the Search Page. Styling will be coming in Sprint 3.

### Sprint 3 App Demo
<img width="230" alt="Sprint 3 Gif" src="http://g.recordit.co/UcSH9iwJyO.gif">

With Sprint 3, we completed a lot of the UI for the App. Additionally, the recent searches area is now fully functional. We also implemented a system to dynamically change the brawler image we show based on the highest trophy brawler of the player.

### Sprint 4 App Demo
<img width="230" alt="Sprint 4 Gif" src="https://media.giphy.com/media/LrEt1cIIgBEyzIy1Pd/giphy.gif">

With sprint 4, we finished all of our required User Stories and even added in strong Auto Layout support. Our App now has a built in Trophy Graph that maps out trophy gains and losses over the past 25 games. Additionally, we now show a brief battlelog to give the player a sense of how they are doing over their previous games. 

[High Resolution Final Demo](https://youtu.be/R7m99P3O8qg)

### Demos on Other Devices
#### iPad
<img width="230" alt="StatStars running on iPad" src="https://i.imgur.com/LpQ7prr.png">
<img width="230" alt="StatStars running on iPad" src="https://i.imgur.com/VUhrSYm.png">

#### iPhone 8
<img width="230" alt="StatStars running on iPhone 8" src="https://i.imgur.com/at5QlnB.png">
<img width="230" alt="StatStars running on iPhone 8" src="https://i.imgur.com/bC51kEl.png">

## Schema

### Models

#### Player

| Property       | Type   | Description                                                                                |
| -------------- | ------ | ------------------------------------------------------------------------------------------ |
| tag            | String | A unique tag, provided from brawlstars for each player of the game                         |
| ourRank        | Number | [Optional] if API doesn't provide Ranking this will be a ranking with respect to our users |
| brawlstarsRank | Number | Global Ranking of Player                                                                   |

#### Match

| Property       | Type   | Description                                          |
| -------------- | ------ | ---------------------------------------------------- |
| trophiesEarned | Number | The number of trophies gained or lost during a match |
| battleTime     | Number | The time the battle happened                         |
| event          | Event  | The details about the match                          |

#### Event

| Property | Type   | Description                      |
| -------- | ------ | -------------------------------- |
| map      | String | the map that the was played      |
| id       | String | the type of Game that was played |

### Networking

#### List of network requests by screen

Our application does not use any requests other than API requests from Brawlstars API

#### API Endpoints

Base URL -

| HTTP Verb | Endpoint                                     | Description                                                                                                                     |
| --------- | -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| GET       | /players/{playerTag}                         | Get information about a single player by player tag. Player tags can be found either in game or by from clan member list.       |
| GET       | /players/{playerTag}/battleLog               | Get list of recent battle results for a player.                                                                                 |
| GET       | /rankings/{countryCode}/players              | Get player rankings for a country or global rankings.                                                                           |
| GET       | /rankings/{countryCode}/brawlers/{brawlerId} | Get brawler rankings for a country or global rankings. Brawler identifiers can be found by using the /v1/brawlers API endpoint. |
| GET       | /brawlers                                    | Get list of available brawlers.                                                                                                 |
| GET       | /brawlers/{brawlerId}                        | Get information about a brawler.                                                                                                |
