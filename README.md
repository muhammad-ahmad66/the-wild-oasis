# The Willd – Cabin Booking Dashboard

**Live Demo**: [View the live app here](https://the-willd.netlify.app/)

---

## Overview

**The Willd** is a modern React-based booking dashboard for cabin rentals, designed with scalability, performance, and usability in mind. It features advanced state management, clean UI components, and seamless user experience across authentication, booking workflows, and data visualization.

---

## Features

- **Authentication & Authorization**
  - Powered by **Supabase** for secure user signup, login, and role-based access control.

- **API Integration**
  - CRUD endpoints for cabins, bookings, guest/users, and settings.
  - Fully managed via Supabase backend.

- **Data Management**
  - Filtering, sorting, and paginating cabin and booking lists.
  - Optimized with **prefetching** using **React Query** for seamless UX.
  - Live updating and cache invalidation.

- **Reusable Components**
  - **Portal Window Component** for popups/modal dialogs.
  - Shared **Pagination**, **Filter**, **Sort**, and **Table/List** UI components.
  - Chart components implemented with **Recharts** (Pie Charts, Line Charts, and more).

- **Custom Hooks & Patterns**
  - Tailored hooks for data fetching (`useCabins`, `useBookings`, `useUser`, etc.).
  - Advanced patterns like **Compound Components** and **Render Props** to increase flexibility & composition.
  - Theme toggler (**Light/Dark Mode**) support.

- **Dashboard & Data Visualization**
  - Insightful charts and statistics for overview and metrics.
  - Real-time dashboard UI updating.

---

## Tech Stack

| Layer               | Tools / Libraries                  |
|--------------------|------------------------------------|
| Frontend           | React, React Router                |
| State & Data Caching | React Query                        |
| Charts & Visualization | Recharts                          |
| Styling            | Styled Components                   |
| Backend            | Supabase (Auth, API, Database)    |
| Design Patterns    | Compound Components, Render Props  |
| Utilities          | Custom Hooks, Theming (Dark Mode)  |

---

## Getting Started

1. **Clone the repository**  

   ```bash
   git clone https://github.com/your-username/the-willd.git
   cd the-willd
