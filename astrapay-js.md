# AstraPay SDK for Node.js

> Lightweight Node.js SDK to integrate **M-Pesa STK Push** into your JavaScript applications easily.

---

## 🚀 Features

- ✅ Simple STK Push integration
- 🔐 Secure token generation
- ⚡ Fast and minimal, works with any Node.js backend
- 🧱 Supports RESTful workflows

---

## 📦 Installation

```bash
npm install astrapay
🧾 How to Get M-Pesa Credentials (Daraja Portal)
Go to Safaricom Daraja Portal

Create an account or log in

Create a new app under My Apps

Select MPesa Sandbox

After creating your app, you’ll get:

Consumer Key

Consumer Secret

Use the test credentials below for sandbox testing:

yaml
Copy
Edit
Shortcode: 174379
Passkey: bfb279f9aa9bdbcf158e97dd71a467cd2e0c893059b10f78e6b72ada1ed2c919
Callback URL: https://yourdomain.com/callback
🧑‍💻 Basic Usage
js
Copy
Edit
const AstraPay = require("astrapay");

const client = new AstraPay({
  consumerKey: "YOUR_CONSUMER_KEY",
  consumerSecret: "YOUR_CONSUMER_SECRET",
  shortcode: "174379",
  passkey: "YOUR_PASSKEY",
  callbackUrl: "https://yourdomain.com/callback"
});

client.pay({ phone: "254712345678", amount: 10 })
  .then(console.log)
  .catch(console.error);
⚙️ Example Response
json
Copy
Edit
{
  "MerchantRequestID": "12345-67890",
  "CheckoutRequestID": "ws_CO_XXXXXXXXXXXXX",
  "ResponseCode": "0",
  "ResponseDescription": "Success. Request accepted for processing",
  "CustomerMessage": "Success. Request accepted for processing"
}
📘 Notes
Use Safaricom’s test credentials for development

Switch to production credentials for live use

Handle STK callback data on your callbackUrl endpoint

🤝 Contributing
Pull requests are welcome. Please fork and open a PR.

📄 License
MIT License
© 2025 Astra Softwares

yaml
Copy
Edit

---

Would you like:
- A live hosted version of this README for npm?
- Or GitHub Actions to auto-publish when pushing to `main`?

Let me know, and I can prep those too.
