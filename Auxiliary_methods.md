![DataH](https://user-images.githubusercontent.com/67437213/160717510-3a182d88-0908-4f5c-aae2-b5e52b2c879d.JPG)
Let's talk about some auxiliary methods in the code. These methods were built to help in the decision of the tiebreaker, in the following hands possibilities: Four of a kind, Full house, Three of a kind, Two pair and One pair. All have the same structure and return a specific list, which contains the keys that forms the possibility. 

# Auxiliary methods
```python
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
