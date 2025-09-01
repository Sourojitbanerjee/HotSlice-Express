# 🍕 HotSlice Express - Pizza Delivery Application

A full-stack pizza delivery application built with React, Node.js, Express, and MongoDB. Features real-time inventory management, custom pizza builder, integrated payments, and comprehensive admin controls.

## 📁 Project Structure

```
hotslice-express/
├─ server/                  # Node + Express + MongoDB API
│  ├─ src/
│  │  ├─ config/
│  │  │  └─ db.js           # MongoDB connection configuration
│  │  ├─ middleware/
│  │  │  ├─ auth.js         # JWT authentication middleware
│  │  │  └─ adminOnly.js    # Admin role verification middleware
│  │  ├─ models/
│  │  │  ├─ User.js         # User schema with roles (admin/user)
│  │  │  ├─ Token.js        # Email verification tokens
│  │  │  ├─ MenuItem.js     # Pizza bases, sauces, cheese, veggies
│  │  │  ├─ Inventory.js    # Stock management schema
│  │  │  └─ Order.js        # Order tracking and status management
│  │  ├─ routes/
│  │  │  ├─ auth.routes.js  # Registration, login, email verification
│  │  │  ├─ menu.routes.js  # Pizza customization options
│  │  │  ├─ order.routes.js # Order placement and tracking
│  │  │  └─ admin.routes.js # Inventory and order management
│  │  ├─ utils/
│  │  │  ├─ mailer.js       # Email service integration
│  │  │  └─ razorpay.js     # Payment gateway integration
│  │  └─ server.js          # Express server setup and configuration
│  ├─ .env.example          # Environment variables template
│  ├─ package.json
│  └─ README.md
└─ client/                  # React Frontend (Vite)
   ├─ index.html
   ├─ package.json
   └─ src/
      ├─ main.jsx           # React app entry point
      ├─ App.jsx            # Main app component with routing
      ├─ api/axios.js       # API client configuration
      ├─ contexts/
      │  ├─ AuthContext.jsx # Global authentication state
      │  └─ CartContext.jsx # Shopping cart state management
      ├─ components/
      │  ├─ Navbar.jsx      # Navigation component
      │  ├─ ProtectedRoute.jsx # Route protection for auth
      │  └─ PizzaBuilder/   # Pizza customization components
      │     ├─ BaseSelector.jsx    # Pizza base selection
      │     ├─ SauceSelector.jsx   # Sauce selection
      │     ├─ CheeseSelector.jsx  # Cheese selection
      │     └─ VeggieSelector.jsx  # Vegetable toppings
      ├─ pages/
      │  ├─ Home.jsx        # Landing page
      │  ├─ Login.jsx       # User authentication
      │  ├─ Register.jsx    # User registration with email verification
      │  ├─ Dashboard.jsx   # User/Admin dashboard
      │  ├─ BuildPizza.jsx  # Pizza customization interface
      │  └─ Checkout.jsx    # Payment and order confirmation
      └─ styles.css         # Global styles and responsive design
```

## 🚀 Features

### 🔐 Authentication System
- **User Registration** with email verification
- **Secure Login** with JWT tokens
- **Password Reset** functionality
- **Role-based Access** (Admin/User)
- **Protected Routes** for authenticated users

### 🍕 Pizza Customization
- **Interactive Pizza Builder** with real-time preview
- **Multiple Base Options**: Thin, Thick, Stuffed, Gluten-free, Whole wheat
- **Sauce Varieties**: Tomato, Pesto, BBQ, White, Buffalo
- **Cheese Selection**: Mozzarella, Cheddar, Parmesan, Feta, Vegan
- **Fresh Vegetables**: Multiple topping options
- **Dynamic Pricing** with real-time calculation

### 💳 Payment Integration
- **Razorpay Integration** for secure payments
- **Test Mode Support** for development
- **Order Confirmation** with payment verification
- **Transaction Tracking** and receipt generation

### 📦 Order Management
- **Real-time Order Tracking**: Received → In Kitchen → Out for Delivery
- **Order History** for customers
- **Status Updates** reflected across user and admin dashboards
- **Order Details** with itemized pricing

### 🏪 Admin Panel
- **Comprehensive Inventory Management**
  - Real-time stock tracking for all ingredients
  - Low stock alerts and notifications
  - Automatic inventory updates after orders
  - Bulk restocking capabilities
- **Order Management Dashboard**
  - View all incoming orders
  - Update order status in real-time
  - Order analytics and reporting
- **User Management** and role assignment

### 📧 Notification System
- **Email Notifications** for:
  - Account verification
  - Order confirmations
  - Status updates
  - Low inventory alerts to admins
- **In-app Notifications** for real-time updates

## 🛠️ Technology Stack

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - Database with Mongoose ODM
- **JWT** - Authentication tokens
- **bcryptjs** - Password hashing
- **Nodemailer** - Email service
- **Razorpay** - Payment gateway

