Security Practices
1. API Key Management
Store sensitive credentials (e.g., OPENAI_KEY) in .env files, excluded via .gitignore.
Replit users: Use Replit Secrets for environment variables, not plaintext .env files.
Rotate API keys immediately if exposed. See Troubleshooting for guidance.
2. Dependency Management
Dependencies (Next.js, Node.js, Python libraries) are scanned for vulnerabilities using GitHub Dependabot.
Update dependencies:
npm update
pip install --upgrade -r requirements.txt
Monitor GitHub Security Advisories for critical updates.
3. Code Contributions
Pull requests (PRs) must:
Pass automated tests (see CI/CD Pipeline).
Be reviewed by at least one maintainer.
Avoid hardcoded secrets or sensitive data.
Branch protection rules enforce PR reviews on the main branch.
4. AI and API Security
AI Diagnostics API (/api/ai/diagnose):
Uses rate-limiting to prevent abuse (max 100 requests/min).
Validates OBD-II codes to prevent injection attacks (e.g., regex: ^P[0-9]{4}$).
Employs JWT-based authentication for API access.
NLP Chatbot:
Sanitizes user inputs to mitigate prompt injection attacks (e.g., using sanitize-html for React inputs).
Limits response length to prevent resource exhaustion.
Inventory Forecasting:
Encrypts API keys for third-party services (e.g., AutoZone API) using AES-256.
Validates API responses to prevent malformed data exploits.
AI models are hosted on secure endpoints (HTTPS) and monitored for anomalous behavior.
5. Replit Deployment
Restrict public access to sensitive endpoints in Replit’s deployment settings.
Use Replit Secrets for environment variables.
Audit project permissions regularly to prevent unauthorized access.
6. Data Privacy
Customer data in the Customer Portal is encrypted in transit (HTTPS) and at rest (if applicable).
Avoid logging sensitive data (e.g., OBD-II codes, customer details) in console outputs or public logs.
Known Security Considerations
OBD-II Diagnostics: AI model accuracy is 85%. Verify AI suggestions manually to avoid safety risks.
Inventory Forecasting: Ensure third-party APIs (e.g., AutoZone) comply with their security policies.
NLP Chatbot: Continuous monitoring for prompt injection vulnerabilities is required.
Disclosure Policy
We follow a 90-day disclosure timeline after validating and fixing vulnerabilities.
Public disclosure includes:
Issue summary.
Affected versions and components.
Mitigation or patch details.
Coordinated disclosure ensures proper credit for reporters
