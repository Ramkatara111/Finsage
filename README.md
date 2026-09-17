# FinSage 💰

> A full-stack personal finance management web application for tracking monthly income and expenses, analyzing spending patterns, managing budgets, and exploring AI-powered investment guidance.

## 🌐 Live Demo

**Frontend:** https://fin-sage-rho.vercel.app/

> **Note:** The application requires the backend API and MongoDB configuration to be available for authentication, budget persistence, and AI-powered investment features.

---

## 📌 About FinSage

FinSage is a MERN-style financial management application designed to help users understand their monthly finances in one place.

Users can:

- Create an account and securely log in
- Track monthly income and expenses
- Organize expenses into different categories
- Save and update budgets month by month
- View financial summaries and spending charts
- Calculate monthly and yearly savings
- Receive spending insights based on budget data
- Get AI-generated investment recommendations
- Ask an AI financial assistant questions about investments and financial planning

The application uses a React frontend, an Express/Node.js backend, MongoDB for persistent storage, JWT-based authentication with HTTP-only cookies, and Google's Gemini API for AI-powered investment features.

---

## ✨ Features

### 🔐 Authentication

- User registration and login
- Password hashing with `bcryptjs`
- JWT-based authentication
- HTTP-only authentication cookies
- Protected routes for authenticated users
- Login persistence through authentication checks
- Logout functionality

### 📊 Budget Management

Users can create budgets for individual months and track:

| Category | Description |
|---|---|
| Monthly Income | Total monthly income |
| Housing | Rent, mortgage, utilities, etc. |
| Transportation | Car payments, fuel, public transport |
| Food & Groceries | Groceries and meals |
| Healthcare | Insurance and medical expenses |
| Entertainment | Movies, games, hobbies, etc. |
| Dining Out | Restaurants and takeout |
| Education | Courses, books and training |
| Debt Payments | Credit cards and loans |

Budgets are stored by user and month using a unique `user + monthKey` database index, allowing an existing month's budget to be updated instead of creating duplicates.

### 📈 Financial Dashboard

The dashboard provides an overview of the user's financial activity, including:

- Monthly income
- Category-wise expenses
- Total expenses
- Savings potential
- Percentage of income spent by category
- Historical monthly budget data
- Visual spending and financial charts

Charts are built using **Recharts**.

### 🧮 Budget Calculator

The budget calculator:

- Accepts income and expense information
- Groups expenses into essentials, lifestyle, investment, and debt
- Calculates total expenses
- Calculates monthly savings
- Projects yearly savings
- Generates rule-based spending insights
- Displays budget information using charts
- Supports moving between months
- Loads previously saved monthly budgets

### 🤖 AI Investment Guidance

FinSage integrates Google's Gemini API to provide:

- Low-risk investment suggestions
- Moderate-risk investment suggestions
- High-risk investment suggestions
- Expected return ranges returned by the AI
- Detailed explanations of investment options
- An AI chat interface for financial and investment questions

Investment recommendations are generated from the user's entered savings amount.

> **Important:** AI-generated financial information is for educational purposes and should not be treated as personalized financial advice or a guarantee of investment returns.

### 🎨 Modern UI

The frontend includes:

- Responsive layouts
- Tailwind CSS styling
- Framer Motion animations
- Heroicons
- Interactive cards
- Responsive charts
- Dark-themed dashboard and investment pages
- Protected navigation and authentication-aware routing

---

## 🛠️ Tech Stack

### Frontend

- **React 19**
- **Vite**
- **React Router**
- **Tailwind CSS**
- **Framer Motion**
- **Recharts**
- **Heroicons**
- **Headless UI**
- **Google Generative AI SDK**

### Backend

- **Node.js**
- **Express 5**
- **MongoDB**
- **Mongoose**
- **JWT**
- **bcryptjs**
- **Cookie Parser**
- **CORS**
- **dotenv**
- **Google Generative AI SDK**

### Deployment

The project is structured as separate frontend and backend applications and can be deployed independently.

Example deployment configuration in the project includes:

- Frontend: Vercel
- Backend: Render
- Database: MongoDB

---

## 🏗️ Project Architecture

```text
FinSage/
│
├── client/                         # React + Vite frontend
│   ├── public/
│   └── src/
│       ├── assets/
│       ├── components/
│       │   └── Navbar.jsx
│       ├── context/
│       │   ├── AuthContext.jsx
│       │   └── BudgetContext.jsx
│       ├── routes/
│       │   ├── Home.jsx
│       │   ├── Login.jsx
│       │   ├── SignUp.jsx
│       │   ├── Dashboard.jsx
│       │   ├── BudgetCalculator.jsx
│       │   └── Investments.jsx
│       ├── App.jsx
│       ├── App.css
│       └── index.css
│
├── server/                         # Node.js + Express backend
│   ├── config/
│   │   └── db.js
│   ├── controllers/
│   │   ├── auth.controller.js
│   │   └── budget.controller.js
│   ├── middleware/
│   │   └── auth.middleware.js
│   ├── models/
│   │   ├── User.model.js
│   │   └── Budget.model.js
│   ├── routes/
│   │   ├── auth.route.js
│   │   ├── budget.route.js
│   │   └── investment.route.js
│   ├── app.js
│   └── package.json
│
└── README.md
```

---

## 🔄 Application Flow

