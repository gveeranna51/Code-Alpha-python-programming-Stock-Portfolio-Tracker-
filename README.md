# Code-Alpha-python-programming-Stock-Portfolio-Tracker-
My second task in code alpha python programming internship 
# --- Stock Portfolio Tracker ---

# Hardcoded stock prices (dictionary)
stock_prices = {
    "AAPL": 180,
    "TSLA": 250,
    "GOOGL": 140,
    "AMZN": 130,
    "MSFT": 350
}

portfolio = {}  # to store user’s stock and quantity

print("Available stocks and prices:")
for stock, price in stock_prices.items():
    print(f"{stock}: ${price}")

# Take user input
while True:
    stock_name = input("\nEnter stock symbol (or 'done' to finish): ").upper()
    if stock_name == "DONE":
        break
    if stock_name not in stock_prices:
        print("Stock not found! Please enter a valid symbol.")
        continue
    try:
        quantity = int(input(f"Enter quantity of {stock_name}: "))
        portfolio[stock_name] = portfolio.get(stock_name, 0) + quantity
    except ValueError:
        print("Please enter a valid number!")

# Calculate total investment
total_value = 0
print("\nYour Portfolio:")
print("----------------------------")
for stock, qty in portfolio.items():
    value = qty * stock_prices[stock]
    total_value += value
    print(f"{stock} - {qty} shares × ${stock_prices[stock]} = ${value}")

print("----------------------------")
print(f"Total Investment Value: ${total_value}")

# Optional: Save to file
save_option = input("\nDo you want to save the portfolio to a file? (yes/no): ").lower()
if save_option == "yes":
    with open("portfolio.txt", "w") as f:
        f.write("Stock Portfolio Tracker\n")
        f.write("----------------------------\n")
        for stock, qty in portfolio.items():
            f.write(f"{stock} - {qty} shares × ${stock_prices[stock]} = ${qty * stock_prices[stock]}\n")
        f.write("----------------------------\n")
        f.write(f"Total Investment Value: ${total_value}\n")
    print("✅ Portfolio saved to 'portfolio.txt' successfully!")
