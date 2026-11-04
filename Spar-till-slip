from datetime import datetime
import random

# ====================== CONFIG ======================
STORE_NAME = "SPAR"
BRANCH = "SPAR Greenpoint"
ADDRESS = "12 Main Road, Greenpoint, Cape Town"
PHONE = "021 555 1234"
VAT_NUMBER = "4123456789"
VAT_RATE = 0.15          # South African VAT 15%
CURRENCY = "R"

# Sample products (you can expand this list)
PRODUCTS = {
    "Milk 2L Full Cream": 32.99,
    "Brown Bread": 18.50,
    "Eggs 18s": 54.99,
    "Chicken Breast 1kg": 89.99,
    "Bananas 1kg": 24.99,
    "Coca-Cola 2L": 29.99,
    "Sunlight Dishwashing Liquid": 42.50,
    "Potato Chips 150g": 19.99,
    "Apples 1.5kg": 34.99,
    "Yoghurt 1kg": 27.99,
    "Rice 2kg": 48.99,
    "Toilet Paper 9s": 89.99,
}


def generate_till_number():
    return f"T{random.randint(1000, 9999)}"


def generate_transaction_number():
    return f"{random.randint(100000, 999999)}"


def print_receipt(items: list[dict]):
    """
    items = [
        {"name": "Milk 2L Full Cream", "qty": 2, "price": 32.99},
        ...
    ]
    """
    now = datetime.now()
    till_no = generate_till_number()
    trans_no = generate_transaction_number()

    # Calculate totals
    subtotal = sum(item["qty"] * item["price"] for item in items)
    vat = subtotal * VAT_RATE / (1 + VAT_RATE)   # VAT inclusive calculation
    total = subtotal

    # ====================== PRINT RECEIPT ======================
    width = 42
    print("=" * width)
    print(STORE_NAME.center(width))
    print(BRANCH.center(width))
    print(ADDRESS.center(width))
    print(f"Tel: {PHONE}".center(width))
    print(f"VAT No: {VAT_NUMBER}".center(width))
    print("-" * width)
    print(f"Date: {now.strftime('%Y-%m-%d %H:%M:%S')}")
    print(f"Till: {till_no}   Trans: {trans_no}")
    print("-" * width)
    print(f"{'Item':<22} {'Qty':>4} {'Price':>7} {'Total':>7}")
    print("-" * width)

    for item in items:
        name = item["name"][:21]
        qty = item["qty"]
        price = item["price"]
        line_total = qty * price
        print(f"{name:<22} {qty:>4} {CURRENCY}{price:>6.2f} {CURRENCY}{line_total:>6.2f}")

    print("-" * width)
    print(f"{'Subtotal':<30} {CURRENCY}{subtotal:>8.2f}")
    print(f"{'VAT (15% incl.)':<30} {CURRENCY}{vat:>8.2f}")
    print(f"{'TOTAL':<30} {CURRENCY}{total:>8.2f}")
    print("-" * width)
    print("Payment Method: CASH / CARD")
    print(f"Amount Tendered: {CURRENCY}{total + 50:.2f}")  # example change
    print(f"Change:          {CURRENCY}50.00")
    print("-" * width)
    print("Thank you for shopping at SPAR!")
    print("Please come again.")
    print("=" * width)
    print("*** This is a computer generated slip ***".center(width))
    print("=" * width)


def main():
    # Example shopping basket
    basket = [
        {"name": "Milk 2L Full Cream", "qty": 2, "price": PRODUCTS["Milk 2L Full Cream"]},
        {"name": "Brown Bread", "qty": 1, "price": PRODUCTS["Brown Bread"]},
        {"name": "Eggs 18s", "qty": 1, "price": PRODUCTS["Eggs 18s"]},
        {"name": "Coca-Cola 2L", "qty": 2, "price": PRODUCTS["Coca-Cola 2L"]},
        {"name": "Bananas 1kg", "qty": 1, "price": PRODUCTS["Bananas 1kg"]},
        {"name": "Sunlight Dishwashing Liquid", "qty": 1, "price": PRODUCTS["Sunlight Dishwashing Liquid"]},
    ]

    print_receipt(basket)


if __name__ == "__main__":
    main()
