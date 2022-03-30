![DataH](https://user-images.githubusercontent.com/67437213/160717510-3a182d88-0908-4f5c-aae2-b5e52b2c879d.JPG)
### Card treatment
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
