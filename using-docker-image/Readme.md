# 🚗 Car Rental Portal - Quick Start with Docker

Pre-built Docker image available! No need to build from source - just pull and run.

[![Docker](https://img.shields.io/badge/docker-chetan0808%2Fcarrental--web-blue.svg)](https://hub.docker.com/r/chetan0808/carrental-web)
[![Docker Pulls](https://img.shields.io/docker/pulls/chetan0808/carrental-web.svg)](https://hub.docker.com/r/chetan0808/carrental-web)

---

## 🎯 What You Get

✅ Complete PHP car rental website  
✅ MySQL database with sample data  
✅ Admin panel for management  
✅ phpMyAdmin for database access  
✅ **NO manual installation or configuration needed!**

---

## 📦 Prerequisites

Only 2 things needed:

1. **Docker Desktop** installed
   - [Download for Windows/Mac](https://www.docker.com/products/docker-desktop/)
   - [Install on Linux](https://docs.docker.com/engine/install/)

2. **3 files from this package:**
   - `docker-compose.yml` ✅
   - `carrental.sql` ✅
   - `README.md` (this file) ✅

---

## ⚡ Quick Start (3 Steps)

### Step 1: Verify Docker is Running

Open terminal/command prompt and check:

```bash
docker --version
docker-compose --version
If Docker Desktop is not running, start it first.

Step 2: Create Project Folder
Windows:

text
cd Desktop
mkdir car-rental
cd car-rental
Mac/Linux:

bash
cd ~/Desktop
mkdir car-rental
cd car-rental
Copy the 3 files (docker-compose.yml, carrental.sql, README.md) into this folder.

Step 3: Start the Application
bash
docker-compose up -d
That's it! ✨

First time takes 5-10 minutes (downloads MySQL, phpMyAdmin, and app image ~540MB).

🌐 Access the Application
After the containers start, open your browser:

Service	URL
Main Website	http://localhost/
Admin Panel	http://localhost/admin/
Database Manager	http://localhost:8081/
🔑 Login Credentials
User Login
text
Email: test@gmail.com
Password: Test@123
Admin Login
text
Username: admin
Password: Test@12345
phpMyAdmin
text
Username: root
Password: rootpassword
📱 Features Overview
For Users
Browse available cars

Book vehicles by date

Manage bookings

Submit testimonials

Update profile

For Admins
Manage vehicles (add/edit/delete)

Approve/reject bookings

View all users

Manage brands

View contact queries

Manage testimonials

🛠️ Common Commands
Check Status
bash
# See if containers are running
docker-compose ps
You should see 3 containers:

carrental-web (PHP/Apache)

carrental-db (MySQL)

carrental-phpmyadmin (Database UI)

Stop Application
bash
docker-compose down
Start Again
bash
docker-compose up -d
View Logs (if something goes wrong)
bash
docker-compose logs
Restart Everything
bash
docker-compose restart
🐛 Troubleshooting
❌ "Port 80 is already in use"
Another program (like Skype, XAMPP, IIS) is using port 80.

Quick Fix:

Edit docker-compose.yml, find this section:

text
web:
  ports:
    - "80:80"
Change to:

text
web:
  ports:
    - "8080:80"
Save and run:

bash
docker-compose down
docker-compose up -d
Access at: http://localhost:8080/

❌ "Docker daemon not running"
Solution: Open Docker Desktop app and wait for it to start (green light at bottom).

❌ Blank page appears
Database might still be initializing.

Solution:

bash
# Wait 30 seconds
# Then refresh browser (Ctrl+R)

# Or restart
docker-compose restart
❌ "Cannot connect to Docker daemon"
Windows: Docker Desktop not running or WSL 2 not enabled
Mac: Docker Desktop not running
Linux: Docker service not started

Solution:

bash
# Linux only
sudo systemctl start docker
📁 What's Inside?
text
car-rental/
├── docker-compose.yml      # Container configuration
├── carrental.sql           # Database with sample data
└── README.md              # This file
When you run docker-compose up, it automatically:

Pulls PHP/Apache image from Docker Hub (chetan0808/carrental-web)

Pulls MySQL 8.0 image

Pulls phpMyAdmin image

Creates network for inter-container communication

Imports carrental.sql into MySQL

Starts all services

🎓 For College Projects
What to Demonstrate
Technology Stack:

PHP 8.2

MySQL 8.0

Apache 2.4

Docker containerization

Bootstrap frontend

Architecture:

text
┌─────────────────────────────────┐
│   Docker Containers (3 Total)  │
├─────────────────────────────────┤
│  carrental-web (PHP/Apache)     │
│           ↓                     │
│  carrental-db (MySQL)           │
│           ↓                     │
│  carrental-phpmyadmin (DB UI)   │
└─────────────────────────────────┘
Key Features:

User authentication

CRUD operations

Session management

Database relationships

Responsive design

Testing Checklist
Before presenting, test:

 User registration works

 User login works

 Car browsing works

 Booking creation works

 Admin login works

 Admin can manage vehicles

 Admin can view bookings

 phpMyAdmin accessible

🔄 Updating the Application
If a new version is released:

bash
# Stop current version
docker-compose down

# Pull latest image
docker pull chetan0808/carrental-web:latest

# Start with new version
docker-compose up -d
💾 Backup Your Data
Export Database
bash
docker-compose exec db mysqldump -uroot -prootpassword carrental > my_backup.sql
Restore Database
bash
docker-compose exec -T db mysql -uroot -prootpassword carrental < my_backup.sql
🌍 Running on Different Machines
This setup works on:

✅ Windows 10/11 (with Docker Desktop)

✅ macOS (Intel and Apple Silicon)

✅ Linux (Ubuntu, Debian, Fedora, etc.)

Same 3 files, same commands, same results!

📊 Database Schema
The carrental database includes:

Table	Records	Description
tblvehicles	8	Sample cars (BMW, Audi, etc.)
tblbrands	6	Car brands
tblusers	1	Test user account
admin	1	Admin account
tblbooking	Sample	Booking records
🚀 Next Steps
After getting it running:

Explore the code:

bash
# Enter the web container
docker-compose exec web bash
cd /var/www/html
ls -la
Add your own vehicles:

Login to admin panel

Go to "Manage Vehicles"

Click "Add Vehicle"

Customize design:

Modify CSS files (changes reflect immediately)

Change logo and images

Deploy to cloud:

AWS EC2

DigitalOcean

Google Cloud

📞 Support & Issues
Need help?

Check Troubleshooting section above

View logs: docker-compose logs

GitHub Issues: Report a problem

Docker Hub: Image page

🔗 Resources
Docker Documentation

Docker Compose Documentation

MySQL Documentation

PHP Documentation

👨‍💻 Developer
Chetan Pawar

Docker Hub: chetan0808

GitHub: @chetan080808

⭐ Like this project?
Give it a star on GitHub and Docker Hub!

Pull the image:

bash
docker pull chetan0808/carrental-web:latest
Made with ❤️ using Docker | Ready to run in 3 commands

text

***

## 📝 Create Both Files

Run these commands on your EC2:

```bash
# For main project README
cd ~/project/car-rental-portal-project
nano README.md
# Paste content #1, save with Ctrl+X, Y, Enter

# For Docker Hub users README
cd ~/project/car-rental-portal-project/using-docker-image
nano README.md
# Paste content #2, save with Ctrl+X, Y, Enter

# Verify both files
cat ~/project/car-rental-portal-project/README.md | head -20
cat ~/project/car-rental-portal-project/using-docker-image/README.md | head -20
