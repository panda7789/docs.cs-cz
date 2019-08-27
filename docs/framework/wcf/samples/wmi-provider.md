---
title: Poskytovatel WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 89e2d370919519953e714cb0d0020587b3f53c9d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038512"
---
# <a name="wmi-provider"></a>Poskytovatel WMI
Tato ukázka předvádí, jak shromažďovat data ze služeb Windows Communication Foundation (WCF) za běhu pomocí poskytovatele rozhraní WMI (Windows Management Instrumentation) (WMI), který je integrovaný do WCF. Tato ukázka také ukazuje, jak přidat uživatelem definovaný objekt WMI do služby. Ukázka aktivuje zprostředkovatele rozhraní WMI pro [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a ukazuje, jak shromažďovat data ze `ICalculator` služby za běhu.  
  
 WMI je implementace standardu WBEM (Web-Based Enterprise Management) od Microsoftu. Další informace o sadě WMI SDK naleznete v tématu [rozhraní WMI (Windows Management Instrumentation)](/windows/desktop/WmiSdk/wmi-start-page). WBEM je oborovým standardem, jak aplikace vystavují instrumentaci pro správu externích nástrojů pro správu.  
  
 Služba WCF implementuje poskytovatele rozhraní WMI, součást, která zpřístupňuje instrumentaci za běhu prostřednictvím rozhraní kompatibilního se standardem WBEM. Nástroje pro správu se můžou ke službám připojit prostřednictvím rozhraní za běhu. WCF zpřístupňuje atributy služeb, jako jsou adresy, vazby, chování a naslouchací procesy.  
  
 V konfiguračním souboru aplikace je aktivovaný integrovaný zprostředkovatel rozhraní WMI. To se provádí pomocí `wmiProviderEnabled` atributu [ \<> diagnostiky](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) v [ \<části System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , jak je znázorněno v následující ukázkové konfiguraci:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Tato položka konfigurace zpřístupňuje rozhraní WMI. Aplikace pro správu se teď můžou přes toto rozhraní připojit a přistupovat k instrumentaci správy aplikace.  
  
## <a name="custom-wmi-object"></a>Vlastní objekt WMI  
 Přidání objektů WMI do služby umožňuje zobrazit uživatelsky definované informace spolu s integrovanými informacemi o zprostředkovateli rozhraní WMI. Toho je možné dosáhnout publikováním schématu služby do služby WMI pomocí aplikace Installutil. exe. Pokyny k tomuto účelu, společně s dalšími podrobnostmi, najdete v pokynech k instalaci na konci tématu.  
  
## <a name="accessing-wmi-information"></a>Přístup k informacím WMI  
 Data rozhraní WMI jsou dostupná mnoha různými způsoby. Společnost Microsoft poskytuje rozhraní API služby WMI pro skripty, C++ Visual Basic aplikace, aplikace a .NET Framework https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi) (.  
  
 Tato ukázka používá dva skripty Java: jednu k vytvoření výčtu služeb spuštěných v počítači společně s některými jejich vlastnostmi a druhou pro zobrazení uživatelsky definovaných dat WMI. Skript otevře připojení ke zprostředkovateli rozhraní WMI, analyzuje data a zobrazí shromážděná data.  
  
 Spusťte ukázku pro vytvoření spuštěné instance služby WCF. Když je služba spuštěná, spusťte každý skript Java pomocí následujícího příkazu na příkazovém řádku:  
  
```  
cscript EnumerateServices.js  
```  
  
 Skript přistupuje k instrumentaci obsaženému ve službě a generuje následující výstup:  
  
```  
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
  
 V dalším kroku spusťte druhý skript Java, který zobrazí uživatelem definovaná data rozhraní WMI:  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 Skript přistupuje k uživatelsky definovanému instrumentaci obsaženému ve službách a generuje následující výstup:  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 Výstup ukazuje, že v počítači je spuštěna jedna služba. Služba zpřístupňuje jeden koncový bod, který `ICalculator` implementuje kontrakt. Nastavení chování a vazeb, která jsou implementována koncovým bodem, jsou uvedena jako součet jednotlivých prvků zásobníku zpráv.  
  
 Rozhraní WMI není omezené na vystavení instrumentace infrastruktury WCF. Aplikace může vystavit vlastní datové položky specifické pro doménu přes stejný mechanismus. WMI je jednotný mechanismus pro kontrolu a kontrolu webové služby.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste v Windows Communication Foundation Samples provedli [postup jednorázového nastavení](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Publikujte schéma služby pro rozhraní WMI spuštěním příkazu InstallUtil. exe (výchozí umístění pro InstallUtil. exe je "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") v souboru Service. dll v adresáři hostování. Tento krok je nutné provést pouze v případě, že byly provedeny změny v souboru Service. dll.
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Pokud jste nainstalovali WCF po instalaci ASP.NET, bude pravděpodobně nutné spustit "% WINDIR% \ Microsoft. Net\Framework\v3.0\Windows Communications Foundation\servicemodelreg.exe "-r-x" udělte účtu ASPNET oprávnění k publikování objektů WMI.  
  
5. Zobrazit data z ukázky, která se procházela prostřednictvím rozhraní WMI, `cscript EnumerateServices.js` pomocí `cscript EnumerateCustomObjects.js`příkazů: nebo.  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Viz také:

- [Ukázky monitorování technologie AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
