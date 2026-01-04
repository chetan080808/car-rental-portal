# 🚗 Car Rental Portal – PHP & MySQL (with Docker & Docker Hub Image)

A complete car rental management system built with PHP, MySQL, and Docker. This single README explains:

- How to run the **main project** (build/run with Docker from source)
- How to run the project using the **prebuilt Docker image from Docker Hub** (for easy sharing with non‑technical users)

GitHub removed password authentication for Git operations; use access tokens or SSH when pushing this project. [web:68][web:69]

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Option 1 – Run From Source with Docker](#option-1--run-from-source-with-docker)
  - [Clone Repository](#clone-repository)
  - [Project Structure](#project-structure)
  - [Start Containers](#start-containers)
  - [Application URLs](#application-urls)
  - [Default Credentials](#default-credentials)
  - [Useful Docker Commands](#useful-docker-commands)
- [Option 2 – Run Using Prebuilt Docker Image (Docker Hub)](#option-2--run-using-prebuilt-docker-image-docker-hub)
  - [Folder Contents for Sharing](#folder-contents-for-sharing)
  - [Quick Start (for your friend/college demo)](#quick-start-for-your-friendcollege-demo)
- [Ports & Configuration](#ports--configuration)
- [Troubleshooting](#troubleshooting)
- [For College / Presentation Talking Points](#for-college--presentation-talking-points)
- [Author](#author)

---

## 🧾 Overview

This system simulates a real‑world car rental portal:

- **User side** – browse cars, make bookings, manage profile, submit testimonials.
- **Admin side** – manage vehicles, brands, bookings, users, CMS pages, and contact queries.
- **Database** – MySQL schema with sample data (`carrental.sql`).
- **Deployment** – Docker and Docker Compose for reproducible local or cloud environments. [web:52][web:53]

---

## ✨ Features

**User portal:**

- Registration, login, logout  
- Browse available vehicles with details and images  
- Book cars for selected dates  
- View booking history  
- Submit testimonials  
- Use contact form to send enquiries  
- Update profile and change password  

**Admin panel:**

- Admin authentication  
- Dashboard with booking and vehicle summaries  
- Vehicle management (add/edit/delete vehicles)  
- Brand management  
- Booking approval / rejection  
- User management  
- Testimonial moderation  
- Static pages management (About, FAQs, etc.)  
- View and respond to contact queries  

---

## 🛠 Tech Stack

- **Backend:** PHP 8.x  
- **Frontend:** HTML5, CSS3, Bootstrap, JavaScript  
- **Database:** MySQL 8.x  
- **Web server:** Apache 2.4  
- **Containerization:** Docker & Docker Compose (multi‑container stack) [web:52]  

---

## 📦 Prerequisites

You need the following on the machine where you run the project:

- **Git** (if cloning from GitHub)
- **Docker** (Engine / Docker Desktop)  
- **Docker Compose** (v2+; bundled with recent Docker Desktop)  
- At least **4 GB RAM** and **5 GB free disk space**  

Official Docker docs and beginner guides show how to install Docker Desktop on Windows, macOS, and Linux. [web:52][web:53]

---

## OPTION 1 – Run From Source with Docker

This option is for you (developer) or any technical user who has the full project code. The main project folder contains PHP source, `Dockerfile`, `docker-compose.yml`, and `carrental.sql`.

### 🧬 Clone Repository

```bash
git clone https://github.com/chetan080808/car-rental-portal.git
cd car-rental-portal/carrental
If the repo/folder name differs, adjust the path accordingly.

🗂 Project Structure
Inside carrental you should see something like:

text
carrental/
├── admin/                 # Admin panel PHP files and assets
├── assets/                # Front-end CSS, JS, images, fonts
├── includes/              # Shared PHP includes (config, header, footer, etc.)
├── Dockerfile             # PHP + Apache image build instructions
├── docker-compose.yml     # Multi-container configuration
├── carrental.sql          # MySQL schema + sample data
├── index.php              # Home page
├── car-listing.php
├── vehical-details.php
├── my-booking.php
├── my-testimonials.php
├── post-testimonial.php
├── contact-us.php
└── other PHP pages...
▶️ Start Containers
From the carrental directory:

bash
# Build and start containers in the background
docker-compose up --build -d
What this does:

Builds a PHP+Apache image using the Dockerfile

Starts:

carrental-web (PHP + Apache)

carrental-db (MySQL 8)

carrental-phpmyadmin (phpMyAdmin)

Creates a network so containers can talk to each other

Imports carrental.sql into MySQL on first run

Give MySQL some time to initialize and import the SQL:

bash
sleep 30    # optional but recommended on first run
docker-compose ps
You should see all three services with status Up.

🌐 Application URLs
By default:

User site:
http://localhost/

Admin panel:
http://localhost/admin/

phpMyAdmin:
http://localhost:8081/

You can change these ports if they conflict with anything else; see the Ports & Configuration section below. [web:66]

🔑 Default Credentials
User login

text
Email:    test@gmail.com
Password: Test@123
Admin login

text
Username: admin
Password: Test@12345
phpMyAdmin

text
Username: root
Password: rootpassword
Change these values if you plan to expose the app beyond local development.

🐳 Useful Docker Commands (Source Setup)
From the carrental directory:

bash
# See all services and status
docker-compose ps

# Follow logs for all services
docker-compose logs -f

# Logs per service
docker-compose logs web
docker-compose logs db
docker-compose logs phpmyadmin

# Stop containers (data persists)
docker-compose down

# Stop + remove DB volume (fresh DB next time)
docker-compose down -v

# Restart all services
docker-compose restart

# Open a shell in the web container
docker-compose exec web bash

# Connect to MySQL directly
docker-compose exec db mysql -uroot -prootpassword carrental
