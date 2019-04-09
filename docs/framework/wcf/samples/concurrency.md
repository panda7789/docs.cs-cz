---
title: Souběžnost
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: f0d4996a7ea8ab49df780635127f39064b1050c9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119142"
---
# <a name="concurrency"></a><span data-ttu-id="58a9d-102">Souběžnost</span><span class="sxs-lookup"><span data-stu-id="58a9d-102">Concurrency</span></span>
<span data-ttu-id="58a9d-103">Ukázka souběžnosti znázorňuje použití <xref:System.ServiceModel.ServiceBehaviorAttribute> s <xref:System.ServiceModel.ConcurrencyMode> výčet, který řídí, zda instance služby zpracovává zprávy postupně sekvenčně nebo současně.</span><span class="sxs-lookup"><span data-stu-id="58a9d-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="58a9d-104">Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="58a9d-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="58a9d-105">Tato ukázka definuje kontrakt nové `ICalculatorConcurrency`, který dědí z `ICalculator`, poskytuje dvě další operace Kontrola stavu služby souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="58a9d-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="58a9d-106">Změnou nastavení souběžnosti můžete sledovat změny v chování pomocí klienta.</span><span class="sxs-lookup"><span data-stu-id="58a9d-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="58a9d-107">V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="58a9d-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58a9d-108">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="58a9d-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="58a9d-109">K dispozici jsou tři režimy souběžnosti:</span><span class="sxs-lookup"><span data-stu-id="58a9d-109">There are three concurrency modes available:</span></span>  
  
-   `Single`<span data-ttu-id="58a9d-110">: Každá instance služby zpracovává jednu zprávu najednou.</span><span class="sxs-lookup"><span data-stu-id="58a9d-110">: Each service instance processes one message at a time.</span></span> <span data-ttu-id="58a9d-111">Toto je výchozí režim.</span><span class="sxs-lookup"><span data-stu-id="58a9d-111">This is the default concurrency mode.</span></span>  
  
-   `Multiple`<span data-ttu-id="58a9d-112">: Každá instance služby zpracovává více zpráv souběžně.</span><span class="sxs-lookup"><span data-stu-id="58a9d-112">: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="58a9d-113">Implementace služby musí být bezpečná pro vlákno pro použití tohoto režimu souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="58a9d-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
-   `Reentrant`<span data-ttu-id="58a9d-114">: Každá instance služby zpracovává zprávy jeden po druhém, ale přijímá znovu zadaných volání.</span><span class="sxs-lookup"><span data-stu-id="58a9d-114">: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="58a9d-115">Služba přijímá pouze tato volání zavoláním navýšení kapacity. Vícenásobný jsou popsané v článku [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="58a9d-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="58a9d-116">Vytvoření instance režimu se týká použití souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="58a9d-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="58a9d-117">V <xref:System.ServiceModel.InstanceContextMode.PerCall> vytváření instancí, souběžnost není odpovídající, protože každá zpráva se zpracuje pomocí nové instance služby.</span><span class="sxs-lookup"><span data-stu-id="58a9d-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="58a9d-118">V <xref:System.ServiceModel.InstanceContextMode.Single> vytváření instancí, buď <xref:System.ServiceModel.ConcurrencyMode.Single> nebo <xref:System.ServiceModel.ConcurrencyMode.Multiple> souběžnosti je relevantní, v závislosti na tom, jestli jedna instance zpracovává zprávy postupně sekvenčně nebo současně.</span><span class="sxs-lookup"><span data-stu-id="58a9d-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="58a9d-119">V <xref:System.ServiceModel.InstanceContextMode.PerSession> vytváření instancí, všechny režimy souběžnosti můžou být relevantní.</span><span class="sxs-lookup"><span data-stu-id="58a9d-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="58a9d-120">Určuje chování souběžnosti s třídu služby `[ServiceBehavior(ConcurrencyMode=<setting>)]` atributu, jak je znázorněno v ukázce kódu, který následuje.</span><span class="sxs-lookup"><span data-stu-id="58a9d-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="58a9d-121">Tak, že změníte, které řádky jsou označené jako komentář, můžete experimentovat s `Single` a `Multiple` režimy souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="58a9d-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="58a9d-122">Nezapomeňte znovu sestavit službě po změně režimu souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="58a9d-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
```csharp
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {     
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {     
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 <span data-ttu-id="58a9d-123">Ukázka používá <xref:System.ServiceModel.ConcurrencyMode.Multiple> souběžnosti ovládacím prvkem <xref:System.ServiceModel.InstanceContextMode.Single> vytváření instancí ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="58a9d-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="58a9d-124">Klientský kód byl změněn na používání asynchronních proxy.</span><span class="sxs-lookup"><span data-stu-id="58a9d-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="58a9d-125">Díky tomu se klient několik volání služby bez čekání na odpověď mezi jednotlivými voláními.</span><span class="sxs-lookup"><span data-stu-id="58a9d-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="58a9d-126">Podívejte se na rozdíl v chování souběžný režim služby.</span><span class="sxs-lookup"><span data-stu-id="58a9d-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="58a9d-127">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="58a9d-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="58a9d-128">Režim souběžnosti, ve kterém je služba spuštěná v části se zobrazí, se nazývá každé operace a zobrazí počet operací.</span><span class="sxs-lookup"><span data-stu-id="58a9d-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="58a9d-129">Všimněte si, že pokud je režim `Multiple`, výsledky jsou vráceny v jiném pořadí, než jak byly volány, protože služba zpracovává více zpráv souběžně.</span><span class="sxs-lookup"><span data-stu-id="58a9d-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="58a9d-130">Změnou souběžný režim `Single`, výsledky se vrátí v pořadí jejich byly volány, protože služba každou zprávu zpracovává postupně.</span><span class="sxs-lookup"><span data-stu-id="58a9d-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="58a9d-131">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="58a9d-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="58a9d-132">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="58a9d-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="58a9d-133">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58a9d-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="58a9d-134">Pokud pomocí Svcutil.exe lze generovat proxy serveru klienta, ujistěte se, že složku zahrnujete `/async` možnost.</span><span class="sxs-lookup"><span data-stu-id="58a9d-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3.  <span data-ttu-id="58a9d-135">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58a9d-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="58a9d-136">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58a9d-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="58a9d-137">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="58a9d-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="58a9d-138">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="58a9d-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="58a9d-139">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="58a9d-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="58a9d-140">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="58a9d-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
