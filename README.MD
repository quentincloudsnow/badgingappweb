# Badging App

The Badging App is a 'Fake'  web application that allows users to enter guest information and generate badges. It includes authentication and badge printing features.
This is mainly to be used for training purpose, to learn how to automate this type of screen using ServiceNow RPA Hub technology or other RPA tech.

## Table of Contents
- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Usage](#usage)
- [Authentication](#authentication)
- [Printing Badges](#printing-badges)
- [License](#license)

## Features

- User authentication for access to the dashboard
- Dashboard for entering guest information and printing badges
- Calendar view for selecting access expiration date
- Selection of building location from a list
- Guest email and other information fields

## Getting Started

### Prerequisites

- Node.js and npm installed on your machine
- Git for version control

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/badging-app.git
   cd badging-app


## Starting and Stopping the App with PM2

If you prefer to use `pm2` for process management and automatic restarts, you can follow these steps to start and stop the Badging App:

### Prerequisites

- `pm2` installed on your machine. If not installed, you can install it globally using npm:

   ```bash
   npm install -g pm2


## Starting the App
Navigate to the project directory:

cd badging-app

Start the app using pm2:

pm2 start app.js --name badging-app

pm2 status
pm2 logs badging-app

The --name flag sets a custom name for the app process.
You can view the status and logs of the app using:

## Stopping the App

pm2 stop badging-app
pm2 delete badging-app


## Consideration

For this to work from the internet, you are likely to need Nginx and do port redirection to internal node.js port this app is using. Check the default conf file in this repo for an example. thanks

Quentin.Carton@servicenow.com