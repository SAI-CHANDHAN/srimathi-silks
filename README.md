
# Srimathi Silks

![React](https://img.shields.io/badge/React-19-61DAFB?logo=react) ![Vite](https://img.shields.io/badge/Vite-8-646CFF?logo=vite) ![Firebase](https://img.shields.io/badge/Firebase-Firestore%20%2B%20Auth-FFCA28?logo=firebase) ![Razorpay](https://img.shields.io/badge/Payments-Razorpay-0052CC?logo=razorpay) ![License](https://img.shields.io/badge/License-Not%20Specified-red) ![Last Commit](https://img.shields.io/github/last-commit/SAI-CHANDHAN/srimathi-silks2?logo=github) ![Deploy](https://img.shields.io/badge/Deploy-Vercel-black?logo=vercel)

> Live Demo: https://srimathisilks.vercel.app/

## Short Project Description

Srimathi Silks is a modern e-commerce and catalog experience for a premium saree boutique. The application combines a polished storefront, product discovery tools, WhatsApp-based enquiry flow, Firebase-backed admin controls, and serverless media and payment integrations to help the business manage inventory and orders efficiently.

## Table of Contents

- [Features](#features-)
- [Screenshots](#screenshots-)
- [Tech Stack](#tech-stack-)
- [Project Architecture](#project-architecture-)
- [Folder Structure](#folder-structure-)
- [Installation](#installation-)
- [Environment Variables](#environment-variables-)
- [Running Locally](#running-locally-)
- [Build for Production](#build-for-production-)
- [Deployment Instructions](#deployment-instructions-)
- [API Endpoints](#api-endpoints-)
- [Authentication Flow](#authentication-flow-)
- [Database Schema Overview](#database-schema-overview-)
- [Admin Features](#admin-features-)
- [User Features](#user-features-)
- [Performance Optimizations](#performance-optimizations-)
- [Security Features](#security-features-)
- [Future Enhancements](#future-enhancements-)
- [Known Limitations](#known-limitations-)
- [Contributing Guidelines](#contributing-guidelines-)
- [License](#license-)
- [Author](#author-)

## Features ✨

- 🛍️ Elegant product catalog with category, fabric, and price-based filtering
- 📱 WhatsApp-driven enquiry flow for quick customer conversion
- 🧑‍💼 Secure admin dashboard to create, edit, and delete products
- 📦 Order management with payment and fulfillment status tracking
- 🖼️ Image uploads and proxying through Telegram-backed serverless endpoints
- 💳 Razorpay order creation for online payment workflows
- 🔍 Product detail pages with gallery-style browsing and size-chart support
- 📱 Responsive UI designed for mobile and desktop experiences
- ⚡ Performance-conscious rendering with lazy loading and skeleton states

## Screenshots 📸

> Screenshots will be added here as the app evolves.

![Home Page Placeholder](https://github.com/user-attachments/assets/1794bb46-c44f-4be6-b10f-c63813ab7a76)

![Products Page Placeholder](https://srimathisilks.vercel.app/products)

![Admin Dashboard Placeholder](https://srimathisilks.vercel.app/admin)

## Tech Stack 🛠️

| Layer | Technologies |
| --- | --- |
| Frontend | React 19, Vite, React Router, Tailwind CSS, Framer Motion, Lucide Icons |
| State & Data | Firebase Authentication, Firestore, React hooks |
| Backend/API | Node.js serverless functions on Vercel, Zod validation, rate limiting |
| Media | Telegram Bot API, Sharp, Multer |
| Payments | Razorpay SDK |
| Tooling | ESLint, PostCSS, Autoprefixer |

### Major Dependencies

- React, React DOM, React Router DOM
- Firebase, Firebase Admin
- Axios
- Razorpay
- Zod
- Framer Motion
- Lucide React
- Multer
- Sharp
- Form Data
- CLSX

## Project Architecture 🧱

The application follows a modular architecture:

1. The React/Vite frontend serves the storefront and admin dashboard.
2. Firebase handles authentication and Firestore persistence for products and orders.
3. Vercel serverless API routes manage image uploads, admin verification, Razorpay order creation, and Telegram-backed media proxying.
4. Admin actions are protected by Firebase ID tokens verified by the server.
5. Customer enquiries are stored as orders and routed to WhatsApp through the storefront flow.

```text
User Browser
  └─ React + Vite frontend
       ├─ Firebase Auth + Firestore
       ├─ WhatsApp enquiry flow
       └─ Vercel serverless APIs
            ├─ Telegram image upload/proxy
            ├─ Razorpay order creation
            └─ Admin verification + rate limiting
```

## Folder Structure 🌳

```text
srimathi-silks2/
├── api/
│   ├── _lib/
│   ├── image/
│   ├── razorpay/
│   ├── delete-telegram-media.js
│   └── upload-image.js
├── public/
├── scripts/
├── server/
│   ├── firebaseAdmin.js
│   ├── http.js
│   ├── rateLimit.js
│   ├── validation.js
│   └── verifyAdmin.js
├── src/
│   ├── assets/
│   ├── components/
│   ├── config/
│   ├── context/
│   ├── hooks/
│   ├── pages/
│   ├── scripts/
│   ├── services/
│   └── utils/
├── package.json
├── vercel.json
└── vite.config.js
```

## Installation ⚙️

```bash
git clone https://github.com/SAI-CHANDHAN/srimathi-silks2.git
cd srimathi-silks2
npm install
```

## Environment Variables 🌐

Create a `.env` file in the project root for local development and add the required values below.

| Variable | Required | Description |
| --- | --- | --- |
| `VITE_FIREBASE_API_KEY` | Yes | Firebase client API key |
| `VITE_FIREBASE_AUTH_DOMAIN` | Yes | Firebase auth domain |
| `VITE_FIREBASE_PROJECT_ID` | Yes | Firebase project ID |
| `VITE_FIREBASE_STORAGE_BUCKET` | Yes | Firebase storage bucket |
| `VITE_FIREBASE_MESSAGING_SENDER_ID` | Yes | Firebase messaging sender ID |
| `VITE_FIREBASE_APP_ID` | Yes | Firebase app ID |
| `VITE_ADMIN_EMAILS` | Yes | Comma-separated admin emails allowed to access the dashboard |
| `VITE_IMAGE_UPLOAD_ENDPOINT` | Optional | Override for image upload API endpoint |
| `VITE_API_BASE_URL` | Optional | Base URL used for image proxying |
| `VITE_RAZORPAY_CREATE_ORDER_URL` | Optional | Override for Razorpay order creation endpoint |
| `RAZORPAY_KEY_ID` | Yes for payments | Razorpay key ID |
| `RAZORPAY_KEY_SECRET` | Yes for payments | Razorpay secret |
| `TELEGRAM_BOT_TOKEN` | Yes for media uploads | Telegram bot token used for image uploads and proxying |
| `TELEGRAM_CHANNEL_ID` | Yes for media uploads | Telegram channel or chat ID |
| `ADMIN_EMAILS` | Yes on server | Server-side list of authorized admin emails |
| `FIREBASE_SERVICE_ACCOUNT_JSON` | Alternative | Full Firebase Admin service account JSON |
| `FIREBASE_CLIENT_EMAIL` | Alternative | Firebase admin client email |
| `FIREBASE_PRIVATE_KEY` | Alternative | Firebase admin private key |
| `FIREBASE_PROJECT_ID` | Alternative | Firebase admin project ID |

<details>
<summary>Example environment file</summary>

```env
VITE_FIREBASE_API_KEY=your_key
VITE_FIREBASE_AUTH_DOMAIN=your-project.firebaseapp.com
VITE_FIREBASE_PROJECT_ID=your-project
VITE_FIREBASE_STORAGE_BUCKET=your-project.firebasestorage.app
VITE_FIREBASE_MESSAGING_SENDER_ID=123456789
VITE_FIREBASE_APP_ID=1:123456789:web:abc123
VITE_ADMIN_EMAILS=admin@example.com
RAZORPAY_KEY_ID=rzp_test_xxx
RAZORPAY_KEY_SECRET=xxx
TELEGRAM_BOT_TOKEN=xxx
TELEGRAM_CHANNEL_ID=xxx
ADMIN_EMAILS=admin@example.com
```

</details>

## Running Locally ▶️

```bash
npm run dev
```

Then open http://localhost:5173.

## Build for Production 🏗️

```bash
npm run build
```

The production build output is generated in the `dist/` directory.

## Deployment Instructions 🚀

This project is configured for Vercel deployment via `vercel.json` and serverless API routes under `api/`.

1. Create a new Vercel project and connect this repository.
2. Set all required environment variables in the Vercel dashboard.
3. Deploy the project.
4. Ensure your Firebase and Telegram credentials are available in the production environment.

```bash
vercel --prod
```

## API Endpoints 🔌

| Method | Endpoint | Purpose |
| --- | --- | --- |
| `POST` | `/api/upload-image` | Upload an image to Telegram and return proxyable metadata |
| `POST` | `/api/delete-telegram-media` | Delete previously uploaded Telegram media |
| `POST` | `/api/razorpay/create-order` | Create a Razorpay order |
| `GET` | `/api/image/[...path]` | Proxy Telegram media for browser-safe delivery |

## Authentication Flow 🔐

- Admins sign in with Firebase Authentication using their email and password.
- The client stores the Firebase ID token and sends it with privileged requests.
- The server verifies the token using Firebase Admin SDK.
- Only users whose email appears in the configured admin allow-list can access the admin dashboard and upload endpoints.

## Database Schema Overview 🗄️

The project uses Firestore collections for content and orders.

| Collection | Fields |
| --- | --- |
| `products` | `id`, `name`, `price`, `category`, `fabric`, `description`, `images`, `sizeLength`, `sizeChartText`, `sizeChartImage`, `inStock`, `createdAt` |
| `orders` | `id`, `productName`, `price`, `image`, `selectedSize`, `customer`, `paymentMethod`, `paymentStatus`, `orderStatus`, `createdAt`, `razorpayPaymentId` |

## Admin Features 🧑‍💼

- Add, edit, and remove products
- Upload product images and size charts
- Manage stock availability
- View and update order status
- Filter and bulk-manage orders
- Remove outdated media from Telegram-backed storage

## User Features 👩‍💼

- Browse curated saree collections
- Filter by category, fabric, size, and price
- View detailed product pages
- Enquire on WhatsApp with pre-filled customer details
- See product availability and new-arrival badges

## Performance Optimizations ⚡

- Lazy-loaded images and product cards
- Skeleton loading states for smoother perception of load times
- Product caching in the frontend service layer
- Optimized image upload using Sharp before media transfer
- Telegram image proxy with cache-friendly headers

## Security Features 🔒

- Firebase-based admin authentication
- Server-side ID token verification
- Rate limiting for upload, delete, and payment endpoints
- Security headers and CSP for API responses
- Input validation using Zod for API payloads
- Admin-only access to image upload and delete endpoints

## Future Enhancements 🚧

- Full checkout flow with payment confirmation and receipt generation
- Customer account and saved address management
- Search indexing and analytics dashboards
- Multi-language and multi-currency support
- Inventory sync and export/import tools

## Known Limitations ⚠️

- The project currently relies on Telegram as the media storage backend for uploaded images.
- The backend rate limiting is in-memory and is suitable for small deployments.
- No dedicated test suite is currently included.
- The README uses placeholders for screenshots and live demo URL until production assets are published.

## Contributing Guidelines 🤝

Contributions are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Make your changes and test locally.
4. Open a pull request with a clear description.

```bash
npm run lint
npm run build
```

## License 📄

No license has been specified for this repository yet. Please contact the maintainer before reusing or redistributing the codebase.

## Author 👤

- Name: Sai Chandhan Reddy Annapureddy
- GitHub: https://github.com/SAI-CHANDHAN
- Portfolio: https://saichandhan.online/
- LinkedIn: https://www.linkedin.com/in/saichandhanannapureddy/

---

Built with care for a premium saree shopping experience.
