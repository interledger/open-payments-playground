# Open Payments Express App

A lightweight application to show the Open Payments API functions.

## Requirements

Before you begin, you need to install the following tools:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Node (>= v18.18)](https://nodejs.org/en/download/)
- [Git](https://git-scm.com/downloads)

## 🚀 Quickstart

### 1. Clone the repository

Open `Visual Studio Code` and open a `terminal` in your Visual Studio Code. Then run this command below:

```bash
git clone https://github.com/FinHubSA/open-payments-express.git
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Setup `.env` file

- Follow this tutorial to setup your [test wallet](https://openpayments.dev/sdk/before-you-begin/)
- Create a new `.env` file, right next to the `.env.example` and copy all code from `.env.example` to `.env`.
- Copy key ID and the wallet address into the `.env` file.
- Put the private key in the root folder i.e. open-payments-express/private.key.
  > Note: The private key file was saved and generated automatically when you created `Developer Keys` for your wallet address.

### 4. Start the Server

```bash
# Development mode with auto-restart
npm run dev
```
This command does two things:
- Runs `tsx scripts/generate-schemas.ts`, which generates the latest schemas and TypeScript types from the definitions in `openapi`. It puts these files in the `public/schemas` folder and the `types` folder respectively.
- Starts the development server with `tsx watch`, so changes to `.ts` files auto-restart the server.

The server will start on `http://localhost:3001`

## 📂 Project Structure

```
├── openapi/ # JSON Schemas for the different servers
│ ├── auth-server.json # Auth server schema
│ ├── resource-server.json # Resource server schema
│ └── wallet-address-server.json # Wallet address server schema
│ 
├── scripts/ # Build scripts for generating artifacts
│ ├── generate-schemas.js # Generates TypeScript types and individual schemas to make for API call fields
│ 
├── services/ # Service layer for making Open Payments requests
│ └── open-payments.ts
│ |
├── types/ # Generated types from the generate-schemas.js build script
| |  ├── access-incoming.d.ts
| |  ├── access-outgoing.d.ts
| |  └── ...
| 
├── public/ # Frontend demo
│ ├── schemas # Generated schemas from the generate-schemas.js build script
| |  ├── access-incoming.json
| |  ├── access-outgoing.json
| |  └── ...
| |
│ ├── lib # javascript libraries for the UI
| |  ├── json-text-editor.min.js # for the <andypf-json-viewer/> element which displays json responses
| |  └── json-ui-editor.min.js # for rendering the html forms from the public/schemas folder
| |
│ ├── script.js # The logc for rendering forms, submitting, forms and request history
│ └── style.css # The styling
| |
├── index.html # The main UI file for displaying the frontend
└── ... # Other files for the project
```
