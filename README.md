# Hi Secure Solutions - E-commerce + ERP Web Application

A complete Smart E-commerce + ERP Web Application for "Hi Secure Solutions", a business engaged in Electronics & Security Systems, LED TVs, and Electronic Gadgets.

## 🚀 Features

### Core Features
- **Product Management**: Full CRUD operations with auto-image fetching from Unsplash/Pexels/Pixabay
- **Catalog & Search**: Category-wise navigation, live search, filters, and sorting
- **User Roles**: Admin, Customer, Supplier, and Service Staff dashboards
- **Shopping Cart**: Cart management with coupon application
- **Checkout & Payments**: Multiple payment methods (Cash, Card, UPI, QR Scan, Wallet)
- **Invoice Generation**: Multi-format printing (A4, A5, POS rolls, labels)
- **QR Code Integration**: Dynamic QR codes for payments and invoices
- **ERP Module**: Inventory, purchase orders, supplier management
- **Cloud Integration**: Firebase Storage for images and invoices
- **WhatsApp & Email**: Automated notifications and business enquiries
- **Reports & Analytics**: Sales, inventory, and expense reports with Excel/CSV export
- **Bulk Import/Export**: Excel/CSV support for products

## 🛠️ Tech Stack

### Frontend
- React.js 18
- TypeScript
- Tailwind CSS
- React Router
- Axios
- jsPDF (for invoice generation)
- QRCode.react (for QR codes)
- React Hot Toast (notifications)

### Backend
- Node.js
- Express.js
- TypeScript
- MongoDB (via Mongoose)
- Firebase Admin SDK (for storage)
- Razorpay (payments)
- Nodemailer (email)
- Multer (file uploads)
- XLSX (Excel handling)
- QRCode (QR generation)

## 📦 Installation

### Prerequisites
- Node.js >= 18.0.0
- MongoDB (local or MongoDB Atlas)
- Firebase project (for storage)
- Razorpay account (for payments)
- Email account (for notifications)

### Setup Steps

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd "Billing Website"
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**

   Create `.env` file in `apps/server/`:
   ```env
   # Database
   MONGODB_URI=mongodb://localhost:27017/hi-secure
   # Or use MongoDB Atlas: mongodb+srv://user:pass@cluster.mongodb.net/hi-secure

   # JWT
   JWT_SECRET=your-super-secret-jwt-key-change-in-production
   JWT_REFRESH_SECRET=your-refresh-secret-key
   JWT_EXPIRES=15m
   JWT_REFRESH_EXPIRES=7d

   # Web URL
   WEB_URL=http://localhost:5173

   # Razorpay
   RAZORPAY_KEY_ID=your-razorpay-key-id
   RAZORPAY_KEY_SECRET=your-razorpay-key-secret

   # Email (Gmail example)
   EMAIL_HOST=smtp.gmail.com
   EMAIL_PORT=587
   EMAIL_USER=your-email@gmail.com
   EMAIL_PASS=your-app-password
   BUSINESS_EMAIL=smssiddiq2011@gmail.com

   # Firebase (for storage)
   FIREBASE_PROJECT_ID=your-firebase-project-id
   FIREBASE_CLIENT_EMAIL=your-firebase-client-email
   FIREBASE_PRIVATE_KEY=your-firebase-private-key

   # Image APIs (optional)
   UNSPLASH_ACCESS_KEY=your-unsplash-access-key
   PEXELS_API_KEY=your-pexels-api-key

   # WhatsApp (optional)
   WA_ACCESS_TOKEN=your-whatsapp-access-token
   WA_PHONE_NUMBER_ID=your-whatsapp-phone-number-id
   WA_VERIFY_TOKEN=your-verify-token
   ```

   Create `.env` file in `apps/web/`:
   ```env
   VITE_API_URL=http://localhost:4000/api
   ```

4. **Start the development servers**
   ```bash
   npm run dev
   ```

   This will start:
   - Backend server on `http://localhost:4000`
   - Frontend dev server on `http://localhost:5173`

## 📁 Project Structure

