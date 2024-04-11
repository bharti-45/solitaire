# solitaire
import random
class Card(object):
    def __init__(self,suit,value):
        self.suit = suit
        self.value = value

    def show(self):
        print ("{} of {}".format(self.value,self.suit))
class Deck(object):
    def __init__(self):
        self.cards = []
        self.build()

    def build(self):
        for i in ("Spades","Clubs","Hearts","Diamonds"):
            for j in range(1,14):
                self.cards.append(Card(i,j))
    def show(self):
        for c in self.cards:
            c.show()

    def shuffle(self):
        for i in range(len(self.cards)-1,0,-1):
            r= random.randint(0,i)
            self.cards[i],self.cards[r] = self.cards[r],self.cards[i]

    def drawCard(self):
        return self.cards.pop()


class Player(object):
    def __init__(self,name):
        self.name = name
        self.hand = []

    def draw(self,deck):
        self.hand.append(deck.drawCard())
        return self 
    def showHand(self):
        for card in self.hand:
            card.show()

#card = Card("Clubs",6)
#card.show()
deck = Deck()
deck.shuffle()
#card = deck.draw()
#deck.show()
#card.show()
player = Player("Bharti")
player.draw(deck)
player.showHand()
