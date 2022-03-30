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
``` python
   def hand_rank(self):

      if self.is_royal_straight_flush() == True:
         return 10
      elif self.is_straight_flush() == True:
         return 9
      elif self.is_four() == True:
         return 8
      elif self.is_full_house() == True:
         return 7
      elif self.is_flush() == True:
         return 6
      elif self.is_straight() == True:
         return 5
      elif self.is_three() == True:
         return 4
      elif self.is_two_pair() == True:
         return 3
      elif self.is_one_pair() == True:
         return 2
      else:
         return 1

   def tie_breaker(self, hand2:str = None):

      self.hand2: str = hand2        
      global decision

      if self.hand_rank() == self.hand2.hand_rank():            

         if self.hand_rank() == 10:
            decision = 'DRAW'  

         elif self.hand_rank() == 9 or self.hand_rank() == 5:
            if self.high_card() > self.hand2.high_card():
               decision = 'WIN'
            if self.high_card() < self.hand2.high_card():
               decision = 'LOSS'

         elif self.hand_rank() == 8:
            if self.high_card_four_of_a_kind() > self.hand2.high_card_four_of_a_kind():
               decision = 'WIN'
            if self.high_card_four_of_a_kind() < self.hand2.high_card_four_of_a_kind():
               decision = 'LOSS'

         elif self.hand_rank() == 7 or self.hand_rank() == 4:
            if self.high_card_full_house_or_three() > self.hand2.high_card_full_house_or_three():
               decision = 'WIN'
            if self.high_card_full_house_or_three() < self.hand2.high_card_full_house_or_three():
               decision = 'LOSS'
                     
         elif self.hand_rank() == 6 or self.hand_rank() == 1:
            hand_1 = self.value()
            hand_2 = self.hand2.value()

            for i in range(5):                    
               if hand_1[i] > hand_2[i]:
                  decision = 'WIN'
                  break
               if hand_1[i] < hand_2[i]:                        
                  decision = 'LOSS'
                  break                    
               else:
                  pass

         elif self.hand_rank() == 3:
            keys_hand_1 = self.high_card_two_pair()
            keys_hand_2 = self.hand2.high_card_two_pair()
                                
            hand_1 = self.value()
            hand_2 = self.hand2.value()
                                
            for j in keys_hand_1:
               for k in hand_1:
                  if j in hand_1:
                     hand_1.remove(j)
                  else:
                     pass

            for m in keys_hand_2:
               for n in hand_2:
                  if m in hand_2:
                     hand_2.remove(m)
                  else:
                     pass
                                          
            for i in range(2):
               if keys_hand_1[i] > keys_hand_2[i]:
                  decision = 'WIN'
                  break
               if keys_hand_1[i] < keys_hand_2[i]:
                  decision = 'LOSS'
                  break
               else:
                  pass

            if keys_hand_1[:2] == keys_hand_2[:2]:
               if hand_1 > hand_2:
                  decision = 'WIN'                 
               if hand_1 < hand_2:
                  decision = 'LOSS'
                    

         elif self.hand_rank() == 2:
            keys_hand_1 = self.high_card_one_pair()
            keys_hand_2 = self.hand2.high_card_one_pair()
                
            hand_1 = self.value()
            hand_2 = self.hand2.value()
              
            for j in keys_hand_1:
               for k in hand_1:
                  if j in hand_1:
                     hand_1.remove(j)
                  else:
                     pass                

            for m in keys_hand_2:
               for n in hand_2:
                  if m in hand_2:
                     hand_2.remove(m)
                  else:
                     pass                                  

            if keys_hand_1 > keys_hand_2:
               decision = 'WIN'                    
            if keys_hand_1 < keys_hand_2:
               decision = 'LOSS'
            for i in range(3):              
               if hand_1[i] > hand_2[i]:
                  decision = 'WIN'
                  break                   
               if hand_1[i] < hand_2[i]:
                  decision = 'LOSS'
                  break
                  
        return decision      
                                                   
    def compare_with(self, hand2:str = None) -> str:
        self.hand2: str = hand2

        if self.hand_rank() > self.hand2.hand_rank():            
            result = 'WIN'
        elif self.hand_rank() < self.hand2.hand_rank():            
            result = 'LOSS'
        else:
            self.tie_breaker(self.hand2)
            result = decision

        return result
        
```

