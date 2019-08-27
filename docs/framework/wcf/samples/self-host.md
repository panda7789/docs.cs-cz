---
title: Vlastní hostování
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: a1fecb0ade00604d9a6e019ec50ceca04abeb545
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044755"
---
# <a name="self-host"></a><span data-ttu-id="35ae2-102">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="35ae2-102">Self-Host</span></span>
<span data-ttu-id="35ae2-103">Tato ukázka předvádí, jak implementovat samoobslužnou službu v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="35ae2-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="35ae2-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="35ae2-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="35ae2-105">Konfigurační soubor služby byl přejmenován ze souboru Web. config do App. config a upraven tak, aby nakonfiguroval základní adresu, kterou hostitel používá.</span><span class="sxs-lookup"><span data-stu-id="35ae2-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="35ae2-106">Zdrojový kód služby byl změněn tak, aby implementoval statickou `Main` funkci, která vytváří a otevírá hostitele služby, který poskytuje nakonfigurovanou základní adresu.</span><span class="sxs-lookup"><span data-stu-id="35ae2-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="35ae2-107">Implementace služby byla upravena pro zápis výstupu do konzoly pro každou operaci.</span><span class="sxs-lookup"><span data-stu-id="35ae2-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="35ae2-108">Klient se nezměnil, s výjimkou konfigurace správné adresy koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="35ae2-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35ae2-109">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="35ae2-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="35ae2-110">Ukázka implementuje statickou hlavní funkci pro vytvoření <xref:System.ServiceModel.ServiceHost> pro daný `CalculatorService` typ, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="35ae2-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="35ae2-111">Když je služba hostovaná ve službě Internetová informační služba (IIS) nebo aktivační služba procesů systému Windows (WAS), poskytuje hostující prostředí základní adresu služby.</span><span class="sxs-lookup"><span data-stu-id="35ae2-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="35ae2-112">V případě samostatného hostitele je nutné zadat základní adresu sami.</span><span class="sxs-lookup"><span data-stu-id="35ae2-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="35ae2-113">To `add` se provádí pomocí elementu, [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)podřízeného prvku adres BaseAddresses >, [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) podřízenosti [ \<> hostitele](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), podřízeného > služby, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="35ae2-113">This is done using the `add` element, child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="35ae2-114">Při spuštění ukázky se požadavky na operace a odpovědi zobrazí v oknech služba i klientská konzola.</span><span class="sxs-lookup"><span data-stu-id="35ae2-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="35ae2-115">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="35ae2-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="35ae2-116">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="35ae2-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="35ae2-117">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35ae2-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="35ae2-118">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35ae2-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="35ae2-119">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="35ae2-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="35ae2-120">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="35ae2-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="35ae2-121">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="35ae2-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="35ae2-122">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="35ae2-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="35ae2-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="35ae2-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="35ae2-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35ae2-124">See also</span></span>

- [<span data-ttu-id="35ae2-125">Hostování technologie AppFabric a ukázky trvalosti</span><span class="sxs-lookup"><span data-stu-id="35ae2-125">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
