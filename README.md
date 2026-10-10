# Terra Nova

Terra Nova is an NGO management and donation platform that connects NGOs, donors, volunteers, and administrators in one place.

The platform supports transparent campaigns, secure donations, volunteer coordination, NGO verification, and administrative oversight.

## Links

- Live application: [terra-nova-ngo.netlify.app](https://terra-nova-ngo.netlify.app)
- Backend API: [terra-nova-backend.onrender.com](https://terra-nova-backend.onrender.com)
- Repository: [github.com/Purva9322376122/terra-nova](https://github.com/Purva9322376122/terra-nova)

## Main features

- Public campaign browsing and impact information
- One-time, monthly, and annual donations through Razorpay
- Donor accounts, donation history, receipts, and campaign wishlists
- Volunteer registration, hour logging, dashboards, and certificates
- NGO registration, Darpan ID validation, approval, and campaign management
- Campaign image uploads and donation tracking for NGOs
- Admin dashboard for NGOs, donations, volunteers, subscribers, and analytics
- OTP verification, password reset, email notifications, and role-based JWT authentication
- Responsive frontend for desktop and mobile screens

## Technology stack

### Frontend

- HTML5, CSS3, and vanilla JavaScript
- Chart.js for dashboard analytics
- Razorpay Checkout for donation payments

### Backend

- Node.js and Express
- MongoDB with Mongoose
- JWT and bcryptjs for authentication
- Nodemailer for transactional email
- Multer for campaign image uploads
- express-rate-limit and CORS middleware

### Hosting and services

- Netlify for the frontend
- Render for the backend
- MongoDB Atlas for the database
- Brevo SMTP for email delivery
- Razorpay for payment processing

## Project structure

```text
Project/
├── Frontend/       # Public pages, dashboards, styles, and browser scripts
├── ngo-backend/    # Express server, routes, models, authentication, and services
└── README.md
```

## Local setup

### Prerequisites

- Node.js 18 or later
- A MongoDB database, such as MongoDB Atlas
- Razorpay test credentials for payment testing
- SMTP credentials if email features are needed locally

### Installation

```bash
git clone https://github.com/Purva9322376122/terra-nova.git
cd terra-nova/ngo-backend
npm install
```

Create `ngo-backend/.env` using the variable names below, then initialize any required seed data:

```bash
node createAdmin.js
node seedApprovedNgos.js
```

Start the backend in development mode:

```bash
npm run dev
```

Serve the `Frontend/` directory with a local static server, such as VS Code Live Server. Make sure the frontend API configuration points to the local backend URL.

## API overview

The backend exposes REST endpoints for:

- Donor and volunteer registration, OTP verification, login, profiles, and password reset
- NGO registration, approval, profiles, campaigns, and donations
- Admin management of NGOs, donations, volunteers, subscribers, and approved Darpan IDs
- Public campaigns, donations, payment order creation and verification, subscriptions, and volunteer applications

The API base URL is configured through the frontend configuration and the `BACKEND_URL` environment variable.

## Deployment

### Frontend

Deploy the `Frontend/` directory to Netlify or another static hosting provider.

### Backend

Deploy `ngo-backend/` to Render or another Node.js hosting provider. Configure the start command as:

```bash
node server.js
```

Add all required environment variables through the hosting provider's secret configuration. Do not upload the `.env` file.

### Database and storage

Use MongoDB Atlas or another managed MongoDB service in production. The current backend stores uploaded campaign images on local disk; a persistent object-storage service such as S3 or Cloudinary is recommended for production deployments.

## Security notes

- Passwords are hashed before storage.
- JWT authentication protects role-specific routes.
- OTP and password-reset tokens expire.
- Payment signatures are verified on the backend.
- Rate limiting and input validation are enabled for sensitive routes.
- Uploaded files are restricted to supported image types and sizes.
- Production deployments must use strong secrets, HTTPS, restricted CORS, and a correctly configured host policy.

## Known limitations

- Razorpay is currently configured for test-mode payments.
- Render free-tier cold starts may delay the first request after inactivity.
- Local campaign-image storage is ephemeral on some hosting providers.
- Email delivery does not currently include a durable retry queue.

## Future improvements

- Move campaign images to durable object storage.
- Add queued and retryable email delivery.
- Add multilingual support and a mobile application.
- Add richer analytics and automated tax-certificate generation.

## License

No license has been specified for this repository yet.