```
.
├── apps/
│   ├── server/          # Backend (Node.js + Express)
│   │   ├── src/
│   │   │   ├── integrations/  # Firebase, Email, WhatsApp, Razorpay
│   │   │   ├── middleware/    # Auth middleware
│   │   │   ├── modules/       # Feature modules
│   │   │   │   ├── admin/
│   │   │   │   ├── auth/
│   │   │   │   ├── cart/
│   │   │   │   ├── coupons/
│   │   │   │   ├── inventory/
│   │   │   │   ├── invoices/
│   │   │   │   ├── orders/
│   │   │   │   ├── payments/
│   │   │   │   ├── products/
│   │   │   │   ├── service/
│   │   │   │   ├── suppliers/
│   │   │   │   └── users/
│   │   │   └── routes.ts
│   │   └── package.json
│   └── web/             # Frontend (React)
│       ├── src/
│       │   ├── components/    # Reusable components
│       │   ├── contexts/      # React contexts (Auth)
│       │   ├── hooks/         # Custom hooks
│       │   ├── pages/         # Page components
│       │   ├── api.ts         # API client
│       │   └── App.tsx
│       └── package.json
└── package.json
```

## 🔐 User Roles

- **Admin**: Full access to all features, reports, and settings
- **Customer**: Browse products, place orders, view invoices
- **Supplier**: Manage stock supply, purchase orders
- **Service Staff**: Manage service jobs, installations, repairs

## 📧 Email Configuration

All business enquiries are automatically sent to: **smssiddiddiq2011@gmail.com**

To configure email:
1. For Gmail, enable 2-factor authentication
2. Generate an App Password
3. Use the App Password in `EMAIL_PASS`

## 💳 Payment Integration

### Razorpay Setup
1. Create a Razorpay account
2. Get your Key ID and Key Secret from dashboard
3. Add them to `.env` file

### UPI QR Codes
QR codes are automatically generated for each invoice. Configure your UPI ID in the environment variables.

## 📦 Product Image Fetching

The system automatically fetches product images from:
1. Unsplash (requires API key)
2. Pexels (requires API key)
3. Pixabay (free tier available)

If images don't match, you can manually upload images via the admin panel.

## 🖨️ Invoice Printing

Invoices can be printed in multiple formats:
- **A4**: Standard invoice format
- **A5**: Compact format
- **POS**: Thermal printer format
- **Labels**: Product labels and warranty stickers

## 📊 Reports & Analytics

Admin dashboard provides:
- Sales reports (daily, monthly, yearly)
- Inventory reports
- Expense tracking
- Export to Excel/CSV
- Low stock alerts

## 🔄 Bulk Operations

### Import Products
1. Prepare Excel file with columns: Name, Brand, Model, Category, Price, Stock, Description, Warranty
2. Go to Admin → Products → Bulk Import
3. Upload the file

### Export Products
1. Go to Admin → Products → Bulk Export
2. Download the Excel file

## 🚀 Deployment

### Backend Deployment
1. Build the backend:
   ```bash
   npm run -w apps/server build
   ```
2. Set environment variables on your hosting platform
3. Start the server:
   ```bash
   npm run -w apps/server start
   ```

### Frontend Deployment
1. Build the frontend:
   ```bash
   npm run -w apps/web build
   ```
2. Deploy the `dist` folder to your hosting platform (Netlify, Vercel, etc.)

## 📝 API Documentation

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user

### Products
- `GET /api/products` - List products (with filters)
- `GET /api/products/:id` - Get product details
- `POST /api/products` - Create product (Admin/Staff)
- `PUT /api/products/:id` - Update product (Admin/Staff)
- `DELETE /api/products/:id` - Delete product (Admin)
- `POST /api/products/:id/fetch-images` - Auto-fetch images
- `POST /api/products/bulk/import` - Bulk import
- `GET /api/products/bulk/export` - Bulk export

### Cart
- `GET /api/cart` - Get user cart
- `POST /api/cart/add` - Add item to cart
- `PUT /api/cart/update` - Update cart item
- `DELETE /api/cart/remove/:productId` - Remove item
- `POST /api/cart/apply-coupon` - Apply coupon

### Orders
- `GET /api/orders` - List orders
- `GET /api/orders/:id` - Get order details
- `POST /api/orders` - Create order
- `PUT /api/orders/:id/status` - Update order status (Admin/Staff)

### Invoices
- `GET /api/invoices` - List invoices
- `GET /api/invoices/:id` - Get invoice details
- `POST /api/invoices/generate` - Generate invoice

### Payments
- `POST /api/payments/razorpay/order` - Create Razorpay order
- `GET /api/payments/upi/qr` - Get UPI QR code

### Admin
- `GET /api/admin/dashboard` - Dashboard stats
- `GET /api/admin/reports/sales` - Sales report
- `GET /api/admin/reports/inventory` - Inventory report
- `GET /api/admin/reports/expenses` - Expenses report
- `GET /api/admin/analytics` - Analytics data

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## 📄 License

This project is proprietary software for Hi Secure Solutions.

## 📞 Support

For support, email smssiddiq2011@gmail.com

---

Built with ❤️ for Hi Secure Solutions

