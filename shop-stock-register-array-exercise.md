# CDG-HYD-JFS-060

## Shop Stock Register Array Exercise

**Level:** Beginner  
**Application:** Interactive console application  
**Approach:** Object-oriented programming with arrays

Implementation requirements:

- Use two classes: one to own the arrays and perform operations, and one to contain `main()` and handle the menu.
- Keep array fields private.
- Use `Scanner`, loops, conditions, and methods.
- Display the menu repeatedly until Exit is selected.
- Keep records in memory while the program runs.
- Assume users type integers at numeric prompts; still validate ranges and state.
- Use arrays rather than collection classes for storage.
- Do not let invalid input change existing data.

Repeated menus are omitted from the sample sessions for readability.

## 1. Problem statement

A small stationery shop sells three products: Pen, Notebook, and Pencil. The shopkeeper needs a console application to check stock, add newly received stock, and reduce stock when items are sold.

Create a **Shop Stock Register**. The products are predefined; users do not add new product names in this exercise.

The register starts with:

| Product number | Product | Initial quantity |
| --- | --- | --- |
| 1 | Pen | 10 |
| 2 | Notebook | 5 |
| 3 | Pencil | 8 |

Store product names and quantities in two arrays. Matching indexes describe the same product.

## 2. Console menu

```text
SHOP STOCK REGISTER

1. Display stock
2. Add stock
3. Sell product
4. Display out-of-stock products
5. Exit

Enter your choice:
```

## 3. Required operations

| Operation | Required behavior |
| --- | --- |
| Display stock | Show every product number, name, and current quantity. |
| Add stock | Read a product number and quantity received. Increase that product's stock. |
| Sell product | Read a product number and quantity sold. Decrease stock only if sufficient stock exists. |
| Display out-of-stock products | Show the products whose current quantity is zero. If there are none, show `All products are in stock.` |
| Exit | Display `Thank you!` and stop. |

After successfully adding or selling stock, display the product's updated quantity.

## 4. Rules and validation

1. Product numbers must be from 1 to 3.
2. Quantities added or sold must be positive integers.
3. A sale must not make the stock negative.
4. Zero stock is valid and means the product is out of stock.
5. Validate the product number before asking for quantity.
6. Reject invalid product numbers with `Invalid product number.`
7. Reject zero or negative operation quantities with `Quantity must be greater than zero.`
8. Reject a sale larger than available stock with `Insufficient stock. Available quantity: <quantity>.`
9. Reject menu choices outside 1 to 5 with `Invalid choice. Choose 1 to 5.`

## 5. Suggested object-oriented design

| Class | Responsibility |
| --- | --- |
| `StockRegister` | Own product names and quantities; perform stock operations. |
| `StockApplication` | Contain `main()`, read inputs, display the menu, and call the register object. |

Suggested fields in `StockRegister`:

```java
private String[] productNames = {"Pen", "Notebook", "Pencil"};
private int[] quantities = {10, 5, 8};
```

| Suggested method | Responsibility |
| --- | --- |
| `isValidProductNumber(int productNumber)` | Check whether the product number is from 1 to 3. |
| `displayStock()` | Display product numbers, names, and stock quantities. |
| `addStock(int productNumber, int quantity)` | Validate and increase stock. |
| `sellProduct(int productNumber, int quantity)` | Validate and reduce stock. |
| `displayOutOfStockProducts()` | Loop through stock and display products with zero quantity. |

**Hints:** Convert a product number to an index using `productNumber - 1`. Addition changes `quantities[index]` by `+ quantity`; a successful sale changes it by `- quantity`. Do not change product names.

## 6. Sample console session

```text
Enter your choice: 1
1. Pen: 10
2. Notebook: 5
3. Pencil: 8

Enter your choice: 2
Enter product number: 2
Enter quantity received: 3
Stock added. Notebook stock: 8.

Enter your choice: 3
Enter product number: 1
Enter quantity to sell: 4
Sale recorded. Pen stock: 6.

Enter your choice: 3
Enter product number: 3
Enter quantity to sell: 8
Sale recorded. Pencil stock: 0.

Enter your choice: 1
1. Pen: 6
2. Notebook: 8
3. Pencil: 0

Enter your choice: 4
Out-of-stock products:
3. Pencil

Enter your choice: 5
Thank you!
```

## 7. Sample validation cases

Each row is an independent case.

| Starting state | Sample input | Expected output |
| --- | --- | --- |
| Initial stock | Add stock, product `4` | `Invalid product number.` |
| Initial stock | Add stock, product `1`, quantity `0` | `Quantity must be greater than zero.` Pen stock stays at 10. |
| Initial stock | Sell product `2`, quantity `6` | `Insufficient stock. Available quantity: 5.` Notebook stock stays at 5. |
| Initial stock | Display out-of-stock products | `All products are in stock.` |
| Any state | Menu choice `8` | `Invalid choice. Choose 1 to 5.` |

## 8. Completion checklist

- Initialize both arrays with the predefined products.
- Keep the name and quantity at each matching index associated correctly.
- Increase stock only for valid additions.
- Decrease stock only for valid sales with sufficient quantity.
- Display zero-stock products using a loop.
- Produce the sample results and validation messages.

**Skills practised:** parallel arrays, index conversion, updating array elements, loops, methods, and validation.

