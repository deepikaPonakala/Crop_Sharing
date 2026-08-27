# 🌾 Crop Sharing Platform

A full-stack web application that provides a direct digital marketplace connecting **farmers and buyers**. Farmers can list their agricultural produce with pricing, quantity, location, images, and transport options, while buyers can browse crops, place orders, calculate transportation costs, and track their orders.

The platform is designed to reduce dependency on intermediaries and provide a more transparent and convenient way for farmers and buyers to interact.

---

# 🌱 Overview

The **Crop Sharing Platform** is designed to create a direct connection between agricultural producers and customers.

### Farmers can:

* Register and log in as farmers
* Add agricultural crops
* Specify crop quantity and price
* Add crop descriptions
* Add farm location and address
* Upload crop images
* Specify available transportation options
* View their uploaded crops
* Manage buyer requests
* View orders related to their crops
* Accept or reject requests

### Buyers can:

* Register and log in as buyers
* Browse available crops
* View crop details and farmer information
* Search for a destination address
* Select transportation
* Calculate transportation cost
* Calculate total order cost
* Place crop orders
* View order details
* Track their orders
* Submit and view reviews

---

# 🚀 Key Features

## 👨‍🌾 Farmer Features

### Farmer Registration & Login

Farmers can create an account by providing their details and can securely log in using their email and password.

Authentication uses:

* JWT
* bcrypt password hashing
* Role-based access

---

### 🌾 Crop Listing

Farmers can add crops with information such as:

* Crop name
* Quantity
* Price per kilogram
* Crop description
* State
* Source city
* Farm address
* Latitude
* Longitude
* Available transport types
* Crop image

Example:

```text
Crop: Tomatoes
Quantity: 1000 kg
Price: ₹40/kg
Location: Guntur, Andhra Pradesh
Transport: Truck, Lorry, Tractor, Van
```

---

### 📦 My Uploads

Farmers can view the crops they have uploaded and manage their listings.

---

### 📩 Buyer Requests

Farmers can receive buyer requests and manage their status.

Requests can be:

* Pending
* Accepted
* Rejected

---

### 🚚 Farmer Orders

Farmers can view orders placed for their crops and manage the order-related workflow.

---

# 🛒 Buyer Features

## Buyer Registration & Login

Buyers can create accounts and log in securely.

---

## 🔎 Browse Crops

Buyers can browse crops available on the marketplace.

Crop information includes:

* Crop name
* Price
* Quantity
* Description
* Farmer information
* Location
* Crop image

---

## 🌾 Crop Details

Buyers can open an individual crop listing to view complete information before ordering.

The crop details page displays:

```text
Crop Name
Price
Quantity
Description

Farmer Details
    Name
    Phone
    Country
    State
    Village
```

---

# 🛍️ Order Workflow

The buyer order process works as follows:

```text
Browse Crops
     ↓
Select Crop
     ↓
View Crop Details
     ↓
Place Order
     ↓
Enter Quantity
     ↓
Enter Destination
     ↓
Select Transport
     ↓
Calculate Transport Cost
     ↓
Calculate Total Cost
     ↓
Confirm Order
     ↓
Order Created
     ↓
Order Success Page
```

---

# 🚚 Transport Cost Calculation

The platform includes a transport-cost calculation system.

The buyer selects:

* Destination address
* Transport type
* Quantity

The application obtains the destination's:

* Latitude
* Longitude

using address search.

The system then sends the source and destination coordinates to the backend.

Example request:

```json
{
  "source_lat": 16.29151890,
  "source_lon": 80.45415880,
  "destination_lat": 17.3850,
  "destination_lon": 78.4867,
  "vehicle": "Truck"
}
```

The backend calculates the transportation cost using transport-related database information.

The result contains information such as:

```text
Distance
Transport Rate
Loading Charge
Toll
Transport Cost
```

---

# 💰 Total Order Cost

The final order amount is calculated as:

```text
Crop Cost = Quantity × Crop Price

Total Amount =
Crop Cost + Transport Cost
```

For example:

```text
Quantity       = 100 kg
Crop Price     = ₹40/kg

Crop Cost      = ₹4,000

Transport Cost = ₹800

Total Amount   = ₹4,800
```

