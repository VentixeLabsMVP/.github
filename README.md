# .github
> ⚠️ **Note:** Currently, the email is hardcoded (line 59 in `VerificationProvider`). This can be changed to use the actual user's email.
# 🎟️ Event Platform MVP – Based on Figma Design

A functioning prototype of an event website based on a Figma design. The goal is to implement the core features of an event platform for both administrators and users.

---

## ✨ Features

- Full CRUD operations for events (Create, Read, Update, Delete)  
- JWT authentication via an external Auth API  
- User registration and login flow  
- Email verification using Azure Communication Services  
- Admin-style dashboard for event management  
- Alpha-stage user flow for ticket booking

---

## 🔐 Authentication & Email Flow

1. When trying to **book an event**, the user must have a valid **JWT token**  
2. If the token is missing → user is redirected to the **Login page**  
3. From the Login page, the user can:
   - Log in with an existing account, **or**
   - Register a new account via the **Register page**

### 👤 Account Registration

- The `AccountService` uses **Microsoft Identity** to register the user  
- The `EmailConfirmed` flag is initially set to `false`  
- The service sends a request to the **Verification API** → which then calls the **Azure email service** to send a verification code  
> ⚠️ **Note:** Currently, the email is hardcoded (line 59 in `VerificationProvider`). This can be changed to use the actual user's email.

---

## ✅ Verification Flow

- After registration, the user is redirected to the **Verification Page**  
- They enter the received code  
- If valid, the code is verified via the Verification API  
- The user's `EmailConfirmed` is set to `true`  
- User is redirected to **Login**  
- On successful login, the system returns a **JWT token**  
- The token is required to **book an event**

---

## 🚫 MVP Limitations

- Ticket reservations **cannot be deleted** in this version  
- Users can **only create bookings**, not view or cancel them

---
## 🔮 Next Steps (Post-MVP Ideas)

- Add a **"My Tickets"** page showing reserved tickets  
- Allow users to **cancel bookings**  
- Option to **send ticket to email**  
- Send **confirmation emails** after booking


