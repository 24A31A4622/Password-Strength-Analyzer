# Password Strength Analyzer – Cybersecurity UI

This is a real-time password strength analyzer built with React and Vite, designed with a hacker-style cybersecurity dashboard interface. It helps users understand how strong their passwords are and how to improve them.

## 🔐 What this tool does

- Analyzes the strength of a password as you type (Very Weak → Very Strong).
- Evaluates:
  - Length (short vs. long, passphrase-style passwords).
  - Character diversity (lowercase, uppercase, digits, symbols).
  - Some very common weak passwords (like `password`, `123456`, `qwerty`).
- Shows a **security status**:
  - `STATUS: AT RISK`
  - `STATUS: NEEDS IMPROVEMENT`
  - `STATUS: SECURE`
- Provides **human-readable recommendations** to make the password harder to guess.

The rules are inspired by common password security guidance (OWASP / NIST), which emphasize sufficient length and avoiding common/guessable passwords.

> Note: This is a **front-end analyzer** for education and UX. Real applications must also enforce password rules and use secure hashing (bcrypt/Argon2) on the 

## 🧠 Why this is useful

Weak passwords are still a major cause of account compromise.  
This project aims to:

- Teach users what makes a password stronger in a simple, visual way.
- Encourage:
  - Longer passwords (12+ characters preferred).
  - Diversity of character types.
  - Avoiding reuse of the same password across services.
- Provide a **cybersecurity-themed interface** that feels like a real security tool, not just a plain form.

This can be integrated later into login/signup flows to nudge users towards safer passwords, as recommended by password policy best practices.

## 🛠 Tech Stack

- **Frontend**: React + Vite
- **Styling**: Custom CSS (dark, hacker-style UI)
- **Language**: JavaScript (ES6+)

No backend is included yet. In the future, a Node.js/Express backend can be added to handle secure password storage and history checks.

## 🚀 Getting started (local setup)

1. Clone or download the project.
2. Install dependencies:

```bash
npm install
```

3. Start the dev server:

```bash
npm run dev
```

4. Open the URL shown in the terminal (usually `http://localhost:5173/`).

You’ll see the **Password Analyzer Console** with:

- Input field + eye icon to show/hide password.
- Strength, score, and status.
- Animated logs and security hints.

## 📏 How strength is calculated

The scoring logic works roughly like this

- +1 if length ≥ 8 characters  
- +1 extra if length ≥ 12 characters  
- +1 if password includes both lowercase and uppercase letters  
- +1 if it includes at least one digit  
- +1 if it includes at least one symbol  
- If the password is in a small list of **very common passwords**, score is forced to Very Weak

So:

- Score 0–1 → Very Weak  
- Score 2 → Weak  
- Score 3 → Medium  
- Score 4 → Strong  
- Score 5 → Very Strong  

This matches many simple password-checker implementations that consider length and diversity as core factors.[web:75][web:70][web:73]

## 🔭 Planned backend & improvements

Planned future work:

- **Backend (Node.js / Express)**:
  - Store only hashed passwords (bcrypt/Argon2) instead of plain text.[web:19]
  - Maintain password history to prevent reuse of old passwords (password history policy).[web:62]
- **Stronger analysis**:
  - Check against larger common-password lists.
  - Estimate approximate “time to crack” based on strength.
- **Deployment**:
  - Host the frontend using GitHub Pages, Netlify, or similar so anyone can use the tool from a public URL.

This project is part of a broader journey into **secure, user-friendly applications**, combining frontend engineering with practical cybersecurity principles.
