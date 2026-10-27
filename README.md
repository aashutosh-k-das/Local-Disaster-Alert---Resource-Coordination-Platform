# Local Disaster Alert & Resource Coordination Platform

A full-stack web platform for helping communities report local disasters, coordinate volunteers, and manage requests for emergency resources and assistance.

## What it does

The platform brings citizens, volunteers, and administrators into one coordination workflow:

- Citizens can register, report incidents, and request help.
- Volunteers can review and respond to community needs.
- Administrators can manage users, disasters, and requests.
- Real-time communication keeps connected clients synchronized.
- Map support helps visualize locations and disaster-related activity.

## Features

- Role-based access for **Citizen**, **Volunteer**, and **Admin** users
- Protected dashboards and JWT-based authentication
- Disaster reporting and tracking
- Resource and assistance request management
- Real-time updates with Socket.IO
- Interactive maps with Leaflet and React Leaflet
- Optional Google Maps API integration
- File uploads served by the backend
- REST API with MongoDB persistence
- Responsive React interface with Tailwind CSS
- Health-check endpoint at `/api/health`

## Tech stack

### Frontend

- React 19
- Vite
- React Router
- Tailwind CSS
- Axios
- Leaflet and React Leaflet
- Socket.IO Client
- React Hot Toast

### Backend

- Node.js
- Express
- MongoDB and Mongoose
- Socket.IO
- JSON Web Token authentication
- bcryptjs
- Multer
- Morgan

## Repository structure

```text
.
├── client/                 # React/Vite frontend
│   ├── public/
│   └── src/
└── server/                 # Express/MongoDB backend
    ├── config/
    ├── controllers/
    ├── middlewares/
    ├── models/
    ├── routes/
    ├���─ uploads/
    └── server.js
```

## Requirements

- Node.js 18 or newer
- npm
- MongoDB, local or hosted
- Optional Google Maps API key

## Local development

### 1. Clone the repository

```bash
git clone https://github.com/aashutosh-k-das/Local-Disaster-Alert---Resource-Coordination-Platform.git
cd Local-Disaster-Alert---Resource-Coordination-Platform
```

### 2. Configure and run the backend

```bash
cd server
npm install
cp .env.example .env
```

Set the values in `server/.env`:

```env
PORT=5000
MONGO_URI=mongodb://127.0.0.1:27017/ldarcp
JWT_SECRET=replace_with_a_secure_secret
JWT_EXPIRES_IN=7d
CLIENT_URL=http://localhost:5173
GOOGLE_MAPS_API_KEY=
```

Start the API:

```bash
npm run dev
```

For a normal Node.js start, use:

```bash
npm start
```

The backend runs at `http://localhost:5000` by default. Check that it is running with:

```bash
curl http://localhost:5000/api/health
```

### 3. Configure and run the frontend

In a second terminal:

```bash
cd client
npm install
cp .env.example .env
```

Set the values in `client/.env`:

```env
VITE_API_URL=http://localhost:5000/api
VITE_SOCKET_URL=http://localhost:5000
VITE_GOOGLE_MAPS_API_KEY=
```

Start the Vite development server:

```bash
npm run dev
```

The frontend is typically available at `http://localhost:5173`.

## Available scripts

### Client scripts

Run these commands from `client/`:

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Vite development server |
| `npm run build` | Create a production build |
| `npm run lint` | Run ESLint |
| `npm run preview` | Preview the production build |

### Server scripts

Run these commands from `server/`:

| Command | Description |
| --- | --- |
| `npm run dev` | Start the API with Nodemon |
| `npm start` | Start the API with Node.js |

## API route groups

| Route | Purpose |
| --- | --- |
| `/api/auth` | Registration and login |
| `/api/users` | User-related operations |
| `/api/disasters` | Disaster creation and management |
| `/api/requests` | Assistance and resource requests |
| `/api/health` | Backend health check |

## Environment variables

The repository provides example files at:

- `client/.env.example`
- `server/.env.example`

Never commit real secrets. Keep `.env` files local and use a strong, unique `JWT_SECRET` outside development.

## Production checklist

Before deploying, make sure to:

- Use HTTPS for the frontend, API, and Socket.IO connection.
- Configure a production MongoDB connection string.
- Set `NODE_ENV=production`.
- Set an explicit production `CLIENT_URL`.
- Restrict CORS to trusted origins.
- Store uploads in durable object storage when appropriate.
- Add monitoring, backups, rate limiting, and automated tests.
- Run the client production build with `npm run build`.

## Contributing

1. Fork the repository.
2. Create a feature branch:

   ```bash
   git checkout -b feature/your-feature
   ```

3. Install dependencies and make your changes.
4. Run the relevant lint and build commands.
5. Commit and push your branch.
6. Open a pull request with a clear description of the change.

## License

No license has been specified for this repository yet. Add a license file if you intend to permit reuse or redistribution.
