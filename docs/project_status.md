# Thoughtless - Project Status

## User Preferences
- **Voice Input:** Primary input method when available
- **Concise Output:** ~6 lines max for web interfaces due to screen zoom
- **Command Execution:** Use "run command" button, no direct terminal access
- **File Operations:** Provide complete file replacements, not partial edits

## Project Overview
**Thoughtless** enables users of multiple AI chatbots to contribute conversations to a central Firestore database for public display. Core purpose: demonstrate AI is for meaningful dialogue, not information search.

**User Roles:** Public (view), Supporters (view+comment), Contributors (create+contribute), Admin (manage users)

## Current Architecture ✅
- **Firebase Project:** `thoughtlessdatalayer`
- **API Endpoint:** `https://thoughtlessapi-m646gpqtna-uc.a.run.app`
- **Backend:** Modular Express.js on Firebase Functions
- **Security:** Firebase Auth + encrypted credential storage
- **Gemini Integration:** OAuth2 authentication working ✅

## File Structure
```
backend/functions/
├── index.js              # Main router (25 lines)
├── routes/
│   ├── database.js       # Database operations (~300 lines)
│   └── chatbots.js       # Chatbot + OAuth2 endpoints (~260 lines)
└── adaptors/
    └── gemini.js         # Gemini OAuth2 integration ✅

frontend/
├── public/
└── components/
    └── gemini-oauth.js   # OAuth2 UI component ✅
```

## Working API Endpoints
**Base URL:** `https://thoughtlessapi-m646gpqtna-uc.a.run.app`

**Database:** `/createChat`, `/updateChat/:chatId`, `/addMessage`, `/getChatList`, `/getChat/:chatId`
**Auth:** `/health`, `/user-status`, `/setup-profile`, `/store-keys`  
**OAuth2:** `/oauth/config`, `/oauth/callback`, `/oauth/status`

## Data Structure
```javascript
// Chat: {id, title, provider, model, contributorId, metadata, timestamps}
// Message: {id, role, content, metadata, timestamp}
// User: {uid, email, displayName, role, timestamps}
// Credentials: {uid, encryptedKeys, oauthTokens, updatedAt}
```

## Immediate Next Steps
1. **Test OAuth2 Flow:** Deploy test HTML page to Firebase Hosting
2. **Add Claude Adapter:** Create adaptors/claude.js  
3. **Frontend Integration:** Connect components to web/mobile apps

## Development Status
- ✅ **Deployed:** Backend API fully functional
- ✅ **Gemini:** OAuth2 integration complete
- ⏳ **Testing:** OAuth2 flow verification needed
- ⏳ **Claude:** Adapter pending
- ⏳ **Frontend:** Integration pending

Last Updated: 2025-08-17