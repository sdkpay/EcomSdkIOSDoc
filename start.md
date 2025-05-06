# [EcomSdkIOSDoc](https://sdkpay.github.io/EcomSdkIOSDoc)

#### [Регистрация заказов в платежном шлюзе Сбера](https://sdkpay.github.io/EcomSdkIOSDoc/order_registration) | [Начало работы](https://sdkpay.github.io/EcomSdkIOSDoc/start) | [Сценарий оплаты](https://sdkpay.github.io/EcomSdkIOSDoc/payment_script) | [Работа в режиме песочницы](https://sdkpay.github.io/EcomSdkIOSDoc/sandbox_mode) | [Вспомогательные структуры данных](https://sdkpay.github.io/EcomSdkIOSDoc/data_structures) | [Актуальная версия SDK](https://sdkpay.github.io/EcomSdkIOSDoc/version) | [Поддержка](https://sdkpay.github.io/EcomSdkIOSDoc/support)

<br>

# Начало работы
> Xcode 14+  
> Версия iOS 14.0 и более поздние

<br>

## Подключение SDK к проекту

### Настройка info.plist

Для корректной работы SDK в файле **info.plist** приложения должны быть добавлены следующие параметры
```
<key>NSAppTransportSecurity</key>
    <dict>
        <key>NSExceptionDomains</key>
        <dict>
            <key>gate1.spaymentsplus.ru</key>
            <dict>
                <key>NSExceptionAllowsInsecureHTTPLoads</key>
                <true/>
            </dict>
        </dict>
    </dict>
<key>NSLocationWhenInUseUsageDescription</key>
<string>Данные о местонахождении собираются и отправляются на сервер для безопасного проведения оплаты</string>
```
> NSLocationWhenInUseUsageDescription - Если у вас уже используется этот параметр, то дублировать его не нужно

### Подключение SDK

Подключите SDK одним из удобных Вам способов: [SPM](https://sdkpay.github.io/EcomSdkIOSDoc/start#spm) / [Бинарный артефакт](https://sdkpay.github.io/EcomSdkIOSDoc/start#binary-artifact)

### SPM

```
dependencies: [
    .package(url: "https://github.com/sdkpay/EcomSdkPackage", .upToNextMajor(from: "1.1.7"))
]
```

### Binary artifact

Подключить SDK для успешной работы также можно с помощью [бинарного артефакта](https://github.com/sdkpay/ecomsdkpackage). Перетащите скачанный файл **EcomSdk.xcframework** в *Frameworks, Libraries, and Embedded Content*, а также выставите у зависимости параметр *Embed & Sign*

<br>

## Настройка SDK

Для инициализации SDK необходимо вызвать метод `setup` и передать в него список параметров, указанных в таблице ниже

|Параметр|Дефолтное значение|Описание|
|-|-|-|
|paymentConfig|SPaymentConfig(card = true, bindings = true, sbp = true)|Класс содержащий список доступных способов оплаты.  Структура [SPaymentConfig](https://sdkpay.github.io/EcomSdkIOSDoc/data_structures#spaymentconfig)|
|environment|SEnvironment.prod|Стенд для работы с SDK, подробнее работа со стендами описана в разделе ["Работа в режиме песочницы"](https://sdkpay.github.io/EcomSdkIOSDoc/sandbox_mode)|
|resultViewNeeded|true|С помощью данного параметра можно отключить отображение экрана статуса операции|
|completion|((EcomError?) -> Void)?|Блок, отрабатыващий после инициализации SDK.<br>Структура [EcomError](https://sdkpay.github.io/EcomSdkIOSDoc/data_structures#ecomerror)|

### Swift

```
import EcomSdk

Ecom.setup(
    paymentConfig: SPaymentConfig = SPaymentConfig(),
    environment: SEnvironment = .prod,
    resultViewNeeded: Bool = true,
    completion: ((EcomError?) -> Void)? = nil
)
```

### Objective-C

```
#import <EcomSdk/EcomSdk.h>

[Ecom setupWithPaymentConfig: paymentConfig
                              enviroment: SEnvironmentProd
                              resultViewNeeded: true
                              completion: nil]
```
### Дополнительно, при инициализации EcomSDK совместно со SPaySDK
```
func application(_ app: UIApplication,
                open url: URL,
                options: [UIApplication.OpenURLOptionsKey: Any] = [:]) -> Bool {
    Ecom.getAuthURL(url)
    return true
}
```
