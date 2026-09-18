
# Foster

<p align="center">
  <a href="https://fosterstores.onrender.com">
    <img src="public/images/laptopFoster.png" alt="Foster application preview" width="650">
  </a>
</p>

<p align="center">
  <a href="README-pt.md">Português</a>
  ·
  <a href="README.md">English</a>
</p>

<p align="center">
  Web application for registering, organizing and locating business establishments.
</p>

## About

**Foster** is a web application focused on the registration and visualization of business establishments.

The current application provides a complete basic flow for:

- registering an establishment;
- storing its information in a SQLite database;
- listing registered establishments;
- displaying establishments on an interactive map;
- viewing detailed information for a selected establishment;
- providing location data, business hours, contact information, images and access instructions.

The project started as an academic and experimental application and evolved into a functional server-side web system built with **Node.js, Express, Handlebars and SQLite**.

> **Current scope:** Foster is a business establishment directory and management prototype. It is **not a complete ERP**.

## What Foster Is

Foster currently provides a small but functional application stack with:

- **Server-side web application** powered by Express and Handlebars;
- **SQLite persistence** for registered establishments;
- **Map visualization** using Leaflet and OpenStreetMap tiles;
- **Establishment registration** through a web form;
- **Establishment details** with images, opening hours, contact and location;
- **Accessibility support** through the VLibras integration;
- **Automated browser tests** written with Selenium and Python;
- **OpenAPI/Swagger documentation** for the application's current routes.

## What Foster Is Not

The current project does not implement the core modules expected from a full ERP, such as:

- user authentication and authorization;
- roles and permissions;
- customers and suppliers;
- products and inventory;
- purchasing and sales;
- accounts payable and receivable;
- invoicing and fiscal operations;
- financial management;
- business dashboards and management reports;
- audit trails;
- multi-company management;
- a mature public REST API.

These capabilities may become part of future development, but they are not part of the current implementation.

## Current Architecture

At its current stage, Foster intentionally uses a small and simple architecture:

~~~
Browser
   │
   ▼
Express Server
   │
   ├── Handlebars Views
   ├── Application Routes
   └── SQLite Database
~~~

### Main components

- **Node.js** — JavaScript runtime.
- **Express** — web server and routing.
- **Handlebars** — server-side HTML rendering.
- **SQLite** — local relational database.
- **Leaflet** — interactive map rendering.
- **OpenStreetMap** — map tile provider.
- **Swagger UI / OpenAPI** — route documentation.
- **VLibras** — Brazilian Sign Language accessibility support.
- **Selenium + Python** — browser automation and functional testing.

## Main Routes

The current application exposes the following main flows:

| Route | Purpose |
|---|---|
| `/` | Application landing page |
| `/stores` | List and map registered establishments |
| `/store?id=<id>` | View establishment details |
| `/create-store` | Open the registration form |
| `/save-store` | Persist a new establishment |
| `/api-docs` | View the OpenAPI/Swagger documentation |

## Data Model

The current database is intentionally small and centered on the `stores` entity.

The stored information includes:

- geographic coordinates;
- establishment name;
- description;
- WhatsApp/contact number;
- image URLs;
- product or access information;
- opening hours;
- weekend availability.

This model is suitable for the current directory-oriented scope, but it is not yet a business-domain model for a full ERP.

## Testing

The repository includes Python/Selenium scripts used for browser automation and functional testing.

Current examples include:

- automated establishment registration;
- repeated form submission for data-volume testing;
- navigation through application pages;
- interaction testing for VLibras.

The current test structure is useful for validation of the existing prototype, but it is not yet a complete unit, integration and end-to-end testing strategy.

## Running Locally

### Requirements

- [Node.js](https://nodejs.org/)
- [NPM](https://www.npmjs.com/)
- [Git](https://git-scm.com/) — optional, but recommended

### 1. Clone the repository

~~~bash
git clone https://github.com/JacanaFSilva/Foster.git
cd Foster
~~~

### 2. Install dependencies

~~~bash
npm install
~~~

### 3. Start the application

~~~bash
npm start
~~~

The application starts on:

~~~text
http://localhost:3000
~~~

Swagger documentation is available at:

~~~text
http://localhost:3000/api-docs
~~~

For development with automatic restart:

~~~bash
npm run dev
~~~

## Live Application

- **Main deployment:** https://fosterstores.onrender.com
- **Test deployment:** https://foster-7u8w.onrender.com/

> Deployments may differ from the local environment and should not be considered a guarantee of persistent production data.

## Project Structure

~~~
Foster/
├── public/                 # Static assets, CSS, JavaScript and images
├── src/
│   ├── database/           # SQLite setup and persistence logic
│   ├── views/              # Handlebars templates
│   ├── pages.js            # Application route handlers
│   ├── server.js           # Express server
│   └── swagger.json        # OpenAPI documentation
├── Templates/              # Alternative application templates
├── test/                    # Selenium/Python automation
├── package.json
├── README.md
└── README-pt.md
~~~

## Current Status

Foster is a **functional small-scale web application**, but it should be understood as a prototype/foundation rather than a finished enterprise management platform.

The current implementation is strongest in:

- simple architecture;
- clear user flow;
- establishment registration and visualization;
- map integration;
- local persistence;
- basic automated testing;
- easy customization of the presentation layer.

Before expanding the project into a larger business platform, the technical foundation should be strengthened in areas such as:

- parameterized database queries;
- authentication and authorization;
- input validation and error handling;
- database migrations and stronger persistence infrastructure;
- automated testing coverage;
- application configuration by environment;
- domain-oriented data modeling;
- auditability and operational security.

## Future Direction

The long-term direction of Foster can evolve from a directory and establishment management system into a broader business platform.

A possible evolution path is:

~~~
Establishment Management
        │
        ▼
Users / Roles / Permissions
        │
        ▼
Customers / Suppliers / Products
        │
        ▼
Inventory / Purchases / Sales
        │
        ▼
Financial Management
        │
        ▼
Reports / Dashboards / Audit
~~~

This roadmap represents **future scope**, not functionality currently implemented in the repository.

## License

This project is distributed under the license included in the repository.
