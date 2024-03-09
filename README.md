
# Test Telegram Bot Repository

This repository contains the source code for testing our Telegram bot with payment API integration. Follow the steps below to set up and test the bot locally.

## Prerequisites

Before you begin, make sure you have the following installed:
- Git
- RVM (Ruby Version Manager)
- Ruby (we use version 3.0.0)
- Ngrok

## Getting Started

### 1. Clone the Repository

Clone the specific branch we're working on to your local machine:

```bash
git clone -b f001-telegram_payment_api_integration --single-branch https://github.com/samzhab/test_telegram_bot.git
```

### 2. Set Up Ruby Environment

Install RVM and Ruby (version 3.0.0), and create a gemset:

```bash
# Install RVM
\curl -sSL https://get.rvm.io | bash -s stable

# Install Ruby 3.0.0
rvm install 3.0.0

# Create and use a new RVM gemset
rvm use 3.0.0@test_tg_bot --create
```

### 3. Install Dependencies

Install the necessary gems:

```bash
# In your project directory
bundle install
```

### 4. Set Up Environment Variables

Create a `.env` file in the main directory of the project and fill it with your environment variables:

```
TELEGRAM_BOT_TOKEN=your_telegram_bot_token_here
PAYMENT_PROVIDER_CHAPA_TOKEN=your_chapa_token_here
PAYMENT_PROVIDER_STRIPE_TOKEN=your_stripe_token_here (optional)
PAYMENT_PROVIDER_CHAPA_SECRET=your_chapa_secret_here
CHAPA_TRANSACTION_ENDPOINT=your_chapa_transaction_endpoint_here
PAYMENT_PROVIDER_CHAPA_VERIFY=your_chapa_verify_endpoint_here
USER_EMAIL=ali@gmail.com
USER_PHONE_NUMBER=09837477458
CALLBACK_URL=https://your_ngrok_url_here/chapa_payment_verification
WEBHOOK_URL=https://your_ngrok_url_here
RETURN_URL=https://t.me/samaelLabsDemoBot
```

Replace `your_*_here` with the actual values you obtained from your environment setup.

### 5. Start the Bot and Ngrok

First, run the verification script:

```bash
ruby verify_chapa.rb
```

Then, start Ngrok to create a local tunnel:

```bash
ngrok http 4567
```

Copy the Ngrok tunnel URL (e.g., `https://f97e-194-110-113-238.ngrok-free.app`) and update the `CALLBACK_URL` and `WEBHOOK_URL` in your `.env` file accordingly.

Finally, run the bot:

```bash
ruby telegram_bot.rb
```

## Testing

Ensure that all the environment requirements are fulfilled. Run your tests to verify that the setup is working correctly.

## Support

If you encounter any issues or need further assistance, please open an issue in this repository or contact the project maintainers.
