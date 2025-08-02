# AstraPay SDK - Multi-language Integration

AstraPay is a lightweight SDK that allows developers to integrate **M-Pesa STK Push** into their applications with minimal effort. It supports multiple languages and frameworks including **Node.js**, **Python**, **Flask**, **Django**, **React**, **Vue**, **Next.js**, and **PHP**.

---

## 🚀 Installation

### Javascript & frameworks

```bash
npm install astrapay
```

### Python & frameworks

```bash
pip install astrapay
```

### PHP & frameworks

```bash
composer require astrasoftwares/astrapay
```

---

## 🔐 Getting Your M-Pesa Credentials

1. Visit the [Safaricom Daraja Portal](https://developer.safaricom.co.ke/).
2. Register or log in.
3. Create a new app to get:

   * **Consumer Key**
   * **Consumer Secret**
   * **Passkey**
   * **Business Shortcode** (e.g., `174379` for sandbox)
4. Define a **Callback URL** — this is the endpoint Safaricom will notify with payment status.

📌 **Best Practice:**
Store credentials in a `.env` file and use environment variables to load them safely:

```env
MPESA_CONSUMER_KEY=xxx
MPESA_CONSUMER_SECRET=xxx
MPESA_PASSKEY=xxx
MPESA_SHORTCODE=174379
MPESA_CALLBACK_URL=https://yourdomain.com/callback
```

---

## 🧪 Code Examples

### 🟦 Node.js (Basic)

```js
const AstraPay = require("astrapay");

const client = new AstraPay({
  consumerKey: process.env.MPESA_CONSUMER_KEY,
  consumerSecret: process.env.MPESA_CONSUMER_SECRET,
  shortcode: process.env.MPESA_SHORTCODE,
  passkey: process.env.MPESA_PASSKEY,
  callbackUrl: process.env.MPESA_CALLBACK_URL
});

client.pay({ phone: "254712345678", amount: 10 })
  .then(console.log)
  .catch(console.error);
```

### 🌐 Express.js API

```js
app.post("/api/pay", async (req, res) => {
  const { phone, amount } = req.body;
  const response = await client.pay({ phone, amount });
  res.json(response);
});
```

### 🐍 Python

```python
from astrapay import AstraMpesa

client = AstraMpesa(
  consumer_key=os.getenv("MPESA_CONSUMER_KEY"),
  consumer_secret=os.getenv("MPESA_CONSUMER_SECRET"),
  shortcode=os.getenv("MPESA_SHORTCODE"),
  passkey=os.getenv("MPESA_PASSKEY"),
  callback_url=os.getenv("MPESA_CALLBACK_URL")
)

res = client.pay(phone="254712345678", amount=10)
print(res)
```

### 🧠 Flask

```python
@app.route("/pay", methods=["POST"])
def pay():
    phone = request.json.get("phone")
    amount = request.json.get("amount")
    res = client.pay(phone, amount)
    return jsonify(res)
```

### 🧠 Django

```python
def pay_view(request):
    phone = request.POST.get("phone")
    amount = request.POST.get("amount")
    res = client.pay(phone, amount)
    return JsonResponse(res)
```

### 🐘 PHP

```php
require 'vendor/autoload.php';

use Astrapay\AstraMpesa;

$client = new AstraMpesa([
  'consumerKey' => getenv('MPESA_CONSUMER_KEY'),
  'consumerSecret' => getenv('MPESA_CONSUMER_SECRET'),
  'shortcode' => getenv('MPESA_SHORTCODE'),
  'passkey' => getenv('MPESA_PASSKEY'),
  'callbackUrl' => getenv('MPESA_CALLBACK_URL')
]);

$response = $client->pay('254712345678', 10);
print_r($response);
```

### ⚛️ React / Vue / Next.js

> Never expose your credentials in frontend. Use a backend endpoint:

```js
fetch("/api/pay", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ phone: "254712345678", amount: 10 })
})
  .then(res => res.json())
  .then(console.log);
```

---

## 📚 Documentation

### 📘 Python Documentation

[View Python Docs →](https://github.com/astrasoftwares/astrapay/blob/main/Astrapay-python.md)

### 📗 JavaScript Documentation

[View JavaScript Docs →](https://github.com/astrasoftwares/astrapay/blob/main/astrapay-js.md)

### 📙 PHP Documentation

[View PHP Docs →](https://github.com/astrasoftwares/astrapay/blob/main/astrapay-php.md)

---

## 🧩 Supported Platforms

| Language / Framework | Supported |
| -------------------- | --------- |
| Node.js              | ✅         |
| Express.js           | ✅         |
| Python               | ✅         |
| Flask                | ✅         |
| Django               | ✅         |
| React (via API)      | ✅         |
| Vue (via API)        | ✅         |
| Next.js (via API)    | ✅         |
| PHP                  | ✅         |
| Laravel                  | ✅     |

---

## 📄 License

MIT — Made with ❤️ by [Astra Softwares](https://astrasoft.tech)
