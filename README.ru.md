# BitControl.App

*Домашняя страница: [`https://ru.bitcontrol.app`](https://bitcontrol.app)*

*Read this in other languages: [English](README.md), [Русский](README.ru.md).*

## Часто задаваемые вопросы
- [Как запускать приложение?](#как-запускать-приложение)
- [Есть ли версия для смартфона?](#есть-ли-версия-для-смартфона)
- [Как зарегистрироваться?](#как-зарегистрироваться)
- [Что такое идентификационный токен?](#что-такое-идентификационный-токен)
- [С какими криптобиржами работает приложение?](#с-какими-криптобиржами-работает-приложение)
- [Какие данные BitControl.App получает по API бирж?](#какие-данные-bitcontrolapp-получает-по-api-бирж)
- [Насколько безопасно использовать BitControl.App?](#насколько-безопасно-использовать-bitcontrolapp)
- [Какие торговые роботы есть?](#какие-торговые-роботы-есть)
- [Нужен ли приложению постоянный доступ к интернету?](#нужен-ли-приложению-постоянный-доступ-к-интернету)
- [Какие параметры можно передавать при запуске?](#какие-параметры-можно-передавать-при-запуске)
- [С какой базой данных работает приложение?](#с-какой-базой-данных-работает-приложение)
- [Как автоматически запускать приложение при старте системы Linux?](#как-автоматически-запускать-приложение-при-старте-системы-linux)

### Как запускать приложение?
#### Windows (7, 8, 10)
1. Скачайте бинарный файл "[bitcontrol-windows.exe](https://github.com/BitcontrolApp/bitcontrol/releases/download/1.1/bitcontrol-windows.exe)" на персональный компьютер;
2. Запустите приложение и разрешите брандмауэру доступ к сети;
3. Интерфейс приложения открывается через любой браузер по адресу: [http://localhost:8087](http://localhost:8087).

#### MacOS (с процессором Apple M1, Intel AMD)
1. Скачайте бинарный файл "[bitcontrol-macos](https://github.com/BitcontrolApp/bitcontrol/releases/download/1.1/bitcontrol-macos)" на персональный компьютер;
2. Сделайте файл исполняемым - `chmod +x bitcontrol-macos`;
3. Запустите приложение (удерживая клавишу _Control_ чтобы разрешить использование программы, загруженной не из App Store);
4. Интерфейс приложения открывается через любой браузер по адресу: [http://localhost:8087](http://localhost:8087).

На данный момент приложение не добавлено в официальный Mac App Store, по этому при первом запуске может возникать сообщение: _Приложение «bitcontrol-macos» нельзя открыть, так как его автор является неустановленным разработчиком._ Открыть приложение можно нажав и удерживая клавишу _Control_, щёлкните приложение, после этого выберите «Открыть» в контекстном меню, а затем нажмите «Открыть» в появившемся диалоговом окне.

#### Linux (Ubuntu, Fedora, Debian, CentOS)
1. Скачайте бинарный файл "[bitcontrol-linux](https://github.com/BitcontrolApp/bitcontrol/releases/download/1.1/bitcontrol-linux)" на персональный компьютер или на свой web-сервер;
2. Сделайте файл исполняемым - `chmod +x bitcontrol-linux`;
3. Запустите приложение - `./bitcontrol-linux -username admin -password qwerta`;
4. Интерфейс приложения открывается через любой браузер по адресу: [http://localhost:8087](http://localhost:8087) или http://IP_вашего_сервера:8087 если запустили приложение на web-сервере.

:warning: **Обязательно используйте параметры `-username` и `-password` для Basic аутентификации когда запускаете приложения на web сервере!**
См. [Какие параметры можно передавать при запуске?](#какие-параметры-можно-передавать-при-запуске)

Чтобы добавить приложение в автозагрузку "Systemd" см. [Как автоматически запускать приложение при старте системы Linux?](#как-автоматически-запускать-приложение-при-старте-системы-linux)


### Есть ли версия для смартфона?
Приложение можно запустить на любом сервере с ОС Linux и пользоваться через обычный браузер. Верстка интерфейса оптимизирована под мобильные устройства всех разрешений.

### Как зарегистрироваться?
Для работы приложения регистрация обязательная. При первом использовании приложение потребует ввести юзернейм (уникальное имя пользователя) и действующий емейл, а также принятие правил и условий. После регистрации в приложении сохранится **идентификационный токен**, по которому в дальнейшем сервер аналитики будет вас идентифицировать для предоставления данных.

### Что такое идентификационный токен?
Это уникальный UUID хеш пользователя, используется для получения данных с серверов аналитики. Количество запросов с каждого токена ограничено. Его нельзя сообщать третьим лицам.

### С какими криптобиржами работает приложение?
Для контроля динамики портфелей, на данный момент, приложение умеет работать с биржами:
- [Binance](https://www.binance.com)
- [Exmo](https://exmo.com)
- [Gate.io](https://www.gate.io)
- [Huobi](https://www.huobi.com)
- [Kraken](https://www.kraken.com)
- [Kucoin](https://www.kucoin.com)
- [Kuna](https://kuna.io)
- [OKX (Okex)](https://www.okx.com)

Изучаем API и добавим [FTX](https://ftx.com), [Bitfinex](https://www.bitfinex.com), [Crypto.com](https://crypto.com/exchange), [Bybit](https://www.bybit.com/), [Gemini](https://gemini.com), [Bitstamp](https://www.bitstamp.net).

### Какие данные BitControl.App получает по API бирж?
Приложение запрашивает API криптобирж для получения персональных данных:
- Открытые ордера, по торговым парам добавленных в портфель (каждые 30 секунд)
- Количество заблокированных монет/токенов по торговым парам, добавленным в портфель (каждые 25 секунд)
- Последние сделки для вычисления средней цены покупки криптоактива, только по торговым парам добавленным в портфель (каждые 60 секунд)
- Биржевой стакан по запросу клиента (каждые 10 секунд. Только при выборе торговой пары в портфеле, на странице "Аналитика" или "Рынки")

Большинство API разрешают получить все данные одним или двумя запросами. Это позволяет значительно минимизировать количество запросов в минуту, чтобы гарантированно избежать блокировок IP биржами.

Для получения публичных данных таких как история цен, актуальные цены и аналитика запрашивается API наших серверов каждые 5 секунд.

### Насколько безопасно использовать BitControl.App?
Поскольку ваши ApiKey и SecretKey криптобирж хранятся только у вас и используются напрямую с API биржами, безопасность утечки данных напрямую зависит от уровня защиты вашего персонального компьютера или сервера, на котором запущено приложение.

Ограничения API бирж позволяют создавать ApiKey с уровнем доступа "Разрешить только чтение", что вполне достаточно для корректной работы приложения. Если вы используете торговые роботы, то уровень доступа должен позволять создавать и отменять ордера.

### Какие торговые роботы есть?
*«Спекулянт (Спот)»* - Определяет 9 уровней по числам Фибоначчи. Если цена не высокая, определяет 5 коридоров и торгует в пределах каждого по 20% от депозита. Таким образом не важно куда идёт цена, важнее волатильность инструмента. Средняя прибыль 3,5-7% в месяц.

На данный момент доступно около 70+ торговых пар к USDT и 120+ к BTC. Робот умеет торговать парами к USDT, BTC, ETH. Рекомендуем создать робота для каждой валюты котировок, например один для торговых пар к USDT, а второй для пар к BTC.

Робот каждый день анализирует графики и если цена инструмента не высокая, с высокой волатильностью и динамикой то он добавляет его в свой «белый список».

### Нужен ли приложению постоянный доступ к интернету?
Нет, приложение может синхронизировать все данные при запуске. Но если вы используете торговых роботов, то для правильной их работы настоятельно рекомендуем использовать приложение на VPS сервере с постоянным доступом к сети.

:warning: **Обязательно используйте параметры `-username` и `-password` для Basic аутентификации когда запускаете приложения на web сервере!**

Например, чтобы запустить приложение с доступом по Basic аутентификации, логином, например, "superadmin" и паролем "superpass" используйте команду:

`./bitcontrol-linux -username superadmin -password superpass`

### С какой базой данных работает приложение?
BitControl.App умеет работать с SQLite (по умолчанию) и MySQL. Для использования MySQL нужно запустить приложение с параметром `-dbtype mysql`.

Например, чтобы запустить приложение с поддержкой MySQL, с базой данных, например, "mydatabase", пользователем "mydbuser" и паролем "mydbpass" используйте команду:

`./bitcontrol-linux -dbtype mysql -dbname mydatabase -dbuser mydbuser -dbpass mydbpass`

### Какие параметры можно передавать при запуске?
`-username` логин для Basic аутентификации

`-password` пароль для Basic аутентификации

`-dbtype` тип базы данных (sqlite или mysql. По умолчанию: sqlite)

`-dbname` имя базы данных (по умолчанию: bitcontrol)

`-dbuser` пользователь базы данных (по умолчанию: root)

`-dbpass` пароль базы данных

### Как автоматически запускать приложение при старте системы Linux?
Для автозагрузки приложения используйте **Systemd** - демон автозагрузки служб в Linux.
1. Создайте файл "bitcontrol.service" - `nano bitcontrol.service`
2. Вставьте в файл:
```[Unit]
Description="BitControl.App Service"

[Service]
Restart=always
RestartSec=5
ExecStart=/<path-to-app>/bitcontrol-linux -username superadmin -password superpass -dbtype mysql -dbname mydatabase -dbuser mydbuser -dbpass mydbpass

[Install]
WantedBy=multi-user.target
```

где \<path-to-app\> - путь к приложению на сервере. Передаваемые параметры по вашему усмотрению.

3. Скопируйте файл в /etc/systemd/system/ - `cp bitcontrol.service /etc/systemd/system/bitcontrol.service`
4. Включите службу в автозагрузку - `systemctl enable bitcontrol`

Теперь приложение будет автоматически запускаться при старте системы. Также вы можете использовать службу "service" для управления процессом:

`service bitcontrol stop|start|restart|status`

Чтобы следить за логами используйте команду - `journalctl -u bitcontrol.service -f`