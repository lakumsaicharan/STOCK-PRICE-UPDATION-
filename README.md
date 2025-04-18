# Product Pricing Update Script

## Overview

This notebook provides a complete solution to the "Product Pricing Update" problem using product and sales data.

## Functionality

The script performs the following steps:

1. **Load Input Data**
   - Reads product details from `products.csv`
   - Reads recent 30-day sales data from `sales.csv`

2. **Merge and Prepare Data**
   - Combines both datasets based on SKU to match product info with corresponding sales figures

3. **Apply Pricing Rules**
   - **Rule 1:** Increase price by 15% if stock < 20 and quantity_sold > 30
   - **Rule 2:** Decrease price by 30% if stock > 200 and quantity_sold == 0
   - **Rule 3:** Decrease price by 10% if stock > 100 and quantity_sold < 20
   - **Rule 4 (Always Applied):** Ensure final price is at least 20% above the cost price

4. **Price Rounding**
   - Final prices are rounded to 2 decimal places

5. **Output**
   - Generates an output file `updated_prices.csv` containing:
     - `sku`
     - `current_price`
     - `new_price`

## Files

- `products.csv` - Product catalog with pricing, cost, and stock
- `sales.csv` - Sales volume per product for the last 30 days
- `updated_prices.csv` - Resulting updated prices per SKU

## Example Rule Application

For SKU `A123`:
- Original Price: 649.99
- Cost Price: 500.00
- Stock: 150
- Quantity Sold: 10

**Rule Applied:** Rule 3 (Overstocked Inventory) → 10% discount  
**Adjusted Price:** 649.99 × 0.9 = 584.99  
**Minimum Profit Check:** 500.00 × 1.2 = 600.00  
**Final Price:** 600.00
