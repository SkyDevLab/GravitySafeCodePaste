# Gravity Safe Code Paste 🛡️

**Paste freely. Share safely.**

Gravity Safe Code Paste is a client-side developer security utility that helps sanitize code, configuration, and SQL before sharing it with teammates, AI assistants, GitHub issues, forums, or other public/private channels.

## 🚀 Live Demo

https://skyrunner-dev-ops.github.io/GravitySafeCodePaste/

## ✨ What Gravity Does

Gravity looks for common sensitive information and replaces it with safer placeholders while keeping the surrounding code/configuration structure usable.

### Supported modes

- ☕ **Java**
- 🟦 **C#**
- 🐍 **Python**
- ⚙️ **Config** — JSON, appsettings-style configuration, `.env`, YAML and other key/value formats
- 🧩 **Other** — conservative fallback for mixed/unsupported code
- 🗄️ **SQL**

### Security-sensitive data

Depending on the input format, Gravity can detect patterns such as:

- API keys and access tokens
- Passwords and secrets
- JWT / bearer tokens
- Database connection strings
- Internal URLs and endpoints
- Local filesystem paths
- Cloud credentials and private key material
- Emails, IP addresses and other potentially sensitive values

### Optional identifier anonymization

Gravity also supports **Change identifiers** mode. When enabled, application-specific identifiers can be renamed consistently, for example:

```text
EmployeeAttendance      → AttendanceRecord
EmployeeAttendanceId    → AttendanceRecordId
ProjectManagement       → SampleProject
```

The feature is intentionally conservative so language keywords, standard-library names, and common framework APIs are not blindly renamed.

## 🔐 Privacy First

Gravity is designed as a browser-side utility. Your pasted text is processed locally by the web application rather than requiring a backend service for sanitization.

**Important:** Gravity uses heuristic/pattern-based detection. It is not a guarantee that every secret, proprietary value, or sensitive artifact will be detected. Always review the sanitized result before sharing it.

## 🧩 Project Structure

The sanitizer is designed around a modular architecture:

```text
GravitySafeCodePaste/
├── index.html
├── css/
│   └── styles.css
├── js/
│   ├── app.js
│   ├── sanitizer-utils.js
│   ├── replacement-map.js
│   ├── detector.js
│   ├── java.js
│   ├── csharp.js
│   ├── python.js
│   ├── config.js
│   ├── other.js
│   └── sql.js
└── assets/
    └── gravity-logo.png
```

Each language module can focus on syntax-aware extraction and sanitization while shared utilities handle common detection and replacement behavior.

## 🧪 Example

Input:

```text
"DefaultConnection": "Data Source=PROD-SQL-99;Database=CustomerPortal;User ID=portaladmin;Password=SuperSecret123;"
```

Sanitized output can become:

```text
"DefaultConnection": "Data Source=<DB_SERVER>;Database=<DATABASE>;User ID=<DB_USER>;Password=<REDACTED_PASSWORD>;"
```

The exact replacement depends on the active sanitizer and detection rules.

## 🛠️ Running Locally

Because the application is intended to be client-side, the project can be served as a static site.

For example:

```bash
git clone https://github.com/SkyDevLab/GravitySafeCodePaste.git
cd GravitySafeCodePaste
```

Then open `index.html` in a browser or serve the directory with any simple static HTTP server.

## 🌐 GitHub Pages

The project is published as a static GitHub Pages application.

Repository:

https://github.com/SkyDevLab/GravitySafeCodePaste

Live site:

https://skyrunner-dev-ops.github.io/GravitySafeCodePaste/

## 🤝 Contributing

Issues, feature ideas, detector improvements, language-specific edge cases, and UI improvements are welcome.

When proposing sanitizer changes, please include examples that use **different names and values from the existing demo data** so the rules stay generic rather than becoming tied to sample inputs.

## ⚠️ Disclaimer

Gravity Safe Code Paste is a developer convenience and privacy aid, not a replacement for a dedicated secrets scanner, DLP solution, secure code review, or organizational security controls.

Always review sanitized output before sharing sensitive code or configuration.

## 📄 License

Add the project's chosen license here when finalized.
