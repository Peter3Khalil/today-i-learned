# Manage multiple environments

## Example

You will define different variables for each environment by creating these `.env` files.

`.env.development` (For local development):

```bash
NEXT_PUBLIC_API_URL=http://localhost:3000/api
NEXT_PUBLIC_APP_MODE=development
```

`.env.production` (For production):

```bash
NEXT_PUBLIC_API_URL=https://api.example.com
NEXT_PUBLIC_APP_MODE=production
```

`.env.staging` (For staging):

```bash
NEXT_PUBLIC_API_URL=https://staging-api.example.com
NEXT_PUBLIC_APP_MODE=staging
```

`.env.test` (For testing):

```bash
NEXT_PUBLIC_API_URL=http://localhost:3000/test/api
NEXT_PUBLIC_APP_MODE=test
```

You can then run your app with the following command:

```bash
# For local development
$ next dev

# For production
$ next start

# For staging
$ next start -p 3001

# For testing
$ next test
```
