# coffee
# Coffee Machine project at HyperSkill

class CoffeeMachine:

    def __init__(self):
        self.water_ammount = 400
        self.milk_ammount = 540
        self.beans_ammount = 120
        self.cups_ammount = 9
        self.money_ammount = 550

        self.state = "main_menu"

    def run(self, action):
        action = action
        if self.state == "main_menu":
            if action == "exit":
                self.state = "exit"
            elif action == "remaining":
                self.state = "main_menu"
                print("The coffee machine has:")
                print(self.water_ammount, " of water")
                print(self.milk_ammount, " of milk")
                print(self.beans_ammount, " of coffee beans")
                print(self.cups_ammount, " of disposable cups")
                print(self.money_ammount, " of money")
            elif action == "buy":
                self.state = "coffee_menu"
            elif action == "fill":
                self.state = "fill_water"
                print("Write how many ml of water you want to add:")
            elif action == "take":
                print("I gave you §", self.money_ammount)
                self.money_ammount = 0

        elif self.state == "fill_water":
                self.water_ammount = self.water_ammount + int(action)
                print("Write how many ml of milk you want to add:")
                self.state = "fill_milk"

        elif self.state == "fill_milk":
                self.milk_ammount = self.milk_ammount + int(action)
                print("Write how many grams fo coffee beans you want to add:")
                self.state = "fill_coffee_beans"

        elif self.state == "fill_coffee_beans":
                self.beans_ammount = self.beans_ammount + int(action)
                print("Write how many disposable cups of coffee you want to add:")
                self.state = "fill_cups"

        elif self.state == "fill_cups":
                self.cups_ammount = self.cups_ammount + int(action)
                self.state = "main_menu"

        elif self.state == "coffee_menu":
            if action == "1":
                if self.water_ammount < 250:
                    print("Sorry, not enough water!")
                elif self.beans_ammount < 16:
                    print("Sorry, not enough coffee beans!")
                elif self.cups_ammount < 1:
                    print("Sorry, not enough cups")
                else:
                    self.water_ammount = self.water_ammount - 250
                    self.beans_ammount = self.beans_ammount - 16
                    self.money_ammount = self.money_ammount + 4
                    self.cups_ammount = self.cups_ammount - 1
                    print("I have enough resources, making you a coffee!")
                self.state = "main_menu"
            elif action == "2":
                if self.water_ammount < 350:
                    print("Sorry, not enough water!")
                elif self.milk_ammount < 75:
                    print("Sorry, not enough milk!")
                elif self.beans_ammount < 20:
                    print("Sorry, not enough coffee beans!")
                elif self.cups_ammount < 1:
                    print("Sorry, not enough cups")
                else:
                    self.water_ammount = self.water_ammount - 350
                    self.milk_ammount = self.milk_ammount - 75
                    self.beans_ammount = self.beans_ammount - 20
                    self.money_ammount = self.money_ammount + 7
                    self.cups_ammount = self.cups_ammount - 1
                    print("I have enough resources, making you a coffee!")
                self.state = "main_menu"
            elif action == "3":
                if self.water_ammount < 200:
                    print("Sorry, not enough water!")
                elif self.milk_ammount < 100:
                    print("Sorry, not enough milk!")
                elif self.beans_ammount < 12:
                    print("Sorry, not enough coffee beans!")
                elif self.cups_ammount < 1:
                    print("Sorry, not enough cups")
                else:
                    self.water_ammount = self.water_ammount - 200
                    self.milk_ammount = self.milk_ammount - 100
                    self.beans_ammount = self.beans_ammount - 12
                    self.money_ammount = self.money_ammount + 6
                    self.cups_ammount = self.cups_ammount - 1
                    print("I have enough resources, making you a coffee!")
                self.state = "main_menu"
            elif action == "back":
                self.state = "main_menu"



kuraffemaskin = CoffeeMachine() # lager en kaffemaskin
while True:
    if kuraffemaskin.state == "main_menu":
        print("Write action (buy, fill, take, remaining, exit):")
    elif kuraffemaskin.state == "coffee_menu":
        print("What do you want to buy? 1 - espresso, 2 - latte, 3 - cappuccino, 'back' - to main menu:")
    elif kuraffemaskin.state == "exit":
        break
    action = input(">")
    kuraffemaskin.run(action)
