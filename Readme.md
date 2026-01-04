# 🚗 Car Rental Portal - PHP & MySQL

A complete car rental management system built with PHP, MySQL, and Docker. Features user registration, vehicle booking, admin panel, and payment tracking.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Docker](https://img.shields.io/badge/docker-ready-brightgreen.svg)
![PHP](https://img.shields.io/badge/PHP-8.2-purple.svg)
![MySQL](https://img.shields.io/badge/MySQL-8.0-orange.svg)

## 📋 Table of Contents

- [Features](#features)
- [Technology Stack](#technology-stack)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

---

## ✨ Features

### User Features
- 🔐 User registration and authentication
- 🚙 Browse available vehicles with filters
- 📅 Book vehicles with date selection
- 📝 Manage bookings (view, cancel)
- 💬 Submit testimonials
- 📱 Contact form
- 👤 Profile management
- 🔒 Password reset functionality

### Admin Features
- 📊 Dashboard with statistics
- 🚗 Vehicle management (CRUD operations)
- 📦 Brand management
- 📋 Booking management (approve/reject)
- 👥 User management
- 💬 Testimonial moderation
- 📧 Contact query management
- 📄 Page content management

---

## 🛠️ Technology Stack

| Component | Technology | Version |
|-----------|-----------|---------|
| **Backend** | PHP | 8.2 |
| **Database** | MySQL | 8.0 |
| **Web Server** | Apache | 2.4 |
| **Frontend** | HTML5, CSS3, JavaScript | - |
| **Framework** | Bootstrap | 4.x |
| **Containerization** | Docker & Docker Compose | Latest |
| **Database Driver** | PDO (PHP Data Objects) | - |

---

## 📦 Prerequisites

Before you begin, ensure you have the following installed:

- **Docker Desktop** (v20.10 or higher)
  - [Windows/Mac Download](https://www.docker.com/products/docker-desktop/)
  - [Linux Installation](https://docs.docker.com/engine/install/)
- **Docker Compose** (v2.0 or higher) - Usually included with Docker Desktop
- **Git** (for cloning the repository)
- **4GB RAM** minimum (8GB recommended)
- **5GB free disk space**

---

## 🚀 Installation & Setup

### Method 1: Using Docker (Recommended)

#### Step 1: Clone the Repository

```bash
git clone https://github.com/chetan080808/car-rental-portal.git
cd car-rental-portal
Step 2: Navigate to Project Directory
bash
cd carrental
Step 3: Build and Start Containers
bash
# Build and start all containers
docker-compose up --build -d

# View logs (optional)
docker-compose logs -f
First-time build takes 5-10 minutes to download images and install dependencies.

Step 4: Wait for Database Initialization
bash
# Wait for MySQL to initialize (30 seconds)
sleep 30

# Verify containers are running
docker-compose ps
You should see 3 containers with "Up" status:

carrental-web (PHP/Apache)

carrental-db (MySQL)

carrental-phpmyadmin (Database Manager)

Step 5: Access the Application
Open your browser and navigate to:

Service	URL	Description
Main Website	http://localhost/	User-facing portal
Admin Panel	http://localhost/admin/	Admin dashboard
phpMyAdmin	http://localhost:8081/	Database management
🔑 Default Login Credentials
User Account
text
Email: test@gmail.com
Password: Test@123
Admin Account
text
Username: admin
Password: Test@12345
phpMyAdmin
text
Username: root
Password: rootpassword
⚠️ Change these credentials in production!

📁 Project Structure
text
car-rental-portal/
├── carrental/
│   ├── admin/                  # Admin panel
│   │   ├── includes/          # Admin config files
│   │   ├── img/               # Admin images
│   │   ├── js/                # Admin JavaScript
│   │   ├── css/               # Admin stylesheets
│   │   └── *.php              # Admin pages
│   ├── assets/                # Frontend assets
│   │   ├── css/               # Stylesheets
│   │   ├── js/                # JavaScript files
│   │   ├── images/            # Images
│   │   ├── fonts/             # Font files
│   │   └── switcher/          # Color theme switcher
│   ├── includes/              # Core includes
│   │   ├── config.php         # Database configuration
│   │   ├── header.php         # Header template
│   │   ├── footer.php         # Footer template
│   │   └── *.php              # Other includes
│   ├── Dockerfile             # Docker build instructions
│   ├── docker-compose.yml     # Multi-container setup
│   ├── carrental.sql          # Database dump
│   ├── index.php              # Homepage
│   └── *.php                  # Other pages
└── README.md                  # This file
⚙️ Configuration
Database Configuration
Edit includes/config.php and admin/includes/config.php:

php
<?php 
define('DB_HOST', getenv('DB_HOST') ?: 'db');
define('DB_USER', getenv('DB_USER') ?: 'root');
define('DB_PASS', getenv('DB_PASS') ?: 'rootpassword');
define('DB_NAME', getenv('DB_NAME') ?: 'carrental');
?>
Environment Variables
Modify docker-compose.yml to change credentials:

text
environment:
  - DB_HOST=db
  - DB_USER=root
  - DB_PASS=your_secure_password
  - DB_NAME=carrental
Port Configuration
If ports are already in use, modify in docker-compose.yml:

text
services:
  web:
    ports:
      - "8080:80"    # Change 8080 to any free port
  
  phpmyadmin:
    ports:
      - "8082:80"    # Change 8082 to any free port
Then access at: http://localhost:8080/

🐳 Docker Commands
Starting the Application
bash
# Start containers
docker-compose up -d

# Start with rebuild
docker-compose up --build -d

# View logs
docker-compose logs -f

# View specific service logs
docker-compose logs web
docker-compose logs db
Stopping the Application
bash
# Stop containers (data persists)
docker-compose down

# Stop and remove volumes (deletes database)
docker-compose down -v
Managing Containers
bash
# Check running containers
docker-compose ps

# Restart all services
docker-compose restart

# Restart specific service
docker-compose restart web

# Execute commands in container
docker-compose exec web bash
docker-compose exec db mysql -uroot -prootpassword
Viewing Resource Usage
bash
docker stats
🗄️ Database Management
Import Database Manually
bash
docker-compose exec db mysql -uroot -prootpassword carrental < carrental.sql
Export Database Backup
bash
docker-compose exec db mysqldump -uroot -prootpassword carrental > backup.sql
Access MySQL CLI
bash
docker-compose exec db mysql -uroot -prootpassword carrental
Example queries:

sql
-- Show all tables
SHOW TABLES;

-- Count vehicles
SELECT COUNT(*) FROM tblvehicles;

-- View all bookings
SELECT * FROM tblbooking;
🐛 Troubleshooting
Issue 1: Port Already in Use
Error: Bind for 0.0.0.0:80 failed: port is already allocated

Solution:

bash
# Find what's using the port
sudo lsof -i :80

# Stop the service (example: Apache)
sudo systemctl stop apache2

# Or change port in docker-compose.yml
Issue 2: Containers Won't Start
bash
# View error logs
docker-compose logs

# Remove all containers and volumes
docker-compose down -v

# Rebuild from scratch
docker-compose up --build -d
Issue 3: Database Connection Failed
Solution:

bash
# Wait for database to fully initialize
sleep 30

# Check database is running
docker-compose exec db mysql -uroot -prootpassword -e "SELECT 1;"

# Restart web container
docker-compose restart web
Issue 4: Blank Page or 403 Forbidden
Solution:

bash
# Fix permissions
docker-compose exec web chown -R www-data:www-data /var/www/html
docker-compose exec web chmod -R 755 /var/www/html

# Restart Apache
docker-compose restart web
Issue 5: CSS/JS Not Loading
Clear browser cache (Ctrl+Shift+R)

Check browser console (F12) for errors

Verify files exist in container:

bash
docker-compose exec web ls -la /var/www/html/assets/
🔧 Development
Enable PHP Error Display
Edit Dockerfile and add:

text
RUN echo "display_errors = On" >> /usr/local/etc/php/php.ini && \
    echo "error_reporting = E_ALL" >> /usr/local/etc/php/php.ini
Rebuild:

bash
docker-compose up --build -d
Live Code Updates
The project uses volume mounting, so changes to PHP files are reflected immediately without rebuilding.

Adding New PHP Extensions
Edit Dockerfile:

text
RUN docker-php-ext-install pdo pdo_mysql mysqli gd zip
📊 Database Schema
Main Tables
Table	Description
admin	Admin user credentials
tblbooking	Vehicle booking records
tblbrands	Car brands (Maruti, BMW, etc.)
tblcontactusinfo	Business contact information
tblcontactusquery	Customer inquiries
tblpages	Static page content
tblsubscribers	Newsletter subscribers
tbltestimonial	Customer testimonials
tblusers	Registered users
tblvehicles	Vehicle inventory
🚀 Deployment
Deploy to AWS EC2
Launch Ubuntu EC2 instance

Install Docker and Docker Compose

Clone repository

Update security group (ports 80, 443)

Run docker-compose up -d

Configure domain and SSL certificate

Detailed guide: AWS Deployment Guide

Deploy to DigitalOcean
Similar to AWS, use Docker Droplet or regular Ubuntu droplet with Docker installed.

🤝 Contributing
Contributions are welcome! Please follow these steps:

Fork the repository

Create a feature branch (git checkout -b feature/AmazingFeature)

Commit your changes (git commit -m 'Add AmazingFeature')

Push to branch (git push origin feature/AmazingFeature)

Open a Pull Request

📝 License
This project is licensed under the MIT License - see the LICENSE file for details.

👨‍💻 Author
Chetan Namane

GitHub: @chetan080808

Docker Hub: chetan0808

LinkedIn: https://www.linkedin.com/in/chetan-namane/

🙏 Acknowledgments
Bootstrap for responsive design

Font Awesome for icons

Docker for containerization

MySQL community

PHP community

📞 Support
If you encounter any issues or have questions:

Check Troubleshooting section

Open an Issue

Contact: chetannamne2609@gmail.com

🗺️ Roadmap
 Add payment gateway integration

 Implement email notifications

 Add multi-language support

 Mobile app (React Native)

 Advanced search filters

 Rating and review system

 SMS notifications

 Google Maps integration


