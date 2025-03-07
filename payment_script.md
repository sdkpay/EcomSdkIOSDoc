# [EcomSdkIOSDoc](https://sdkpay.github.io/EcomSdkIOSDoc)

##### [Начало работы](https://sdkpay.github.io/EcomSdkIOSDoc/start) | [Сценарий оплаты](https://sdkpay.github.io/EcomSdkIOSDoc/payment_script) | [Работа в режиме песочницы](https://sdkpay.github.io/EcomSdkIOSDoc/sandbox_mode) | [Вспомогательные структуры данных](https://sdkpay.github.io/EcomSdkIOSDoc/data_structures) | [Актуальная версия SDK](https://sdkpay.github.io/EcomSdkIOSDoc/version)
---

## Сценарий оплаты

Для запуска сценария оплаты SDK необходимо необходимо вызвать метод `payWithBankInvoiceId` и передать в него **[SBankInvoicePaymentRequest](https://sdkpay.github.io/EcomSdkIOSDoc/data_structures#sbankinvoicepaymentrequest)**  
Результат оплаты будет получен колбеком в виде структуры **[SPayState](https://sdkpay.github.io/EcomSdkIOSDoc/data_structures#spaystate)**

### Swift

```
import EcomSdk

let request = SBankInvoicePaymentRequest(
    merchantLogin: "ВАШ merchantLogin",
    bankInvoiceId: "ВАШ bankInvoiceId",
    orderNumber: "ВАШ orderNumber",
    apiKey: "ВАШ apiKey"
)

Ecom.payWithBankInvoiceId(paymentRequest: request) { state in
    switch state {
    case .success:
    // Успешная оплата
    case .waiting:
    // Статус оплаты не подтвержден
    case .error:
    // Произошла ошибка во время оплаты
    case .cancel:
    // Пользователь закрыл SDK самостоятельно
    @unknown default:
    // Неизвестная ошибка
    }
}
```

### Objective-C

```
SBankInvoicePaymentRequest *request = [[SBankInvoicePaymentRequest alloc]
    initWithMerchantLogin:@"ВАШ merchantLogin"
    bankInvoiceId:@"ВАШ bankInvoiceId"
    orderNumber:@"ВАШ orderNumber"
    apiKey:@"ВАШ apiKey"];

[Ecom payWithBankInvoiceId:request completion:^(EcomPaymentState state) {
    switch (state) {
        case EcomPaymentStateSuccess:
            // Успешная оплата
            break;
        case EcomPaymentStateWaiting:
            // Статус оплаты не подтвержден
            break;
        case EcomPaymentStateError:
            // Произошла ошибка во время оплаты
            break;
        case EcomPaymentStateCancel:
            // Пользователь закрыл SDK самостоятельно
            break;
        default:
            // Неизвестная ошибка
            break;
    }
}];
```
