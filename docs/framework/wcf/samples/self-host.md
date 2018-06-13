---
title: Vlastní hostování
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: d4fc6c55f0eb528e6ae8d19d733c67d7f7ce135f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502673"
---
# <a name="self-host"></a><span data-ttu-id="79eda-102">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="79eda-102">Self-Host</span></span>
<span data-ttu-id="79eda-103">Tento příklad ukazuje, jak implementovat samoobslužné hostovanou službu v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="79eda-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="79eda-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="79eda-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="79eda-105">Konfigurační soubor služby má byl přejmenován ze souboru Web.config na App.config a upravit tak, aby konfigurace základní adresu, která hostitel používá.</span><span class="sxs-lookup"><span data-stu-id="79eda-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="79eda-106">Zdrojový kód služby se změnilo implementovat statického `Main` funkce, která vytvoří a otevře poskytující základní adresu nakonfigurované hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="79eda-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="79eda-107">Implementace služby se změnilo zapisovat výstup do konzoly pro každou operaci.</span><span class="sxs-lookup"><span data-stu-id="79eda-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="79eda-108">Klient byl beze změny, s výjimkou konfigurace adresa správná koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="79eda-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79eda-109">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="79eda-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="79eda-110">Ukázka implementuje statické hlavní funkce, která se vytvořit <xref:System.ServiceModel.ServiceHost> pro v dané `CalculatorService` zadejte, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="79eda-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="79eda-111">Pokud služba je hostovaná v Internetové informační služby (IIS) nebo služby Aktivace procesů systému Windows (WAS), je základní adresa služby poskytované hostitelské prostředí.</span><span class="sxs-lookup"><span data-stu-id="79eda-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="79eda-112">V případě vlastním hostováním zadejte základní adresu sami.</span><span class="sxs-lookup"><span data-stu-id="79eda-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="79eda-113">To se provádí pomocí `add` element, podřízená položka [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), podřízeným [ \<hostitele >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), podřízeným [ \<služby > ](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) jak je předvedeno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="79eda-113">This is done using the `add` element, child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="79eda-114">Při spuštění vzorového operaci požadavky a odpovědi se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="79eda-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="79eda-115">Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="79eda-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="79eda-116">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="79eda-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="79eda-117">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="79eda-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="79eda-118">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="79eda-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="79eda-119">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="79eda-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="79eda-120">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="79eda-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="79eda-121">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="79eda-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="79eda-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="79eda-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="79eda-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="79eda-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="79eda-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="79eda-124">See Also</span></span>  
 [<span data-ttu-id="79eda-125">Ukázky trvalosti a hostování AppFabric</span><span class="sxs-lookup"><span data-stu-id="79eda-125">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
