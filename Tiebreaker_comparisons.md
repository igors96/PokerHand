![DataH](https://user-images.githubusercontent.com/67437213/160717510-3a182d88-0908-4f5c-aae2-b5e52b2c879d.JPG)

### Tie-breaker and comparisons of two hands
``` python
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
