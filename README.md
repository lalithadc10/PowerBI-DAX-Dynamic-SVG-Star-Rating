#  Power BI DAX Dynamic SVG Star Rating

##  Project Overview

> **Project Note:**  
> This is a mini Power BI project created to explore how **DAX and SVG can be combined to create custom and dynamic visuals**.

Instead of displaying product ratings only as numbers, I created a **dynamic SVG star rating** that visually represents the average rating of each product.

The main objective was to understand how a simple business requirement can be transformed into a more intuitive visual using **DAX + SVG**.

---

#  Business Question

> **Which products are performing well, and how satisfied are customers with those products?**

To answer this question, I combined product-level metrics such as:

- Product Name
- Category
- Average Rating
- Total Revenue
- Total Orders

The dynamic star rating makes the customer-rating information easier to understand at a glance.

---

#  Why This Approach?

I started with a simple idea:

> **A rating such as 4.03 is useful, but a visual representation can make it easier to understand quickly.**

Power BI already provides standard visuals and conditional formatting, so the goal was not to use SVG just for decoration.

Instead, I wanted to understand:

- How DAX can control a visual
- How SVG can be generated dynamically
- How a custom visual can improve readability
- How visual design can support a business question

---

#  Dynamic SVG Star Rating

The SVG rating is generated dynamically based on the product's `avg_rating`.

For example:

| Average Rating | Visual |
|---|---|
| 4.5 | ⭐⭐⭐⭐☆ |
| 4.0 | ⭐⭐⭐⭐☆ |
| 3.5 | ⭐⭐⭐☆☆ |
| 3.0 | ⭐⭐⭐☆☆ |

The DAX measure reads the current product's rating and determines which stars should be filled or remain empty.

---

#  How It Works

Product Average Rating
          ↓
      DAX Measure
          ↓
 Determine Filled Stars
          ↓
       Generate SVG
          ↓
   Return Image URL
          ↓
 Display Inside Power BI
 

#  DAX Logic

The star rating is created using a DAX measure.

The measure first retrieves the product's average rating using `SELECTEDVALUE()` and then checks each star position using `IF()`.

```DAX
SVG Star Rating = 

VAR Rating =
    SELECTEDVALUE(
        product_summary[avg_rating],
        0
    )

VAR Star1 =
    IF(
        Rating >= 1,
        "%231713C7",
        "%23D9D9D9"
    )

VAR Star2 =
    IF(
        Rating >= 2,
        "%231713C7",
        "%23D9D9D9"
    )

VAR Star3 =
    IF(
        Rating >= 3,
        "%231713C7",
        "%23D9D9D9"
    )

VAR Star4 =
    IF(
        Rating >= 4,
        "%231713C7",
        "%23D9D9D9"
    )

VAR Star5 =
    IF(
        Rating >= 5,
        "%231713C7",
        "%23D9D9D9"
    )

RETURN