---

# 🗺️ Location Search

The application uses **OpenStreetMap Nominatim** for destination address search.

When a buyer enters an address, matching locations are displayed.

After selecting an address, the application stores:

```text
Destination Address
Latitude
Longitude
```

These coordinates are then used for transport-cost calculation.

---

# ⭐ Reviews

The application includes a review system.

Users can access the review functionality through the reviews page.

The backend contains a dedicated review controller and review model for managing review-related operations.

---

# 🛠️ Technology Stack

## Frontend

* HTML5
* CSS3
* JavaScript
* Fetch API
* Browser Local Storage
* OpenStreetMap Nominatim API

## Backend

* Node.js
* Express.js
* MySQL2
* JWT
* bcrypt
* Multer
* Axios
* CORS
* Body Parser
* dotenv

## Database

* MySQL

## Authentication

* JSON Web Tokens (JWT)
* bcrypt password hashing

## Version Control

* Git
* GitHub

---

# 📁 Project Structure

```text
Crop_Sharing/
│
├── backend/
│   │
│   ├── config/
│   │   └── db.js
│   │
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── cropController.js
│   │   ├── orderController.js
│   │   ├── requestController.js
│   │   ├── reviewController.js
│   │   └── transportController.js
│   │
│   ├── middleware/
│   │   ├── authMiddleware.js
│   │   └── uploadMiddleware.js
│   │
│   ├── models/
│   │   ├── Crop.js
│   │   ├── Request.js
│   │   ├── User.js
│   │   ├── orderModel.js
│   │   └── reviewModel.js
│   │
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── cropRoutes.js
│   │   ├── orderRoutes.js
│   │   ├── requestRoutes.js
│   │   ├── reviewRoutes.js
│   │   ├── transportRoutes.js
│   │   └── userRoutes.js
│   │
│   ├── package.json
│   ├── package-lock.json
│   └── server.js
│
├── frontend/
│   │
│   ├── css/
│   │   ├── add_crop.css
│   │   ├── common.css
│   │   ├── farmer-dashboard.css
│   │   ├── home.css
│   │   ├── login.css
│   │   ├── order-details.css
│   │   └── style.css
│   │
│   ├── js/
│   │   ├── add_crop.js
│   │   ├── buyer.js
│   │   ├── crop_details.js
│   │   ├── farmer.js
│   │   ├── login.js
│   │   ├── main.js
│   │   ├── my-orders.js
│   │   ├── order-details.js
│   │   ├── order.js
│   │   ├── order_success.js
│   │   ├── register.js
│   │   └── reviews.js
│   │
│   ├── add_crop.html
│   ├── buyer_dashboard.html
│   ├── crop_details.html
│   ├── farmer_dashboard.html
│   ├── farmer_orders.html
│   ├── index.html
│   ├── login.html
│   ├── logout.html
│   ├── my-orders.html
│   ├── my_uploads.html
│   ├── order-details.html
│   ├── order.html
│   ├── order_success.html
│   ├── register.html
│   └── reviews.html
│
├── public/
│   └── images/
│       ├── Okra.jpg
│       ├── banana.jpg
│       ├── beans.jpg
│       ├── beetroot.jpg
│       ├── bittergourd.jpg
│       ├── bottlegourd.webp
│       ├── brinjal.webp
│       ├── cabbage.jpg
│       ├── capsicum.jpg
│       ├── carrot.jpg
│       ├── cauliflower.jpg
│       ├── coriander.jpg
│       ├── corn.jpg
│       ├── cotton.jpg
│       ├── cucumber.jpg
│       ├── garlic.jpg
│       ├── ginger.png
│       ├── grapes.jpg
│       ├── green_chillies.jpg
│       ├── groundnut.jpg
│       ├── guava.jpg
│       ├── keera.jpg
│       ├── lemon.jpg
│       ├── onion.jpg
│       ├── orange.jpg
│       ├── paddy_rice.jpg
│       ├── papaya.png
│       ├── pineapple.jpg
│       ├── potato.jpg
│       ├── pumpkin.jpg
│       ├── raddish.jpg
│       ├── sugarcane.jpg
│       ├── tomatoes.jpeg
│       ├── turmeric.jpg
│       └── wheat.jpg
│
├── .gitignore
└── README.md
```

