# Advanced Babysteps Appointment Booking System

This project implements a full-stack appointment booking system for a prenatal care service, allowing users to view doctor availability and book appointments.

## Table of Contents

- [Overview](#overview)
- [Installation](#installation)
- [Running the Application](#running-the-application)
- [Backend](#backend)
  - [Technologies Used](#technologies-used-backend)
  - [Data Models](#data-models)
  - [API Endpoints](#api-endpoints)
- [Frontend](#frontend)
  - [Technologies Used](#technologies-used-frontend)
  - [User Interface](#user-interface)
  - [State Management](#state-management)
- [Assumptions and Design Decisions](#assumptions-and-design-decisions)
- [Optional Enhancements](#optional-enhancements)

## Overview

This application provides a platform for users to:

- View a list of doctors.
- Select a doctor and view their available time slots for the next 7 days.
- Book appointments by selecting a time slot and providing patient details.
- Manage their upcoming appointments (view, edit, cancel).

## Installation

1.  **Clone the repository:**

    ```bash
    git clone <repository-url>
    cd <repository-directory>
    ```

2.  **Backend Installation:**

    ```bash
    cd backend
    npm install
    ```

3.  **Frontend Installation:**

    ```bash
    cd ../frontend
    npm install
    ```

4.  **MongoDB Setup:**

    -   Ensure MongoDB is installed and running on your local machine.
    -   Create a database named `appointment-booking`.

## Running the Application

1.  **Start the Backend:**

    ```bash
    cd ../backend
    npm run dev #or npm start if you are not using nodemon
    ```

    (The backend will run on `http://localhost:5000`).

2.  **Start the Frontend:**

    ```bash
    cd ../frontend
    npm start
    ```

    (The frontend will run on `http://localhost:3000`).

## Backend

### Technologies Used (Backend)

-   Node.js
-   Express.js
-   MongoDB
-   Mongoose
-   Moment.js
-   cors

### Data Models

-   **Doctor:**
    -   `name` (String): Doctor's name.
    -   `workingHours` (Object): Daily working hours (`{ start: "09:00", end: "17:00" }`).
-   **Appointment:**
    -   `doctorId` (ObjectId): Reference to a Doctor.
    -   `date` (Date): Date and time of the appointment.
    -   `duration` (Number): Duration in minutes (e.g., 30, 60).
    -   `appointmentType` (String): E.g., "Routine Check-Up", "Ultrasound".
    -   `patientName` (String): Name of the patient.
    -   `notes` (String, optional).

### API Endpoints

-   **Doctor Endpoints:**
    -   `GET /doctors`: Retrieve a list of all doctors.
    -   `GET /doctors/:id/slots?date=YYYY-MM-DD`: Compute and return available time slots for a doctor on a given date.
-   **Appointment Endpoints:**
    -   `GET /appointments`: Retrieve all appointments.
    -   `GET /appointments/:id`: Retrieve a specific appointment.
    -   `POST /appointments`: Create a new appointment (validates time slot availability).
    -   `PUT /appointments/:id`: Update an appointment (validates time slot availability).
    -   `DELETE /appointments/:id`: Cancel an appointment.

## Frontend

### Technologies Used (Frontend)

-   React
-   Axios
-   Moment.js
-   (Optional UI libraries like Material-UI or Bootstrap)

### User Interface

-   **Doctor Selection:** Displays a list of doctors.
-   **Calendar/Slot View:** Shows available time slots for a selected doctor and date.
-   **Appointment Booking:** A form to capture patient details.
-   **Appointment Management:** Lists upcoming appointments with edit/cancel options.

### State Management

-   React's `useState` hook is used to manage component state.
-   (Optional: Redux or Context API could be used for more complex state management.)

## Assumptions and Design Decisions

-   Doctor working hours are the same every day.
-   Appointments start at fixed 30-minute intervals.
-   No user authentication is implemented.
-   Basic error handling is implemented on both the backend and frontend.
-   The calendar view displays the next 7 days from the selected date.
-   Date format used is YYYY-MM-DD.
-   The backend is configured to run on localhost port 5000, and the frontend on port 3000.

## Optional Enhancements

-   Implement real-time updates for slot availability using WebSockets (Socket.io).
-   Enhance the calendar view using a third-party calendar component.
-   Add user authentication.
-   Add Doctor Specializations.
-   Add better styling with a UI library.
-   Add more robust error handling.
-   Add unit and integration tests.
