---
title: Poskytovatel WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 519f63f8dfc558a83a98ca44f74e926beb81c190
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327227"
---
# <a name="wmi-provider"></a><span data-ttu-id="261a6-102">Poskytovatel WMI</span><span class="sxs-lookup"><span data-stu-id="261a6-102">WMI Provider</span></span>
<span data-ttu-id="261a6-103">Tento příklad ukazuje, jak shromažďovat data ze služby Windows Communication Foundation (WCF) za běhu pomocí zprostředkovatele Windows Management Instrumentation (WMI), který je součástí WCF.</span><span class="sxs-lookup"><span data-stu-id="261a6-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="261a6-104">Tato ukázka také ukazuje, jak přidat ke službě WMI objekt definovaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="261a6-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="261a6-105">Ukázka aktivuje zprostředkovatele rozhraní WMI na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a ukazuje, jak shromažďovat data z `ICalculator` service za běhu.</span><span class="sxs-lookup"><span data-stu-id="261a6-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="261a6-106">Rozhraní WMI se výlučně implementace Microsoftu Web-Based Enterprise Management (WBEM) standard.</span><span class="sxs-lookup"><span data-stu-id="261a6-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="261a6-107">Další informace o sadě SDK rozhraní WMI najdete v tématu [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="261a6-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="261a6-108">WBEM je oborový standard pro aplikace jak vystavit WMI pro externí nástroje pro správu.</span><span class="sxs-lookup"><span data-stu-id="261a6-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="261a6-109">WCF implementuje zprostředkovatele WMI, komponenty, která zveřejňuje instrumentace za běhu pomocí rozhraní WBEM kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="261a6-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="261a6-110">Nástroje pro správu můžou připojit ke službám prostřednictvím rozhraní za běhu.</span><span class="sxs-lookup"><span data-stu-id="261a6-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="261a6-111">WCF zpřístupňuje atributy služeb, jako jsou adresy, vazby, chování a naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="261a6-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="261a6-112">Předdefinovaný poskytovatel rozhraní WMI dojde v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="261a6-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="261a6-113">To se provádí prostřednictvím `wmiProviderEnabled` atribut [ \<diagnostiky >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) v [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) části, jak je znázorněno v následující ukázce konfigurace:</span><span class="sxs-lookup"><span data-stu-id="261a6-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="261a6-114">Tato položka konfigurace vystavuje rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="261a6-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="261a6-115">Správa aplikací teď můžete připojit přes toto rozhraní a přístup WMI aplikace.</span><span class="sxs-lookup"><span data-stu-id="261a6-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="261a6-116">Vlastní WMI objekt</span><span class="sxs-lookup"><span data-stu-id="261a6-116">Custom WMI Object</span></span>  
 <span data-ttu-id="261a6-117">Přidání objektů WMI ke službě umožňuje zobrazit informace definované uživatelem, spolu s předdefinované informace o poskytovateli WMI.</span><span class="sxs-lookup"><span data-stu-id="261a6-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="261a6-118">Toho lze dosáhnout publikování schématu služby WMI pomocí Installutil.exe aplikace.</span><span class="sxs-lookup"><span data-stu-id="261a6-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="261a6-119">Pokyny k instalaci na konci tohoto tématu najdete pokyny k tomu, společně s další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="261a6-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="261a6-120">Přístup k informacím o rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="261a6-120">Accessing WMI Information</span></span>  
 <span data-ttu-id="261a6-121">Dat služby WMI může přistupovat mnoho různých způsobů.</span><span class="sxs-lookup"><span data-stu-id="261a6-121">WMI data can be accessed many different ways.</span></span> <span data-ttu-id="261a6-122">Společnost Microsoft poskytuje rozhraní API služby WMI pro skripty, Visual Basic aplikací, aplikací v jazyce C++ a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="261a6-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi).</span></span>  
  
 <span data-ttu-id="261a6-123">Tento příklad používá dva skripty v jazyce Java: jeden výčet služby spuštěné v počítači společně s jejich vlastností a druhou pro zobrazení dat služby WMI definovaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="261a6-123">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="261a6-124">Skript otevře připojení k poskytovateli služby WMI, analyzuje data a zobrazuje data, shromáždit.</span><span class="sxs-lookup"><span data-stu-id="261a6-124">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="261a6-125">Spuštění ukázky vytvořit běžící instance služby WCF.</span><span class="sxs-lookup"><span data-stu-id="261a6-125">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="261a6-126">Zatímco je služba spuštěna, spusťte každý skript jazyka Java pomocí následujícího příkazu na příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="261a6-126">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="261a6-127">Skript přistupuje k nim instrumentace obsažené ve službě a vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="261a6-127">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="261a6-128">V dalším kroku spusťte druhý skriptu Java pro zobrazení dat uživatelem definované rozhraní WMI:</span><span class="sxs-lookup"><span data-stu-id="261a6-128">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="261a6-129">Skript přistupuje k nim uživatelem definované instrumentace obsažené ve službách a vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="261a6-129">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="261a6-130">Výstup ukazuje, že je jediné služby spuštěné v počítači.</span><span class="sxs-lookup"><span data-stu-id="261a6-130">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="261a6-131">Služba poskytuje jeden koncový bod, který implementuje `ICalculator` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="261a6-131">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="261a6-132">Nastavení chování a vazby, které implementují koncového bodu jsou uvedené jako součet jednotlivých prvků zásobníkem zpráv.</span><span class="sxs-lookup"><span data-stu-id="261a6-132">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="261a6-133">Služba WMI není omezena pouze na vystavení WMI infrastruktury WCF.</span><span class="sxs-lookup"><span data-stu-id="261a6-133">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="261a6-134">Aplikace může zpřístupnit vlastní domény datových položek prostřednictvím stejný mechanismus.</span><span class="sxs-lookup"><span data-stu-id="261a6-134">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="261a6-135">Služba WMI není jednotný mechanismus pro řízení a kontrolu webové služby.</span><span class="sxs-lookup"><span data-stu-id="261a6-135">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="261a6-136">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="261a6-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="261a6-137">Ujistěte se dá provést [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="261a6-137">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="261a6-138">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="261a6-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="261a6-139">Publikování služby schématu WMI spuštěním InstallUtil.exe (výchozí umístění pro InstallUtil.exe je "% WINDIR%\Microsoft.NET\Framework\v4.0.30319") na service.dll soubor v adresáři hostování.</span><span class="sxs-lookup"><span data-stu-id="261a6-139">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="261a6-140">Tento krok je pouze potřeba provést, pokud byly provedeny změny do souboru service.dll.</span><span class="sxs-lookup"><span data-stu-id="261a6-140">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="261a6-141">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="261a6-141">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="261a6-142">Pokud jste nainstalovali WCF po instalaci technologie ASP.NET, budete muset spustit "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows komunikace Foundation\servicemodelreg.exe "- r - x oprávnění účtu ASPNET k publikování objektů WMI.</span><span class="sxs-lookup"><span data-stu-id="261a6-142">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="261a6-143">Zobrazit data z ukázkové prezentované prostřednictvím rozhraní WMI pomocí příkazů: `cscript EnumerateServices.js` nebo `cscript EnumerateCustomObjects.js`.</span><span class="sxs-lookup"><span data-stu-id="261a6-143">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="261a6-144">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="261a6-144">The samples may already be installed on your computer.</span></span> <span data-ttu-id="261a6-145">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="261a6-145">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="261a6-146">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="261a6-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="261a6-147">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="261a6-147">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="261a6-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="261a6-148">See also</span></span>

- [<span data-ttu-id="261a6-149">Ukázky AppFabric monitorování</span><span class="sxs-lookup"><span data-stu-id="261a6-149">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
