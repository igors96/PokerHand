![DataH](https://user-images.githubusercontent.com/67437213/160717510-3a182d88-0908-4f5c-aae2-b5e52b2c879d.JPG)

### Coding the hand possibilities

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
