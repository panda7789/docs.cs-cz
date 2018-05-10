---
title: Poskytovatel WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: d135466c402fa21b6a1b11f208ca900f58748bdb
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="wmi-provider"></a>Poskytovatel WMI
Tento příklad ukazuje, jak ke shromažďování dat ze služby Windows Communication Foundation (WCF) v době běhu pomocí zprostředkovatele Windows Management Instrumentation (WMI), která je integrována do WCF. Tato ukázka také ukazuje, jak přidat objekt uživatelské rozhraní WMI pro službu. Ukázka aktivuje zprostředkovatele rozhraní WMI na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a ukazuje, jak získat data z `ICalculator` služby za běhu.  
  
 Služba WMI je implementace Web-Based Enterprise Management (WBEM) standardní společnosti Microsoft. Další informace o sadě SDK rozhraní WMI najdete v tématu [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx). WBEM je oborový standard pro jak aplikace vystavit WMI pro externí nástroje pro správu.  
  
 WCF implementuje zprostředkovatele rozhraní WMI, komponenty, která zveřejňuje instrumentace za běhu prostřednictvím rozhraní WBEM kompatibilní. Nástroje pro správu můžete připojit ke službám prostřednictvím rozhraní za běhu. WCF zpřístupní atributy služeb, jako je adresy, vazby, chování a naslouchací procesy.  
  
 Předdefinované zprostředkovatele rozhraní WMI je aktivovaná v konfiguračním souboru aplikace. To se provádí prostřednictvím `wmiProviderEnabled` atribut [ \<diagnostics >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) v [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) části, jak znázorňuje následující ukázka konfigurace:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Tato položka konfigurace vystavuje rozhraní WMI. Aplikace pro správu teď můžete připojit přes toto rozhraní a přístup WMI aplikace.  
  
## <a name="custom-wmi-object"></a>Objekt vlastní WMI  
 Přidávání objektů WMI ke službě umožňuje odhalit uživatelem definované informace společně s integrovanou informace zprostředkovatele rozhraní WMI. To se provádí pomocí aplikace Installutil.exe publikování schématu služby WMI. Pokyny k tomu, společně s další podrobnosti naleznete v pokynů pro instalaci na konci tohoto tématu.  
  
## <a name="accessing-wmi-information"></a>Přístup k informacím o rozhraní WMI  
 Data rozhraní WMI je přístupná mnoha různými způsoby. Společnost Microsoft poskytuje rozhraní API služby WMI pro skripty, aplikacích jazyka Visual Basic, aplikací C++ a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).  
  
 Tato ukázka používá dva skriptů jazyka Java: jednu pro zobrazení výčtu služby spuštěné v počítači spolu s některé jejich vlastností a druhou pro zobrazení dat uživatelské rozhraní WMI. Skript otevře připojení ke zprostředkovateli rozhraní WMI, analyzuje data a zobrazí údaje získané.  
  
 Spusťte vzorek k vytvoření spuštěnou instanci služby WCF. Když je služba spuštěná, spusťte skript každý Java pomocí následujícího příkazu na příkazovém řádku:  
  
```  
cscript EnumerateServices.js  
```  
  
 Skript přistupuje k instrumentaci obsažené ve službě a vytvoří následující výstup:  
  
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
  
 Potom spusťte druhý Java skript, který chcete zobrazit data uživatelské rozhraní WMI:  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 Skript přistupuje k instrumentaci uživatelem definované součástí služby a vytvoří následující výstup:  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 Výstup ukazuje, že je jediná služba na tomto počítači spuštěna. Službu zpřístupní jeden koncový bod, který implementuje `ICalculator` kontrakt. Nastavení chování a vazby, které jsou implementované v koncovém bodě jsou uvedeny jako součet jednotlivých elementů zasílání zpráv zásobníku.  
  
 Rozhraní WMI se neomezuje na vystavení WMI infrastruktury WCF. Aplikace můžou zpřístupnit vlastní položky dat specifické pro doménu prostřednictvím shodný mechanismus. Služba WMI je jednotná mechanismus kontroly a řízení webové služby.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Publikujte schéma služby WMI na service.dll soubor v adresáři hostování spuštěním InstallUtil.exe (výchozí umístění InstallUtil.exe je "% WINDIR%\Microsoft.NET\Framework\v4.0.30319"). Tento krok stačí provést, pokud byly provedeny změny do souboru service.dll. Další informace najdete v tématu poskytuje informace o správě instrumentaci aplikace v: http://msdn2.microsoft.com/library/ms186147.aspx v části "Jak k: publikování schéma k rozhraní WMI pro Instrumentovány aplikace".  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Pokud jste nainstalovali WCF po instalaci technologie ASP.NET, budete muset spustit "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows komunikace Foundation\servicemodelreg.exe "- r - x oprávnění účtu ASPNET k publikování objekty rozhraní WMI.  
  
5.  Zobrazit data z ukázkové prezentované prostřednictvím rozhraní WMI pomocí příkazů: `cscript EnumerateServices.js` nebo `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
