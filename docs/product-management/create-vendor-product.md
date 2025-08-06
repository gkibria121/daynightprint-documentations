---
id: create-vendor-product
title: How to Create a Vendor Product
description: Step-by-step guide to adding a vendor product.
sidebar_position: 0
---

# How to Create a Vendor Product

To show a product on the customer-facing form, you must create a **Vendor Product**. Here's how:

## Step 1: Go to the Vendor Products

Navigate to the **Vendor Products** menu item, then click on **Add New Vendor Product**. This will open the vendor product creation form.

## Step 2: Fill Out Basic Information

The first section is **Basic Information**, which includes:

- **Product**: Select the product from the list of existing products.
- **Vendor**: Select the vendor from the list of registered vendors.
- **Rating**: Set a rating to give this vendor priority if the same product is available from multiple vendors.
- **VAT Rate**: Define the VAT rate to be used for tax calculations.
- **Should Calculate Price**: Choose `Yes` or `No` using radio buttons.
  - If set to **Yes**, the system will attempt to calculate the price dynamically based on customer input.
  - ⚠️ This feature is currently in **Beta** mode.

## Step 3: Add Additional Configuration

After completing the basic information, you will need to fill out the following sections:

- **Pricing Rules**
- **Pricing Rule Meta**
- **Delivery Options**
- **Quantity Pricing**

Each of these sections is discussed below in detail.

> 📌 Proper configuration of these sections ensures the vendor product will work correctly in pricing and delivery flows.

## Pricing Rules

**Pricing Rules** are used to add extra charges to a vendor product based on specific attribute selections made by the customer.

For example:

- Choosing the **color "Red"** might add an additional **10%** to the base price.
- Selecting a premium **material** may also increase the cost.

These rules allow flexible pricing strategies depending on product variations or customizations.

### How to Add a Pricing Rule

1. Click on the **Add** button in the Pricing Rules section.
2. For each pricing rule, fill in the following:
   - **Attribute**: The name of the variation (e.g., `Color`, `Material`).
   - **Value**: The specific option (e.g., `Red`, `Cotton`).
   - **Price**: The extra charge or percentage to apply (e.g., `+10%`, `+20` BDT).

You can add multiple rules to cover different combinations of attributes and values.

> 💡 These rules are used during price calculation if **"Should Calculate Price"** is enabled in the Basic Information section, and when the user selects their product specifications.

### Pricing Rule Meta

**Pricing Rule Meta** defines how a specific pricing rule will be displayed and behave on the customer-facing form. It allows for dynamic form behavior, input validation, and default value setup.

#### 🔧 Configuration Options:

- **Attribute**
  The pricing attribute or rule label that will be shown to the customer (e.g., _Booklet/Brochure Type_).

- **Default Value**
  You can preselect a default value (e.g., _Saddle Stitched (Staple Bound)_) for the rule to guide user choice.

- **Description**
  Optional field to provide contextual help or notes about the rule.

- **Input Type**
  Determines how users will interact with the rule (e.g., `radio`, `dropdown`, `text`, etc.).

#### ✅ Rule Behavior Controls:

- **Required**
  Make the field mandatory before form submission.

- **Has Other**
  Allow users to enter a custom value outside the predefined options.

#### 🔁 Conditional Logic (Dynamic Field Visibility):

You can **enable conditional logic** to show or hide a pricing rule field based on other selections.
Each rule has:

- **Action** (Show/Hide)
- **Match Type** (All/Any)
- One or more **conditions** consisting of:

  - **Attribute** (e.g., Orientation)
  - **Condition** (e.g., is)
  - **Value** (e.g., Landscape)

Example:

```text
Show this field if All of the following match:
Orientation is Landscape
```

#### 🔐 Custom Validation (Pattern Matching & Function)

You can **enable custom validation** for pricing rules. This ensures that user inputs follow specific formats or rules.

There are two types of validations supported:

- **1. Pattern Validation (Regex):**
  Use regular expressions to validate format.
  **Example:** To allow only numbers: `/^\d+$/`

- **2. Validation Function:**
  Define a custom arrow function to validate the input.
  The function must return:

  - `true` if the input is valid.
  - A **string message** if the input is invalid.

  **Example:**

  ```js
  (value) => value.length > 0 || "This field cannot be empty";
  ```

  **Example 2:**

  ```js
  (value) => /^[0-9]+$/.test(value) || "Only numbers are allowed";
  ```

These validations ensure robust and user-friendly forms when customers provide custom pricing input.

> 🔄 **Note:**
> Whenever you add or modify a **pricing rule**, you **must refresh the pricing rule meta**.
> This ensures that the pricing rule meta entries are updated to reflect the latest changes.

---

## 🛻 Delivery Options

To define how and when a product can be delivered, you can configure **Delivery Slots** in the **Delivery Options** section of the Vendor Product form.

### ➕ How to Add a Delivery Slot

Click the **"Add New"** button inside the Delivery Options section. This will let you define a new delivery slot with the necessary details.

Each delivery slot includes the following fields:

| Field            | Description                                                                                     |
| ---------------- | ----------------------------------------------------------------------------------------------- |
| **Label**        | Name or title of the delivery slot (e.g., "Standard 5–10 Days Delivery")                        |
| **Start Date**   | When the delivery window begins (in working days from the order date, e.g., `5`)                |
| **Start Time**   | The time of day the delivery window starts (e.g., `09:00 AM`)                                   |
| **End Date**     | When the delivery window ends (e.g., `10`)                                                      |
| **End Time**     | The time of day the delivery window ends (e.g., `09:00 PM`)                                     |
| **Max Quantity** | Maximum number of items allowed per order for this slot                                         |
| **Price**        | Cost for using this delivery slot                                                               |
| **Cutoff Time**  | The latest time the customer can place an order to be eligible for this slot (e.g., `11:50 AM`) |

---

### 📦 Example: 5–10 Working Days Delivery

Let’s walk through an example:

- **Label**: `5–10 Working Days`
- **Start Date**: `5`
- **Start Time**: `09:00 AM`
- **End Date**: `10`
- **End Time**: `09:00 PM`
- **Max Quantity**: `100`
- **Price**: `10`
- **Cutoff Time**: `11:50 AM`

📌 **What this means:**

> If a customer places an order **before 11:50 AM**, they will be eligible for this delivery slot. The item will be delivered **between the 5th and 10th working day**, anytime from **9:00 AM to 9:00 PM**, with a cost of **10** and a maximum quantity of **100** items.

## 💰 Quantity Pricing

**Quantity Pricing** allows you to define how product pricing changes based on the ordered quantity. This is especially useful for setting **bulk discounts** or handling **tiered pricing models**.

---

### 🧾 Fields

Each entry in Quantity Pricing includes:

| Field        | Description                                                        |
| ------------ | ------------------------------------------------------------------ |
| **Quantity** | The quantity for which this specific price applies                 |
| **Price**    | The price that will be charged when the user selects this quantity |

You can define multiple quantity-price pairs to reflect different cost relationships.

---

### 📌 Example

| Quantity | Price |
| -------- | ----- |
| 10       | 150   |
| 100      | 1200  |
| 110      | 1250  |

> 💡 The system uses these entries to determine total pricing based on selected quantity.
