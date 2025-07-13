# 🎓 MongoDB Database Structure

**👨‍💻 Author**: Lucy Castro

**🧠 Learning Focus**: NoSQL Schema Design, Document Modeling, MongoDB Aggregation

**🛠️ Tools**: MongoDB Atlas/Compass, Mongoose ODM

**💾 Database**: MongoDB (NoSQL)


## 📄 Description

This repository contains MongoDB design exercises focused on translating real-world business scenarios into optimized NoSQL schemas
Exercises implement:

- Embedded documents vs. references

- Document structure optimization

- Complex query patterns

- Real-time data modeling for web interfaces

- Three business cases modeled:

- Optical Store Management (Level 1)

- Food Delivery System (Level 2)

- E-commerce Interfaces (UI-driven schema design)

## 💻 Technologies Used

🔹 MongoDB 6.0+ (Document Database)

🔹 Mongoose.js (Schema Modeling)

🔹 Atlas CLI (Cloud Deployment)

🔹 JSON (Data Structure)

🔹 Aggregation Pipeline (Advanced Queries)


## 📋 Requirements

✅ MongoDB Atlas account (Signup)

✅ Node.js v18+

✅ Mongoose npm package

✅ Basic JavaScript knowledge


## 🛠️ Setup
bash

git clone https://github.com/Lucy-SD/S2T3_DataStructureMongoDB

Install dependencies -> npm install mongoose

Configure connection -> echo "ATLAS_URI='your_mongodb_uri'" > .env


## 📂 Exercise Catalog
<details> <summary><strong>👓 Level 1: Optical Store</strong></summary>

An optician, called "Cul d'Ampolla", wants to computerize customer management and eyeglass sales.

First of all, the optician wants to know who the supplier of each pair of glasses is. Specifically, they want to know about each supplier : The name, address (street, number, floor, door, city, postal code and country), telephone, fax, NIF.

About the glasses, you want to know: The brand, the prescription of each lens, the type of frame (floating, plastic or metal), the color of the frame, the color of each lens and the price.

From the customers you want to store: Name, postal address, telephone, email, registration date.
When a new customer arrives, store the customer who recommended the establishment (provided someone recommended it).
Our system will need to indicate which employee sold each pair of glasses. It will define the day/time the sale was made.
Exercise 1: Customer View Schema
Imagine we have the graphical interface from the point of view of an Optician customer. How would you design the database that would facilitate the information?
Exercise 2: Glasses Viwe Schema
What if the point of view was the interface and the glasses were the same?

</details><details> <summary><strong>🍕 Level 2: Food Delivery System</strong></summary>
Exercise 1: Pizzeria Schema

You have been hired to design a website that allows you to order food at home online.

Keep the following guidelines in mind when modeling what the project database would look like:

For each client we store a unique identifier: Name, surname, address, postal code, town, province, telephone number.

A person can place many orders, but a single order can only be placed by a single person. A unique identifier is stored for each order: Date/time of placement, whether the order is for home delivery or for collection in store, the quantity of products selected of each type, the total price, and a note with additional information.

An order can consist of one or several products.


The products can be pizzas, hamburgers and drinks. A unique identifier is stored for each product: Name, description, image, price. In the case of pizzas, there are several categories that can change names throughout the year.

An order is managed by a single store and a store can manage many orders. A unique identifier is stored for each store: Address, postal code, city, province.


Many employees can work in a store and an employee can only work in one store. For each employee, a unique identifier is stored: Name, surname, NIF, Telephone, if they work as a cook or delivery person. For home delivery orders, it is important to store who the delivery person is who delivers the order and the date/time of delivery.

</details>

## 🎯 Learning Goals

✅ Design schemas for different access patterns

✅ Implement relationships (embedding vs. referencing)

✅ Model hierarchical data (addresses, nested objects)

✅ Optimize for UI data requirements

✅ Handle temporal data (categories changing yearly)


## 🏆 Best Practices Implemented

✔️ Context-Driven Schemas: Different views (customer/glasses) require different structures

✔️ Mixed Referencing: Critical data embedded, less accessed data referenced

✔️ Enum Constraints: frameType: ['floating','plastic','metal']

✔️ Indexed Fields: Frequently queried fields like category indexed

✔️ Self-Referencing: Customer referrals within same collection


## 🤝 Contributions

⭐ Star the repository

🍴 Fork the project

📥 Submit pull request with schema validations


## 🚀 Thanks for Visiting = )
