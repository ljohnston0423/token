# Agora Token Generation Server

This is a simple Express.js server that generates Agora tokens for video chat applications. It's designed to be deployed on Render.com.

## Features

- Generates Agora tokens with proper privileges
- CORS enabled for cross-origin requests
- Environment variable configuration
- Health check endpoint
- Error handling

## Setup

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   ```
3. Copy `.env.example` to `.env` and fill in your Agora credentials:
   ```bash
   cp .env.example .env
   ```
4. Update the `.env` file with your Agora App ID and Certificate

## Development

Run the server in development mode:
```bash
npm run dev
```

## Production

Start the server:
```bash
npm start
```

## API Endpoints

### Health Check
```
GET /health
```

### Generate Token
```
POST /token
Content-Type: application/json

{
  "channelName": "your_channel_name",
  "uid": "user_id"
}
```

Response:
```json
{
  "token": "generated_token",
  "appId": "your_app_id",
  "channelName": "your_channel_name",
  "uid": "user_id",
  "expiresAt": 1234567890
}
```

## Deployment on Render

1. Create a new Web Service on Render
2. Connect your GitHub repository
3. Configure the following:
   - Build Command: `npm install`
   - Start Command: `npm start`
4. Add the following environment variables:
   - `AGORA_APP_ID`
   - `AGORA_APP_CERTIFICATE`
   - `PORT` (optional, defaults to 3000)
   - `NODE_ENV` (optional, defaults to production)

## Security Considerations

- Never commit your `.env` file
- Keep your Agora credentials secure
- Use HTTPS in production
- Consider implementing rate limiting for the token endpoint
- Consider implementing authentication for the token endpoint

## License

MIT 