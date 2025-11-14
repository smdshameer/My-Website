# Install Security Packages

After applying the security fixes, you need to install the new dependencies.

## Installation Steps

1. **Navigate to the project root:**
   ```bash
   cd "E:\Billing Website"
   ```

2. **Install new dependencies:**
   ```bash
   npm install
   ```

   This will install:
   - `express-rate-limit` - For rate limiting
   - `xss` - For XSS protection
   - `express-validator` - For additional validation (optional)

3. **Verify installation:**
   ```bash
   npm list express-rate-limit xss
   ```

## What Was Fixed

See `SECURITY_FIXES.md` for complete details of all security vulnerabilities that were fixed.

## Important Notes

- The TypeScript errors about `express-rate-limit` will be resolved after running `npm install`
- Make sure to update your `.env` file with secure JWT secrets
- Test the application after installation to ensure everything works

