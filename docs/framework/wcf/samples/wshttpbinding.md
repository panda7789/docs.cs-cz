---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 5d76cb2e4d9f3173c1eb3fda45e1f1c65efeadde
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959811"
---
# <a name="wshttpbinding"></a>WSHttpBinding
Tato ukázka předvádí, jak implementovat typickou službu a typický klient pomocí Windows Communication Foundation (WCF). Tato ukázka se skládá z programu klientské konzoly (Client. exe) a knihovny služeb hostované službou Internetová informační služba (IIS). Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď. Kontrakt je definován `ICalculator` rozhraním, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení). Klient provádí synchronní požadavky na určitou matematickou operaci a služba odpovídá výsledku. Aktivita klienta se zobrazí v okně konzoly.  
  
> [!IMPORTANT]
>  Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Tato ukázka zveřejňuje `ICalculator` kontrakt [ \<pomocí > WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Konfigurace této vazby byla rozšířena v souboru Web. config.  
  
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
  
 Na základním `binding` prvku `maxReceivedMessageSize` hodnota vám umožní nakonfigurovat maximální velikost příchozí zprávy (v bajtech). `hostNameComparisonMode` Hodnota umožňuje nakonfigurovat, jestli se má název hostitele považovat za při demultiplexování zprávy službě. `messageEncoding` Hodnota umožňuje nakonfigurovat, zda má být pro zprávy použit text nebo kódování MTOM. `textEncoding` Hodnota umožňuje nakonfigurovat kódování znaků pro zprávy. `bypassProxyOnLocal` Hodnota umožňuje nakonfigurovat, jestli se má používat proxy server HTTP pro místní komunikaci. `transactionFlow` Hodnota určuje, zda je aktuální transakce předávána (Pokud je operace konfigurovaná pro tok transakce).  
  
 V elementu [> ReliableSessionjepovolenálogickáhodnota,kteráurčuje,jestlijsoupovolenéspolehlivérelace.\<](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) `ordered` Hodnota určuje, zda je zachováváno řazení zpráv. Hodnota `inactivityTimeout` určuje, jak dlouho může být relace nečinná, než bude chyba.  
  
 V [> zabezpečení hodnota určuje, který režim zabezpečení má být použit. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `mode` V této ukázce se používá zabezpečení zpráv. to je důvod, proč [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) [ \<je > zprávy](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) zadán v > zabezpečení.  
  
 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
