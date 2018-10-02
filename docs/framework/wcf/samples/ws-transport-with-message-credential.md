---
title: Přenos WS s pověřením zpráv
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 44f37e3576b508e679d45a3cbafacfb5a68a7838
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030178"
---
# <a name="ws-transport-with-message-credential"></a>Přenos WS s pověřením zpráv
Tento příklad ukazuje použití zabezpečení přenosu SSL v kombinaci pomocí provádí ve zprávě pověření klienta. Tento příklad používá `wsHttpBinding` vazby.  
  
 Ve výchozím nastavení `wsHttpBinding` vazby poskytuje komunikaci pomocí protokolu HTTP. Když je nakonfigurován pro zabezpečení přenosu, vazba podporuje komunikaci přes protokol HTTPS. HTTPS zajišťuje důvěrnost a ochrana integrity pro zprávy, které jsou přenášeny přenosu. Je ale omezený na přenos HTTPS podporuje sadu ověřovacích mechanismů, které lze použít k ověření klienta ke službě. Nabízí Windows Communication Foundation (WCF) `TransportWithMessageCredential` režim zabezpečení, která slouží k překonání tohoto omezení. Pokud je nakonfigurovaný tento režim zabezpečení, se používá zabezpečení přenosu důvěrnost a integrita stanovit přenášené zprávy a provádět ověřování služby. Ověření klienta je ale provést vložením pověření klienta přímo ve zprávě. To umožňuje použít libovolný typ přihlašovacích údajů, který podporuje režim zabezpečených zpráv pro ověřování klientů a zajistit přitom ochranu plynoucí z režim zabezpečení transport.  
  
 V této ukázce `UserName` typ přihlašovacích údajů se používá k ověření klienta ke službě.  
  
 Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje. `wsHttpBinding` Vazby je zadán a nakonfigurovat v konfiguračních souborech aplikace pro klienta a služby.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Programového kódu v ukázce je téměř shodná s [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) služby. Jeden další operace poskytované kontrakt služby - `GetCallerIdentity`. Tato operace vrátí název identity volajícího volajícímu.  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 Musíte vytvořit certifikát a přiřaďte ho pomocí Průvodce certifikát webového serveru před sestavováním a spouštěním vzorku. Definice koncového bodu a definice vazby v konfiguraci souboru nastavení Povolit `TransportWithMessageCredential` režim zabezpečení, jak je znázorněno v následující ukázková konfigurace pro klienta.  
  
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
  
 Zadaná adresa používá schéma https://. Konfigurace vazby nastaví režim zabezpečení na `TransportWithMessageCredential`. Stejný režim zabezpečení musí být zadaný v souboru Web.config dané služby.  
  
 Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořen s Makecert.exe, výstrahu zabezpečení se zobrazí při pokusu o přístup protokolu https: adresy, jako například `https://localhost/servicemodelsamples/service.svc `, v prohlížeči. Povolit klienta WCF pro práci s testovací certifikát na místě, byla přidána další kód klienta pro potlačení výstrahy zabezpečení. Tento kód a související třídy se nevyžaduje při použití certifikátů produkčního prostředí.  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
3.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také