---

# 🗄️ Database

The application uses a MySQL database named:

```text
crop_marketplace
```

The database contains the following tables:

```text
users
crops
buyer_requests
crop_transport
orders
requests
reviews
road_distances
transport_rates
```

---

# 📊 Database Tables

## users

Stores registered user information.

Important information includes:

* User ID
* Name
* Email
* Password hash
* Role
* Country
* State
* Village
* Phone
* Registration information

Roles include:

```text
farmer
buyer
```

---

## crops

Stores crop listings created by farmers.

Crop information includes:

* Crop ID
* Farmer ID
* Crop name
* Quantity
* Price
* Details
* State
* Source city
* Farm address
* Latitude
* Longitude
* Image
* Transport information

---

## buyer_requests

Stores buyer requests related to crop listings.

---

## requests

Stores request-related information and statuses between buyers and farmers.

---

## crop_transport

Stores transportation options associated with crop listings.

Examples:

```text
Truck
Lorry
Tractor
Van
Auto
```

---

## orders

Stores completed/placed buyer orders.

Order information includes details such as:

* Buyer
* Crop
* Farmer
* Quantity
* Crop price
* Transport cost
* Total amount
* Destination address
* Destination coordinates
* Transport type
* Order status

---

## reviews

Stores review information associated with the platform's review functionality.

---

## road_distances

Stores road-distance information used by the transportation system.

---

## transport_rates

Stores transportation rates used for calculating delivery costs.

---

# 🔐 Authentication

Authentication is implemented using **JWT**.

The general flow is:

```text
User Login
     ↓
Backend validates credentials
     ↓
Password verified using bcrypt
     ↓
JWT generated
     ↓
Token stored on client
     ↓
Token sent with protected API requests
     ↓
Authentication middleware verifies token
     ↓
Request allowed
```

Protected requests use:

```http
Authorization: Bearer <token>
```

The authenticated user's ID is available through the request user information.

---

# 🖼️ Image Handling

Crop images uploaded by farmers are handled using **Multer**.

Uploaded crop images are stored locally under:

```text
backend/uploads/crops/
```

The database stores the image path associated with the crop.

Example:

```text
uploads/crops/example.jpg
```

The repository also contains predefined crop images under:

```text
public/images/
```

### Important

The `backend/uploads/` directory is intentionally excluded from Git because uploaded user content should not be committed to the repository.

When deploying the application, uploaded images should ideally be moved to persistent/cloud storage.

---

# ⚙️ Installation

## 1. Clone the repository

```bash
git clone https://github.com/deepikaPonakala/Crop_Sharing.git
```

Then:

```bash
cd Crop_Sharing
```

---

# 🗄️ 2. Configure MySQL

Create a MySQL database:

```sql
CREATE DATABASE crop_marketplace;
```

The required tables must then be created/imported into the database.

The project expects the following database:

```text
Database: crop_marketplace
```

---

# 🔑 3. Create the Environment File

Inside:

```text
backend/
```

create:

```text
.env
```

Example:

```env
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=crop_marketplace

JWT_SECRET=your_secret_key

PORT=3000
```

### Never commit `.env`

The `.env` file contains sensitive information and should remain local.

---

# 📦 4. Install Backend Dependencies

Open a terminal:

```bash
cd backend
```

Then:

```bash
npm install
```

---

# ▶️ 5. Start the Backend

Run:

```bash
npm start
```

or:

```bash
node server.js
```

The backend will run on:

```text
http://localhost:3000
```

The application uses:

```js
const PORT = process.env.PORT || 3000;
```

so the port can also be provided by a deployment platform.

---

# 🌐 6. Open the Frontend

The frontend contains pages such as:

```text
login.html
register.html
index.html
```

For local development, the application should be accessed through the configured server rather than relying on arbitrary file paths.

The login page is:

```text
http://localhost:3000/login.html
```

---

# 🖥️ Application Pages

## General

