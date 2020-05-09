# Discord API Wrapper for Panel
## API Link: <a href="https://discord-api.auto-deploy.dev/">https://discord-api.auto-deploy.dev/</a>

**Watch this Demo:**
[![Watch the video](https://img.youtube.com/vi/1EsX1kEK52s/0.jpg)](https://www.youtube.com/watch?v=1EsX1kEK52s)

### DISCLAIMER
- This API has no connection with the original Discord Company.
- This API just serves as a wrapper, and does not store sensitive personal information or secrets of the OAUTH. 
- We only store your `access_token` and at any time you may Email me at <a href="mailto:igadget28@gmail.com">igadget28@gmail.com</a> or contact me on Discord 𝑰𝑮#1337 to get it removed or exported. 
- This API extends Flask (A Python Framework)
- <b>Please ensure that your POST `Content-Type` is set to "application/json".</b>
---

> POST /login
- The POST parameters needed are as below. 
- `redirect_uri` is where you would like to catch the auth code emitted from Discord and POST it into the API.
- You may read the return types of this API <a href="https://discord.com/developers/docs/topics/oauth2" target="_blank">here</a>.
- <b>NOTE</b>: <br> This POST step is only once. Upon sending the POST request. This API will provide you with an unique `token` as an exchange to easily use another API. You may have request for a new `token` if your token is invalidated or expired. 
```json
{
    "grant_type": "authorization_code",
    "client_id": "YOUR_CLIENT_ID",
    "client_secret": "YOUR_CLIENT_SECRET",
    "redirect_uri": "YOUR_REDIRECT_URI",
    "code": "YOUR_CODE",
    "scope": "YOUR SCOPES"
}
```
> RETURN FOR /login
```
{
  "access_token": "ACCESS_TOKEN_FROM_DISCORD",
  "message": "Token has been generated",
  "token": "YOUR_UNIQUE_TOKEN" // Do not give anyone
}
```

---

> POST /user
- The POST parameters needed are as below. 
- You only need to pass the `token` into the POST Parameter from the `/login` endpoint.
- You may read the return types <a href="https://discord.com/developers/docs/resources/user#get-current-user" target="_blank">here</a>.
```json
{
	"token": "YOUR_UNIQUE_TOKEN"
}
```
> RETURN FOR /user
```
// These data are from Discord itself
{
  "avatar": "AVATAR",
  "discriminator": "#1337",
  "email": "EMAIL", // This depends on scope
  "flags": 0,
  "id": "YOUR_ID",
  "locale": "en-US",
  "mfa_enabled": true,
  "premium_type": 2,
  "public_flags": 128,
  "username": "𝑰𝑮",
  "verified": true
}
```

---

> POST /guilds
- The POST parameters needed are as below. 
- You only need to pass the `token` into the POST Parameter from the `/login` endpoint.
- You may read the return types <a href="https://discord.com/developers/docs/resources/user#get-current-user-guilds" target="_blank">here</a>.
```json
{
	"token": "YOUR_UNIQUE_TOKEN"
}
```
> RETURN FOR /guilds
```
{
    "total": 100, // This parameter is custom, this helps you count the amount of Guilds. 
    "guilds": [] // Array of JSON Objects
}
```

---

> POST /guilds/mine
- The POST parameters needed are as below. 
- This endpoint ONLY returns your Guilds!
- You only need to pass the `token` into the POST Parameter from the `/login` endpoint.
- You may read the return types <a href="https://discord.com/developers/docs/resources/user#get-current-user-guilds" target="_blank">here</a>.
```json
{
	"token": "YOUR_UNIQUE_TOKEN"
}
```
> RETURN FOR /guilds/mine
```
{
    "total": 100, // This parameter is custom, this helps you count the amount of Guilds. 
    "guilds": [] // Array of JSON Objects
}
```

### Status Codes
- These are modified status codes. You may read more about the status from Discord <a href="https://discord.com/developers/docs/topics/opcodes-and-status-codes" target="_blank">here</a>.

|  Code |  Message |
| ------------ | ------------ |
| 200 | All Ok |
| 400 | BAD REQUEST: The request was improperly formatted, or the server couldn't understand it. Your token has been invalidated. |
| 401 | UNAUTHORIZED: Your access token is invalid. Please request a new one with /login. Your token has been invalidated. |
| 403 | FORBIDDEN: The access token provided has no access to this resource. Your token has been invalidated.  |
| 404 | NOT FOUND: The requested endpoint is not found. Your token has been invalidated. |
| 405 | METHOD NOT ALLOWED: The requested endpoint does not allow this action. Your token has been invalidated.  |
| 429 | TOO MANY REQUESTS: Your access token is being rate limited by Discord. Try again in a bit. Your token has been invalidated. |
| 500 | INTERNAL ERROR: An internal error has occurred. Please make an issue on GitHub or contact on Discord. Your token has been invalidated. |
| 502 | GATEWAY UNAVAILABLE: Discord Gateway APIs are dead. Your token has been invalidated. |
