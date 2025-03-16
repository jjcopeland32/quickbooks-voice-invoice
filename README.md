# QuickBooks Voice-to-Invoice Tool

A web application that allows users to create invoices in QuickBooks using voice commands.

## Features

- 🔐 **User Authentication**: Secure login/register system
- 🔄 **QuickBooks OAuth Integration**: Connect your QuickBooks account seamlessly
- 🎙️ **Voice Recognition**: Create invoices using natural language
- 📱 **Responsive Design**: Works on desktop and mobile devices
- 🔒 **Secure API Communication**: Built with robust error handling

## Tech Stack

- **Frontend**: HTML, CSS, JavaScript
- **Backend**: Node.js, Express
- **Database**: MongoDB
- **Authentication**: JWT (JSON Web Tokens)
- **QuickBooks Integration**: Intuit OAuth 2.0
- **Voice Recognition**: Web Speech API

## Project Structure

```
.
├── backend/                 # Backend Node.js application
│   ├── src/                 # Source code
│   │   ├── app.js           # Main application file
│   │   ├── server.js        # Server configuration
│   │   ├── config/          # Configuration files
│   │   ├── controllers/     # Request handlers
│   │   ├── middleware/      # Middleware functions
│   │   ├── models/          # MongoDB models
│   │   └── routes/          # API routes
│   ├── .env                 # Environment variables (not included in repo)
│   └── package.json         # Dependencies
├── frontend/                # Frontend web application
│   ├── css/                 # Stylesheets
│   ├── js/                  # JavaScript files
│   │   ├── config.js        # Frontend configuration
│   │   ├── auth.js          # Authentication module
│   │   └── app.js           # Main application logic
│   ├── assets/              # Images and icons
│   └── index.html           # Main HTML file
└── API_ERROR_HANDLING.md    # Documentation for API error handling
```

## Setup Instructions

### Prerequisites

- Node.js (v14 or higher)
- MongoDB
- QuickBooks Developer Account

### Installation

1. Clone the repository:
   ```
   git clone https://github.com/jjcopeland32/quickbooks-voice-invoice.git
   cd quickbooks-voice-invoice
   ```

2. Install dependencies:
   ```
   # Backend dependencies
   cd backend
   npm install
   
   # Frontend dependencies (if using any build tools)
   cd ../frontend
   npm install
   ```

3. Create a `.env` file in the backend directory with the following variables:
   ```
   PORT=8081
   MONGODB_URI=mongodb://localhost:27017/quickbooks-voice-tool
   JWT_SECRET=your_jwt_secret_key_here
   JWT_EXPIRY=24h
   QUICKBOOKS_CLIENT_ID=your_quickbooks_client_id_here
   QUICKBOOKS_CLIENT_SECRET=your_quickbooks_client_secret_here
   QUICKBOOKS_REDIRECT_URI=http://localhost:8081/auth/qbo/callback
   ENCRYPTION_KEY=32_char_hex_encryption_key_for_tokens
   ```

4. Start the development server:
   ```
   # From the backend directory
   npm run dev
   ```

5. Open your browser and navigate to `http://localhost:8081`

### QuickBooks Developer Setup

1. Create a developer account at [Intuit Developer](https://developer.intuit.com/)
2. Create a new app
3. Set the redirect URI to `http://localhost:8081/auth/qbo/callback`
4. Copy the Client ID and Client Secret to your `.env` file

## Usage

1. Register a new account or login
2. Connect your QuickBooks account
3. Click the microphone button on the dashboard
4. Speak your invoice details (e.g., "Create an invoice for John Doe for 2 hours of consulting at $150 per hour")
5. Review and confirm the invoice details
6. The invoice will be created in your QuickBooks account

## API Documentation

The application provides the following main endpoints:

### Authentication

- `POST /api/auth/register` - Register a new user
- `POST /api/auth/login` - Log in an existing user
- `GET /api/auth/me` - Get current user profile
- `GET /api/auth/profile` - Get detailed user profile
- `POST /api/auth/logout` - Log out user

### QuickBooks Integration

- `GET /auth/qbo` - Initiate QuickBooks OAuth flow
- `GET /auth/qbo/callback` - Handle QuickBooks OAuth callback

### Invoices

- `POST /api/invoices` - Create a new invoice
- `GET /api/invoices` - Get list of invoices

## Error Handling

The application has robust error handling for both frontend and backend. See [API_ERROR_HANDLING.md](./API_ERROR_HANDLING.md) for details on how errors are handled.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- [Intuit Developer](https://developer.intuit.com/) for the QuickBooks API
- [Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API) for voice recognition