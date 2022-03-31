![DataH](https://user-images.githubusercontent.com/67437213/160717510-3a182d88-0908-4f5c-aae2-b5e52b2c879d.JPG)
### Card treatment
In this part of the code, we'll find 3 methods to treat the cards of the hand. First, extract_suit() is a function that extracts the suit of each card and sends it to a list. The function value() extracts the number of the card and does the conversion of the letters "T", "J", "Q", "K", "A" to numbers, putting them in a descending order list. Last, the function hand_dist() counts how many times a number appears in a hand, and returns a dictionary with the key being the number and the value being the counting of occurrences. 

``` python        
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
            number = 14

         elif card[0] == "K":
            number = 13

         elif card[0] == "Q":
            number = 12

         elif card[0] == "J":
            number = 11

         elif card[0] == "T":
            number = 10

         else:
            number = int(card[0:-1])

         dist[number] += 1

      return dist
```
