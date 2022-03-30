![DataH](https://user-images.githubusercontent.com/67437213/160717510-3a182d88-0908-4f5c-aae2-b5e52b2c879d.JPG)
# Poker hands evaluator

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=UNDER%20DEVELOPMENT&color=GREEN&style=for-the-badge)

### This is a project in Python 3.7.13 written by Igor Nogueira, to help a famous casino to increase its revenue by the development of a online poker game to be further offered to the users. Here, you'll find a poker hands evaluator, that receives two poker hands and determines if the first hand wins or loses to the second hand.

## Contents
   - [Poker game](#Poker-game)
     - 
   

### Poker game

![poker hand](https://user-images.githubusercontent.com/67437213/160718241-0023ae13-875e-4129-92b6-a10132238eff.JPG)

#### Poker is a card game that can be played by 2 or more people, which consists (in the most popular mode) that each player has five cards in its hand, evaluates what's the rank of your hand (there are 10 possible hand ranks, later it'll be described) and bets poker chips, which represents some money value. In this project we'll consider a deck of 52 cards, four cards to each denomination.

### Each card has a value, which is defined by the number of the card or the following letters: J, Q, K, A. Specifying the values:
+ From 2 to 10, the value is the number;
+ J = 11; Q = 12; K = 13; A = 14.

### Each card has a suit, which can be: Spades (S), Diamonds (D), Clubs (C) or Hearts (H).

### Hand Ranks

### There are 10 possible hand ranks, which are described as follows:
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

``` python
class PokerHand(object):

   def __init__(self, hand:str = None):
       self.hand: str = hand       

   def __iter__(self):
       return iter(self.hand.split())

   def __str__(self):
       return str(list(self))
```
``` python
def extract_number(self):

   numbers = []
   for card in PokerHand(self.hand):
      number = card[0]
      numbers.append(number)
   return numbers

def extract_suit(self):

   suits = []
   for card in PokerHand(self.hand):
      suit = card[1]
      suits.append(suit)
   return suits

def value(self):

   values = []        
   for card in PokerHand(self.hand):
      if card[0] == "A":
         value = 14
         values.append(value)

      elif card[0] == "K":
         value = 13
         values.append(value)

      elif card[0] == "Q":
         value = 12
         values.append(value)

      elif card[0] == "J":
         value = 11
         values.append(value)

      elif card[0] == "T":
         value = 10
         values.append(value)

      else:
         value = int(card[0:-1])
         values.append(value)

   return sorted(values, reverse = True)

def hand_dist(self):
      
   dist = {i:0 for i in range(2, 15)}
   for card in PokerHand(self.hand):
      if card[0] == "A":
         value = 14

      elif card[0] == "K":
         value = 13

      elif card[0] == "Q":
         value = 12

      elif card[0] == "J":
         value = 11

      elif card[0] == "T":
         value = 10

      else:
         value = int(card[0:-1])

      dist[value] += 1

   return dist
```


``` python
def is_flush(self):

   if len(set(self.extract_suit())) == 1:
      return True
   else:
      return False    

def is_straight(self):

   list_straight = []
   list_values = self.value()        
   for i in range(4):
      if list_values[i] == list_values[i+1] + 1:
         list_straight.append(list_values[i])
      if len(list_straight) == 4:
         return True
      else:
         return False

def is_straight_flush(self):

   if self.is_straight() == True and self.is_flush() == True:
      return True
   else:
      return False

def is_royal_straight_flush(self):

   if self.is_straight_flush() == True and max(self.value()) == 14:
      return True
   else:
      return False

def is_one_pair(self):  

   keys_is_one_pair = []        
   hand_dist = self.hand_dist()
   for key, value in hand_dist.items():
      if value == 2:
         keys_is_one_pair.append(key)                
      else:
         pass
        
   if len(keys_is_one_pair) == 1:
      return True
   else:
      return False

def is_two_pair(self): 

   keys_two_pair = []       
   hand_dist = self.hand_dist()
   for key, value in hand_dist.items():
      if value == 2:
         keys_two_pair.append(key)                
      else:
         pass
       
   if len(keys_two_pair) == 2:
      return True
   else:
      return False

def is_full_house(self):       

   keys_full_house = []              
   hand_dist = self.hand_dist()
   for key, value in hand_dist.items():
      if value == 2 or value == 3:
         keys_full_house.append(key)           
      else:
         pass        

   if len(keys_full_house) == 2 and self.is_two_pair() == False:
      return True
   else:
      return False

def is_four(self): 

   keys_is_four = []        
   hand_dist = self.hand_dist()
   for key, value in hand_dist.items():
      if value == 4:
         keys_is_four.append(key)              
      else:
         pass
        
   if len(keys_is_four) == 1:
      return True
   else:
      return False

def is_three(self): 

   keys_is_three = []        
   hand_dist = self.hand_dist()
   for key, value in hand_dist.items():
      if value == 3:
         keys_is_three.append(key)                               
      else:
         pass

   if len(keys_is_three) == 1 and self.is_full_house() == False:
      return True
   else:
      return False

def high_card(self):

   max_card = max(self.value())   
   return max_card
```
``` python
def high_card_full_house_or_three(self):

   key_full_house_or_three = [] 
   hand_dist = self.hand_dist()
   for key, value in hand_dist.items():
      if value == 3:
         key_full_house_or_three.append(key)
      else:
         pass
         
   return key_full_house_or_three

def high_card_four_of_a_kind(self):
        
   key_four_of_a_kind = [] 
   hand_dist = self.hand_dist()
   for key, value in hand_dist.items():
      if value == 4:
         key_four_of_a_kind.append(key)
      else:
         pass

   return key_four_of_a_kind

def high_card_two_pair(self):        

   key_two_pair = [] 
   hand_dist = self.hand_dist()
   for key, value in hand_dist.items():
      if value == 2:
         key_two_pair.append(key)
      else:
         pass

   if len(key_two_pair) == 2:
      key_two_pair = sorted(key_two_pair, reverse = True)

   return key_two_pair

def high_card_one_pair(self):        

   key_one_pair = [] 
   hand_dist = self.hand_dist()
   for key, value in hand_dist.items():
      if value == 2:
         key_one_pair.append(key)
      else:
         pass

   return key_one_pair
```
