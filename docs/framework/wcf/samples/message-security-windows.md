---
title: Zabezpečení zpráv – Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: 8706eee341dd1a5852efae0aad5195e09f62fec4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183498"
---
# <a name="message-security-windows"></a>Zabezpečení zpráv – Windows
Tato ukázka ukazuje, <xref:System.ServiceModel.WSHttpBinding> jak nakonfigurovat vazbu pro použití zabezpečení na úrovni zprávy s ověřováním systému Windows. Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). V této ukázce je služba hostována v Internetové informační službě (IIS) a klient je konzolová aplikace (.exe).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Výchozí zabezpečení [ \<pro>wsHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) je zabezpečení zpráv pomocí ověřování systému Windows. Konfigurační soubory v `mode` této ukázce `Message` explicitně nastavují atribut>[ \<zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) a `clientCredentialType` atribut `Windows`. Tyto hodnoty jsou výchozí hodnoty pro tuto vazbu, ale byly explicitně nakonfigurovány, jak je znázorněno v následující ukázkové konfiguraci k prokázání jejich použití.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding>  
            <security mode="Message">  
                <message clientCredentialType="Windows"/>  
            </security>  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 Konfigurace koncového bodu klienta se skládá z absolutní adresy pro koncový bod služby, vazbu a smlouvu. Vazby klienta je `securityMode` nakonfigurován s příslušnou a `authenticationMode`.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
            "http://localhost/servicemodelsamples/service.svc"
            binding="wsHttpBinding"
            bindingConfiguration="Binding1"
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- The default security for the WSHttpBinding is -->  
      <!-- Message security using Windows authentication. -->  
      <!-- This configuration explicitly defines the security mode -->  
      <!-- as Message and the clientCredentialType as Windows -->  
      <!-- for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Zdrojový kód služby byl upraven <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> tak, aby demonstroval, jak lze použít pro přístup k identitě volajícího.  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. První metoda s `GetCallerIdentity` názvem - - vrátí název volající identity zpět klientovi. Stisknutím klávesy ENTER v okně konzoly vypněte klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
