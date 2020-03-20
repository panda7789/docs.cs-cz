---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: c54cbf1fe881ef2ce5dffb0bc0c6dac4049135b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143366"
---
# <a name="wshttpbinding"></a>WSHttpBinding
Tato ukázka ukazuje, jak implementovat typické služby a typické klienta pomocí Windows Communication Foundation (WCF). Tato ukázka se skládá z programu klientské konzole (client.exe) a knihovny služeb hostované internetovou informační službou (IIS). Služba implementuje smlouvu, která definuje vzor komunikace požadavek odpověď. Kontrakt je definován `ICalculator` rozhraním, které zveřejňuje matematické operace (sčítání, odčítání, násobení a dělení). Klient provádí synchronní požadavky na danou operaci matematiky a odpovědi služby s výsledkem. Aktivita klienta je viditelná v okně konzoly.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Tato ukázka `ICalculator` zveřejňuje smlouvy pomocí [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Konfigurace této vazby byla rozšířena v souboru Web.config.  
  
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
  
 Na základní `binding` prvek `maxReceivedMessageSize` hodnota umožňuje nakonfigurovat maximální velikost příchozí zprávy (v bajtů). Hodnota `hostNameComparisonMode` umožňuje nakonfigurovat, zda je název hostitele považován při de-multiplexování zpráv do služby. Hodnota `messageEncoding` umožňuje nakonfigurovat, zda chcete pro zprávy použít kódování textu nebo mtom. Hodnota `textEncoding` umožňuje konfigurovat kódování znaků pro zprávy. Hodnota `bypassProxyOnLocal` umožňuje nakonfigurovat, zda chcete použít proxy server HTTP pro místní komunikaci. Hodnota `transactionFlow` konfiguruje, zda je aktuální transakce tok (pokud je operace nakonfigurována pro tok transakce).  
  
 U prvku [ \<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) nakonfiguruje povolená logická hodnota, zda jsou povoleny spolehlivé relace. Hodnota `ordered` konfiguruje, zda je zachováno řazení zpráv. Hodnota `inactivityTimeout` konfiguruje, jak dlouho může být relace nečinná před chybou.  
  
 V [ \<>zabezpečení ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `mode` hodnota konfiguruje, který režim zabezpečení by měl být použit. V této ukázce se používá zabezpečení zpráv, což je důvod, proč je [ \<zpráva>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) zadána [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)uvnitř>zabezpečení .  
  
 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