| Page            | Purpose      |
| --------------- | ------------ |
| `index.html`    | Home page    |
| `login.html`    | Login        |
| `register.html` | Registration |
| `logout.html`   | Logout       |

## Farmer

| Page                    | Purpose                |
| ----------------------- | ---------------------- |
| `farmer_dashboard.html` | Farmer dashboard       |
| `add_crop.html`         | Add crop               |
| `my_uploads.html`       | Farmer's crop listings |
| `farmer_orders.html`    | Farmer orders          |

## Buyer

| Page                   | Purpose          |
| ---------------------- | ---------------- |
| `buyer_dashboard.html` | Buyer dashboard  |
| `crop_details.html`    | Crop details     |
| `order.html`           | Place an order   |
| `order_success.html`   | Successful order |
| `my-orders.html`       | Buyer's orders   |
| `order-details.html`   | Order details    |
| `reviews.html`         | Reviews          |

---

# 🔌 API Structure

The backend follows a controller/model/route architecture.

```text
Frontend
   ↓
API Route
   ↓
Controller
   ↓
Model
   ↓
MySQL
```

Main API areas include:

### Authentication

```text
/api/auth
```

Handles registration and login.

### Crops

```text
/api/crops
```

Handles crop creation, retrieval, farmer crop listings, and deletion.

### Orders

```text
/api/orders
```

Handles buyer order operations.

### Requests

```text
/api/requests
```

Handles buyer/farmer requests.

### Reviews

```text
/api/reviews
```

Handles review operations.

### Transport

```text
/api/transport
```

Transport calculation is available through:

```text
POST /api/transport/calculate
```

---

# 🧩 Backend Architecture

The backend follows separation of concerns.

## Routes

Routes define API endpoints.

```text
routes/
```

## Controllers

Controllers contain request-handling logic.

```text
controllers/
```

## Models

Models communicate with the MySQL database.

```text
models/
```

## Middleware

Middleware handles functionality such as:

* JWT authentication
* File uploads

```text
middleware/
```

## Configuration

Database configuration is located in:

```text
backend/config/db.js
```

---

# 🔄 Complete System Workflow

```text
                    CROP SHARING PLATFORM
                             │
             ┌───────────────┴───────────────┐
             │                               │
          FARMER                           BUYER
             │                               │
          Register                        Register
             │                               │
           Login                           Login
             │                               │
      Farmer Dashboard                Buyer Dashboard
             │                               │
        Add Crop                       Browse Crops
             │                               │
      Crop Information                Crop Details
             │                               │
      Upload Image                    Select Quantity
             │                               │
     Select Transport                Destination Search
             │                               │
             │                         Select Transport
             │                               │
             │                       Calculate Transport
             │                               │
             │                        Calculate Total
             │                               │
             │                         Place Order
             │                               │
             └───────────────┬───────────────┘
                             │
                           MySQL
                             │
                    Order / Request Data
```

---

# 🔒 Security

The project uses several security mechanisms:

### Password Hashing

Passwords are hashed using:

```text
bcrypt
```

Passwords should never be stored as plain text.

### JWT Authentication

Protected API requests use JWT authentication.

### Environment Variables

Database credentials and JWT secrets are stored in:

```text
.env
```

rather than inside the source code.

### Git Ignore

Local/private resources such as:

```text
.env
node_modules/
backend/uploads/
```

are excluded from Git.

---

# ☁️ Deployment

The project can be deployed using cloud services.

A possible deployment architecture is:

```text
GitHub
   │
   ├── Node.js / Express Backend
   │        ↓
   │      Render
   │
   └── MySQL Database
            ↓
         Railway
```

The deployed backend must use cloud database credentials instead of:

```env
DB_HOST=localhost
```

For production, environment variables should be configured directly in the hosting platform.

Example:

```env
DB_HOST=<cloud-mysql-host>
DB_USER=<cloud-mysql-user>
DB_PASSWORD=<cloud-mysql-password>
DB_NAME=<cloud-mysql-database>
JWT_SECRET=<production-secret>
PORT=<platform-port>
```

Do not place production credentials in GitHub.

---

# ⚠️ Deployment Considerations

The current application stores uploaded crop images under:

```text
backend/uploads/crops/
```