```text
                    ┌──────────────────┐
                    │   React Client   │
                    │  Vite + React    │
                    └────────┬─────────┘
                             │
                             │ REST API
                             ▼
                    ┌──────────────────┐
                    │ Express Backend  │
                    │   Node.js API    │
                    └───────┬─────┬────┘
                            │     │
                ┌───────────┘     └──────────────┐
                ▼                                ▼
       ┌─────────────────┐              ┌─────────────────┐
       │    MongoDB      │              │   Gemini API    │
       │ Users + Budgets │              │ AI Investments  │
       └─────────────────┘              └─────────────────┘
```

---

## 🔌 API Endpoints

### Authentication

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| `POST` | `/api/auth/register` | Register a new user | Public |
| `POST` | `/api/auth/login` | Log in a user | Public |
| `GET` | `/api/auth/me` | Get the currently authenticated user | Protected |
| `GET` | `/api/auth/logout` | Log out the current user | Protected |

### Budgets

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| `POST` | `/api/budgets` | Create/update a monthly budget | Protected |
| `GET` | `/api/budgets` | Get all budgets for the user | Protected |
| `GET` | `/api/budgets/:monthKey` | Get a budget for a specific month | Protected |

### Investments

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| `POST` | `/api/investments/recommendations` | Generate investment recommendations | API-based |
| `POST` | `/api/investments/chat` | Ask the AI financial assistant a question | API-based |

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/FinSage.git
cd FinSage
```

### 2. Install frontend dependencies

```bash
cd client
npm install
```

### 3. Install backend dependencies

Open another terminal:

```bash
cd server
npm install
```

---

## 🔑 Environment Variables

Create a `.env` file inside the `server` directory:

```env
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
GEMINI_API_KEY=your_gemini_api_key
NODE_ENV=development
PORT=4000
```

Create a `.env` file inside the `client` directory:

```env
VITE_API_URL=http://localhost:4000
```

For production, set `VITE_API_URL` to your deployed backend URL.

### Environment Variable Summary

| Variable | Location | Purpose |
|---|---|---|
| `MONGO_URI` | Server | MongoDB connection string |
| `JWT_SECRET` | Server | JWT signing secret |
| `GEMINI_API_KEY` | Server | Google Gemini API access |
| `NODE_ENV` | Server | Environment configuration |
| `PORT` | Server | Backend port |
| `VITE_API_URL` | Client | Backend API base URL |

> Never commit `.env` files, API keys, JWT secrets, or database credentials to GitHub.

---

## ▶️ Run Locally

### Start the backend

```bash
cd server
npm run dev
```

The backend runs on:

```text
http://localhost:4000
```

### Start the frontend

In another terminal:

```bash
cd client
npm run dev
```

Vite will provide the local frontend URL, normally:

```text
http://localhost:5173
```

---

## 🧠 How Budget Analysis Works

FinSage calculates the user's financial position from the entered monthly data.

```text
Monthly Savings
      =
Monthly Income - Total Expenses
```

The budget calculator also groups spending into:

```text
Essential
Lifestyle
Investment
Debt
```

The application then uses these values to generate visual summaries and rule-based spending insights.

---

## 🔒 Security

The current implementation includes several security-related measures:

- Passwords are hashed using `bcryptjs`
- Authentication uses JWT tokens
- Authentication cookies are configured as HTTP-only
- CORS is configured with allowed origins
- Protected API routes verify authentication
- User budgets are associated with authenticated user IDs
- MongoDB compound indexing prevents duplicate monthly budgets for the same user

> Security configuration should still be reviewed and hardened before using the application with real financial data.

---

## 📱 Main Pages

| Route | Purpose |
|---|---|
| `/` | Landing page |
| `/signup` | Create an account |
| `/login` | User login |
| `/budget` | Create and analyze monthly budgets |
| `/dashboard` | View financial dashboard and history |
| `/investments` | Explore AI-powered investment guidance |

`/budget`, `/dashboard`, and `/investments` are protected routes and require authentication.

---

## 🎯 Key Technical Highlights

This project demonstrates practical implementation of:

- Full-stack JavaScript development
- React component architecture
- React Context API for global state
- Protected routing
- REST API development with Express
- MongoDB schema design with Mongoose
- Authentication and authorization middleware
- Password hashing
- JWT authentication
- HTTP-only cookies
- CRUD-style budget management
- Monthly data persistence
- Data visualization with Recharts
- Responsive UI development with Tailwind CSS
- Animation using Framer Motion
- Generative AI integration using Gemini API
- Frontend/backend deployment configuration
- CORS and production cookie configuration

---

## 🔮 Future Improvements

Potential improvements for future versions include:

- Expense transaction-level tracking
- Recurring expenses
- Custom expense categories
- Savings goal creation and progress tracking
- Budget alerts and notifications
- Export financial reports to CSV/PDF
- More advanced financial analytics
- Improved AI prompt validation and structured responses
- Region-specific investment information
- Better investment suitability and risk profiling
- Automated financial reports
- Unit and integration testing
- Improved production error handling and observability

---

## ⚠️ Disclaimer

FinSage is a software project intended for learning, financial organization, and educational exploration.

Investment information generated by the AI system may be incomplete, inaccurate, outdated, or unsuitable for a particular individual's circumstances. Expected returns are not guaranteed.

Users should independently verify financial information and consult a qualified financial professional before making investment decisions.

---

## 👨‍💻 Author

**Ram Katara**

Electronics & Communication Engineering (VLSI)  
Maharaja Agrasen Institute of Technology, New Delhi

### Connect

- GitHub: [Ramkatara111](https://github.com/Ramkatara111)
- LinkedIn: [Ram Katara](https://www.linkedin.com/)

---

