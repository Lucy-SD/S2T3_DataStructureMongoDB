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
Exercise 1: Customer View Schema

javascript
// Schema based on image_1 interface
const customerSchema = new Schema({
  name: String,
  address: {
    street: String,
    number: String,
    floor: String,
    door: String,
    postalCode: String,
    country: String
  },
  telephone: String,
  email: String,
  registerDate: Date,
  recommendedBy: { type: Schema.Types.ObjectId, ref: 'Customer' }, // Self-reference
  purchases: [{
    glasses: { type: Schema.Types.ObjectId, ref: 'Glasses' },
    soldBy: { type: Schema.Types.ObjectId, ref: 'Employee' },
    saleDate: Date
  }]
});
Exercise 2: Glasses View Schema

javascript
// Schema based on image_2 interface
const glassesSchema = new Schema({
  brand: String,
  prescription: {
    left: Number,
    right: Number
  },
  frameType: { type: String, enum: ['floating', 'plastic', 'metal'] },
  frameColor: String,
  lensColor: String,
  price: Number,
  supplier: {
    name: String,
    nif: String,
    address: {
      street: String,
      number: String,
      city: String,
      postalCode: String,
      country: String
    },
    telephone: String,
    fax: String
  }
});
</details><details> <summary><strong>🍕 Level 2: Food Delivery System</strong></summary>
Exercise 1: Pizzeria Schema

javascript
// Schema based on image_3 interface
const orderSchema = new Schema({
  orderNumber: String,
  timestamp: Date,
  deliveryType: { type: String, enum: ['delivery', 'pickup'] },
  items: [{
    product: { type: Schema.Types.ObjectId, ref: 'Product' },
    quantity: Number,
    notes: String
  }],
  totalPrice: Number,
  customer: {
    name: String,
    surname: String,
    address: {
      street: String,
      number: String,
      floor: String,
      postalCode: String,
      town: String,
      province: String
    },
    telephone: String
  },
  store: { type: Schema.Types.ObjectId, ref: 'Store' },
  deliveryPerson: { type: Schema.Types.ObjectId, ref: 'Employee' },
  deliveryTime: Date
});

const pizzaSchema = new Schema({
  name: String,
  description: String,
  imageUrl: String,
  price: Number,
  category: { type: String, index: true } // Categories change yearly
});
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


## 🖼️ UI-Driven Design Samples

Interface	Schema Approach

Customer Profile
(image_1)	Embedded purchases array with populated glasses
Product View
(image_2)	Fully embedded supplier details
Order Tracking
(image_3)	Hybrid: customer details embedded, products referenced

## 🤝 Contributions

⭐ Star the repository

🍴 Fork the project

Add new schema designs:

bash
/level1/
   optical-customer.js
   optical-glasses.js
/level2/
   pizzeria-orders.js
Include sample documents in /data/

📥 Submit pull request with schema validations

## ⚠️ Deployment Notes

Atlas Setup: Enable mongodb+srv protocol in connection string

Index Management: Create indexes after initial data load

javascript
// Example index creation
db.glasses.createIndex({ brand: 1, price: -1 })
Data Population: Use mongorestore for sample datasets

## 🚀 Design Challenge: For advanced practice, implement aggregation pipelines that:

Calculate monthly sales per supplier (Optical Store)

Find average delivery time per store (Pizzeria)

Show customer lifetime value (Optical Store)

Submit solutions to advanced-aggregations/ folder!
