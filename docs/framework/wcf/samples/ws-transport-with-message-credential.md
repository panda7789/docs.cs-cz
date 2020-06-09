---
title: Přenos WS s pověřením zpráv
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 0082a9df5c112b66315236aad91bc891b80d27c7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596381"
---
# <a name="ws-transport-with-message-credential"></a>Přenos WS s pověřením zpráv
Tato ukázka demonstruje použití zabezpečení přenosu SSL v kombinaci s přihlašovacími údaji klienta, které jsou přenášeny ve zprávě. Tato ukázka používá `wsHttpBinding` vazbu.  
  
 Ve výchozím nastavení `wsHttpBinding` Vazba poskytuje komunikaci pomocí protokolu HTTP. Pokud je nakonfigurovaná pro zabezpečení přenosu, vazba podporuje komunikaci pomocí protokolu HTTPS. Protokol HTTPS poskytuje ochranu proti utajení a integritě zpráv, které jsou přenášeny přes drát. Sada ověřovacích mechanismů, které lze použít k ověření klienta ke službě, je však omezená na to, co podporuje přenos HTTPS. Windows Communication Foundation (WCF) nabízí `TransportWithMessageCredential` režim zabezpečení, který je navržený k překonání tohoto omezení. Pokud je tento režim zabezpečení nakonfigurovaný, použije se k zajištění důvěrnosti a integrity odesílaných zpráv a k provedení ověření služby zabezpečení přenosu. Ověřování klienta se ale provádí tak, že přihlašovací údaje klienta vložíte přímo do zprávy. To vám umožní používat libovolný typ přihlašovacích údajů, který je podporovaný režimem zabezpečení zpráv pro ověřování klientů, a přitom zachovat výhody režimu zabezpečení přenosu.  
  
 V této ukázce se k `UserName` ověření klienta pro službu používá typ přihlašovacích údajů.  
  
 Tato ukázka je založená na [Začínáme](getting-started-sample.md) , která implementuje službu kalkulačky. `wsHttpBinding`Vazba je určena a nakonfigurována v konfiguračních souborech aplikace pro klienta a službu.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Kód programu v ukázce je skoro stejný jako služba [Začínáme](getting-started-sample.md) . Kontrakt služby poskytuje ještě jednu další operaci – `GetCallerIdentity` . Tato operace vrátí název volajícího volajícímu.  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 Před vytvořením a spuštěním ukázky musíte vytvořit certifikát a přiřadit ho pomocí Průvodce certifikátem webového serveru. Definice koncového bodu a definice vazby v nastavení konfiguračního souboru umožňují `TransportWithMessageCredential` režim zabezpečení, jak je znázorněno v následující ukázkové konfiguraci pro klienta.  
  
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
  
 Zadaná adresa používá `https://` schéma. Konfigurace vazby nastaví režim zabezpečení na `TransportWithMessageCredential` . V souboru Web. config služby musí být zadaný stejný režim zabezpečení.  
  
 Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořený pomocí nástroje MakeCert. exe, zobrazí se výstraha zabezpečení při pokusu o přístup k protokolu https: adresa, například `https://localhost/servicemodelsamples/service.svc` , z prohlížeče. Aby mohl klient služby WCF pracovat s testovacím certifikátem, byl do klienta přidán nějaký další kód, který výstrahu zabezpečení potlačí. Tento kód a doprovodná třída nejsou při použití produkčních certifikátů vyžadovány.  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
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
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetová informační služba (IIS)](iis-server-certificate-installation-instructions.md).  
  
3. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
