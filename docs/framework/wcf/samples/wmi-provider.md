---
title: Poskytovatel WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: d135466c402fa21b6a1b11f208ca900f58748bdb
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807303"
---
# <a name="wmi-provider"></a><span data-ttu-id="eaa06-102">Poskytovatel WMI</span><span class="sxs-lookup"><span data-stu-id="eaa06-102">WMI Provider</span></span>
<span data-ttu-id="eaa06-103">Tento příklad ukazuje, jak ke shromažďování dat ze služby Windows Communication Foundation (WCF) v době běhu pomocí zprostředkovatele Windows Management Instrumentation (WMI), která je integrována do WCF.</span><span class="sxs-lookup"><span data-stu-id="eaa06-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="eaa06-104">Tato ukázka také ukazuje, jak přidat objekt uživatelské rozhraní WMI pro službu.</span><span class="sxs-lookup"><span data-stu-id="eaa06-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="eaa06-105">Ukázka aktivuje zprostředkovatele rozhraní WMI na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a ukazuje, jak získat data z `ICalculator` služby za běhu.</span><span class="sxs-lookup"><span data-stu-id="eaa06-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="eaa06-106">Služba WMI je implementace Web-Based Enterprise Management (WBEM) standardní společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="eaa06-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="eaa06-107">Další informace o sadě SDK rozhraní WMI najdete v tématu [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx).</span><span class="sxs-lookup"><span data-stu-id="eaa06-107">For more information about the WMI SDK, see [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx).</span></span> <span data-ttu-id="eaa06-108">WBEM je oborový standard pro jak aplikace vystavit WMI pro externí nástroje pro správu.</span><span class="sxs-lookup"><span data-stu-id="eaa06-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="eaa06-109">WCF implementuje zprostředkovatele rozhraní WMI, komponenty, která zveřejňuje instrumentace za běhu prostřednictvím rozhraní WBEM kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="eaa06-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="eaa06-110">Nástroje pro správu můžete připojit ke službám prostřednictvím rozhraní za běhu.</span><span class="sxs-lookup"><span data-stu-id="eaa06-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="eaa06-111">WCF zpřístupní atributy služeb, jako je adresy, vazby, chování a naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="eaa06-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="eaa06-112">Předdefinované zprostředkovatele rozhraní WMI je aktivovaná v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="eaa06-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="eaa06-113">To se provádí prostřednictvím `wmiProviderEnabled` atribut [ \<diagnostics >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) v [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) části, jak znázorňuje následující ukázka konfigurace:</span><span class="sxs-lookup"><span data-stu-id="eaa06-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="eaa06-114">Tato položka konfigurace vystavuje rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="eaa06-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="eaa06-115">Aplikace pro správu teď můžete připojit přes toto rozhraní a přístup WMI aplikace.</span><span class="sxs-lookup"><span data-stu-id="eaa06-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="eaa06-116">Objekt vlastní WMI</span><span class="sxs-lookup"><span data-stu-id="eaa06-116">Custom WMI Object</span></span>  
 <span data-ttu-id="eaa06-117">Přidávání objektů WMI ke službě umožňuje odhalit uživatelem definované informace společně s integrovanou informace zprostředkovatele rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="eaa06-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="eaa06-118">To se provádí pomocí aplikace Installutil.exe publikování schématu služby WMI.</span><span class="sxs-lookup"><span data-stu-id="eaa06-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="eaa06-119">Pokyny k tomu, společně s další podrobnosti naleznete v pokynů pro instalaci na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="eaa06-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="eaa06-120">Přístup k informacím o rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="eaa06-120">Accessing WMI Information</span></span>  
 <span data-ttu-id="eaa06-121">Data rozhraní WMI je přístupná mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="eaa06-121">WMI data can be accessed many different ways.</span></span> <span data-ttu-id="eaa06-122">Společnost Microsoft poskytuje rozhraní API služby WMI pro skripty, aplikacích jazyka Visual Basic, aplikací C++ a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).</span><span class="sxs-lookup"><span data-stu-id="eaa06-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).</span></span>  
  
 <span data-ttu-id="eaa06-123">Tato ukázka používá dva skriptů jazyka Java: jednu pro zobrazení výčtu služby spuštěné v počítači spolu s některé jejich vlastností a druhou pro zobrazení dat uživatelské rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="eaa06-123">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="eaa06-124">Skript otevře připojení ke zprostředkovateli rozhraní WMI, analyzuje data a zobrazí údaje získané.</span><span class="sxs-lookup"><span data-stu-id="eaa06-124">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="eaa06-125">Spusťte vzorek k vytvoření spuštěnou instanci služby WCF.</span><span class="sxs-lookup"><span data-stu-id="eaa06-125">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="eaa06-126">Když je služba spuštěná, spusťte skript každý Java pomocí následujícího příkazu na příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="eaa06-126">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="eaa06-127">Skript přistupuje k instrumentaci obsažené ve službě a vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="eaa06-127">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="eaa06-128">Potom spusťte druhý Java skript, který chcete zobrazit data uživatelské rozhraní WMI:</span><span class="sxs-lookup"><span data-stu-id="eaa06-128">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="eaa06-129">Skript přistupuje k instrumentaci uživatelem definované součástí služby a vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="eaa06-129">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="eaa06-130">Výstup ukazuje, že je jediná služba na tomto počítači spuštěna.</span><span class="sxs-lookup"><span data-stu-id="eaa06-130">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="eaa06-131">Službu zpřístupní jeden koncový bod, který implementuje `ICalculator` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="eaa06-131">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="eaa06-132">Nastavení chování a vazby, které jsou implementované v koncovém bodě jsou uvedeny jako součet jednotlivých elementů zasílání zpráv zásobníku.</span><span class="sxs-lookup"><span data-stu-id="eaa06-132">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="eaa06-133">Rozhraní WMI se neomezuje na vystavení WMI infrastruktury WCF.</span><span class="sxs-lookup"><span data-stu-id="eaa06-133">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="eaa06-134">Aplikace můžou zpřístupnit vlastní položky dat specifické pro doménu prostřednictvím shodný mechanismus.</span><span class="sxs-lookup"><span data-stu-id="eaa06-134">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="eaa06-135">Služba WMI je jednotná mechanismus kontroly a řízení webové služby.</span><span class="sxs-lookup"><span data-stu-id="eaa06-135">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eaa06-136">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="eaa06-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="eaa06-137">Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eaa06-137">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="eaa06-138">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eaa06-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="eaa06-139">Publikujte schéma služby WMI na service.dll soubor v adresáři hostování spuštěním InstallUtil.exe (výchozí umístění InstallUtil.exe je "% WINDIR%\Microsoft.NET\Framework\v4.0.30319").</span><span class="sxs-lookup"><span data-stu-id="eaa06-139">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="eaa06-140">Tento krok stačí provést, pokud byly provedeny změny do souboru service.dll.</span><span class="sxs-lookup"><span data-stu-id="eaa06-140">This step only needs to be executed when changes have been made to the service.dll file.</span></span> <span data-ttu-id="eaa06-141">Další informace najdete v tématu poskytuje informace o správě instrumentaci aplikace v: http://msdn2.microsoft.com/library/ms186147.aspx v části "Jak k: publikování schéma k rozhraní WMI pro Instrumentovány aplikace".</span><span class="sxs-lookup"><span data-stu-id="eaa06-141">For more information, see Providing Management Information by Instrumenting Applications at: http://msdn2.microsoft.com/library/ms186147.aspx in the "How To: Publish the Scheme to WMI for an Instrumented Application" section.</span></span>  
  
4.  <span data-ttu-id="eaa06-142">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eaa06-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eaa06-143">Pokud jste nainstalovali WCF po instalaci technologie ASP.NET, budete muset spustit "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows komunikace Foundation\servicemodelreg.exe "- r - x oprávnění účtu ASPNET k publikování objekty rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="eaa06-143">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5.  <span data-ttu-id="eaa06-144">Zobrazit data z ukázkové prezentované prostřednictvím rozhraní WMI pomocí příkazů: `cscript EnumerateServices.js` nebo `cscript EnumerateCustomObjects.js`.</span><span class="sxs-lookup"><span data-stu-id="eaa06-144">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eaa06-145">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="eaa06-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="eaa06-146">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="eaa06-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="eaa06-147">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="eaa06-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eaa06-148">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="eaa06-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="eaa06-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="eaa06-149">See Also</span></span>  
 [<span data-ttu-id="eaa06-150">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="eaa06-150">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
