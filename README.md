# 🛒 Product Inventory Manager

inventory = {}

def add_product():
    name = input("Enter product name: ")
    price = float(input("Enter product price: "))
    stock = int(input("Enter product stock: "))
    inventory[name] = {"price": price, "stock": stock}
    print(f"✅ Product '{name}' added with {stock} in stock at ${price} each.")

def sell_product():
    name = input("Enter product name to sell: ")
    if name not in inventory:
        print("⚠️ Product not found.")
        return
    qty = int(input("Enter quantity to sell: "))
    if qty > inventory[name]["stock"]:
        print("⚠️ Not enough stock!")
    else:
        inventory[name]["stock"] -= qty
        total = qty * inventory[name]["price"]
        print(f"💰 Sold {qty} x {name} for ${total:.2f}")

def list_products():
    if not inventory:
        print("📭 No products in inventory.")
        return
    print("\n=== Inventory Report ===")
    for name, details in inventory.items():
        print(f"- {name}: ${details['price']} | Stock: {details['stock']}")

def restock_product():
    name = input("Enter product name to restock: ")
    if name not in inventory:
        print("⚠️ Product not found.")
        return
    qty = int(input("Enter quantity to add: "))
    inventory[name]["stock"] += qty
    print(f"📦 Restocked {qty} units of {name}. Now {inventory[name]['stock']} in stock.")

def main():
    while True:
        print("\n=== INVENTORY MANAGER ===")
        print("1. Add product")
        print("2. Sell product")
        print("3. Restock product")
        print("4. List inventory")
        print("5. Exit")

        choice = input("Choose: ")
        if choice == "1":
            add_product()
        elif choice == "2":
            sell_product()
        elif choice == "3":
            restock_product()
        elif choice == "4":
            list_products()
        elif choice == "5":
            print("👋 Exiting...")
            break
        else:
            print("⚠️ Invalid choice!")

if __name__ == "__main__":
    main()
