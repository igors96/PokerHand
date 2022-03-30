![DataH](https://user-images.githubusercontent.com/67437213/160717510-3a182d88-0908-4f5c-aae2-b5e52b2c879d.JPG)
# Class definition

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
```
