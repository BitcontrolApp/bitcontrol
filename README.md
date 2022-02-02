# BitControl.App

*Homepage: [`https://bitcontrol.app`](https://bitcontrol.app)*

*Read this in other languages: [English](README.md), [Русский](README.ru.md).*


## Frequently asked Questions
- [How to launch the application?](#how-to-launch-the-application)
- [Is there a smartphone version?](#is-there-a-smartphone-version)
- [How to register?](#how-to-register)
- [What is an identification token?](#what-is-an-identification-token)
- [Which crypto exchanges does this application operate with?](#which-crypto-exchanges-does-this-application-operate-with)
- [What data does BitControl.App receive from the exchanges API?](#what-data-does-bitcontrolapp-receive-from-the-exchanges-api)
- [Is it safe to use BitControl.App?](#is-it-safe-to-use-bitcontrolapp)
- [What trading robots are there?](#what-trading-robots-are-there)
- [Does the application need stable access to the Internet?](#does-the-application-need-stable-access-to-the-internet)
- [What parameters can be passed when launching?](#what-parameters-can-be-passed-when-launching)
- [Which database does the application operate with?](#which-database-does-the-application-operate-with)
- [How do I automatically launch an application on a Linux system?](#how-do-i-automatically-launch-an-application-on-a-linux-system)

### How to launch the application?
#### Windows (7, 8, 10)
1. Download the "[**bitcontrol-windows.exe**](https://github.com/BitcontrolApp/bitcontrol/releases/download/1.1/bitcontrol-windows.exe)" binary file to your PC;
2. Run the application and permit the firewall to access the network;
3. The application interface is opened using any browser via the following address: [http://localhost:8087](http://localhost:8087).

#### MacOS (With processors Apple M1, Intel AMD)
1. Download the "[**bitcontrol-macos**](https://github.com/BitcontrolApp/bitcontrol/releases/download/1.1/bitcontrol-macos)" binary file to your PC;
2. Make a file executable - `chmod +x bitcontrol-macos`;
3. Launch the application (by holding down the _Control_ key to permit the program usage without downloading from the App Store);
4. The application interface is opened using any browser via the following address: [http://localhost:8087](http://localhost:8087).

Currently, the application has not been added to the official Mac App Store, so when you first start it, the following message may appear: _Application "bitcontrol-macos" cannot be opened because its author is an unknown developer._ You can open the application by pressing and holding the _Control_ key, clicking the application, then picking out the “Open” button from the context menu, and after that clicking on the “Open” button from the appeared dialog box.

#### Linux (Ubuntu, Fedora, Debian, CentOS)
1. Download the "[**bitcontrol-linux**](https://github.com/BitcontrolApp/bitcontrol/releases/download/1.1/bitcontrol-linux)" binary file to your PC or your web-server;
2. Make a file executable - `chmod +x bitcontrol-linux`;
3. Run in the terminal using the following command - `./bitcontrol-linux -username admin -password qwerta`;
4. The application interface is opened using any browser via the following address: [http://localhost:8087](http://localhost:8087) or http://IP_web-server:8087 if you launched the application on a web server.

:warning: **Be sure to use both `-username` and `-password` options for Basic authentication when running applications on the web-server!**

See [What parameters can be passed when launching?](#what-parameters-can-be-passed-when-launching)

See [How do I automatically launch an application on a Linux system?](#how-do-i-automatically-launch-an-application-on-a-linux-system) if you want to add an application to the "Systemd" autoload.

### Is there a smartphone version?
The application can be run on any Linux server and used via the preferred browser. The interface layout is optimized for mobile devices of all resolutions.

### How to register?
Registration is a prerequisite for running this application. Upon first use, the application will require you to enter a username (unique username) and a valid email address, as well as to accept all the terms and conditions. After registration, an **identification token** will be stored in the application, by which the analytics server will identify you to provide data.

### What is an identification token?
This is the user's unique UUID hash being used to retrieve data from the analytics servers. The number of requests from each token is limited. It cannot be shared with third parties.

### Which crypto exchanges does this application operate with?
At the moment, in order to maintain the portfolios’ dynamics, the application can operate with the following exchanges:
- [Binance](https://www.binance.com)
- [Exmo](https://exmo.com)
- [Gate.io](https://www.gate.io)
- [Huobi](https://www.huobi.com)
- [Kraken](https://www.kraken.com)
- [Kucoin](https://www.kucoin.com)
- [Kuna](https://kuna.io)
- [OKX (Okex)](https://www.okx.com)

We are looking into API and [FTX](https://ftx.com), [Bitfinex](https://www.bitfinex.com), [Crypto.com](https://crypto.com/exchange), [Bybit](https://www.bybit.com/), [Gemini](https://gemini.com), [Bitstamp](https://www.bitstamp.net) will be added later.

### What data does BitControl.App receive from the exchanges API?
The application requests the crypto exchange API to obtain personal data:
- Opened orders for trading pairs, added to the portfolio (every 30 seconds);
- Number of blocked coins/tokens for trading pairs added to the portfolio (every 25 seconds);
- Last trades for calculating the crypto asset purchase average price, exclusively for trading pairs added to the portfolio (every 60 seconds);
- Order book at the Customer's request (every 10 seconds. Only when choosing a trading pair in the portfolio, on the "Analytics" or "Markets" page).

Most APIs permit you to get all the data in one or two requests. This privileges you to greatly minimize the requests' number per minute in order to guarantee that exchanges do not block IP.

To obtain public data such as price history, current prices, and analytics, the API of our servers is requested every 5 seconds.

### Is it safe to use BitControl.App?
Since your crypto exchange ApiKey and SecretKey are stored only with you and are employed directly with exchange APIs, the data leakage safety directly depends on the protection level of your personal computer or server on which the application is running.

Exchange API restrictions qualify you to create an ApiKey with the "Allow read-only" access level, being quite enough for the application to operate correctly. If using trading robots, the access level should authorize you both to create and cancel orders.

### What trading robots are there?
*«Speculator (Spot)»* - defines 9 levels by Fibonacci numbers. If the price is not increased, it determines 5 corridors and trades within 20% of the deposit each. Therefore, it does not matter where the price goes - the instrument volatility is more meaningful. Average profit is 3.5-7% per month.

There are currently approximately 70+ trading pairs available for USDT and 120+ pairs to BTC. The robot can trade pairs to USDT, BTC, ETH. We suggest creating a robot for each currency pair - for instance, one for the USDT trading pairs, and the second one is for BTC pairs.

The robot analyzes charts daily and adds them to the «white list» if the instrument price is not increased and there is high volatility.

### Does the application need stable access to the Internet?
No, the app can sync all data when launching. But if you employ trading robots, we urgently recommend using the application on a VPS server with constant access to the network.

:warning: **Be sure to use both `-username` and `-password` options for Basic authentication when running applications on the web-server!**

For instance, use the following command: `./bitcontrol-linux -username superadmin -password superpass` to when running an application with Basic authentication access, the "superadmin" login, and the "superpass" password.

### Which database does the application operate with?
BitControl.App is able to operate with SQLite (by default) and MySQL. To use MySQL, you need to start the application with the `-dbtype mysql` option.

For instance, to run a MySQL-enabled application with a database such as "mydatabase", user "mydbuser" and password "mydbpass", use the following command:

`./bitcontrol-linux -dbtype mysql -dbname mydatabase -dbuser mydbuser -dbpass mydbpass`

### What parameters can be passed when launching?
`-username` login for Basic authentication

`-password` password for Basic authentication

`-dbtype` database type (sqlite or mysql. Default: sqlite)

`-dbname` database name (default: bitcontrol)

`-dbuser` database user (default: root)

`-dbpass` database password

### How do I automatically launch an application on a Linux system?
To autoload an application, use **Systemd** - a service autoload assistant in Linux.

1. Create a "bitcontrol.service" file - `nano bitcontrol.service`
2. Insert the following data in the file:
```[Unit]
Description="BitControl.App Service"

[Service]
Restart=always
RestartSec=5
ExecStart=/<path-to-app>/bitcontrol-linux -username superadmin -password superpass -dbtype mysql -dbname mydatabase -dbuser mydbuser -dbpass mydbpass

[Install]
WantedBy=multi-user.target
```

where \<path-to-app\> - is a path to application on the server. The passed parameters are at your discretion.

3. Copy the file to /etc/systemd/system/ - `cp bitcontrol.service /etc/systemd/system/bitcontrol.service`
4. Enable the service on autoload - `systemctl enable bitcontrol`

From this moment, the application will be automatically opened at system launching. You can also employ the followng "service" to manage the process:

`service bitcontrol stop|start|restart|status`

Use the following command for logs monitoring - `journalctl -u bitcontrol.service -f`
