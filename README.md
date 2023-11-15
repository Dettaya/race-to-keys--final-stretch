import random
import string

class User:
    def __init__(self, username):
        self.username = username
        self.keys = {}

    def generate_key(self):
        key = ''.join(random.choices(string.ascii_letters + string.digits, k=10))
        self.keys[key] = 0
        return key

    def buy_key(self, seller, key):
        if key in seller.keys:
            self.keys[key] = seller.keys[key] + 1
            seller.keys[key] += 1
            return True
        return False

    def sell_key(self, buyer, key):
        if key in self.keys and self.keys[key] > 0:
            self.keys[key] -= 1
            buyer.keys[key] = self.keys[key] + 1
            return True
        return False
          
