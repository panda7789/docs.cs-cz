---
title: Přenos WS s pověřením zpráv
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 708869f2350f01e75b949f4817fcf8aac35ea018
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810145"
---
# <a name="ws-transport-with-message-credential"></a>Přenos WS s pověřením zpráv
Tento příklad znázorňuje použití přenosu zabezpečení SSL v kombinaci s pověření klienta provádí ve zprávě. V tomto příkladu `wsHttpBinding` vazby.  
  
 Ve výchozím nastavení `wsHttpBinding` vazby poskytuje komunikaci pomocí protokolu HTTP. Když nakonfigurován pro zabezpečení přenosu, vazba podporuje komunikaci přes protokol HTTPS. HTTPS poskytuje utajení a integrity ochrany pro zprávy, které jsou odeslány prostřednictvím sítě. Je ale omezený na přenos HTTPS podporuje sadu ověřovací mechanismy, které lze použít k ověření klienta ke službě. Nabízí Windows Communication Foundation (WCF) `TransportWithMessageCredential` režim zabezpečení, která je určená k překonání tohoto omezení. Pokud je nakonfigurovaná tento režim zabezpečení, zabezpečení přenosu se používá k zajištění důvěrnosti a integrity pro přenášená zprávy a provádět ověřování služby. Ověření klienta se však provádí umístěním pověření klienta přímo ve zprávě. To umožňuje použít libovolný typ přihlašovacích údajů, který podporuje režim zabezpečení zprávy pro ověřování klientů a zachovat přitom výkon výhodou režim zabezpečení přenosu.  
  
 V této ukázce `UserName` typ přihlašovacích údajů se používá k ověření klienta ke službě.  
  
 Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje. `wsHttpBinding` Vazba je zadán a nakonfigurované v konfiguračních souborech aplikace pro klient a služba.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Program kód v ukázce je téměř shodná s [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) služby. Jeden další operace poskytované kontrakt služby - `GetCallerIdentity`. Tato operace vrátí název identitu volajícího volajícímu.  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 Musíte vytvořit certifikát a přiřaďte ho pomocí Průvodce certifikátem webového serveru před vytváření a spouštění vzorku. Definice služby endpoint a definice vazby v konfiguraci souboru povolit nastavení `TransportWithMessageCredential` režim zabezpečení, jak je znázorněno v následující ukázka konfigurace pro klienta.  
  
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
  
 Zadaná adresa používá schéma https://. Konfigurace vazeb nastaví režim zabezpečení `TransportWithMessageCredential`. Stejný režim zabezpečení je třeba zadat v souboru Web.config dané služby.  
  
 Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořen s Makecert.exe, zobrazí se výstraha zabezpečení při pokusu o přístup protokolu https: adresy, jako například https://localhost/servicemodelsamples/service.svc, z prohlížeče. Povolit klienta WCF pro práci s testovací certifikát na místě, se přidal některé další kód klienta pro potlačení výstrahy zabezpečení. Tento kód a doprovodné třídy, je potřeba, není při použití provozní certifikáty.  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
3.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také
