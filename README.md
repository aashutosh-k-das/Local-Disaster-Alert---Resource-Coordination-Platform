# Local Disaster Alert & Resource Coordination Platform

A full-stack disaster-response coordination platform that helps communities report emergencies, coordinate volunteers, and manage resource requests from a shared web application.

## Overview

The platform connects citizens, volunteers, and administrators during local disasters. It provides role-based dashboards, disaster reporting, resource-request workflows, authentication, and real-time communication support.

## Features

- **Role-based access control** for citizens, volunteers, and administrators
- **Citizen dashboard** for viewing incidents and requesting assistance
- **Volunteer dashboard** for coordinating and responding to community needs
- **Admin dashboard** for managing users, disasters, and requests
- **Disaster reporting and tracking**
- **Resource and assistance request management**
- **JWT authentication** with protected routes
- **Real-time updates** using Socket.IO
- **Map integration** with Leaflet and optional Google Maps configuration
- **File uploads** served through the API
- **REST API** backed by MongoDB
- **Responsive React interface** built with Vite and Tailwind CSS

## Tech Stack

### Frontend

- React
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
- MongoDB with Mongoose
- Socket.IO
- JSON Web Tokens
- bcryptjs
- Multer
- Morgan

## Project Structure

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
    ├── uploads/
    └── server.js
```

## Prerequisites

- Node.js 18 or newer
- npm
- MongoDB, either locally or through a hosted provider
- Optional Google Maps API key, if Google Maps features are enabled

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/aashutosh-k-das/Local-Disaster-Alert---Resource-Coordination-Platform.git
cd Local-Disaster-Alert---Resource-Coordination-Platform
```

### 2. Configure the server

```bash
cd server
npm install
cp .env.example .env
```

Update `server/.env` with values appropriate for your environment:

```env
PORT=5000
MONGO_URI=mongodb://127.0.0.1:27017/ldarcp
JWT_SECRET=replace_with_a_secure_secret
JWT_EXPIRES_IN=7d
CLIENT_URL=http://localhost:5173
GOOGLE_MAPS_API_KEY=
```

Start the backend in development mode:

```bash
npm run dev
```

Or start it normally:

```bash
npm start
```

The API runs at `http://localhost:5000` by default. You can verify it with:

```text
GET http://localhost:5000/api/health
```

### 3. Configure the client

Open a second terminal:

```bash
cd client
npm install
cp .env.example .env
```

Update `client/.env` as needed:

```env
VITE_API_URL=http://localhost:5001/api
VITE_SOCKET_URL=http://localhost:5001
VITE_GOOGLE_MAPS_API_KEY=
```

> Make sure `VITE_API_URL` and `VITE_SOCKET_URL` match the port used by your backend. The server defaults to port `5000`; update these values if you use that default.

Start the frontend:

```bash
npm run dev
```

The Vite development server will print the local URL in the terminal, typically `http://localhost:5173`.

## Available Scripts

### Client

From the `client` directory:

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Vite development server |
| `npm run build` | Create a production build |
| `npm run lint` | Run ESLint |
| `npm run preview` | Preview the production build locally |

### Server

From the `server` directory:

| Command | Description |
| --- | --- |
| `npm run dev` | Start the API with Nodemon |
| `npm start` | Start the API with Node.js |

## API Areas

The backend currently exposes route groups for:

- `/api/auth` — registration and login
- `/api/users` — user-related operations
- `/api/disasters` — disaster creation and management
- `/api/requests` — assistance and resource requests
- `/api/health` — service health check

## Security Notes

- Do not commit `.env` files or real credentials.
- Use a long, unique value for `JWT_SECRET` in non-development environments.
- Use a managed MongoDB connection string with appropriate access controls in production.
- Restrict CORS origins through `CLIENT_URL` when deploying.
- Review uploaded-file handling and storage policies before production deployment.

## Production Considerations

Before deploying, consider:

- Building the client with `npm run build`
- Hosting the frontend and backend behind HTTPS
- Configuring production MongoDB credentials
- Setting `NODE_ENV=production`
- Providing a production `CLIENT_URL`
- Moving uploads to durable object storage
- Adding monitoring, backups, rate limiting, and automated tests

## Contributing

1. Fork the repository.
2. Create a feature branch:

   ```bash
   git checkout -b feature/your-feature
   ```

3. Make and test your changes.
4. Commit your work with a clear message.
5. Push the branch and open a pull request.

## License

No license has been specified for this repository yet. Add a license file if you intend to permit reuse or redistribution.
