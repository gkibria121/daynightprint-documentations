---
id: overview
title: Overview
description: Guide to managing products and vendor products in the system.
sidebar_position: 1
---

# Product Management Overview

To show an item on the **customer-facing form**, we need to add **Vendor Products**. Here's how the process works:

1. **Create a Product**  
   Start by creating a product with the following details:

   - **Product Name**
   - **Product Image**

   > After creating a product, if there are no vendors in the system, you will need to [create a vendor](./create-vendor) before creating a vendor product.

2. **Create a Vendor Product**  
   A vendor product links a product to a vendor and includes vendor-specific details.

3. **Create a Vendor Product**  
   A vendor product links a product to a vendor and includes vendor-specific details.

   To create a vendor product, you need the following:

   - **Pricing Rules**: These are the product attributes the customer will choose from (e.g., size, material, or finish).
   - **Pricing Rule Meta**: Defines how each attribute is displayed to the user. It includes:
     - Input type (selection, checkbox, text input)
     - Default value
     - Conditional logic (e.g., show this field only if another attribute is selected)
     - You can also rename each rule for better display in the customer-facing form.
   - **Price Quantity**: A mapping of quantity to price. For example, a quantity of 10 might cost 50. This defines how the price scales with quantity.
   - **Delivery Rules**: Configure available delivery slots, constraints, and methods.

4. **Add Description**  
   The description added in the vendor product will be visible to customers in the form.

---

### Where to Manage

- **Products Menu Item**  
  Manage the base products available in your system.

- **Vendors Menu Item**  
  Manage all registered vendors.

- **Vendor Products Menu Item**  
  To show an item on the customer-facing form, we need to add vendor products here. This is where products are linked to specific vendors and enhanced with relevant descriptions and configuration options.

---

Once vendor products are set up properly, they will appear in the customer-facing form.
