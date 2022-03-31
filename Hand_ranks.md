![DataH](https://user-images.githubusercontent.com/67437213/160717510-3a182d88-0908-4f5c-aae2-b5e52b2c879d.JPG)

### Hand ranks
Here we have the ranks to each possibility, for helping in the definition of the hand winner.

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
```
