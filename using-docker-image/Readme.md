text
# 🚗 Car Rental Portal - Quick Start with Docker

Run this complete car rental system in 3 commands using prebuilt Docker images.

---

## 📦 What You Need

- **Docker Desktop** installed and running
- **3 files** in a folder:
  - `docker-compose.yml`
  - `carrental.sql`
  - `README.md` (this file)

Download Docker: https://www.docker.com/products/docker-desktop/

---

## ⚡ Quick Start

### Step 1: Open Terminal/Command Prompt

Navigate to the folder with the 3 files:

```bash
cd path/to/car-rental-folder
Step 2: Start Everything
bash
docker-compose up -d
First time takes 5-10 minutes (downloads images ~1.5GB total).

Step 3: Access the Site
Wait 30 seconds, then open browser:

Main site: http://localhost/

Admin panel: http://localhost/admin/

Database manager: http://localhost:8081/

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
🐳 Basic Commands
bash
# Check status
docker-compose ps

# Stop (keeps data)
docker-compose down

# Start again
docker-compose up -d

# View logs if errors
docker-compose logs
🐛 Troubleshooting
❌ "Port 80 is already in use"
Cause: Another program using port 80 (Skype, XAMPP, IIS).

Fix: Edit docker-compose.yml, find:

text
web:
  ports:
    - "80:80"
Change to:

text
web:
  ports:
    - "8080:80"
Then:

bash
docker-compose down
docker-compose up -d
Access at: http://localhost:8080/

❌ Blank page or only header shows
Cause: Database still initializing.

Fix:

bash
# Wait 30 more seconds, then refresh browser
# Or restart:
docker-compose restart
❌ "Docker daemon not running"
Fix: Open Docker Desktop application and wait for it to start (shows green icon).

❌ Database not loading
Cause: carrental.sql file missing or wrong location.

Fix:

bash
# Ensure carrental.sql is in same folder as docker-compose.yml
# Reset database:
docker-compose down -v
docker-compose up -d
❌ "Cannot find carrental.sql"
Fix: Make sure carrental.sql is a file, not a folder. If it's a folder, delete it:

bash
rmdir carrental.sql  # if directory
# Then copy the actual .sql file
🎓 For College Demo
What to say:

"This car rental system uses PHP, MySQL, and Docker containers. Docker packages the web server, database, and application together, making it portable across any machine."

Technologies:

PHP 8.2 (Backend)

MySQL 8.0 (Database)

Apache 2.4 (Web Server)

Docker (Containerization)

Bootstrap (Frontend)

Features to demonstrate:

User registration and login

Browse cars

Make a booking

Admin login

Admin manage vehicles

View database in phpMyAdmin

📊 What's Running?
Three Docker containers:

text
carrental-web       → PHP + Apache (your application)
carrental-db        → MySQL database
carrental-phpmyadmin → Database management UI
Check with:

bash
docker-compose ps
All should show "Up" status.

💾 Reset Everything
To start completely fresh (deletes all data):

bash
docker-compose down -v
docker-compose up -d
This reimports the original database with sample data.

🔄 Update to Latest Version
If a new version is released:

bash
docker pull chetan0808/carrental-web:latest
docker-compose down
docker-compose up -d
📞 Need Help?
Check logs: docker-compose logs

Make sure Docker Desktop is running

Ensure all 3 files are in same folder

Try reset: docker-compose down -v && docker-compose up -d

👤 Author
Chetan Namane

Docker Hub: chetan0808

GitHub: @chetan080808

Docker Image: chetan0808/carrental-web:latest
