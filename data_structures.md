# [EcomSdkIOSDoc](https://sdkpay.github.io/EcomSdkIOSDoc)

##### [Начало работы](https://sdkpay.github.io/EcomSdkIOSDoc/start) | [Сценарий оплаты](https://sdkpay.github.io/EcomSdkIOSDoc/payment_script) | [Работа в режиме песочницы](https://sdkpay.github.io/EcomSdkIOSDoc/sandbox_mode) | [Вспомогательные структуры данных](https://sdkpay.github.io/EcomSdkIOSDoc/data_structures) | [Актуальная версия SDK](https://sdkpay.github.io/EcomSdkIOSDoc/version)
---

# Вспомогательные структуры данных

## SPaymentConfig

#### Конфиг для инициализации SDK

|Параметр|Дефолтное значение|Описание|
|-|-|-|
|card|true|Оплата с помощью ввода данных карты|
|bindings|true|Оплата связкой из списка, сформированного после успешной оплаты способом *card*|
|sbp|true|Оплата с помощью СБП (не может быть единственным включенным способом оплаты)|
