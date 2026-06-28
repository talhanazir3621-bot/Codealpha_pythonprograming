# Codealpha_pythonprograming
This repository contains my project developed as part of the CodeAlpha Internship. It showcases my implementation, programming skills, and practical understanding of software development concepts. The project includes the complete source code, documentation, and required resources.
# task 2 
stock_prices = {
    "AAPL": 180,
    "TSLA": 250,
    "GOOGL": 140,
    "MSFT": 420,
    "AMZN": 170
}

portfolio = {}
total_value = 0

print("Stock Portfolio Tracker")
print("\nAvailable Stocks:")

for stock, price in stock_prices.items():
    print(f"{stock} : ${price}")

print("\nType 'done' when you have finished.\n")

while True:

    stock = input("Enter stock symbol: ").upper()

    if stock == "DONE":
        break

    if stock not in stock_prices:
        print("Stock not available.")
        continue

    try:
        quantity = int(input("Enter quantity: "))

        if quantity <= 0:
            print("Quantity must be greater than 0.")
            continue

    except ValueError:
        print("Please enter a valid number.")
        continue

    portfolio[stock] = portfolio.get(stock, 0) + quantity

print("\nPortfolio Summary")
print("-" * 30)

summary = ""

for stock, quantity in portfolio.items():

    value = stock_prices[stock] * quantity
    total_value += value

    print(f"{stock} | Quantity: {quantity} | Value: ${value}")

    summary += f"{stock} | Quantity: {quantity} | Value: ${value}\n"

print("-" * 30)
print(f"Total Investment Value: ${total_value}")

with open("portfolio_summary.txt", "w") as file:
    file.write("Portfolio Summary\n")
    file.write("-" * 30 + "\n")
    file.write(summary)
    file.write("-" * 30 + "\n")
    file.write(f"Total Investment Value: ${total_value}")

print("\nPortfolio saved to portfolio_summary.txt")
