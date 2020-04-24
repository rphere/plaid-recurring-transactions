# Plaid recurring transactionss
Cloned from https://github.com/plaid/quickstart.git and updated to compute the recurring transactions from any connected bank account using the Plaid API. 

Detecting recurring transactions can help one fish out any subscriptions that they are unwittingly paying for. 


# Quickstart for plaid-python

To run this application locally, first install it and then run either of the flows described below. Additionally, please also refer to the [Quickstart guide](https://plaid.com/docs/quickstart).

## Installing the app
``` bash
git clone https://github.com/rphere/plaid-recurring-transactions.git

# If you use virtualenv
# virtualenv venv
# source venv/bin/activate

```

## The canonical flow
``` bash
# Start the Quickstart with your API keys from the Dashboard
# https://dashboard.plaid.com/account/keys
#
# PLAID_PRODUCTS is a comma-separated list of products to use when
# initializing Link, see https://plaid.com/docs/#item-product-access
# for complete list.

PLAID_CLIENT_ID='CLIENT_ID' \
PLAID_SECRET='SECRET' \
PLAID_PUBLIC_KEY='PUBLIC_KEY' \
PLAID_ENV='sandbox' \
PLAID_PRODUCTS='transactions' \
PLAID_COUNTRY_CODES='US,CA,GB,FR,ES,IE,NL' \
python server_recurring_transactions.py

# Go to http://localhost:5000
```

## The OAuth redirect flow
Some European institutions require an OAuth redirect authentication flow, where the end user is redirected to the bank’s website or mobile app to authenticate. For this flow, you should provide two additional configuration parameters, `PLAID_OAUTH_NONCE` and `PLAID_OAUTH_REDIRECT_URI`.

``` bash
# You will need to whitelist the PLAID_OAUTH_REDIRECT_URI for
# your client ID through the Plaid developer dashboard at
# https://dashboard.plaid.com/team/api.
#
# Set PLAID_OAUTH_NONCE to a unique identifier such as a UUID.
# The nonce must be at least 16 characters long.
#
# Start the Quickstart with your API keys from the Dashboard
# https://dashboard.plaid.com/account/keys
#
# PLAID_PRODUCTS is a comma-separated list of products to use when
# initializing Link, see https://plaid.com/docs/#item-product-access
# for complete list.

PLAID_CLIENT_ID='CLIENT_ID' \
PLAID_SECRET='SECRET' \
PLAID_PUBLIC_KEY='PUBLIC_KEY' \
PLAID_ENV='sandbox' \
PLAID_PRODUCTS='transactions' \
PLAID_COUNTRY_CODES='GB,FR,ES,IE,NL' \
PLAID_OAUTH_REDIRECT_URI='http://localhost:5000/oauth-response.html' \
PLAID_OAUTH_NONCE='nice-and-long-nonce' \
python server_recurring_transactions.py

# Go to http://localhost:5000
```
