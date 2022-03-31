![DataH](https://user-images.githubusercontent.com/67437213/160717510-3a182d88-0908-4f5c-aae2-b5e52b2c879d.JPG)

### Coding the hand possibilities

Here, we'll find the code used to identify each one of the 10 possibilities of configurations to a hand.

- is_flush(): identifies if the hand is a Flush. The number of suits in this hand should be 1.
- is_straight(): identifies if the hand is a Straight. First, the numbers of the cards are taken with the function value(), and after in a loop, verifies if the number in the list is equal to the next, plus 1.
- is_straight_flush(): identifies if the hand is a Straight Flush. If the hand is a Straight and a Flush at the same time, it'll be a Straight Flush.
- is_royal_straight_flush(): identifies if the hand is a Royal Straight Flush. If the hand is a Straight Flush and the highest number is 14 at the same time, it'll be a Royal Straight Flush.
- is_one_pair(): identifies if the hand is a One pair. It's applied the function hand_dist() and sends the key to a list if the number of occurrences is 2. If there's just one number that appears two times, it'll be a One pair.
- is_two_pair(): identifies if the hand is a Two pair. It's applied the function hand_dist() and sends the keys to a list if the number of occurrences is 2. If there's two numbers that appears two times, it'll be a Two pair.
- is_full_house(): identifies if the hand is a Full house. It's applied the function hand_dist() and sends the keys to a list if the number of occurrences is 2 or 3. If there's one number that appears two times and another number that appears three times in the list, and is not a Two pair, it'll be a Full house.
- 

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
