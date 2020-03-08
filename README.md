![Autoshrimp Logo](./autoshrimp-64.png)

# AutoShrimp

Want total automated control over your Shrimpy portfolios? **AutoShrimp** allows your portfolios to be selected and rebalanced based on TradingView webhook alerts. Whether you want to convert all to a stablecoin because you predict markets will drop, or you think alt season is upon us and want to quickly accumulate BTC value. All this can be triggered by your chart analysis whilst not having to worry about logging in and reacting in time.

## Prerequisite

To use AutoShrimp, there are a few dead simple steps to follow. 

1. [Shrimpy](https://shrimpy.io/referral?r=sA7mSLRan) subscription
2. Link your target exchange to Shrimpy, we highly recommend [Binance](https://www.binance.com/en/register?ref=17017553)
3. Create a set portfolios as normal that you want to switch to via TradingView alerts e.g. 100% Altcoins, 100% BTC, 100% Stablecoins, or a balanced portfolio across different coins.
4. Any [TradingView](https://tradingview.go2cloud.org/aff_c?offer_id=2&aff_id=11772) subscription 
5. First create an API key on your Shrimpy account page.
6. Take record of your *public* and *secret* key that are generated for you
7. Download the latest release of AutoShrimp from the repository [releases page](https://github.com/ADWilkinson/auto-shrimp/releases)
8. Unzip the AutoShrimp.zip file

AutoShrimp is a node express based weberver that needs to run 24/7 to be able to recieve your alerts and react to it. Therefore it is advised to run this either on a small machine like ethernet connected Raspberry Pi at home or ideally a cheap cloud VPS.

## Setup

1. Open up the `config.json` file
2. Fill the following fields in with the relevant Shrimpy account details and your chosen exchange
```
{
    "key": "xxx",
    "secret": "xxx",
    "exchange": "BINANCE"
}
```
3. Execute the `AutoShrimp-{platform}` file by opening Command Prompt/Terminal in the AutoShrimp directory and typing `AutoShrimp-win.exe` for windows, `./AutoShrimp-macos` for Mac & `./AutoShrimp-linux` for linux.
4. On a successful start up and connection with your Shrimpy account you should see the following log lines in the terminal:
```
[2020-03-03T16:44:23.671] [DEBUG] debug - AutoShrimp started on port 80
[2020-03-03T16:44:24.267] [DEBUG] debug - Setting up AutoShrimp
[2020-03-03T16:44:24.268] [DEBUG] debug - Writing to account.json
[2020-03-03T16:44:24.277] [INFO] debug - Account information stored in account.json
```
5. The webserver is now running on port 80, this port must now be forwarded on your router or VPS, this process varies on provider/router type so please research appropiate documentation online.
6. To check for a successful setup, find your [IP address](https://whatismyipaddress.com), and paste that into your internet browser with :80 port number appended to the end e.g. 77.102.54.171:80 . If your server is successfully exposed to the internet and ready for TradingView webhook alerts you should get a response that looks like this:

```
{
    "STATUS": "ONLINE",
    "ACCOUNT": {
        "id": 123456,
        "exchange": "Binance",
        "isRebalancing": false
    }
}
```

## TradingView Alerts 

1. Open the create alert window on TradingView
2. Define your paramaters to trigger a portfolio switch and rebalance, e.g. a Moving Average cross over or price level cross
3. Check the **Webhook URL** box and input your webserver address, port and 'alert' appended on the end, this is the URL that recieves your webhook alerts and actions them. e.g. `http://77.102.54.171:80/alert`
4. In the message box you **must** format your message like the example below. Please replace `TARGET_PORTFOLIO` with the desired portfolio on Shrimpy you want the alert to switch and rebalance too in response.

```
TARGET_PORTFOLIO_TEXT
```
5. You're all done! Thank you for using AutoShrimp!

## Support
1. Join the Official Shrimpy [Discord](https://discord.gg/92gM5cd) server
2. My username is **Falco#6843**, please either tag me on there or direct message me.

## Donate
Feel free to buy me a coffee if you find this useful to you, it goes without saying that it's massively appreciated.
- **[PayPal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=FVGFAM7EP3YUA&source=url)**
- **[Coinbase](https://commerce.coinbase.com/checkout/3cefad58-560f-4588-a156-331047429f2b)**

