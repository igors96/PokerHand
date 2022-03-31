![DataH](https://user-images.githubusercontent.com/67437213/160717510-3a182d88-0908-4f5c-aae2-b5e52b2c879d.JPG)
# Class definition
Let's introduce the definiton of the class PokerHand. This class has a constructor, which receives a string representing the five cards of the hand. A example of entry is: "5C 4D 3C TS 8H", and after each card will be convert in a item of a list. The letter 'T' will substitute the value '10' in this code.  

``` python
class PokerHand(object):

   def __init__(self, hand:str = None):
       self.hand: str = hand       

   def __iter__(self):
       return iter(self.hand.split())

   def __str__(self):
       return str(list(self))
```
