# Hotel Room Booking System

A beginner-friendly full-stack hotel booking app with:

- React + Vite frontend
- Node.js + Express backend
- SQLite SQL database
- JWT authentication
- Bcrypt password hashing
- Real-time room availability checks
- Overlap booking prevention

## Features

- View rooms with cards and images
- Search by city/hotel/room keywords
- Filter by city, type (AC / Non-AC), and price range
- Select check-in and check-out dates
- Live availability display
- Register / Login / Logout
- Book room (protected route)
- View personal bookings
- Edit booking dates
- Cancel booking
- Loading skeletons and success/error alerts

## Booking Conflict Rule

The backend prevents overlap with this condition:

`new_checkin <= existing_checkout AND new_checkout >= existing_checkin`

## Project Structure

- `frontend/` React app
- `backend/` Express API + SQLite DB
- `backend/src/data/` dummy JSON data for cities, hotels, and rooms

## Run Backend

```bash
cd backend
npm install
cp .env.example .env
npm start
```

Backend runs on `http://localhost:5000`.

## Run Frontend

```bash
cd frontend
npm install
cp .env.example .env
npm run dev
```

Frontend runs on `http://localhost:5173`.

## API Endpoints

### Auth

- `POST /api/register`
- `POST /api/login`

### Rooms and Search

- `GET /api/cities`
- `GET /api/hotels?city=Bengaluru`
- `GET /api/rooms?city=Hyderabad&type=AC&minPrice=2000&maxPrice=5000&search=Skyline&checkIn=2026-04-12&checkOut=2026-04-14`

### Bookings (JWT Protected)

- `GET /api/bookings`
- `POST /api/book`
- `PUT /api/booking/:id`
- `DELETE /api/booking/:id`

## Notes

- SQLite DB file is auto-created at `backend/hotel_booking.sqlite`
- Sample room, hotel, and city data is seeded on first backend run
- Routes `/book` and `/bookings` are protected in frontend
