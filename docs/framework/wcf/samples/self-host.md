---
title: Vlastní hostování
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: c95ba40d606470f97d32d05b25c9588ed71cdc79
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331504"
---
# <a name="self-host"></a><span data-ttu-id="ce131-102">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="ce131-102">Self-Host</span></span>
<span data-ttu-id="ce131-103">Tento příklad ukazuje, jak implementovat v místním prostředí službu v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ce131-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="ce131-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ce131-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="ce131-105">Konfigurační soubor služby byl přejmenován ze souboru Web.config na App.config a upravit tak, aby konfigurace základní adresu, která hostitel používá.</span><span class="sxs-lookup"><span data-stu-id="ce131-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="ce131-106">Zdrojový kód služby byla změněna k implementaci statickou `Main` funkce, která vytvoří a otevře hostitele služby, který poskytuje základní adresu nakonfigurovanou.</span><span class="sxs-lookup"><span data-stu-id="ce131-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="ce131-107">Implementace služby byl upraven tak zapisovat výstup do konzoly pro každou operaci.</span><span class="sxs-lookup"><span data-stu-id="ce131-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="ce131-108">Klient byl bez úprav, s výjimkou konfigurace adresu správný koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="ce131-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce131-109">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ce131-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ce131-110">Implementuje statické hlavní funkce k vytvoření vzorku <xref:System.ServiceModel.ServiceHost> pro daný `CalculatorService` zadejte, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="ce131-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="ce131-111">Pokud služba je hostovaná v Internetové informační služby (IIS) nebo Windows Process Activation Service (WAS), je základní adresa služby poskytovaný hostitelského prostředí.</span><span class="sxs-lookup"><span data-stu-id="ce131-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="ce131-112">V tomto případě v místním prostředí zadejte základní adresu sami.</span><span class="sxs-lookup"><span data-stu-id="ce131-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="ce131-113">To se provádí pomocí `add` elementu, podřízený [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), podřízený [ \<hostitele >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), podřízený [ \<služby > ](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) jak je ukázáno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="ce131-113">This is done using the `add` element, child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="ce131-114">Při spuštění ukázky operace žádosti a odpovědi se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="ce131-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ce131-115">Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="ce131-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ce131-116">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="ce131-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ce131-117">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce131-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ce131-118">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce131-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ce131-119">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce131-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ce131-120">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="ce131-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ce131-121">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ce131-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ce131-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ce131-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ce131-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ce131-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="ce131-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce131-124">See also</span></span>

- [<span data-ttu-id="ce131-125">Hostování AppFabric a ukázky trvalosti</span><span class="sxs-lookup"><span data-stu-id="ce131-125">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
