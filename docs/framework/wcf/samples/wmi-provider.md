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
# <a name="wmi-provider"></a><span data-ttu-id="37510-102">Poskytovatel WMI</span><span class="sxs-lookup"><span data-stu-id="37510-102">WMI Provider</span></span>
<span data-ttu-id="37510-103">Tato ukázka ukazuje, jak shromažďovat data ze služeb WCF (Windows Communication Foundation) za běhu pomocí zprostředkovatele WMI (WMI) služby WMI ( WMI), který je integrován do WCF.</span><span class="sxs-lookup"><span data-stu-id="37510-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="37510-104">Tato ukázka také ukazuje, jak přidat uživatelem definovaný objekt služby WMI do služby.</span><span class="sxs-lookup"><span data-stu-id="37510-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="37510-105">Ukázka aktivuje zprostředkovatele služby WMI pro [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a `ICalculator` ukazuje, jak shromažďovat data ze služby za běhu.</span><span class="sxs-lookup"><span data-stu-id="37510-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="37510-106">Služba WMI je implementací standardu WBEM (Web-Based Enterprise Management) společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="37510-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="37510-107">Další informace o sdk sady WMI naleznete v [tématu WMI Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="37510-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="37510-108">WBEM je oborový standard pro to, jak aplikace zveřejňují nástroje pro správu externím nástrojům pro správu.</span><span class="sxs-lookup"><span data-stu-id="37510-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="37510-109">WCF implementuje zprostředkovatele služby WMI, součást, která zpřístupňuje instrumentaci za běhu prostřednictvím rozhraní kompatibilního s rozhraním WBEM.</span><span class="sxs-lookup"><span data-stu-id="37510-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="37510-110">Nástroje pro správu se mohou připojit ke službám prostřednictvím rozhraní za běhu.</span><span class="sxs-lookup"><span data-stu-id="37510-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="37510-111">WCF zveřejňuje atributy služeb, jako jsou adresy, vazby, chování a naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="37510-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="37510-112">Vestavěný zprostředkovatel služby WMI je aktivován v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="37510-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="37510-113">To se provádí `wmiProviderEnabled` prostřednictvím atributu [ \<diagnostická>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) v části [ \<system.serviceModel>,](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) jak je znázorněno v následující konfiguraci ukázky:</span><span class="sxs-lookup"><span data-stu-id="37510-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="37510-114">Tato položka konfigurace zpřístupňuje rozhraní služby WMI.</span><span class="sxs-lookup"><span data-stu-id="37510-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="37510-115">Aplikace pro správu se nyní mohou připojit prostřednictvím tohoto rozhraní a získat přístup k nástroji pro správu aplikace.</span><span class="sxs-lookup"><span data-stu-id="37510-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="37510-116">Vlastní objekt wmi</span><span class="sxs-lookup"><span data-stu-id="37510-116">Custom WMI Object</span></span>  
 <span data-ttu-id="37510-117">Přidání objektů služby WMI do služby umožňuje odhalit uživatelem definované informace spolu s informacemi o integrovaném zprostředkovateli služby WMI.</span><span class="sxs-lookup"><span data-stu-id="37510-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="37510-118">Toho lze dosáhnout publikováním schématu služby do služby WMI pomocí aplikace Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="37510-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="37510-119">Pokyny k dosažení tohoto cíle, spolu s dalšípodrobnosti naleznete v návodu k nastavení na konci tématu.</span><span class="sxs-lookup"><span data-stu-id="37510-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="37510-120">Přístup k informacím o systému WMI</span><span class="sxs-lookup"><span data-stu-id="37510-120">Accessing WMI Information</span></span>  

<span data-ttu-id="37510-121">K datům wmi lze přistupovat mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="37510-121">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="37510-122">Společnost Microsoft poskytuje rozhraní WMI rozhraní API pro skripty, aplikace jazyka Visual Basic, aplikace jazyka C++ a rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37510-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="37510-123">Další informace naleznete [v tématu Using WMI](/windows/desktop/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="37510-123">For more information, see [Using WMI](/windows/desktop/wmisdk/using-wmi).</span></span>
  
 <span data-ttu-id="37510-124">Tato ukázka používá dva skripty jazyka Java: jeden pro výčet služeb spuštěných v počítači spolu s některými jejich vlastnostmi a druhý pro zobrazení uživatelem definovaných dat služby WMI.</span><span class="sxs-lookup"><span data-stu-id="37510-124">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="37510-125">Skript otevře připojení k poskytovateli služby WMI, analyzuje data a zobrazí shromážděná data.</span><span class="sxs-lookup"><span data-stu-id="37510-125">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="37510-126">Spusťte ukázku a vytvořte spuštěnou instanci služby WCF.</span><span class="sxs-lookup"><span data-stu-id="37510-126">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="37510-127">Během spuštění služby spusťte každý skript jazyka Java pomocí následujícího příkazu na příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="37510-127">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```console  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="37510-128">Skript přistupuje k instrumentaci obsažené ve službě a vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="37510-128">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="37510-129">Dále spusťte druhý skript Java a zobrazte uživatelem definovaná data služby WMI:</span><span class="sxs-lookup"><span data-stu-id="37510-129">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="37510-130">Skript přistupuje k uživatelem definované instrumentaci obsažené ve službách a vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="37510-130">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="37510-131">Výstup ukazuje, že v počítači je spuštěna jedna služba.</span><span class="sxs-lookup"><span data-stu-id="37510-131">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="37510-132">Služba zpřístupňuje jeden koncový bod, který implementuje `ICalculator` smlouvy.</span><span class="sxs-lookup"><span data-stu-id="37510-132">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="37510-133">Nastavení chování a vazby, které jsou implementovány koncový bod jsou uvedeny jako součet jednotlivých prvků zásobníku zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="37510-133">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="37510-134">Služby WMI se neomezují pouze na odhalení nástrojů pro správu infrastruktury WCF.</span><span class="sxs-lookup"><span data-stu-id="37510-134">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="37510-135">Aplikace můžete vystavit své vlastní datové položky specifické pro doménu prostřednictvím stejného mechanismu.</span><span class="sxs-lookup"><span data-stu-id="37510-135">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="37510-136">Služba WMI je jednotný mechanismus pro kontrolu a kontrolu webové služby.</span><span class="sxs-lookup"><span data-stu-id="37510-136">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="37510-137">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="37510-137">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="37510-138">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37510-138">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="37510-139">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37510-139">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="37510-140">Publikovat schéma služeb do služby WMI spuštěním programu InstallUtil.exe (výchozí umístění souboru InstallUtil.exe je %WINDIR%\Microsoft.NET\Framework\v4.0.30319") v souboru service.dll v hostitelském adresáři.</span><span class="sxs-lookup"><span data-stu-id="37510-140">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="37510-141">Tento krok je třeba provést pouze v případě, že byly provedeny změny v souboru service.dll.</span><span class="sxs-lookup"><span data-stu-id="37510-141">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="37510-142">Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37510-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="37510-143">Pokud jste nainstalovali WCF po instalaci ASP.NET, bude pravděpodobně nutné spustit %WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x, aby účet ASPNET měl oprávnění k publikování objektů služby WMI.</span><span class="sxs-lookup"><span data-stu-id="37510-143">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="37510-144">Zobrazení dat ze vzorku, které se objevily prostřednictvím služby WMI pomocí příkazů: `cscript EnumerateServices.js` nebo `cscript EnumerateCustomObjects.js`.</span><span class="sxs-lookup"><span data-stu-id="37510-144">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="37510-145">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="37510-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="37510-146">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="37510-146">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="37510-147">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="37510-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="37510-148">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="37510-148">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="37510-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="37510-149">See also</span></span>

- <span data-ttu-id="37510-150">[Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="37510-150">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
