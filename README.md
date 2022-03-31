![DataH](https://user-images.githubusercontent.com/67437213/160717510-3a182d88-0908-4f5c-aae2-b5e52b2c879d.JPG)
# Poker hands evaluator

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=UNDER%20DEVELOPMENT&color=GREEN&style=for-the-badge)

### This is a project in Python 3.7.13 written by Igor Nogueira, to help a famous casino to increase its revenue by the development of a online poker game to be further offered to the users. Here, you'll find a poker hands evaluator, that receives two poker hands and determines if the first hand wins or loses to the second hand.

## Contents
* [Poker game](#Poker-game)
* [Hand Ranks](#Hand-Ranks)
* [Code explained](#Code-explained)
   * [Class definition](#Class-definition)
   * [Card treatment](#Card-treatment)
   * [Coding the hand possibilities](#Coding-the-hand-possibilities)
   * [Auxiliary methods](#Auxiliary-methods)
   * [Hand ranks](#Hand-ranks)
   * [Tie-breaker and comparisons of two hands](#Tie-breaker-and-comparisons-of-two-hands)
   * [Tests](#Tests)
   
### Poker game

![poker hand](https://user-images.githubusercontent.com/67437213/160718241-0023ae13-875e-4129-92b6-a10132238eff.JPG)

Poker is a card game that can be played by 2 or more people, which consists (in the most popular mode) that each player has five cards in its hand, evaluates what's the rank of your hand (there are 10 possible hand ranks, later it'll be described) and bets poker chips, which represents some money value. In this project we'll consider a deck of 52 cards, four cards to each denomination.

Each card has a value, which is defined by the number of the card or the following letters: J, Q, K, A. Specifying the values:
+ From 2 to 10, the value is the number;
+ J = 11; Q = 12; K = 13; A = 14.

Each card has a suit, which can be: Spades (S), Diamonds (D), Clubs (C) or Hearts (H).

### Hand Ranks

There are 10 possible hand ranks, which are described as follows:
![hand ranks](https://user-images.githubusercontent.com/67437213/160902018-4a2417a5-6012-4cfa-ac22-d5521543f209.JPG)

<table border="1">    
  <tr>
    <th colspan="5">Hand ranks</th>
  </tr>        
  <tr>
    <td><b>Hand possible</b></td>
    <td><b>Rank</b></td>
    <td><b>Probability</b></td>
    <td><b>Description</b></td>
    <td><b>Tiebreaker</b></td>    
  </tr>
  <tr>
    <td>Royal Flush or Royal Straight Flush</td>
    <td>1st</td>
    <td>0.000154%</td>
    <td>The sequence is: A, K, Q, J, 10, all of the same suit.</td>
    <td>There's no possibility to have a tiebreaker in this case.</td>
  </tr>
  <tr>
    <td>Straight Flush</td>
    <td>2nd</td>
    <td>0.00139%</td>
    <td>It happens when there are five cards in denomination sequence, which the high value is from 6 to K(13) and in the same suit.</td>
    <td>The tiebreaker is by the high value of the sequence.</td>
  </tr>
  <tr>
    <td>Four of a kind</td>
    <td>3rd</td>
    <td>0.02401%</td>
    <td>Happens when there are four cards of the same denomination.</td>
    <td>The tiebreaker is by the high value of the four of a kind.</td>    
  </tr>
  <tr>
    <td>Full house</td>
    <td>4th</td>
    <td>0.1441%</td>
    <td>It's described when there are three cards of the same denomination and two of another denomination.</td>
    <td>The tiebreaker consists in analyzing the high value of the three of a kind in the hand.</td>    
  </tr>
  <tr>
    <td>Flush</td>
    <td>5th</td>
    <td>0.1965%</td>
    <td>Happens when there are five cards of the same suit, but not in denomination sequence.</td>
    <td>The tiebreaker is the high value of the card, and goes like that until break the tie. It's possible to have a draw if ties in all comparisons.</td>    
  </tr>
  <tr>
    <td>Straight</td>
    <td>6th</td>
    <td>0.3925%</td>
    <td>It happens when there are five cards in denomination sequence, not necessarily in the same suit.</td>
    <td>The tiebreaker is by the high value of the sequence.</td>    
  </tr>
  <tr>
    <td>Three of a kind</td>
    <td>7th</td>
    <td>2.1128%</td>
    <td>Happens when there are three cards of the same denomination.</td>
    <td>The tiebreaker consists in analyzing the high value of the three of a kind.</td>    
  </tr>
  <tr>
    <td>Two pair</td>
    <td>8th</td>
    <td>4.7539%</td>
    <td>Happens when there are two cards of the same denomination and two cards of another denomination.</td>
    <td>The tiebreaker consists in analyzing the high value of the two pairs, one by one. If doesn't break the tie, the comparison goes to the remaining card denomination by the high value. It's possible to have a draw if ties in all comparisons.</td>    
  </tr>
  <tr>
    <td>One pair</td>
    <td>9th</td>
    <td>42.2569%</td>
    <td>Happens when there are two cards of the same denomination.</td>
    <td>The tiebreaker consists in analyzing the high value of the one pair. If doesn't break the tie, the comparison goes to the 3 remaining cards denomination by the high value, until have a winner. It's possible to have a draw if ties in all comparisons.</td>    
  </tr>
  <tr>
    <td>High card</td>
    <td>10th</td>
    <td>50.1177%</td>
    <td>Happens when there aren't any of the another 9 hand ranks. The card with the highest denomination is considered.</td>
    <td>If have a tie, goes to the highest denomination of the 4 remaining cards and so on until break the tie. It's possible to have a draw if ties in all comparisons.</td>    
  </tr>  
</table>

### Code explained
In this section, there are the different stages of the code to reach the solution. Each stage has a link to better explanations.

#### Class definition -> https://github.com/igors96/PokerHand/blob/main/Class_definition.md

#### Card treatment -> https://github.com/igors96/PokerHand/blob/main/Card_treatment.md

#### Coding the hand possibilities -> https://github.com/igors96/PokerHand/blob/main/Hand_possibilities.md

#### Auxiliary methods -> https://github.com/igors96/PokerHand/blob/main/Auxiliary_methods.md

#### Hand ranks -> https://github.com/igors96/PokerHand/blob/main/Hand_ranks.md

#### Tie-breaker and comparisons of two hands -> https://github.com/igors96/PokerHand/blob/main/Tiebreaker_comparisons.md

#### Tests -> https://github.com/igors96/PokerHand/blob/main/Tests.md

