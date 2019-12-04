---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 6ea07f206064a389da8af04a4afd292022b8ca44
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714558"
---
# <a name="wshttpbinding"></a>WSHttpBinding
Tato ukázka předvádí, jak implementovat typickou službu a typický klient pomocí Windows Communication Foundation (WCF). Tato ukázka se skládá z programu klientské konzoly (Client. exe) a knihovny služeb hostované službou Internetová informační služba (IIS). Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď. Kontrakt je definován rozhraním `ICalculator`, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení). Klient provádí synchronní požadavky na určitou matematickou operaci a služba odpovídá výsledku. Aktivita klienta se zobrazí v okně konzoly.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Tato ukázka zveřejňuje kontrakt `ICalculator` pomocí [\<WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Konfigurace této vazby byla rozšířena v souboru Web. config.  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->   
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"   
              transactionFlow="false"   
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"   
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"   
              textEncoding="utf-8"   
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"   
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"   
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 Na základním `binding` element `maxReceivedMessageSize` hodnota umožňuje nakonfigurovat maximální velikost příchozí zprávy (v bajtech). Hodnota `hostNameComparisonMode` umožňuje nakonfigurovat, jestli se má název hostitele při demultiplexování zprávy považovat za nevyhovující. Hodnota `messageEncoding` umožňuje nakonfigurovat, zda má být pro zprávy použit text nebo kódování MTOM. Hodnota `textEncoding` umožňuje nakonfigurovat kódování znaků pro zprávy. Hodnota `bypassProxyOnLocal` umožňuje nakonfigurovat, jestli se má používat proxy server HTTP pro místní komunikaci. Hodnota `transactionFlow` konfiguruje, zda je aktuální transakce předávána (Pokud je operace konfigurovaná pro tok transakce).  
  
 U prvku [\<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) určuje povolená logická hodnota, zda jsou povoleny spolehlivé relace. Hodnota `ordered` konfiguruje, zda je řazení zpráv zachováno. Hodnota `inactivityTimeout` konfiguruje, jak dlouho může být relace nečinná, než bude chyba.  
  
 V [> zabezpečení\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)nakonfiguruje `mode` hodnota, který režim zabezpečení má být použit. V této ukázce se používá zabezpečení zpráv. to je důvod, proč je [\<zpráva](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) zadaná v [\<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).  
  
 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
