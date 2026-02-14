# E-Voting System

A full-stack web application for secure, transparent electronic voting with email verification and admin management. Built with Node.js, Express, and MongoDB.

## 🎯 Features

- **User Authentication**: Voter registration and login with email verification via OTP
- **Email Verification**: Secure OTP delivery using Gmail SMTP or OAuth2
- **Admin Dashboard**: Manage candidates, view voting statistics, and monitor voting participation
- **Voter Dashboard**: View candidates, cast votes, and track voting status
- **Vote Security**: One-time voting per voter with blockchain-ready architecture
- **Session Management**: Secure session handling with flash messages for user feedback
- **Responsive Design**: EJS templating with Bootstrap/CSS styling
- **Password Security**: Bcrypt hashing for secure password storage

## 🛠 Tech Stack

- **Backend**: Node.js, Express.js
- **Database**: MongoDB with Mongoose ODM
- **Frontend**: EJS templating, HTML5, CSS3
- **Authentication**: Sessions, Email OTP verification
- **Email Service**: Nodemailer (Gmail SMTP/OAuth2)
- **Password Hashing**: Bcryptjs
- **Development**: Nodemon for auto-reload

## 📋 Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- MongoDB (local or cloud instance)
- Gmail account (for email configuration)

## 📦 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/e-voting-system.git
   cd e-voting-system
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Setup**
   - Copy `.env.example` to `.env`
   - Configure the following variables:
   ```env
   MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/e-voting
   PORT=3000
   SESSION_SECRET=your_secret_key
   EMAIL_HOST=smtp.gmail.com
   EMAIL_PORT=465
   EMAIL_SECURE=true
   EMAIL_USER=your.email@gmail.com
   EMAIL_PASS=your_app_password
   NODE_ENV=development
   ```

4. **Database Initialization**
   ```bash
   node seed.js
   ```

5. **Start the server**
   ```bash
   npm start
   ```
   The app will run on `http://localhost:3000`

## 🚀 Usage

### Development Mode
```bash
npm run dev
```
Runs with auto-reload using Nodemon.

### Testing Email
```bash
npm run test-email
```
Verifies email configuration and sends a test OTP.

### Seeding Database
```bash
npm run seed
```
Initializes database with sample candidates and admin data.

## 📄 Project Structure

```
├── app.js                 # Main application entry point
├── config/
│   ├── database.js       # MongoDB connection
│   └── mailer.js         # Email configuration
├── controllers/
│   ├── auth.controller.js      # Authentication logic
│   ├── admin.controller.js      # Admin operations
│   └── voter.controller.js      # Voter operations
├── middleware/
│   └── auth.middleware.js       # Authentication guards
├── models/
│   ├── voter.model.js          # Voter schema
│   ├── candidate.model.js       # Candidate schema
│   └── admin.model.js           # Admin schema
├── routes/
│   ├── auth.routes.js          # Auth endpoints
│   ├── admin.routes.js         # Admin endpoints
│   └── voter.routes.js         # Voter endpoints
├── views/
│   ├── pages/                  # Page templates
│   │   ├── landing.ejs
│   │   ├── login.ejs
│   │   ├── register.ejs
│   │   ├── verify-email.ejs
│   │   ├── admin/dashboard.ejs
│   │   └── voter/dashboard.ejs
│   └── partials/               # Reusable components
│       ├── header.ejs
│       ├── navbar.ejs
│       └── footer.ejs
├── public/
│   └── css/                    # Stylesheets
└── scripts/
    ├── test-email.js           # Email testing utility
    └── test-otp.js             # OTP testing utility
```

## 🗄️ Database Schema

### Voter Model
- Voter ID (unique)
- Email (unique, verified)
- Password (bcrypt hashed)
- Role (voter/admin)
- Has Voted (boolean)
- Email OTP verification status

### Candidate Model
- Name
- Party affiliation
- Vote count
- Timestamps (created/updated)

### Admin Model
- Administrator credentials and permissions

## 🔐 Email Configuration

Two methods are supported:

### Option A: Gmail App Password (Recommended)
See `EMAIL_SETUP.md` for step-by-step instructions. Requires 2-step verification enabled on your Gmail account.

### Option B: Gmail OAuth2
More secure. Requires Google Cloud Project setup with OAuth 2.0 credentials.

For detailed setup instructions, refer to [EMAIL_SETUP.md](./EMAIL_SETUP.md).

## 🔑 Key Routes

### Authentication
- `GET /` - Landing page
- `POST /register` - User registration
- `POST /verify-email` - Email OTP verification
- `POST /login` - User login
- `GET /logout` - Logout

### Voter Dashboard
- `GET /voter/dashboard` - View candidates and voting interface
- `POST /voter/vote` - Cast vote for a candidate
- `GET /voter/voted` - Confirmation after voting

### Admin Dashboard
- `GET /admin/dashboard` - View voting statistics
- `POST /admin/add-candidate` - Add new candidate
- `GET /admin/results` - View voting results

## 🧪 Testing

- **Email Testing**: `npm run test-email`
- **OTP Testing**: `node scripts/test-otp.js`
- Register a test voter and verify email OTP delivery

## 🔒 Security Features

- ✅ Password hashing with Bcryptjs
- ✅ Email verification with OTP
- ✅ Session-based authentication
- ✅ Admin role-based access control
- ✅ One-time voting mechanism
- ✅ Environment variables for sensitive data

## ⚙️ Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `MONGODB_URI` | MongoDB connection string | Yes |
| `PORT` | Server port (default: 3000) | No |
| `SESSION_SECRET` | Secret for session encryption | Yes |
| `EMAIL_HOST` | SMTP host (gmail: smtp.gmail.com) | Yes |
| `EMAIL_PORT` | SMTP port (gmail: 465) | Yes |
| `EMAIL_SECURE` | Use TLS (true for gmail) | Yes |
| `EMAIL_USER` | Gmail address | Yes |
| `EMAIL_PASS` | Gmail app password or OAuth token | Yes |
| `NODE_ENV` | Environment (development/production) | No |

## 📝 License

ISC License - See LICENSE file for details

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📞 Support

For issues or questions, please open an [GitHub Issue](https://github.com/yourusername/e-voting-system/issues).

## 📚 Additional Resources

- [EMAIL_SETUP.md](./EMAIL_SETUP.md) - Detailed email configuration guide
- [Express Documentation](https://expressjs.com/)
- [MongoDB Documentation](https://docs.mongodb.com/)
- [EJS Documentation](https://ejs.co/)

---
