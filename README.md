# Variable Types and Functional Programming:
# Task 1:
sales = [200, 400, 500, 980, 780, 1200, 652]

# Calculate total sales
sum_of_sales = sum(sales)

# Calculate average sales
average_sales = sum_of_sales / len(sales)
print("sum of sales is  : ", sum_of_sales)
print("average of sales is : ", average_sales)


###########################################################
# Task 2:
def discount_machine(products_prices):
    total = sum(products_prices.values())
    total_after_discount = total * 0.9
    return total_after_discount


products = {"milk": 18, "apple": 5, "phone": 2500, "shirt": 50, "shoe": 220}
total_to_print = discount_machine(products)
print("total amount of money to pay :", total_to_print)


#################################################################
# Object-Oriented Programming (OOP):
# Task 3 & 4:
class Product:

    def __init__(self, name, price, quantity):
        self.name = name
        self.price = price
        self.quantity = quantity

    def show_details(self):
        print("name of the product is :", self.name)
        print("price of the product is :", self.price)
        print("quantity of the product is :", self.quantity)

    def calculate_total_cost(self, amount):
        total_cost = amount * self.price
        print("the total cost for ", amount, " unit of ", self.name, "is : ", total_cost)


p1 = Product("Iphone", 6500, 12)
p1.show_details()
p1.calculate_total_cost(13)
##############################################################################
# Files I/O and Data Handling:
# Task 5:
import pandas as pd

# Opening the CSV file
input_file_path = 'C:\\Users\\MSI\\Desktop\\r1cs.csv'

# Reading the CSV file into a pandas DataFrame
sales_data = pd.read_csv(input_file_path)

# Displaying the contents of the CSV file
for lines in sales_data.iterrows():
    print(lines)

# Calculate total revenue and average price per item for each product
sales_data['total_revenue'] = sales_data['quantity'] * sales_data['price']

# Group by 'product_name' and aggregate total revenue and average price
grouped_data = sales_data.groupby('product_name').agg(
    total_revenue=pd.NamedAgg(column='total_revenue', aggfunc='sum'),
    average_price=pd.NamedAgg(column='price', aggfunc='mean')
).reset_index()

# Display the results
print(grouped_data)

# Save results to a new CSV file
output_file_path = 'C:\\Users\\MSI\\Desktop\\result_per_product.csv'
grouped_data.to_csv(output_file_path, index=False)

print(f'Results per product saved to {output_file_path}')
