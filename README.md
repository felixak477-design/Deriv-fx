# Deriv Hedge Lab — demo-first starter

A browser prototype using the Deriv legacy WebSocket endpoint to stream ticks/balance, request live Rise/Fall proposals, buy contracts, and subscribe to contract status.

## Run
Requires Node.js 18+.

```sh
npm install
npm run dev
```

Open the Vite URL shown in your terminal. Use `npm run build` to make a production build.

## Connect safely
1. Create/use a Deriv demo account.
2. Generate a demo API token with only the required read and trade permissions.
3. Keep **Demo-only** checked, enter the App ID and token, then Connect.
4. Confirm the login ID is a demo account (normally starts `VRTC`).
5. Wait for enough ticks, request quotes, then test manually.

The default App ID `1089` is a public testing ID and may not be suitable for a deployed app. Register your own Deriv application/App ID for production.

## Important limitations
- The signal is a simple transparent trend/tick heuristic, not trained AI and not a reliable prediction.
- Two opposite contracts do not guarantee profit. Both stakes can be lost, and entry/expiry prices differ.
- The pair button sends two buy requests sequentially, not atomically. Network/API failure can leave one leg open.
- Session realized loss/profit limits prevent new trades but do not close open contracts; emergency stop also does not close them.
- The prototype accepts a personal token directly in the browser. Never publish the token, commit it, or collect users' tokens. For a public multi-user app, replace this with Deriv OAuth 2.0 and a secure backend. Do not put client secrets in frontend code.
- Verify all API payloads against the current official Deriv docs and test thoroughly before any real-money use.

Official docs: https://developers.deriv.com/docs/intro/api-overview/ and https://developers.deriv.com/docs/trading/buy/
