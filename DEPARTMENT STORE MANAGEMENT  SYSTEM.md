#include <stdio.h> 
#include <stdlib.h> 
#include <string.h> 
 
#define MAX_ITEMS 100 
#define NAME_LEN 50 
 
typedef struct { 
    char name[NAME_LEN]; 
    int quantity; 
    float price; 
} Item; 
 
Item inventory[MAX_ITEMS]; 
int item_count = 0; 
 
void addItem() { 
    if (item_count>= MAX_ITEMS) { 
printf("Inventory is full.\n"); 
        return; 
    } 
 
    Item newItem; 
printf("Enter item name: "); 
scanf("%s", newItem.name); 
printf("Enter item quantity: "); 
scanf("%d", &newItem.quantity); 
printf("Enter item price: "); 
scanf("%f", &newItem.price); 
inventory[item_count] = newItem; 
item_count++; 
printf("Item added successfully.\n"); 
} 
void viewItems() { 
if (item_count == 0) { 
printf("No items in inventory.\n"); 
return; 
} 
printf("Current inventory:\n"); 
for (int i = 0; i<item_count; i++) { 
printf("%d. %s - Quantity: %d, Price: $%.2f\n", i + 1, 
inventory[i].name, inventory[i].quantity, inventory[i].price); 
} 
} 
void removeItem() { 
if (item_count == 0) { 
 
printf("No items to remove.\n"); 
        return; 
    } 
 
    char itemName[NAME_LEN]; 
printf("Enter the name of the item to remove: "); 
scanf("%s", itemName); 
 
    for (int i = 0; i<item_count; i++) { 
        if (strcmp(inventory[i].name, itemName) == 0) { 
            for (int j = i; j <item_count - 1; j++) { 
                inventory[j] = inventory[j + 1]; 
            } 
item_count--; 
printf("Item removed successfully.\n"); 
            return; 
        } 
    } 
printf("Item not found.\n"); 
} 
 
int main() { 
    int choice; 
 
    while (1) { 
printf("\nOptions: 1. Add Item 2. View Items 3. Remove Item 
 
4. Exit\n"); 
printf("Enter your choice: "); 
scanf("%d", &choice); 
 
        switch (choice) { 
            case 1: 
addItem(); 
                break; 
            case 2: 
viewItems(); 
                break; 
            case 3: 
removeItem(); 
                break; 
            case 4: 
printf("Exiting the system.\n"); 
exit(0); 
            default: 
printf("Invalid choice. Please try again.\n"); 
        } 
    } 
 
    return 0; 
} 
