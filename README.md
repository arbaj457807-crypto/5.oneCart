# OneCart

OneCart is a full-stack e-commerce application with a customer storefront, an admin dashboard, and an Express/MongoDB backend. It supports user authentication, Google login, product management, cart handling, order placement, Razorpay payments, and admin order status management.

## Features

- Customer registration, login, logout, and Google OAuth login
- Protected customer pages for home, collections, products, cart, checkout, and orders
- Product catalogue with category, subcategory, size, bestseller, and image support
- Cart add, update, and fetch functionality
- Cash on delivery and Razorpay checkout flows
- Admin login with product add/list/remove controls
- Admin order listing and order status updates
- Cloudinary image upload for product images
- MongoDB data storage with Mongoose models

## Tech Stack

| Layer | Technology |
| --- | --- |
| Frontend | React 19, Vite, React Router, Tailwind CSS, Axios, Firebase Auth |
| Admin | React 19, Vite, React Router, Tailwind CSS, Axios |
| Backend | Node.js, Express, MongoDB, Mongoose, JWT, Cookie Parser |
| Services | Cloudinary, Razorpay, Firebase |

## Project Structure

```text
.
|-- admin/       # Admin dashboard
|-- backend/     # Express API server
`-- frontend/    # Customer-facing storefront
```

## Prerequisites

Install the following before running the project:

- Node.js 18 or later
- npm
- MongoDB database URL
- Cloudinary account
- Razorpay account
- Firebase project for Google authentication

## Environment Variables

Create a `.env` file inside `backend/`:

```env
PORT=8000
MONGODB_URL=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret

ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=your_admin_password

CLOUDINARY_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret

RAZORPAY_KEY_ID=your_razorpay_key_id
RAZORPAY_KEY_SECRET=your_razorpay_key_secret
```

Create a `.env` file inside `frontend/`:

```env
VITE_FIREBASE_APIKEY=your_firebase_api_key
VITE_RAZORPAY_KEY_ID=your_razorpay_key_id
```

The frontend and admin currently point to `http://localhost:8000` in their `AuthContext.jsx` files, so run the backend on port `8000` or update those URLs.

## Installation

Install dependencies for each app separately:

```bash
cd backend
npm install

cd ../frontend
npm install

cd ../admin
npm install
```

## Running Locally

Start the backend:

```bash
cd backend
npm run dev
```

Start the customer frontend:

```bash
cd frontend
npm run dev
```

Start the admin dashboard:

```bash
cd admin
npm run dev
```

Default local URLs:

| App | URL |
| --- | --- |
| Backend API | `http://localhost:8000` |
| Frontend | `http://localhost:5173` |
| Admin | `http://localhost:5174` |

## Available Scripts

### Backend

```bash
npm run dev
```

Runs the Express server using Nodemon.

### Frontend and Admin

```bash
npm run dev
npm run build
npm run lint
npm run preview
```

## API Overview

| Module | Base Route | Purpose |
| --- | --- | --- |
| Auth | `/api/auth` | User registration, login, logout, Google login, admin login |
| User | `/api/user` | Current user/admin lookup |
| Product | `/api/product` | Add, list, and remove products |
| Cart | `/api/cart` | Add, update, and fetch cart items |
| Order | `/api/order` | Place orders, Razorpay checkout, payment verification, order listing, status updates |

## Notes

- Product creation expects four image files: `image1`, `image2`, `image3`, and `image4`.
- Admin authentication is based on the `ADMIN_EMAIL` and `ADMIN_PASSWORD` values in the backend `.env` file.
- Cookies are used for authentication, so API requests are made with credentials enabled.
- For production deployment, update CORS origins, cookie security settings, and frontend/admin API base URLs.