Local filesystem storage may not be persistent on some cloud hosting platforms.

For production deployment, consider using:

* Cloudinary
* Amazon S3
* Cloud storage
* Another persistent object-storage service

for farmer-uploaded crop images.

---

# 🧪 Local Development

Recommended development workflow:

```bash
# Clone
git clone https://github.com/deepikaPonakala/Crop_Sharing.git

# Enter project
cd Crop_Sharing

# Backend
cd backend

# Install dependencies
npm install

# Configure .env

# Start server
npm start
```

Then open:

```text
http://localhost:3000/login.html
```

---

# 📦 Backend Dependencies

The backend uses:

* `express`
* `mysql2`
* `bcrypt`
* `jsonwebtoken`
* `multer`
* `axios`
* `cors`
* `body-parser`
* `dotenv`

Install them with:

```bash
npm install
```

---

# 📦 Frontend

The frontend is built using:

```text
HTML
CSS
JavaScript
```

No frontend framework is required.

The frontend communicates with the Express backend using the browser's `fetch()` API.

---

# 🔄 Updating the GitHub Repository

After making changes:

```bash
git status
```

Stage changes:

```bash
git add .
```

Commit:

```bash
git commit -m "Describe your changes"
```

Push:

```bash
git push
```

Do not use `git push --force` for normal updates.

---

# 🚧 Current Limitations

Some aspects should be improved before treating the application as a production-scale system:

* Uploaded crop images currently use local filesystem storage.
* Production deployment requires a cloud MySQL database.
* Production environment variables must be configured on the hosting platform.
* Transport pricing depends on the configured transport/rate data.
* Additional validation and production-level error handling can be added.
* HTTPS should be used in production.
* Cloud image storage is recommended for persistent uploaded files.

---

# 🔮 Future Enhancements

Possible future improvements include:

* 💳 Online payment integration
* 📍 Live map integration
* 🚚 Real-time delivery tracking
* 🔔 Notifications for buyers and farmers
* 📱 Responsive mobile-first interface
* ☁️ Cloud image storage
* 📊 Farmer analytics dashboard
* 📈 Crop price trends
* 🤖 Crop price prediction
* 🌦️ Weather integration
* ⭐ Advanced rating and review system
* 🔎 Advanced crop filtering and search
* 🧾 Downloadable invoices
* 📦 Order status tracking
* 🛡️ Advanced authorization and validation

---

# 👥 User Experience

## Farmer

```text
Register
   ↓
Login
   ↓
Farmer Dashboard
   ↓
Add Crop
   ↓
Manage Crops
   ↓
Receive Requests / Orders
   ↓
Manage Transactions
```

## Buyer

```text
Register
   ↓
Login
   ↓
Buyer Dashboard
   ↓
Browse Crops
   ↓
View Crop Details
   ↓
Place Order
   ↓
Calculate Transport
   ↓
Confirm Order
   ↓
Track Order
   ↓
Review
```

---

# 🌾 Supported Crop Images

The project currently contains predefined images for crops including:

* Okra
* Banana
* Beans
* Beetroot
* Bitter Gourd
* Bottle Gourd
* Brinjal
* Cabbage
* Capsicum
* Carrot
* Cauliflower
* Coriander
* Corn
* Cotton
* Cucumber
* Garlic
* Ginger
* Grapes
* Green Chillies
* Groundnut
* Guava
* Keera
* Lemon
* Onion
* Orange
* Paddy Rice
* Papaya
* Pineapple
* Potato
* Pumpkin
* Radish
* Sugarcane
* Tomatoes
* Turmeric
* Wheat

Images are stored in:

```text
public/images/
```

---

# 📄 License

This project is currently provided for educational and project-development purposes.

---

# 🌱 Project Goal

The goal of the **Crop Sharing Platform** is to use technology to create a direct connection between farmers and buyers.

By allowing farmers to list their produce and buyers to directly discover, evaluate, order, and review agricultural products, the platform aims to make agricultural trade more transparent, accessible, and efficient.

---

## 🌾 Crop Sharing Platform

**Connecting Farmers. Empowering Buyers. Simplifying Agricultural Trade.**
