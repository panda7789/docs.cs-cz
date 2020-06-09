---
title: Poskytovatel WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: a01b4b70d4c497d1efb93bb53a7339f5f7f29ef9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591043"
---
# <a name="wmi-provider"></a><span data-ttu-id="9bad8-102">Poskytovatel WMI</span><span class="sxs-lookup"><span data-stu-id="9bad8-102">WMI Provider</span></span>
<span data-ttu-id="9bad8-103">Tato ukázka předvádí, jak shromažďovat data ze služeb Windows Communication Foundation (WCF) za běhu pomocí poskytovatele rozhraní WMI (Windows Management Instrumentation) (WMI), který je integrovaný do WCF.</span><span class="sxs-lookup"><span data-stu-id="9bad8-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="9bad8-104">Tato ukázka také ukazuje, jak přidat uživatelem definovaný objekt WMI do služby.</span><span class="sxs-lookup"><span data-stu-id="9bad8-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="9bad8-105">Ukázka aktivuje zprostředkovatele rozhraní WMI pro [Začínáme](getting-started-sample.md) a ukazuje, jak shromažďovat data ze `ICalculator` služby za běhu.</span><span class="sxs-lookup"><span data-stu-id="9bad8-105">The sample activates the WMI provider for the [Getting Started](getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="9bad8-106">WMI je implementace standardu WBEM (Web-Based Enterprise Management) od Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="9bad8-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="9bad8-107">Další informace o sadě WMI SDK naleznete v tématu [rozhraní WMI (Windows Management Instrumentation)](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="9bad8-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="9bad8-108">WBEM je oborovým standardem, jak aplikace vystavují instrumentaci pro správu externích nástrojů pro správu.</span><span class="sxs-lookup"><span data-stu-id="9bad8-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="9bad8-109">Služba WCF implementuje poskytovatele rozhraní WMI, součást, která zpřístupňuje instrumentaci za běhu prostřednictvím rozhraní kompatibilního se standardem WBEM.</span><span class="sxs-lookup"><span data-stu-id="9bad8-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="9bad8-110">Nástroje pro správu se můžou ke službám připojit prostřednictvím rozhraní za běhu.</span><span class="sxs-lookup"><span data-stu-id="9bad8-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="9bad8-111">WCF zpřístupňuje atributy služeb, jako jsou adresy, vazby, chování a naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="9bad8-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="9bad8-112">V konfiguračním souboru aplikace je aktivovaný integrovaný zprostředkovatel rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="9bad8-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="9bad8-113">To se provádí pomocí `wmiProviderEnabled` atributu [\<diagnostics>](../../configure-apps/file-schema/wcf/diagnostics.md) v [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) části, jak je znázorněno v následující ukázkové konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="9bad8-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9bad8-114">Tato položka konfigurace zpřístupňuje rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="9bad8-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="9bad8-115">Aplikace pro správu se teď můžou přes toto rozhraní připojit a přistupovat k instrumentaci správy aplikace.</span><span class="sxs-lookup"><span data-stu-id="9bad8-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="9bad8-116">Vlastní objekt WMI</span><span class="sxs-lookup"><span data-stu-id="9bad8-116">Custom WMI Object</span></span>  
 <span data-ttu-id="9bad8-117">Přidání objektů WMI do služby umožňuje zobrazit uživatelsky definované informace spolu s integrovanými informacemi o zprostředkovateli rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="9bad8-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="9bad8-118">Toho je možné dosáhnout publikováním schématu služby do služby WMI pomocí aplikace Installutil. exe.</span><span class="sxs-lookup"><span data-stu-id="9bad8-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="9bad8-119">Pokyny k tomuto účelu, společně s dalšími podrobnostmi, najdete v pokynech k instalaci na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="9bad8-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="9bad8-120">Přístup k informacím WMI</span><span class="sxs-lookup"><span data-stu-id="9bad8-120">Accessing WMI Information</span></span>  

<span data-ttu-id="9bad8-121">K datům WMI lze přistupovat mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="9bad8-121">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="9bad8-122">Microsoft poskytuje rozhraní API služby WMI pro skripty, Visual Basic aplikace, aplikace C++ a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9bad8-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="9bad8-123">Další informace najdete v tématu [použití rozhraní WMI](/windows/desktop/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="9bad8-123">For more information, see [Using WMI](/windows/desktop/wmisdk/using-wmi).</span></span>
  
 <span data-ttu-id="9bad8-124">Tato ukázka používá dva skripty Java: jednu k vytvoření výčtu služeb spuštěných v počítači společně s některými jejich vlastnostmi a druhou pro zobrazení uživatelsky definovaných dat WMI.</span><span class="sxs-lookup"><span data-stu-id="9bad8-124">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="9bad8-125">Skript otevře připojení ke zprostředkovateli rozhraní WMI, analyzuje data a zobrazí shromážděná data.</span><span class="sxs-lookup"><span data-stu-id="9bad8-125">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="9bad8-126">Spusťte ukázku pro vytvoření spuštěné instance služby WCF.</span><span class="sxs-lookup"><span data-stu-id="9bad8-126">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="9bad8-127">Když je služba spuštěná, spusťte každý skript Java pomocí následujícího příkazu na příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="9bad8-127">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```console  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="9bad8-128">Skript přistupuje k instrumentaci obsaženému ve službě a generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9bad8-128">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="9bad8-129">V dalším kroku spusťte druhý skript Java, který zobrazí uživatelem definovaná data rozhraní WMI:</span><span class="sxs-lookup"><span data-stu-id="9bad8-129">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="9bad8-130">Skript přistupuje k uživatelsky definovanému instrumentaci obsaženému ve službách a generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9bad8-130">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="9bad8-131">Výstup ukazuje, že v počítači je spuštěna jedna služba.</span><span class="sxs-lookup"><span data-stu-id="9bad8-131">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="9bad8-132">Služba zpřístupňuje jeden koncový bod, který implementuje `ICalculator` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="9bad8-132">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="9bad8-133">Nastavení chování a vazeb, která jsou implementována koncovým bodem, jsou uvedena jako součet jednotlivých prvků zásobníku zpráv.</span><span class="sxs-lookup"><span data-stu-id="9bad8-133">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="9bad8-134">Rozhraní WMI není omezené na vystavení instrumentace infrastruktury WCF.</span><span class="sxs-lookup"><span data-stu-id="9bad8-134">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="9bad8-135">Aplikace může vystavit vlastní datové položky specifické pro doménu přes stejný mechanismus.</span><span class="sxs-lookup"><span data-stu-id="9bad8-135">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="9bad8-136">WMI je jednotný mechanismus pro kontrolu a kontrolu webové služby.</span><span class="sxs-lookup"><span data-stu-id="9bad8-136">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9bad8-137">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="9bad8-137">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9bad8-138">Ujistěte se, že jste v [Windows Communication Foundation Samples provedli postup jednorázového nastavení](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9bad8-138">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9bad8-139">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9bad8-139">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9bad8-140">Publikujte schéma služby pro rozhraní WMI spuštěním příkazu InstallUtil. exe (výchozí umístění pro InstallUtil. exe je "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") v souboru Service. dll v adresáři hostování.</span><span class="sxs-lookup"><span data-stu-id="9bad8-140">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="9bad8-141">Tento krok je nutné provést pouze v případě, že byly provedeny změny v souboru Service. dll.</span><span class="sxs-lookup"><span data-stu-id="9bad8-141">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="9bad8-142">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9bad8-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9bad8-143">Pokud jste nainstalovali WCF po instalaci ASP.NET, bude pravděpodobně nutné spustit "% WINDIR% \ Microsoft. Net\Framework\v3.0\Windows Communications Foundation\servicemodelreg.exe "-r-x" udělte účtu ASPNET oprávnění k publikování objektů WMI.</span><span class="sxs-lookup"><span data-stu-id="9bad8-143">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="9bad8-144">Zobrazit data z ukázky, která se procházela prostřednictvím rozhraní WMI, pomocí příkazů: `cscript EnumerateServices.js` nebo `cscript EnumerateCustomObjects.js` .</span><span class="sxs-lookup"><span data-stu-id="9bad8-144">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9bad8-145">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="9bad8-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9bad8-146">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="9bad8-146">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9bad8-147">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="9bad8-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9bad8-148">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9bad8-148">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="9bad8-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="9bad8-149">See also</span></span>

- <span data-ttu-id="9bad8-150">[Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9bad8-150">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
