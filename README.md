# HTTPS on localhost dev NUXT 3
HTTPS on localhost dev - NUXT 3

1. Go to project main dir (frontend/);
2. Create private and public key;
```bash
openssl genrsa 2048 > localhost.key
chmod 400 localhost.key
openssl req -new -x509 -nodes -sha256 -days 365 -key localhost.key -out localhost.crt
```
3. Import localhost.crt into the Mac Keychain ("File" > "Import Items");
4. Add to package.json "devhttps":
```bash
"scripts": {
    "dev": "nuxt dev",
    "devhttps": "nuxt dev --https --ssl-cert localhost.crt --ssl-key localhost.key",
    "build": "nuxt build",
    "start": "node .output/server/index.mjs",
    "test": "vitest",
    "generate": "nuxt generate",
    "typecheck": "nuxt typecheck"
  },
```
5. Run in the terminal: npm run devhttps;
