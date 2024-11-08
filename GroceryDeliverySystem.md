class GroceryDeliverySystem:
 def _init_(self):
 self.grocery_list = {}
 def add_item(self, item, quantity):
 if item in self.grocery_list:
 self.grocery_list[item]['quantity'] += quantity
 else:
 self.grocery_list[item] = {'quantity': quantity, 'delivered': False}
 print(f"Added {quantity} of {item}.")
 def view_list(self):
 if not self.grocery_list:
 print("The grocery list is empty.")
 return
 for item, details in self.grocery_list.items():
 status = "Delivered" if details['delivered'] else "Pending"
 print(f"{item}: {details['quantity']} (Status: {status})")
 def remove_item(self, item):
 if item in self.grocery_list:
 del self.grocery_list[item]
 print(f"Removed {item}.")
 else:
 print(f"{item} is not in the list.")
 def mark_delivered(self, item):
 if item in self.grocery_list:
 self.grocery_list[item]['delivered'] = True
 print(f"Marked {item} as delivered.")
 else:
 print(f"{item} is not in the list.")
 def run(self):
 while True:
 print("\nOptions: add, view, remove, deliver, exit")
 choice = input("Choose an option: ").strip().lower()
 if choice == 'add':
 item = input("Enter the item name: ").strip()
 quantity = int(input("Enter the quantity: ").strip())
 self.add_item(item, quantity)
 elif choice == 'view':
 self.view_list()
 elif choice == 'remove':
 item = input("Enter the item name to remove: ").strip()
 self.remove_item(item)
 elif choice == 'deliver':
 item = input("Enter the item name to mark as delivered: ").strip()
 self.mark_delivered(item)
 elif choice == 'exit':
 print("Exiting the system.")
 break
 else:
 print("Invalid choice. Please try again.")
if _name_ == "_main_":
 system = GroceryDeliverySystem()
 system.run()
