# Discord API Wrapper for Panel
## API Link: To be added
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
