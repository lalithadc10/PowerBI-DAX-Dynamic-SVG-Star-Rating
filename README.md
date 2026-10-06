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

The measure first retrieves the product's average rating using `SELECTEDVALUE()` and then checks each star position using IF()

DAX
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





#  Key DAX Concepts Practiced

This project helped me practice:

- `SELECTEDVALUE()` — retrieves the current product's rating
- `IF()` — controls whether each star is filled or empty
- `VAR` — organizes the DAX logic
- Dynamic SVG generation using DAX
- SVG `polygon` — creates the star shape
- SVG `viewBox` — controls the SVG coordinate system
- SVG `width` and `height` — controls the displayed size
- URL encoding for SVG colours
- Power BI **Image URL** data category
- Filter context — allows the visual to respond to the current product

---

#  Business Analysis Approach

I did not want to create the SVG only as a technical exercise.

I connected it to a simple business question:

> **Which products are performing well, and how satisfied are customers with those products?**

The analysis combines:

- Product
- Category
- Average Rating
- Total Revenue
- Total Orders

The rating visual makes it easier to compare customer satisfaction alongside product performance.

For example:

###  High Revenue + High Rating

Potential strong-performing products.

###  High Revenue + Lower Rating

Products that may deserve further investigation.

###  Lower Revenue + High Rating

Products that may have good customer acceptance but lower sales performance.

The purpose is not to assume the reason behind the rating, but to identify **where further analysis may be useful**.

---

#  Why Use SVG?

Power BI already provides standard visuals and conditional formatting.

I used SVG because it provides greater control over the visual design and allows the rating to be displayed directly inside the product table.

SVG provided control over:

- Star shape
- Star size
- Filled and empty states
- Positioning
- Visual appearance

The key concept I learned was:

> **DAX controls the logic, while SVG controls the visual design.**

---

#  Business Questions This Visual Can Support

The visual can help explore questions such as:

1. **Which products have the highest customer ratings?**

2. **Which products generate strong sales but have lower ratings?**

3. **How does customer satisfaction vary across categories?**

4. **Are highly rated products also strong sellers?**

5. **Which products should be investigated further?**

---

#  Final Report View

The final report focuses on:

## **Product Performance & Customer Satisfaction**

The view combines product-level information with the dynamic SVG star rating.

Users can use the category filter to explore different product groups.

The intention was to keep the report simple while still making the customer-rating information visually clear.

---

#  Tools & Technologies

| Tool | Purpose |
|---|---|
| Power BI Desktop | Data visualization and dashboard |
| DAX | Business logic and dynamic calculations |
| SVG | Custom star-rating visual |
| Power BI Image URL | Rendering SVG inside the report |
| GitHub | Project documentation and portfolio |

---

#  What I Learned

This mini-project helped me understand that a Power BI feature becomes more valuable when it is connected to a business question.

My learning journey was:

Business Question
        ↓
Identify Relevant Metrics
        ↓
Create DAX Logic
        ↓
Generate SVG
        ↓
Display as Image URL
        ↓
Improve Visual Communication
        ↓
Support Business Investigation
