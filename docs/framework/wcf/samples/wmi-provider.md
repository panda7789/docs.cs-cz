---
title: Poskytovatel WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 04fdbb7efcae6fdbb78f467352e6106ac5218799
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183193"
---
# <a name="wmi-provider"></a>Poskytovatel WMI
Tato ukázka ukazuje, jak shromažďovat data ze služeb WCF (Windows Communication Foundation) za běhu pomocí zprostředkovatele WMI (WMI) služby WMI ( WMI), který je integrován do WCF. Tato ukázka také ukazuje, jak přidat uživatelem definovaný objekt služby WMI do služby. Ukázka aktivuje zprostředkovatele služby WMI pro [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a `ICalculator` ukazuje, jak shromažďovat data ze služby za běhu.  
  
 Služba WMI je implementací standardu WBEM (Web-Based Enterprise Management) společností Microsoft. Další informace o sdk sady WMI naleznete v [tématu WMI Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page). WBEM je oborový standard pro to, jak aplikace zveřejňují nástroje pro správu externím nástrojům pro správu.  
  
 WCF implementuje zprostředkovatele služby WMI, součást, která zpřístupňuje instrumentaci za běhu prostřednictvím rozhraní kompatibilního s rozhraním WBEM. Nástroje pro správu se mohou připojit ke službám prostřednictvím rozhraní za běhu. WCF zveřejňuje atributy služeb, jako jsou adresy, vazby, chování a naslouchací procesy.  
  
 Vestavěný zprostředkovatel služby WMI je aktivován v konfiguračním souboru aplikace. To se provádí `wmiProviderEnabled` prostřednictvím atributu [ \<diagnostická>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) v části [ \<system.serviceModel>,](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) jak je znázorněno v následující konfiguraci ukázky:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Tato položka konfigurace zpřístupňuje rozhraní služby WMI. Aplikace pro správu se nyní mohou připojit prostřednictvím tohoto rozhraní a získat přístup k nástroji pro správu aplikace.  
  
## <a name="custom-wmi-object"></a>Vlastní objekt wmi  
 Přidání objektů služby WMI do služby umožňuje odhalit uživatelem definované informace spolu s informacemi o integrovaném zprostředkovateli služby WMI. Toho lze dosáhnout publikováním schématu služby do služby WMI pomocí aplikace Installutil.exe. Pokyny k dosažení tohoto cíle, spolu s dalšípodrobnosti naleznete v návodu k nastavení na konci tématu.  
  
## <a name="accessing-wmi-information"></a>Přístup k informacím o systému WMI  

K datům wmi lze přistupovat mnoha různými způsoby. Společnost Microsoft poskytuje rozhraní WMI rozhraní API pro skripty, aplikace jazyka Visual Basic, aplikace jazyka C++ a rozhraní .NET Framework. Další informace naleznete [v tématu Using WMI](/windows/desktop/wmisdk/using-wmi).
  
 Tato ukázka používá dva skripty jazyka Java: jeden pro výčet služeb spuštěných v počítači spolu s některými jejich vlastnostmi a druhý pro zobrazení uživatelem definovaných dat služby WMI. Skript otevře připojení k poskytovateli služby WMI, analyzuje data a zobrazí shromážděná data.  
  
 Spusťte ukázku a vytvořte spuštěnou instanci služby WCF. Během spuštění služby spusťte každý skript jazyka Java pomocí následujícího příkazu na příkazovém řádku:  
  
```console  
cscript EnumerateServices.js  
```  
  
 Skript přistupuje k instrumentaci obsažené ve službě a vytváří následující výstup:  
  
```console  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 Dále spusťte druhý skript Java a zobrazte uživatelem definovaná data služby WMI:  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 Skript přistupuje k uživatelem definované instrumentaci obsažené ve službách a vytváří následující výstup:  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 Výstup ukazuje, že v počítači je spuštěna jedna služba. Služba zpřístupňuje jeden koncový bod, který implementuje `ICalculator` smlouvy. Nastavení chování a vazby, které jsou implementovány koncový bod jsou uvedeny jako součet jednotlivých prvků zásobníku zasílání zpráv.  
  
 Služby WMI se neomezují pouze na odhalení nástrojů pro správu infrastruktury WCF. Aplikace můžete vystavit své vlastní datové položky specifické pro doménu prostřednictvím stejného mechanismu. Služba WMI je jednotný mechanismus pro kontrolu a kontrolu webové služby.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Publikovat schéma služeb do služby WMI spuštěním programu InstallUtil.exe (výchozí umístění souboru InstallUtil.exe je %WINDIR%\Microsoft.NET\Framework\v4.0.30319") v souboru service.dll v hostitelském adresáři. Tento krok je třeba provést pouze v případě, že byly provedeny změny v souboru service.dll.
  
4. Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Pokud jste nainstalovali WCF po instalaci ASP.NET, bude pravděpodobně nutné spustit %WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x, aby účet ASPNET měl oprávnění k publikování objektů služby WMI.  
  
5. Zobrazení dat ze vzorku, které se objevily prostřednictvím služby WMI pomocí příkazů: `cscript EnumerateServices.js` nebo `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Viz také

- [Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