### Frontend
- **React 18** - UI framework
- **Vite** - Build tool and dev server
- **React Router** - Client-side routing
- **Context API** - State management
- **Axios** - HTTP client
- **Tailwind CSS** - Styling framework

## ⚡ Quick Start

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (local installation or MongoDB Atlas)
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/hotslice-express.git
   cd hotslice-express
   ```

2. **Install server dependencies**
   ```bash
   cd server
   npm install
   ```

3. **Install client dependencies**
   ```bash
   cd ../client
   npm install
   ```

### Environment Configuration

1. **Create server environment file**
   ```bash
   cd server
   cp .env.example .env
   ```

2. **Configure environment variables**
   ```env
   # Database
   MONGODB_URI=mongodb://localhost:27017/hotslice
   
   # JWT
   JWT_SECRET=your_super_secret_jwt_key
   
   # Email Service (Gmail example)
   EMAIL_HOST=smtp.gmail.com
   EMAIL_PORT=587
   EMAIL_USER=your-email@gmail.com
   EMAIL_PASS=your-app-password
   
   # Razorpay
   RAZORPAY_KEY_ID=your_razorpay_key_id
   RAZORPAY_SECRET=your_razorpay_secret
   
   # URLs
   CLIENT_URL=http://localhost:5173
   SERVER_URL=http://localhost:5000
   ```

### Running the Application

1. **Start the backend server**
   ```bash
   cd server
   npm run dev
   ```
   Server runs on `http://localhost:5000`

2. **Start the frontend client**
   ```bash
   cd client
   npm run dev
   ```
   Client runs on `http://localhost:5173`

## 🔧 API Endpoints

### Authentication Routes (`/api/auth`)
- `POST /register` - User registration
- `POST /login` - User login
- `GET /verify-email/:token` - Email verification
- `POST /forgot-password` - Password reset request
- `POST /reset-password` - Password reset confirmation

### Menu Routes (`/api/menu`)
- `GET /items` - Get all menu items (bases, sauces, cheese, veggies)
- `GET /items/:category` - Get items by category

### Order Routes (`/api/orders`)
- `POST /` - Create new order
- `GET /user/:userId` - Get user's orders
- `GET /:orderId` - Get specific order details
- `PUT /:orderId/status` - Update order status (admin only)

### Admin Routes (`/api/admin`)
- `GET /inventory` - Get current inventory levels
- `PUT /inventory/:itemId` - Update inventory item
- `GET /orders` - Get all orders
- `GET /dashboard-stats` - Get admin dashboard statistics
- `POST /restock` - Bulk restock items

## 🗄️ Database Schema

### User Model
```javascript
{
  name: String,
  email: String (unique),
  password: String (hashed),
  role: String (enum: ['user', 'admin']),
  isVerified: Boolean,
  createdAt: Date,
  updatedAt: Date
}
```

### Order Model
```javascript
{
  userId: ObjectId (ref: User),
  items: [{
    base: ObjectId (ref: MenuItem),
    sauce: ObjectId (ref: MenuItem),
    cheese: ObjectId (ref: MenuItem),
    veggies: [ObjectId] (ref: MenuItem),
    quantity: Number,
    price: Number
  }],
  totalAmount: Number,
  status: String (enum: ['received', 'in_kitchen', 'out_for_delivery', 'delivered']),
  paymentId: String,
  deliveryAddress: Object,
  createdAt: Date,
  updatedAt: Date
}
```

### Inventory Model
```javascript
{
  menuItemId: ObjectId (ref: MenuItem),
  currentStock: Number,
  minimumThreshold: Number,
  lastRestocked: Date,
  updatedAt: Date
}
```

## 🎯 Development Workflow

### Backend Development
```bash
cd server
npm run dev          # Start with nodemon
npm run start        # Production start
npm run test         # Run tests
```

### Frontend Development
```bash
cd client
npm run dev          # Development server
npm run build        # Production build
npm run preview      # Preview production build
npm run lint         # Run ESLint
```

## 📦 Deployment

### Production Build
1. **Build the client**
   ```bash
   cd client
   npm run build
   ```

2. **Start the server**
   ```bash
   cd server
   npm start
   ```

### Environment Variables for Production
- Set `NODE_ENV=production`
- Use production MongoDB URI
- Configure production email service
- Set up production Razorpay keys

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Team

- **Backend Development** - API design, database modeling, authentication
- **Frontend Development** - React components, UI/UX, responsive design
- **DevOps** - Deployment, CI/CD, environment configuration

## 📞 Support

For support and questions, please contact:
- Email: support@hotslice.com
- GitHub Issues: [Create an issue](https://github.com/yourusername/hotslice-express/issues)

---

## 🚀 Next Steps

- [ ] Add real-time notifications with Socket.io
- [ ] Implement order tracking with GPS
- [ ] Add mobile app with React Native
- [ ] Integrate with third-party delivery services
- [ ] Add customer reviews and ratings system
- [ ] Implement loyalty program and discounts

**Happy Coding! 🍕✨**
