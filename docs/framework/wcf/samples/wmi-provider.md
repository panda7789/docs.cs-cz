---
title: Poskytovatel WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: dd24a6d270a0bd9012bbda2a53913167c9697bc5
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424517"
---
# <a name="wmi-provider"></a><span data-ttu-id="2f447-102">Poskytovatel WMI</span><span class="sxs-lookup"><span data-stu-id="2f447-102">WMI Provider</span></span>
<span data-ttu-id="2f447-103">Tato ukázka předvádí, jak shromažďovat data ze služeb Windows Communication Foundation (WCF) za běhu pomocí poskytovatele rozhraní WMI (Windows Management Instrumentation) (WMI), který je integrovaný do WCF.</span><span class="sxs-lookup"><span data-stu-id="2f447-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="2f447-104">Tato ukázka také ukazuje, jak přidat uživatelem definovaný objekt WMI do služby.</span><span class="sxs-lookup"><span data-stu-id="2f447-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="2f447-105">Ukázka aktivuje zprostředkovatele rozhraní WMI pro [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a ukazuje, jak shromažďovat data ze služby `ICalculator` za běhu.</span><span class="sxs-lookup"><span data-stu-id="2f447-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="2f447-106">WMI je implementace standardu WBEM (Web-Based Enterprise Management) od Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="2f447-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="2f447-107">Další informace o sadě WMI SDK naleznete v tématu [rozhraní WMI (Windows Management Instrumentation)](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="2f447-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="2f447-108">WBEM je oborovým standardem, jak aplikace vystavují instrumentaci pro správu externích nástrojů pro správu.</span><span class="sxs-lookup"><span data-stu-id="2f447-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="2f447-109">Služba WCF implementuje poskytovatele rozhraní WMI, součást, která zpřístupňuje instrumentaci za běhu prostřednictvím rozhraní kompatibilního se standardem WBEM.</span><span class="sxs-lookup"><span data-stu-id="2f447-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="2f447-110">Nástroje pro správu se můžou ke službám připojit prostřednictvím rozhraní za běhu.</span><span class="sxs-lookup"><span data-stu-id="2f447-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="2f447-111">WCF zpřístupňuje atributy služeb, jako jsou adresy, vazby, chování a naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="2f447-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="2f447-112">V konfiguračním souboru aplikace je aktivovaný integrovaný zprostředkovatel rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="2f447-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="2f447-113">To se provádí pomocí atributu `wmiProviderEnabled` [\<diagnostiky >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) v části [\<system. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , jak je znázorněno v následující ukázkové konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="2f447-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="2f447-114">Tato položka konfigurace zpřístupňuje rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="2f447-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="2f447-115">Aplikace pro správu se teď můžou přes toto rozhraní připojit a přistupovat k instrumentaci správy aplikace.</span><span class="sxs-lookup"><span data-stu-id="2f447-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="2f447-116">Vlastní objekt WMI</span><span class="sxs-lookup"><span data-stu-id="2f447-116">Custom WMI Object</span></span>  
 <span data-ttu-id="2f447-117">Přidání objektů WMI do služby umožňuje zobrazit uživatelsky definované informace spolu s integrovanými informacemi o zprostředkovateli rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="2f447-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="2f447-118">Toho je možné dosáhnout publikováním schématu služby do služby WMI pomocí aplikace Installutil. exe.</span><span class="sxs-lookup"><span data-stu-id="2f447-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="2f447-119">Pokyny k tomuto účelu, společně s dalšími podrobnostmi, najdete v pokynech k instalaci na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="2f447-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="2f447-120">Přístup k informacím WMI</span><span class="sxs-lookup"><span data-stu-id="2f447-120">Accessing WMI Information</span></span>  
 <span data-ttu-id="2f447-121">Data rozhraní WMI jsou dostupná mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="2f447-121">WMI data can be accessed many different ways.</span></span> <span data-ttu-id="2f447-122">Společnost Microsoft poskytuje rozhraní API služby WMI pro skripty, C++ Visual Basic aplikace, aplikace a .NET Framework (https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="2f447-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework (https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi).</span></span>  
  
 <span data-ttu-id="2f447-123">Tato ukázka používá dva skripty Java: jednu k vytvoření výčtu služeb spuštěných v počítači společně s některými jejich vlastnostmi a druhou pro zobrazení uživatelsky definovaných dat WMI.</span><span class="sxs-lookup"><span data-stu-id="2f447-123">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="2f447-124">Skript otevře připojení ke zprostředkovateli rozhraní WMI, analyzuje data a zobrazí shromážděná data.</span><span class="sxs-lookup"><span data-stu-id="2f447-124">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="2f447-125">Spusťte ukázku pro vytvoření spuštěné instance služby WCF.</span><span class="sxs-lookup"><span data-stu-id="2f447-125">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="2f447-126">Když je služba spuštěná, spusťte každý skript Java pomocí následujícího příkazu na příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="2f447-126">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```console  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="2f447-127">Skript přistupuje k instrumentaci obsaženému ve službě a generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2f447-127">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="2f447-128">V dalším kroku spusťte druhý skript Java, který zobrazí uživatelem definovaná data rozhraní WMI:</span><span class="sxs-lookup"><span data-stu-id="2f447-128">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="2f447-129">Skript přistupuje k uživatelsky definovanému instrumentaci obsaženému ve službách a generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2f447-129">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```console 
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="2f447-130">Výstup ukazuje, že v počítači je spuštěna jedna služba.</span><span class="sxs-lookup"><span data-stu-id="2f447-130">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="2f447-131">Služba zpřístupňuje jeden koncový bod, který implementuje `ICalculator` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="2f447-131">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="2f447-132">Nastavení chování a vazeb, která jsou implementována koncovým bodem, jsou uvedena jako součet jednotlivých prvků zásobníku zpráv.</span><span class="sxs-lookup"><span data-stu-id="2f447-132">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="2f447-133">Rozhraní WMI není omezené na vystavení instrumentace infrastruktury WCF.</span><span class="sxs-lookup"><span data-stu-id="2f447-133">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="2f447-134">Aplikace může vystavit vlastní datové položky specifické pro doménu přes stejný mechanismus.</span><span class="sxs-lookup"><span data-stu-id="2f447-134">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="2f447-135">WMI je jednotný mechanismus pro kontrolu a kontrolu webové služby.</span><span class="sxs-lookup"><span data-stu-id="2f447-135">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2f447-136">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="2f447-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2f447-137">Ujistěte se, že jste v [Windows Communication Foundation Samples provedli postup jednorázového nastavení](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2f447-137">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2f447-138">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2f447-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2f447-139">Publikujte schéma služby pro rozhraní WMI spuštěním příkazu InstallUtil. exe (výchozí umístění pro InstallUtil. exe je "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") v souboru Service. dll v adresáři hostování.</span><span class="sxs-lookup"><span data-stu-id="2f447-139">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="2f447-140">Tento krok je nutné provést pouze v případě, že byly provedeny změny v souboru Service. dll.</span><span class="sxs-lookup"><span data-stu-id="2f447-140">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="2f447-141">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2f447-141">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2f447-142">Pokud jste nainstalovali WCF po instalaci ASP.NET, bude pravděpodobně nutné spustit "% WINDIR% \ Microsoft. Net\Framework\v3.0\Windows Communications Foundation\servicemodelreg.exe "-r-x" udělte účtu ASPNET oprávnění k publikování objektů WMI.</span><span class="sxs-lookup"><span data-stu-id="2f447-142">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="2f447-143">Pomocí příkazů `cscript EnumerateServices.js` nebo `cscript EnumerateCustomObjects.js`si zobrazte data z ukázky, která se procházela prostřednictvím rozhraní WMI:</span><span class="sxs-lookup"><span data-stu-id="2f447-143">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2f447-144">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="2f447-144">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2f447-145">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="2f447-145">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="2f447-146">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="2f447-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2f447-147">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2f447-147">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="2f447-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f447-148">See also</span></span>

- [<span data-ttu-id="2f447-149">Ukázky monitorování technologie AppFabric</span><span class="sxs-lookup"><span data-stu-id="2f447-149">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
