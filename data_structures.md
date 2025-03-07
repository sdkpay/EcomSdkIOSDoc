# [EcomSdkIOSDoc](https://sdkpay.github.io/EcomSdkIOSDoc)

##### [Начало работы](https://sdkpay.github.io/EcomSdkIOSDoc/start) | [Сценарий оплаты](https://sdkpay.github.io/EcomSdkIOSDoc/payment_script) | [Работа в режиме песочницы](https://sdkpay.github.io/EcomSdkIOSDoc/sandbox_mode) | [Вспомогательные структуры данных](https://sdkpay.github.io/EcomSdkIOSDoc/data_structures) | [Актуальная версия SDK](https://sdkpay.github.io/EcomSdkIOSDoc/version)
---

# Вспомогательные структуры данных

## SPaymentConfig

#### Конфиг для инициализации SDK

|Параметр|Тип|Дефолтное значение|Обязательный|Описание|
|-|:-:|:-:|:-:|-|
|card|Bool|true|Нет|Оплата с помощью ввода данных карты|
|bindings|Bool|true|Нет|Оплата связкой из списка, сформированного после успешной оплаты способом *card*|
|sbp|Bool|true|Нет|Оплата с помощью СБП (не может быть единственным включенным способом оплаты)|

## SBankInvoicePaymentRequest

#### Конфиг для запуска сценария оплаты методом `payWithBankInvoiceId`

|Параметр|Тип|Дефолтное значение|Обязательный|Описание|
|-|:-:|:-:|:-:|-|
|apiKey|String|-|Да|Ключ клиента для работы с сервисами платежного шлюза через Ecom SDK|
|merchantLogin|String|-|Да|Login партнера для работы с сервисами платежного шлюза|
|bankInvoiceId|String|-|Да|Уникальный номер (идентификатор) заказа в Платежном шлюзе Банка|
|orderNumber|String|-|Да|Уникальный номер (идентификатор) заказа в системе Клиента|

## SPayState﻿

#### Результат выполнения метода `payWithBankInvoiceId`

|Статус|Описание|
|-|-|
|success|Успешная оплата|
|waiting|Статус оплаты не подтвержден|
|error|Произошла ошибка во время оплаты|
|cancel|Пользователь закрыл SDK самостоятельно|
