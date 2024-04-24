<h1 align='center'>Chess</h1>

## Table of contents

- [Prerequisites](#prerequisites)
- [Setup](#setup)
  - [Using Docker](#using-docker)
  - [Without Docker](#without-docker)
- [Contributing](#contributing)

## Prerequisites

Before you begin, ensure you have met the following requirements

- Node.js and npm installed on your machine.
- Docker and docker-compose installed (optional, required for Docker setup).
- Access to a PostgreSQL database (can be local or hosted).
- Google OAuth Client Credentials

## Setup

### Using Docker

1. Clone the repository:
   ```bash
   git clone https://github.com/code100x/chess.git
   ```
2. Navigate to the project directory:
   ```bash
   cd chess
   ```
3. Copy the `.env.example` in
   `/apps/frontend`
   `/apps/backend`
   `/packages/db`
   to `.env` in the same directory
4. Replace the Google Client ID and Secret in the `/apps/backend/.env` file.
5. Update the DatabaseURL in the `/packages/db/.env`
    ```bash
   DATABASE_URL="postgresql://postgres:chess100x@172.20.0.8:5432/chess100x"
    ```
6. Run the following command in the root dir to launch all the services:
   ```bash
   docker-compose up
   ```

### Without Docker

1. clone the repository:
   ```bash
   git clone https://github.com/code100x/chess.git
   ```
2. Navigate to the project directory:
   ```bash
   cd chess
   ```
3. `Either`\
   Start a PostgreSQL database using Docker:
   ```bash
   docker run -d \
       --name chess100x \
       -e POSTGRES_USER=postgres \
       -e POSTGRES_PASSWORD=chess100x \
       -e POSTGRES_DB=chess100x \
       -p 5432:5432 \
       postgres
   ```
   based on this command the connection url will be
   ```
   DATABASE_URL=postgresql://postgres:chess100x@localhost:5432/chess100x?schema=public
   ```
   `Or`\
   Get a PostgreSQL any cloud provider. \
   Update the `DATABASE_URL` in the `/packages/db/.env.example`.
4. Copy the `.env.example` in
   `/apps/frontend`
   `/apps/backend`
   `/packages/db`
   to `.env` in the same directory
5. Replace the Google Client ID and Secret in the `/apps/backend/.env` file.
6. Install dependencies in the root dir:
   ```bash
   yarn install
   ```
7. Run database init in the `/packages/db` folder:
   ```bash
   yarn run db:dev
   ```
8. Start the development server in the root dir:
   ```bash
   yarn run dev
   ```
   
## Contributing

We welcome contributions from the community! To contribute to Chess, follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/fooBar`).
3. Make your changes and commit them (`git commit -am 'Add some fooBar'`).
4. Push to the branch (`git push origin feature/fooBar`).
5. Create a new Pull Request.
