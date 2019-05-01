---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: d8453d85afb92c69bdf3066ccb8b31e26a34c6d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006483"
---
# <a name="wshttpbinding"></a>WSHttpBinding
Tento příklad ukazuje, jak implementovat typické služby a typické klienta pomocí Windows Communication Foundation (WCF). Tento příklad se skládá z programu konzoly klienta (client.exe) a knihovna služby hostované v Internetové informační služby (IIS). Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď. Smlouva je definován `ICalculator` rozhraní, které zveřejňuje matematických operací (Přidat odečíst, násobení a dělení). Klient podá synchronní žádosti a odpovědi služby s výsledkem dané matematické operace. Činnost klienta je vidět v okně konzoly.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Tato ukázka poskytuje `ICalculator` smlouvy pomocí [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Došlo k rozbalení konfiguraci této vazby v souboru Web.config.  
  
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
  
 V základní třídě `binding` elementu, `maxReceivedMessageSize` hodnota umožňuje nakonfigurovat maximální velikost příchozí zprávy (v bajtech). `hostNameComparisonMode` Hodnota umožňuje nakonfigurovat, jestli název hostitele je považován za multiplexingu rušit při zprávy do služby. `messageEncoding` Hodnota vám umožní nakonfigurovat, jestli se má používat Text nebo MTOM kódování zprávy. `textEncoding` Hodnota vám umožní nakonfigurovat kódování znaků pro zprávy. `bypassProxyOnLocal` Hodnota vám umožní nakonfigurovat, jestli se má používat proxy server HTTP pro místní komunikace. `transactionFlow` Hodnota konfiguruje, zda se aktuální transakce je naplněn (Pokud je operace je nakonfigurována pro tok transakcí).  
  
 Na [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, povolené logická hodnota konfiguruje, zda jsou povoleny spolehlivé relace. `ordered` Hodnota konfiguruje, zda zpráva pořadí je zachováno. `inactivityTimeout` Hodnota konfiguruje, jak dlouho může být relace nečinná, než se došlo k chybě.  
  
 Na [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), `mode` hodnota konfiguruje, který režim zabezpečení by měl sloužit. V této ukázce zabezpečení zprávy se používá, což je důvod, proč [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) je zadat v rámci [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
