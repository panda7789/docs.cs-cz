---
title: Poskytovatel WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: c3eb97537706282491de1863224e1502d6b56fda
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43532858"
---
# <a name="wmi-provider"></a>Poskytovatel WMI
Tento příklad ukazuje, jak shromažďovat data ze služby Windows Communication Foundation (WCF) za běhu pomocí zprostředkovatele Windows Management Instrumentation (WMI), který je součástí WCF. Tato ukázka také ukazuje, jak přidat ke službě WMI objekt definovaný uživatelem. Ukázka aktivuje zprostředkovatele rozhraní WMI na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a ukazuje, jak shromažďovat data z `ICalculator` service za běhu.  
  
 Rozhraní WMI se výlučně implementace Microsoftu Web-Based Enterprise Management (WBEM) standard. Další informace o sadě SDK rozhraní WMI najdete v tématu [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page). WBEM je oborový standard pro aplikace jak vystavit WMI pro externí nástroje pro správu.  
  
 WCF implementuje zprostředkovatele WMI, komponenty, která zveřejňuje instrumentace za běhu pomocí rozhraní WBEM kompatibilní. Nástroje pro správu můžou připojit ke službám prostřednictvím rozhraní za běhu. WCF zpřístupňuje atributy služeb, jako jsou adresy, vazby, chování a naslouchací procesy.  
  
 Předdefinovaný poskytovatel rozhraní WMI dojde v konfiguračním souboru aplikace. To se provádí prostřednictvím `wmiProviderEnabled` atribut [ \<diagnostiky >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) v [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) části, jak je znázorněno v následující ukázce konfigurace:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Tato položka konfigurace vystavuje rozhraní WMI. Správa aplikací teď můžete připojit přes toto rozhraní a přístup WMI aplikace.  
  
## <a name="custom-wmi-object"></a>Vlastní WMI objekt  
 Přidání objektů WMI ke službě umožňuje zobrazit informace definované uživatelem, spolu s předdefinované informace o poskytovateli WMI. Toho lze dosáhnout publikování schématu služby WMI pomocí Installutil.exe aplikace. Pokyny k instalaci na konci tohoto tématu najdete pokyny k tomu, společně s další podrobnosti.  
  
## <a name="accessing-wmi-information"></a>Přístup k informacím o rozhraní WMI  
 Dat služby WMI může přistupovat mnoho různých způsobů. Společnost Microsoft poskytuje rozhraní API služby WMI pro skripty, Visual Basic aplikací, aplikací v jazyce C++ a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).  
  
 Tento příklad používá dva skripty v jazyce Java: jeden výčet služby spuštěné v počítači společně s jejich vlastností a druhou pro zobrazení dat služby WMI definovaný uživatelem. Skript otevře připojení k poskytovateli služby WMI, analyzuje data a zobrazuje data, shromáždit.  
  
 Spuštění ukázky vytvořit běžící instance služby WCF. Zatímco je služba spuštěna, spusťte každý skript jazyka Java pomocí následujícího příkazu na příkazovém řádku:  
  
```  
cscript EnumerateServices.js  
```  
  
 Skript přistupuje k nim instrumentace obsažené ve službě a vytvoří následující výstup:  
  
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
  
 V dalším kroku spusťte druhý skriptu Java pro zobrazení dat uživatelem definované rozhraní WMI:  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 Skript přistupuje k nim uživatelem definované instrumentace obsažené ve službách a vytvoří následující výstup:  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 Výstup ukazuje, že je jediné služby spuštěné v počítači. Služba poskytuje jeden koncový bod, který implementuje `ICalculator` kontraktu. Nastavení chování a vazby, které implementují koncového bodu jsou uvedené jako součet jednotlivých prvků zásobníkem zpráv.  
  
 Služba WMI není omezena pouze na vystavení WMI infrastruktury WCF. Aplikace může zpřístupnit vlastní domény datových položek prostřednictvím stejný mechanismus. Služba WMI není jednotný mechanismus pro řízení a kontrolu webové služby.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se dá provést [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Publikování služby schématu WMI spuštěním InstallUtil.exe (výchozí umístění pro InstallUtil.exe je "% WINDIR%\Microsoft.NET\Framework\v4.0.30319") na service.dll soubor v adresáři hostování. Tento krok je pouze potřeba provést, pokud byly provedeny změny do souboru service.dll. Další informace najdete v tématu poskytuje informace o správě instrumentace aplikace v: http://msdn2.microsoft.com/library/ms186147.aspx v části "Jak na: publikování schéma k rozhraní WMI pro instrumentované aplikace".  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Pokud jste nainstalovali WCF po instalaci technologie ASP.NET, budete muset spustit "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows komunikace Foundation\servicemodelreg.exe "- r - x oprávnění účtu ASPNET k publikování objektů WMI.  
  
5.  Zobrazit data z ukázkové prezentované prostřednictvím rozhraní WMI pomocí příkazů: `cscript EnumerateServices.js` nebo `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)
