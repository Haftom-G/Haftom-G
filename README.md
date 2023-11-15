import random

class SlotMachine:
    def __init__(self, symbols):
        self.symbols = symbols
        self.slots = [random.choice(symbols) for _ in range(3)]

    def spin(self):
        self.slots = [random.choice(self.symbols) for _ in range(3)]

    def display_slots(self):
        return " ".join(self.slots)

def play_slot_machine(bet_amount):
    symbols = ["Cherry", "Orange", "Plum", "Bell", "Bar", "Seven"]
    slot_machine = SlotMachine(symbols)

    print("Welcome to the Slot Machine!")
    print("Symbols:", symbols)

    while True:
        input("Press Enter to spin the slot machine...")
        slot_machine.spin()
        print("Result:", slot_machine.display_slots())

        if all(symbol == slot_machine.slots[0] for symbol in slot_machine.slots):
            print("Congratulations! You won the jackpot!")
            return bet_amount * 10  # Jackpot multiplier
        else:
            print("Sorry, you didn't win. Try again!")

        play_again = input("Do you want to play again? (yes/no): ")
        if play_again.lower() != 'yes':
            break

    print("Thanks for playing!")

if __name__ == "__main__":
    bet_amount = int(input("Enter your bet amount: "))
    winnings = play_slot_machine(bet_amount)
    print("Your total winnings: $", winnings)
