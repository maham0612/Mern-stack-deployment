Here’s a formatted README file suited for GitHub, based on the deployment steps you used for your MERN stack website:

---

# MERN Stack Application - Deployment Guide

This repository contains a full-stack MERN (MongoDB, Express, React, Node.js) application. The following guide provides the steps necessary to clone, install dependencies, and deploy the application using PM2.

## Prerequisites

Ensure you have the following installed:

- Ubuntu or a compatible Linux operating system
- Node.js (v20.x) installed using [NVM](https://github.com/nvm-sh/nvm)
- MongoDB 8.0
- PM2 (to manage Node.js processes)

## Setup Guide

### 1. Clone the Repository

First, clone the repository to your server or local machine:

```bash
git clone https://github.com/bradtraversy/mern-tutorial.git
cd mern-tutorial/
```

### 2. Install Node.js via NVM

You need Node.js version 20.x. Install it using NVM:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
nvm install 20
```

Verify the installation:

```bash
node -v
npm -v
```

### 3. Install MongoDB 8.0

Set up MongoDB 8.0 by following these commands:

```bash
sudo apt-get install gnupg curl
curl -fsSL https://www.mongodb.org/static/pgp/server-8.0.asc | sudo gpg -o /usr/share/keyrings/mongodb-server-8.0.gpg --dearmor
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-8.0.gpg ] https://repo.mongodb.org/apt/ubuntu noble/mongodb-org/8.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-8.0.list
sudo apt-get update
sudo apt-get install -y mongodb-org
```

Start and enable MongoDB:

```bash
sudo systemctl start mongod
sudo systemctl enable mongod
```

### 4. Install Dependencies

Navigate to the root directory and install the backend dependencies:

```bash
cd mern-tutorial/
npm install
```

Next, install the frontend dependencies:

```bash
cd frontend/
npm install
```

### 5. Build the Frontend

To build the React frontend for production:

```bash
cd frontend/
npm run build
```

### 6. Run the Backend and Frontend with PM2

Start the backend using PM2:

```bash
cd backend/
pm2 start server.js --name "Goalserver-be"
```

Serve the frontend using PM2:

```bash
pm2 serve build/ 5001 --name "Goalfrontend-fe"
```

### 7. Manage Processes

You can manage PM2 processes with the following commands:

View process logs:

```bash
pm2 logs Goalserver-be
```

View the list of processes:

```bash
pm2 ls
```

Delete unused PM2 processes:

```bash
pm2 delete 0 1
```

## License

This project is licensed under the MIT License.

---

Feel free to copy this `README.md` into your repository! Let me know if you'd like any additional details or changes.
