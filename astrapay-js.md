# AstraPay SDK for Node.js

> Lightweight Node.js SDK to integrate **M-Pesa STK Push** into your JavaScript applications.

---

## 🚀 Features

* ✅ Easy M-Pesa STK Push integration
* 🔐 Secure access token generation
* 🧱 Works with any Node.js backend
* 💼 Built for developers in Kenya & beyond

---

## 📆 Installation

```bash
npm install astrapay
```

---

## 🔐 Getting Your M-Pesa Daraja Credentials

1. Visit the [Safaricom Daraja Portal](https://developer.safaricom.co.ke)
2. Create an account or log in
3. Click on **My Apps** → **Add a New App**
4. Select the product **MPesa Sandbox**
5. You'll receive:

   * **Consumer Key**
   * **Consumer Secret**

You’ll also use these **sandbox details**:

* **Shortcode**: `174379`
* **Passkey**:
  `bfb279f9aa9bdbcf158e97dd71a467cd2e0c893059b10f78e6b72ada1ed2c919`
* **Callback URL**: Your webhook endpoint, e.g., `https://yourdomain.com/callback`

---

## 💡 Usage Example

```js
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
```

---

## ✅ Example Successful Response

```json
{
  "MerchantRequestID": "c9aa-485e-a88a-be3f936aa2bc28590",
  "CheckoutRequestID": "ws_CO_010820252054230712345678",
  "ResponseCode": "0",
  "ResponseDescription": "Success. Request accepted for processing",
  "CustomerMessage": "Success. Request accepted for processing"
}
```

---

## 📨 Callback Handling

Safaricom will send payment status updates to your `callbackUrl`. Make sure it accepts POST requests and can log/store transaction responses for verification.

---

## 🤝 Contributing

We welcome contributions!

1. Fork the repo
2. Create your feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Open a Pull Request

---

## 📄 License

MIT License © 2025 [Astra Softwares](https://astrasoft.tech)
