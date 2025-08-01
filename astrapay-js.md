# AstraPay JS SDK

A lightweight Node.js SDK for integrating M-Pesa STK Push payments with ease.

---

## 📦 Installation

```bash
npm install astrapay
```

---

## 🔑 Getting Your M-Pesa Credentials

1. Go to [Safaricom Daraja Portal](https://developer.safaricom.co.ke/).
2. Sign up and create a new application.
3. Generate the following:

   * **Consumer Key**
   * **Consumer Secret**
   * **Passkey**
   * **Business Shortcode** (usually 174379 for sandbox)
4. Set your **Callback URL** (your backend endpoint that Safaricom will notify).

---

## ✨ Basic Node.js Usage

```js
const AstraPay = require("astrapay");

const client = new AstraPay({
  consumerKey: "<YOUR_CONSUMER_KEY>",
  consumerSecret: "<YOUR_CONSUMER_SECRET>",
  shortcode: "174379",
  passkey: "<YOUR_PASSKEY>",
  callbackUrl: "https://yourdomain.com/callback"
});

client.pay({ phone: "254712345678", amount: 10 })
  .then(console.log)
  .catch(console.error);
```

---

## ⚙️ Backend Integration Examples

### Express (Node.js)

```js
const express = require("express");
const bodyParser = require("body-parser");
const AstraPay = require("astrapay");

const app = express();
app.use(bodyParser.json());

const client = new AstraPay({
  consumerKey: "<YOUR_CONSUMER_KEY>",
  consumerSecret: "<YOUR_CONSUMER_SECRET>",
  shortcode: "174379",
  passkey: "<YOUR_PASSKEY>",
  callbackUrl: "https://yourdomain.com/callback"
});

app.post("/api/pay", async (req, res) => {
  const { phone, amount } = req.body;
  const response = await client.pay({ phone, amount });
  res.json(response);
});

app.listen(5000, () => console.log("Server running on port 5000"));
```

---

### React / Vue / Next.js (Frontend)

> ⚠️ Do **NOT** use AstraPay directly in frontend apps. Instead, call a backend API.

```js
// React/Vue fetch example
fetch("http://localhost:5000/api/pay", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    phone: "254712345678",
    amount: 10
  })
})
  .then(res => res.json())
  .then(data => console.log(data));
```

---

---

## ✅ Supported Platforms

| Language / Framework | Support |
| -------------------- | ------- |
| Node.js / Express    | ✅       |
| React (via API)      | ✅       |
| Vue (via API)        | ✅       |
| Next.js (via API)    | ✅       |


---

## 📚 License

MIT — Made with ❤️ by [Astra Softwares](https://astrasoft.tech)
