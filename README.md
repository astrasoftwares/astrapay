# AstraPay SDK

![AstraPay Logo](https://yourdomain.com/logo.png)

[![PyPI version](https://img.shields.io/pypi/v/astrapay.svg)](https://pypi.org/project/astrapay/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**A lightweight Python SDK for integrating M-Pesa STK Push payments**
Built with ❤️ by [Astra Softwares](https://www.astrasoft.tech)

---

## ⚡ Features

* ✅ M-Pesa STK Push made easy
* 🔐 Handles OAuth token generation
* 🌐 Works with Flask, Django, or any framework
* 🧩 No database dependency
* 🔁 Callback URL support
* 🛠️ Developer-first design

---

## 📦 Installation

```bash
pip install astrapay
```

---

## 🧾 Getting Your M-Pesa API Credentials

To use AstraPay, you need API credentials from Safaricom’s [Daraja Portal](https://developer.safaricom.co.ke/daraja).

### Steps to Obtain:

1. **Register/Login** to [https://developer.safaricom.co.ke](https://developer.safaricom.co.ke)
2. Go to the **My Apps** section
3. Click **Create a New App**
4. Under **API Products**, select:

   * `MPesa Sandbox`
5. Give your app a name (e.g., `AstraPay SDK Test`)
6. Submit — you'll get:

   * **Consumer Key**
   * **Consumer Secret**

To get your:

* **Shortcode**: Use `174379` (test paybill)
* **Passkey**: Provided under **Lipa Na M-Pesa Online**
* **Callback URL**: Your own endpoint for receiving transaction status updates (e.g., via Ngrok in development)

---

## 🚀 Quick Usage

```python
from astrapay import AstraMpesa

client = AstraMpesa(
    consumer_key="YOUR_KEY",
    consumer_secret="YOUR_SECRET",
    shortcode="174379",
    passkey="YOUR_PASSKEY",
    callback_url="https://yourdomain.com/callback"
)

response = client.pay(
    phone="254712345678",
    amount=100,
    account_reference="ORDER123",
    description="Order Payment"
)

print(response)
```

---

## 🔌 Flask Integration

```python
from flask import Flask, request, jsonify
from astrapay import AstraMpesa

app = Flask(__name__)

client = AstraMpesa(
    consumer_key="YOUR_KEY",
    consumer_secret="YOUR_SECRET",
    shortcode="174379",
    passkey="YOUR_PASSKEY",
    callback_url="https://yourdomain.com/callback"
)

@app.route("/pay", methods=["POST"])
def pay():
    data = request.json
    res = client.pay(
        phone=data["phone"],
        amount=data["amount"]
    )
    return jsonify(res)

if __name__ == "__main__":
    app.run(debug=True)
```

---

## 🔌 Django Integration

```python
# views.py
from django.http import JsonResponse
from astrapay import AstraMpesa

client = AstraMpesa(
    consumer_key="YOUR_KEY",
    consumer_secret="YOUR_SECRET",
    shortcode="174379",
    passkey="YOUR_PASSKEY",
    callback_url="https://yourdomain.com/callback"
)

def pay_view(request):
    phone = request.POST.get("phone")
    amount = request.POST.get("amount")
    res = client.pay(phone, amount)
    return JsonResponse(res)
```

---

## 📨 Sample Response

```json
{
  "MerchantRequestID": "12345-67890",
  "CheckoutRequestID": "ws_CO_123456789",
  "ResponseCode": "0",
  "ResponseDescription": "Success. Request accepted for processing",
  "CustomerMessage": "Success. Request accepted for processing"
}
```

---

## 📋 Requirements

* Python 3.6+
* `requests` (auto-installed)

---

## 🔁 Callback Handling

The SDK supports Safaricom's callback mechanism. Your app should handle:

* Validating results
* Storing transaction status
* Sending customer notifications

Example callback view (Flask):

```python
@app.route("/callback", methods=["POST"])
def callback():
    data = request.json
    print("Callback received:", data)
    return jsonify({"ResultCode": 0, "ResultDesc": "Accepted"})
```

---

## 👤 Author

**Ishmael Bett**
Founder — [Astra Softwares](https://www.astrasoft.tech)
📧 [info.astrasoft@gmail.com](mailto:info.astrasoft@gmail.com)

---

## 📝 License

This project is licensed under the MIT License.
Feel free to use, modify, and distribute.

---

## 🌍 Coming Soon

* 📊 Transaction status verification
* 🔄 Reversals
* 🧩 WordPress / Shopify plug & play button

---

Happy building with AstraPay! ✨
