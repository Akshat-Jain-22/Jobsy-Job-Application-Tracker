# Jobsy — Job Application Tracker

Jobsy is a full-stack job application tracking web app built with the MERN stack. It helps job seekers keep their applications organized, track each application's status, and stay aware of important deadlines from one dashboard.

## Features

- **User authentication:** Register and log in to a personal account.
- **Private dashboard:** View job applications associated with your account.
- **Application management:** Add, update, search, and delete job applications.
- **Status tracking:** Track applications as `Pending`, `Shortlisted`, or `Rejected`.
- **Deadline validation:** Ensure the deadline is after the application date and is not in the past.
- **Search:** Filter applications by company or position.
- **Progress overview:** View total applications and status counts.
- **Responsive interface:** React-based interface with animated UI elements and toast notifications.
- **Protected routes:** Keep the dashboard available only to authenticated users.

> Note: The repository includes an announcements/reminders page and feature-page descriptions. Automated reminder delivery and analytics charts should not be considered implemented unless you add those behaviours.

## Tech Stack

### Frontend
- React
- Vite
- React Router
- Tailwind CSS
- Axios
- Framer Motion
- React Toastify

### Backend
- Node.js
- Express.js
- MongoDB
- Mongoose
- JSON Web Tokens (JWT)
- bcryptjs
- cookie-parser
- CORS

## Project Structure

```text
abcd/
├── backend/
│   ├── config/          # MongoDB connection
│   ├── controllers/     # Authentication and application logic
│   ├── middleware/      # Authentication middleware
│   ├── models/          # User and application schemas
│   ├── routes/          # API routes
│   ├── index.js         # Express entry point
│   └── package.json
└── frontend/
    ├── public/
    ├── src/
    │   ├── api/         # Application API calls
    │   ├── components/  # Reusable UI components
    │   ├── context/     # Authentication context
    │   ├── handlers/    # UI action handlers
    │   ├── pages/       # Application pages
    │   ├── routes/      # Protected routes
    │   └── utils/       # Axios and helper utilities
    └── package.json
```

## Getting Started

### Prerequisites

Install the following before running the project:

- Node.js (LTS recommended)
- npm
- MongoDB database (local MongoDB or MongoDB Atlas)
- Git (optional)

### 1. Clone the repository

```bash
git clone https://github.com/Akshat-Jain-22/abcd.git
cd abcd
```

### 2. Configure the backend

```bash
cd backend
npm install
```

Create a `.env` file inside the `backend/` directory:

```env
PORT=5000
MONGODB_URI=mongodb://127.0.0.1:27017/jobsy
JWT_SECRET=replace_with_a_long_random_secret
```

For MongoDB Atlas, replace `MONGODB_URI` with your Atlas connection string. Keep `.env` private and never commit real credentials or secrets.

Start the backend:

```bash
npm start
```

The API should be available at `http://localhost:5000`.

### 3. Configure the frontend

Open a second terminal:

```bash
cd frontend
npm install
```

Create a `.env` file inside `frontend/`:

```env
VITE_API_URL=http://localhost:5000/api/v1
```

Start the frontend development server:

```bash
npm run dev
```

Vite will print the local URL in the terminal, typically `http://localhost:5173`.

## API Overview

The API base path is `/api/v1`.

| Method | Endpoint | Description | Authentication |
|---|---|---|---|
| `POST` | `/signup` | Create an account | No |
| `POST` | `/login` | Log in and set the authentication cookie | No |
| `POST` | `/logout` | Log out and clear the cookie | No |
| `GET` | `/me` | Get the current user's details | Yes |
| `GET` | `/applications` | List the current user's applications | Yes |
| `POST` | `/applications` | Create an application | Yes |
| `PUT` | `/applications/:id` | Update an application | Yes |
| `DELETE` | `/applications/:id` | Delete an application | Yes |

The authentication flow uses a JWT stored in an HTTP-only cookie. Authenticated application routes are scoped to the current user.

### Application fields

Each application includes:

- `company` — company name
- `position` — job title or role
- `status` — `pending`, `shortlisted`, or `rejected`
- `appliedDate` — date the application was submitted
- `deadline` — relevant deadline, which must be after the application date and in the future

## Available Scripts

### Backend (`backend/`)

```bash
npm start
```

Starts the Express server.

### Frontend (`frontend/`)

```bash
npm run dev      # Start Vite development server
npm run build    # Build for production
npm run preview  # Preview the production build
npm run lint     # Run ESLint
```

## Deployment Notes

- Deploy the frontend and backend as separate services if needed.
- Set `MONGODB_URI`, `JWT_SECRET`, and `PORT` in the backend hosting provider's environment variables.
- Set `VITE_API_URL` to the deployed backend API base URL in the frontend environment.
- Update the backend CORS allowlist in `backend/index.js` to include the exact deployed frontend origin.
- Because authentication uses cookies across origins, configure HTTPS and compatible cookie/CORS settings in production.
- Never commit `.env` files, database credentials, or JWT secrets.

## Future Improvements

- Add automated deadline and interview reminders.
- Add analytics charts and application conversion statistics.
- Add interview notes, follow-up dates, and offer tracking.
- Add pagination and sorting for larger application lists.
- Add automated tests and CI checks.

## Contributing

Contributions and suggestions are welcome. Fork the repository, create a feature branch, and submit a pull request with a clear description of your changes.

## License

No license has been specified yet. Add a `LICENSE` file if you intend to make the project open source.
