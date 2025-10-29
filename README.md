def calculate_total_cost(format, num_pages, binding_cost, glue_cost, quantity):
    # Define price per page for each format
    price_per_page = {
        'A4': 100,  # Example price per page for A4
        'A5': 50,   # Example price per page for A5
    }
    
    # Check if the format is valid
    if format not in price_per_page:
        return "Invalid format. Please choose 'A4' or 'A5'."
    
    # Calculate total price based on pages, binding, glue, and quantity
    total_price = ((num_pages * price_per_page[format]) + binding_cost + glue_cost) * quantity
    return total_price

def calculate_profit(total_cost, selling_price):
    return selling_price - total_cost

# Input from user with validation
format = input("Enter the format (A4 or A5): ").strip().upper()  # Normalize input to uppercase
num_pages = int(input("Enter the number of pages: "))
binding_cost = float(input("Enter the binding cost: "))
glue_cost = float(input("Enter the glue cost: "))
selling_price = float(input("Enter the selling price per copy: "))
quantity = int(input("Enter the quantity of copies: "))  # New input for quantity

# Calculate total cost and profit
total_cost = calculate_total_cost(format, num_pages, binding_cost, glue_cost, quantity)

# Check if total_cost is a string (error message)
if isinstance(total_cost, str):
    print(total_cost)
else:
    total_selling_price = selling_price * quantity  # Total selling price for all copies
    profit = calculate_profit(total_cost, total_selling_price)

    # Display results
    print(f"\n--- Cost Breakdown ---")
    print(f"Total cost for {quantity} copies of {num_pages} pages in {format} format: {total_cost:.2f} uzs")
    print(f"Total selling price for {quantity} copies: {total_selling_price:.2f} uzs")
    print(f"Profit: {profit:.2f} uzs")
