---
title: WS Dual Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: 5c38b2be8b49dcb1824578e5cf8d4f98f86ce7f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172078"
---
# <a name="ws-dual-http"></a>WS Dual Http
Duální Http Ukázka předvádí, jak nakonfigurovat `WSDualHttpBinding` vazby. Tento příklad se skládá z programu konzoly klienta (.exe) a služby knihovny (.dll) hostované v Internetové informační služby (IIS). Služba implementuje duplexního kontraktu. Smlouva je definován `ICalculatorDuplex` rozhraní, které zveřejňuje matematických operací (Přidat odečíst, násobení a dělení). V této ukázce `ICalculatorDuplex` rozhraní umožňuje klientovi k provádění matematických operací spuštěných výsledek výpočtu přes relaci. Nezávisle na sobě, služba vrátí výsledky v `ICalculatorDuplexCallback` rozhraní. Duplexní kontrakt vyžaduje relaci, protože kontext musí být stanovena ke korelaci sadu zprávy odesílané mezi klientem a službou. `WSDualHttpBinding` Vazba podporuje duplexní komunikaci.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`  
  
 Konfigurace koncového bodu služby se `WSDualHttpBinding`, zadat vazby v konfiguraci koncového bodu, jak je znázorněno.  
  
```xml  
<endpoint address=""  
         binding="wsDualHttpBinding"  
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
```  
  
 Na straně klienta je nutné nakonfigurovat adresu serveru můžete použít pro připojení ke klientovi, jak je znázorněno v následující ukázková konfigurace.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
         "http://localhost/servicemodelsamples/service.svc"   
         binding="wsDualHttpBinding"   
         bindingConfiguration="Binding1"   
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
  </client>  
  
  <bindings>  
    <!-- Configure a WSDualHttpBinding that supports duplex -->  
    <!-- communication. -->  
    <wsDualHttpBinding>  
      <binding name="Binding1"  
               clientBaseAddress="http://localhost:8000/myClient/"  
               useDefaultWebProxy="true"  
               bypassProxyOnLocal="false">  
      </binding>  
    </wsDualHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```  
Press <ENTER> to terminate client once the output is displayed.  
  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 Když spustíte ukázku, uvidíte zpráv vrácených do klienta na rozhraní zpětného volání odeslané ze služby. Zobrazí se každý přechodný výsledek, za nímž následuje celou rovnici. Po dokončení všech operací. Stiskněte klávesu ENTER pro vypnutí klient.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!IMPORTANT]
    >  Při spuštění klienta v konfiguraci mezi počítači, je potřeba, místo localhost v obou `address` atribut [ \<koncový bod > z \<klienta >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elementu a `clientBaseAddress` atribut [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element s názvem příslušný počítač, jak je vidět:  
  
    ```xml  
    <client>  
        <endpoint name = ""  
          address=  
         "http://service_machine_name/servicemodelsamples/service.svc"  
        />  
    </client>  
    ...  
    <wsDualHttpBinding>  
        <binding name="DuplexBinding" clientBaseAddress=  
            "http://client_machine_name:8000/myClient/">  
        </binding>  
    </wsDualHttpBinding>  
    ```  
