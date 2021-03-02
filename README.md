# CoffeeMachine
Small Coffee Machine Project

class CoffeeMachine:
    water = 400
    milk = 540
    beans = 120
    cups = 9
    money = 550

    def __init__(self, water, milk, beans, money):
        self.water = water
        self.milk = milk
        self.beans = beans
        self.money = money
        self.input_data = ''

    def process_input(self, input_data):
        self.input_data = input("Write action (buy, fill, take, remaining, exit):")
        if self.input_data == "buy":
            input_data = input("What do you want to buy? 1 - espresso, 2 - latte, 3 - cappuccino, back - to main menu:")
            if input_data == "1":
                espresso.buy()
            elif input_data == "2":
                latte.buy()
            elif input_data == "3":
                cappuccino.buy()
            else:
                self.process_input(input_data)
                
        elif self.input_data == "fill":
            CoffeeMachine.water += int(input("Write how many ml of water do you want to add:"))
            CoffeeMachine.milk += int(input("Write how many ml of milk do you want to add:"))
            CoffeeMachine.beans += int(input("Write how many grams of coffee beans do you want to add:"))
            CoffeeMachine.cups += int(input("Write how many disposable cups of coffee do you want to add:"))
            CoffeeMachine.current_state = 'choosing an action'
            self.process_input(input_data)

        elif self.input_data == "take":
            print('I gave you {} dollars. Now I have 0.'.format(CoffeeMachine.money))
            CoffeeMachine.money = 0
            self.process_input(input_data)

        elif self.input_data == "remaining":
            print("The coffee machine has:")
            print('{} of water'.format(CoffeeMachine.water))
            print('{} of milk'.format(CoffeeMachine.milk))
            print('{} of coffee beans'.format(CoffeeMachine.beans))
            print('{} of disposable cups'.format(CoffeeMachine.cups))
            print('${} of money'.format(CoffeeMachine.money))
            self.process_input(input_data)

        else:
            return
            
    def buy(self):
        if CoffeeMachine.water - self.water < 0:
            print("Sorry, not enough water")
            print()
            self.process_input(self.input_data)
        elif CoffeeMachine.milk - self.milk < 0:
            print("Sorry, not enough milk")
            print()
            self.process_input(self.input_data)
        elif CoffeeMachine.beans - self.beans < 0:
            print("Sorry, not enough coffee beans")
            print()
            self.process_input(self.input_data)
        elif CoffeeMachine.cups - 1 < 0:
            print("Sorry, not enough disposable cups")
            print()
            self.process_input(self.input_data)
        else:
            print("I have enough resources, making you a coffee!")
            CoffeeMachine.water -= self.water
            CoffeeMachine.milk -= self.milk
            CoffeeMachine.beans -= self.beans
            CoffeeMachine.cups -= 1
            CoffeeMachine.money += self.money
            self.process_input(self.input_data)
            