### Testes

```python
import unittest

class TestPokerHands(unittest.TestCase):
    
    def test_poker_hand(self):        
        self.assertTrue(PokerHand("TC TH 5C 5H KH").compare_with(PokerHand("9C 9H 5C 5H AC")) == 'WIN')
        self.assertTrue(PokerHand("TS TD KC JC 7C").compare_with(PokerHand("JS JC AS KC TD")) == 'LOSS')
        self.assertTrue(PokerHand("7H 7C QC JS TS").compare_with(PokerHand("7D 7C JS TS 6D")) == 'WIN')
        self.assertTrue(PokerHand("5S 5D 8C 7S 6H").compare_with(PokerHand("7D 7S 5S 5D JS")) == 'LOSS')
        self.assertTrue(PokerHand("AS AD KD 7C 3D").compare_with(PokerHand("AD AH KD 7C 4S")) == 'LOSS')
        self.assertTrue(PokerHand("TS JS QS KS AS").compare_with(PokerHand("AC AH AS AS KS")) == 'WIN')
        self.assertTrue(PokerHand("TS JS QS KS AS").compare_with(PokerHand("TC JS QC KS AC")) == 'WIN')
        self.assertTrue(PokerHand("TS JS QS KS AS").compare_with(PokerHand("QH QS QC AS 8H")) == 'WIN')
        self.assertTrue(PokerHand("AC AH AS AS KS").compare_with(PokerHand("TC JS QC KS AC")) == 'WIN')
        self.assertTrue(PokerHand("AC AH AS AS KS").compare_with(PokerHand("QH QS QC AS 8H")) == 'WIN')
        self.assertTrue(PokerHand("TC JS QC KS AC").compare_with(PokerHand("QH QS QC AS 8H")) == 'WIN')
        self.assertTrue(PokerHand("7H 8H 9H TH JH").compare_with(PokerHand("JH JC JS JD TH")) == 'WIN')
        self.assertTrue(PokerHand("7H 8H 9H TH JH").compare_with(PokerHand("4H 5H 9H TH JH")) == 'WIN')
        self.assertTrue(PokerHand("7H 8H 9H TH JH").compare_with(PokerHand("7C 8S 9H TH JH")) == 'WIN')
        self.assertTrue(PokerHand("7H 8H 9H TH JH").compare_with(PokerHand("TS TH TD JH JD")) == 'WIN')
        self.assertTrue(PokerHand("7H 8H 9H TH JH").compare_with(PokerHand("JH JD TH TC 4C")) == 'WIN')
        self.assertTrue(PokerHand("JH JC JS JD TH").compare_with(PokerHand("4H 5H 9H TH JH")) == 'WIN')
        self.assertTrue(PokerHand("JH JC JS JD TH").compare_with(PokerHand("7C 8S 9H TH JH")) == 'WIN')
        self.assertTrue(PokerHand("JH JC JS JD TH").compare_with(PokerHand("TS TH TD JH JD")) == 'WIN')
        self.assertTrue(PokerHand("JH JC JS JD TH").compare_with(PokerHand("JH JD TH TC 4C")) == 'WIN')
        self.assertTrue(PokerHand("4H 5H 9H TH JH").compare_with(PokerHand("7C 8S 9H TH JH")) == 'WIN')
        self.assertTrue(PokerHand("4H 5H 9H TH JH").compare_with(PokerHand("TS TH TD JH JD")) == 'LOSS')
        self.assertTrue(PokerHand("4H 5H 9H TH JH").compare_with(PokerHand("JH JD TH TC 4C")) == 'WIN')
        self.assertTrue(PokerHand("7C 8S 9H TH JH").compare_with(PokerHand("TS TH TD JH JD")) == 'LOSS')
        self.assertTrue(PokerHand("7C 8S 9H TH JH").compare_with(PokerHand("JH JD TH TC 4C")) == 'WIN')
        self.assertTrue(PokerHand("TS TH TD JH JD").compare_with(PokerHand("JH JD TH TC 4C")) == 'WIN')
 
if __name__ == '__main__':
    unittest.main(argv=['first-arg-is-ignored'], exit=False)
