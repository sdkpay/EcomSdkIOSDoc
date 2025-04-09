# [EcomSdkIOSDoc](https://sdkpay.github.io/EcomSdkIOSDoc)

#### [Регистрация заказов в платежном шлюзе Сбера](https://sdkpay.github.io/EcomSdkIOSDoc/order_registration) | [Начало работы](https://sdkpay.github.io/EcomSdkIOSDoc/start) | [Сценарий оплаты](https://sdkpay.github.io/EcomSdkIOSDoc/payment_script) | [Работа в режиме песочницы](https://sdkpay.github.io/EcomSdkIOSDoc/sandbox_mode) | [Вспомогательные структуры данных](https://sdkpay.github.io/EcomSdkIOSDoc/data_structures) | [Актуальная версия SDK](https://sdkpay.github.io/EcomSdkIOSDoc/version) | [Поддержка](https://sdkpay.github.io/EcomSdkIOSDoc/support)

<br>

# Вспомогательные структуры данных

## SPaymentConfig

#### Конфиг для инициализации SDK

|Параметр|Тип|Дефолтное значение|Обязательный|Описание|
|-|:-:|:-:|:-:|-|
|bindings|Bool|true|Нет|Оплата связкой из списка, сформированного после успешной оплаты способом *card*|
|sbp|Bool|true|Нет|Оплата с помощью СБП (не может быть единственным включенным способом оплаты)|
|newCard|Bool|true|Нет|Оплата с помощью новой карты|
|sberPay|Bool|true|Нет|Оплата с помощью SberPay|

<br>

## EcomBankInvoicePaymentRequest

#### Конфиг для запуска сценария оплаты методом `payWithBankInvoiceId`

|Параметр|Тип|Дефолтное значение|Обязательный|Описание|
|-|:-:|:-:|:-:|-|
|merchantLogin|String|-|Да|Login партнера для работы с сервисами платежного шлюза|
|bankInvoiceId|String|-|Да|Уникальный номер (идентификатор) заказа в Платежном шлюзе Банка|
|orderNumber|String|-|Да|Уникальный номер (идентификатор) заказа в системе Клиента|
|apiKey|String|-|Да|Ключ клиента для работы с сервисами платежного шлюза через Ecom SDK|
|redirectUri|String|nil|Нет|Параметр, необходимый для работы с SPaySdk. Выдается саппортом при обращении|

<br>

## SPayState

#### Результат выполнения метода `payWithBankInvoiceId`

|Статус|Описание|
|-|-|
|success|Успешная оплата|
|waiting|Статус оплаты не подтвержден|
|error|Произошла ошибка во время оплаты|
|cancel|Пользователь закрыл SDK самостоятельно|

<!-- <br>

## Платежные инструменты для работы в режиме песочницы

| Тип тестирования | Номер карты | Срок действия карты | CVV |  SMS-код | Пароль |
| --- |:---:|:---:|:---:|:---:|:---:|
| Без 3ds | 4279380620378929 | 06/26 | 353 | нет | нет |
| С 3ds | 2202208020207685 | 05/27 | 133 | 111111 | нет |
| С 3ds | 2201382000000047 | 05/27 | 133 | нет | 1qwezxc | -->

<br>

## EcomError

####  Класс, служащий для передачи ошибок работы сервисов SDK

|Объект|Тип|Описание|
|---|:---:|---|
|errorDescription|String|Описание ошибки|