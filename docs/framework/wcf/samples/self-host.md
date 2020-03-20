---
title: Vlastní hostování
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: a38738c369db3d3f8242bd71ee04a19a669b2cf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144146"
---
# <a name="self-host"></a><span data-ttu-id="a752e-102">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="a752e-102">Self-Host</span></span>
<span data-ttu-id="a752e-103">Tato ukázka ukazuje, jak implementovat samoobslužnou službu v aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="a752e-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="a752e-104">Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a752e-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="a752e-105">Konfigurační soubor služby byl přejmenován z souboru Web.config na App.config a upraven tak, aby nakonfiguroval základní adresu, kterou hostitel používá.</span><span class="sxs-lookup"><span data-stu-id="a752e-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="a752e-106">Zdrojový kód služby byl upraven `Main` tak, aby implementoval statickou funkci, která vytvoří a otevře hostitele služby, který poskytuje nakonfigurovanou základní adresu.</span><span class="sxs-lookup"><span data-stu-id="a752e-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="a752e-107">Implementace služby byla upravena tak, aby zapisovala výstup do konzoly pro každou operaci.</span><span class="sxs-lookup"><span data-stu-id="a752e-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="a752e-108">Klient byl nezměněn, s výjimkou konfigurace správné koncové adresy služby.</span><span class="sxs-lookup"><span data-stu-id="a752e-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a752e-109">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="a752e-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a752e-110">Ukázka implementuje statickou hlavní <xref:System.ServiceModel.ServiceHost> funkci `CalculatorService` k vytvoření a pro daný typ, jak je znázorněno na následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="a752e-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="a752e-111">Pokud je služba hostována v Internetové informační službě (IIS) nebo službě aktivace procesů systému Windows (WAS), základní adresa služby je poskytována hostitelským prostředím.</span><span class="sxs-lookup"><span data-stu-id="a752e-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="a752e-112">V případě vlastní hostované, musíte zadat základní adresu sami.</span><span class="sxs-lookup"><span data-stu-id="a752e-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="a752e-113">To se provádí `add` pomocí elementu, podřízeného [ \<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [ \<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [ \<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) jak je znázorněno v následující ukázce né konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a752e-113">This is done using the `add` element, child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 <span data-ttu-id="a752e-114">Při spuštění ukázky jsou požadavky na operaci a odpovědi zobrazeny v systému Windows služby i klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="a752e-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="a752e-115">Stisknutím klávesy ENTER v každém okně konzoly vypněte službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="a752e-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a752e-116">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="a752e-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a752e-117">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a752e-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a752e-118">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a752e-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a752e-119">Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a752e-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a752e-120">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="a752e-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a752e-121">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="a752e-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a752e-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a752e-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a752e-123">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a752e-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="a752e-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="a752e-124">See also</span></span>

- <span data-ttu-id="a752e-125">[Ukázky hostování a perzistence appfabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a752e-125">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
