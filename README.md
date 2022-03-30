![DataH](https://user-images.githubusercontent.com/67437213/160717510-3a182d88-0908-4f5c-aae2-b5e52b2c879d.JPG)
<h1>Poker hands evaluator</h1>

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=UNDER%20DEVELOPMENT&color=GREEN&style=for-the-badge)

### This is a project written by Igor Nogueira, to help a famous casino to increase its revenue by the development of a online poker game to be further offered to the users. Here, you'll find a poker hands evaluator, that receives two poker hands and determines if the first hand wins or loses to the second hand.

### Let's introduce what's a poker game:

![poker hand](https://user-images.githubusercontent.com/67437213/160718241-0023ae13-875e-4129-92b6-a10132238eff.JPG)

### Poker is a card game that can be played by 2 or more people, which consists (in the most popular mode) that each player has five cards in its hand, evaluates what's the rank of your hand (there are 10 possible hand ranks, later it'll be described) and bets poker chips, which represents some money value.

### Each card has a value, which is defined by the number of the card or the following letters: J, Q, K, A. Specifying the values:
+ From 2 to 10, the value is the number;
+ J = 11; Q = 12; K = 13; A = 14.

### Each card has a suit, which can be: Spades (S), Diamonds (D), Clubs (C) or Hearts (H).

### Hand Ranks

### There are 10 possible hand ranks, which are described as follows:

![hand ranks poker](https://user-images.githubusercontent.com/67437213/160733480-17037b8a-a481-4d9b-80e4-36299d285a2b.JPG)

### Royal Flush or Royal Straight Flush: is the major hand rank that can be appear in a poker hand, but its probability of appearance is 0.000154%. The sequence is: A, K, Q, J, 10, all of the same suit. There's no possibility to have a tiebreaker in this case.

### Straight Flush: is the second main hand rank. Its probability of appearance is 0.00139%. It happens when there are five cards in denomination sequence, which the high value is from 6 to K(13) and in the same suit. The tiebreaker is by the high value of the sequence.

### Four of a kind: is the third in the list of hand ranks. Its probability of appearance is 0.02401%. Happens when there are four cards of the same denomination. The tiebreaker is by the high value of the four of a kind.

### Full house: is the fourth in the list of hand ranks. Its probability of appearance is 0.1441%. It's described when there are three cards of the same denomination and two of another denomination. The tiebreaker consists in analyzing the high value of the three of a kind in the hand.

### Flush: is the fifth in the list of hand ranks. Its probability of appearance is 0.1965%. Happens when there are five cards of the same suit, but not in denomination sequence. The tiebreaker is the high value of the card, and goes like that until break the tie. It's possible to have a draw if ties in all comparisons.

### Straight: is the sixth in the list of hand ranks. Its probability of appearance is 0.3925%. It happens when there are five cards in denomination sequence, not necessarily in the same suit. The tiebreaker is by the high value of the sequence.

### Three of a kind: is the seventh in the list of hand ranks. Its probability of appearance is 2.1128%. Happens when there are three cards of the same denomination. The tiebreaker consists in analyzing the high value of the three of a kind.

### Two pair: is the eighth in the list of hand ranks. Its probability of appearance is 4.7539%. Happens when there are two cards of the same denomination and two cards of another denomination. The tiebreaker consists in analyzing the high value of the two pairs, one by one. If doesn't break the tie, the comparison goes to the remaining card denomination by the high value. It's possible to have a draw if ties in all comparisons.

### One pair: is the ninth in the list of hand ranks. Its probability of appearance is 42.2569%. Happens when there are two cards of the same denomination. The tiebreaker consists in analyzing the high value of the one pair. If doesn't break the tie, the comparison goes to the 3 remaining cards denomination by the high value, until have a winner. It's possible to have a draw if ties in all comparisons.

### High card: is the last in the list of hand ranks. Its probability of appearance is 50.1177%. Happens when there aren't any of the another 9 hand ranks. The card with the highest denomination is considered. If have a tie, goes to the highest denomination of the 4 remaining cards and so on until break the tie. It's possible to have a draw if ties in all comparisons.
