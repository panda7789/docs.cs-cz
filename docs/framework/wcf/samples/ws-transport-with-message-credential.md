---
title: Přenos WS s pověřením zpráv
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 076d4490f6edc6efa8eeb50ae8baa23d5c4e369a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183148"
---
# <a name="ws-transport-with-message-credential"></a>Přenos WS s pověřením zpráv
Tato ukázka ukazuje použití zabezpečení přenosu SSL v kombinaci s pověření klienta přenášených ve zprávě. Tato ukázka `wsHttpBinding` používá vazbu.  
  
 Ve výchozím `wsHttpBinding` nastavení poskytuje vazba komunikaci HTTP. Při konfiguraci pro zabezpečení přenosu podporuje vazba komunikaci HTTPS. Protokol HTTPS poskytuje ochranu důvěrnosti a integrity pro zprávy, které jsou přenášeny po drátě. Sada mechanismů ověřování, které lze použít k ověření klienta ke službě je však omezena na co podporuje přenos HTTPS. Windows Communication Foundation (WCF) nabízí režim `TransportWithMessageCredential` zabezpečení, který je určen k překonání tohoto omezení. Při konfiguraci tohoto režimu zabezpečení se zabezpečení přenosu používá k zajištění důvěrnosti a integrity přenášených zpráv a k provedení ověřování služby. Ověřování klienta se však provádí vložením pověření klienta přímo do zprávy. To umožňuje použít libovolný typ pověření, který je podporován režimem zabezpečení zpráv pro ověřování klienta při zachování výhod výkonu režimu zabezpečení přenosu.  
  
 V této ukázce se k ověření klienta ke službě používá typ `UserName` pověření.  
  
 Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky. Vazba `wsHttpBinding` je určena a nakonfigurována v konfiguračních souborech aplikace pro klienta a službu.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Kód programu v ukázce je téměř totožný se službou [Začínáme.](../../../../docs/framework/wcf/samples/getting-started-sample.md) Existuje jedna další operace poskytovaná `GetCallerIdentity`servisní smlouvou - . Tato operace vrátí volajícímu jméno identity volajícího.  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 Před sestavením a spuštěním ukázky je nutné vytvořit certifikát a přiřadit jej pomocí Průvodce certifikátem webového serveru. Definice koncového bodu a definice vazby `TransportWithMessageCredential` v nastavení konfiguračního souboru umožňují režim zabezpečení, jak je znázorněno v následující ukázkové konfiguraci pro klienta.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Zadaná adresa používá schéma https://. Konfigurace vazby nastaví `TransportWithMessageCredential`režim zabezpečení na . Stejný režim zabezpečení musí být zadán v souboru Web.config služby.  
  
 Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořený pomocí programu Makecert.exe, zobrazí se při pokusu o přístup k adrese https: adresa, například `https://localhost/servicemodelsamples/service.svc`, z prohlížeče. Chcete-li povolit wcf klienta pracovat s certifikátem test na místě, některé další kód byl přidán do klienta potlačit výstrahu zabezpečení. Tento kód a doprovodná třída se nevyžadují při použití produkčních certifikátů.  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
```console  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:
YourDomainName\YourAccountName  
   Enter password:
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Zkontrolujte, zda jste provedli [pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
3. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
