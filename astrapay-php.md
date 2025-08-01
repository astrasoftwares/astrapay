# AstraPay PHP SDK

AstraPay is a lightweight PHP SDK that simplifies integrating **Safaricom M-Pesa STK Push** into your web applications. Built and maintained by [Astra Softwares](https://astrasoft.tech), this SDK allows you to initiate secure mobile payments with ease.

---

## 📦 Installation

Install via Composer:

```bash
composer require astrasoftwares/astrapay
```

> Requires PHP >= 7.4

---

## ⚙️ Getting Started

```php
require 'vendor/autoload.php';

use Astrapay\AstraMpesa;

$client = new AstraMpesa([
  'consumerKey' => 'YOUR_CONSUMER_KEY',
  'consumerSecret' => 'YOUR_CONSUMER_SECRET',
  'shortcode' => '174379',
  'passkey' => 'YOUR_PASSKEY',
  'callbackUrl' => 'https://yourdomain.com/callback'
]);

$response = $client->pay('254712345678', 100); // phone, amount
print_r($response);
```

---

## 🔐 How to Get M-Pesa API Credentials

To integrate with M-Pesa, you’ll need to create a **Safaricom Daraja** developer account and set up your app:

1. **Register on Daraja Portal**
   ➔ [https://developer.safaricom.co.ke](https://developer.safaricom.co.ke)

2. **Create an App**

   * Log in and click “My Apps” → “Add a New App”
   * Choose **M-Pesa Express (STK Push)** product
   * Give it a name and save

3. **Get the following from your App dashboard:**

   * `Consumer Key`
   * `Consumer Secret`

4. **Get your Shortcode and Passkey:**

   * Shortcodes are provided by Safaricom (test or production)
   * You can generate your **passkey** via the Daraja portal (or request from Safaricom if in production)

5. **Set your Callback URL:**

   * Must be publicly accessible (e.g., `https://yourdomain.com/callback`)
   * This is where M-Pesa will send payment confirmations

---

## 🧲 Sample Test Numbers (Sandbox)

| Phone Number | PIN  | OTP    |
| ------------ | ---- | ------ |
| 254708374149 | 1111 | 123456 |

Use the sandbox environment for development/testing. Production use requires approval.

---

## 📖 Documentation

* [Python SDK](https://github.com/astrasoftwares/astrapay/blob/main/Astrapay-python.md)
* [JavaScript SDK](https://github.com/astrasoftwares/astrapay/blob/main/astrapay-js.md)

---

## 🤝 Contribute

Pull requests are welcome! If you find a bug or want a feature added, open an issue or submit a PR.

---

## 🧑‍💻 Author

Built with ❤️ by [Ishmael Bett](https://astrasoft.tech)
📧 [info.astrasoft@gmail.com](mailto:info.astrasoft@gmail.com)

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
