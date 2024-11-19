# Environment Variables Guide

Securely manage sensitive information and environment-specific configurations.

## Best Practices

1. **Storage**
   - Use tools like [Doppler, AWS Secrets Manager, or Vault] to store secrets securely.
   - Environment files (`.env`) should NEVER be committed to the repository.

2. **Usage**
   - Local development:
     - Create a `.env.local` file:
       ```env
       DATABASE_URL=postgresql://user:password@localhost:5432/mydb
       API_KEY=your-api-key
       ```
     - Load variables using a library like `dotenv`:
       ```javascript
       require('dotenv').config();
       console.log(process.env.DATABASE_URL);
       ```

   - CI/CD:
     - Configure environment variables in your CI/CD tool.
     - Example for GitHub Actions:
       ```yaml
       env:
         DATABASE_URL: ${{ secrets.DATABASE_URL }}
       ```

3. **Security Tips**
   - Rotate secrets regularly.
   - Use read-only permissions wherever possible.
   - Audit `.env` files for unused variables.

4. **Common Variables**
   - `DATABASE_URL`: Connection string for the database.
   - `API_KEY`: API key for third-party integrations.
   - `NODE_ENV`: Set to `development`, `staging`, or `production`.

5. **References**
   - [dotenv Documentation](https://github.com/motdotla/dotenv)
   - [AWS Secrets Manager Guide](https://aws.amazon.com/secrets-manager/)

