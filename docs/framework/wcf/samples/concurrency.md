---
title: "Souběžnost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 103a22a729029118b0770e2889c419074be6ad50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="concurrency"></a><span data-ttu-id="db801-102">Souběžnost</span><span class="sxs-lookup"><span data-stu-id="db801-102">Concurrency</span></span>
<span data-ttu-id="db801-103">Ukázka souběžnosti ukazuje, jak pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute> s <xref:System.ServiceModel.ConcurrencyMode> výčtu, který určuje, zda instance služby zpracovává zprávy postupně nebo souběžně.</span><span class="sxs-lookup"><span data-stu-id="db801-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="db801-104">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="db801-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="db801-105">Tento příklad definuje nové smlouvy, `ICalculatorConcurrency`, který dědí z `ICalculator`, poskytuje dva další operace pro zkontrolujte stav služby souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="db801-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="db801-106">Změnou nastavení souběžnosti, můžete sledovat změny v chování pomocí klienta.</span><span class="sxs-lookup"><span data-stu-id="db801-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="db801-107">V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="db801-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db801-108">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="db801-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="db801-109">Nejsou k dispozici tři režimy souběžnosti:</span><span class="sxs-lookup"><span data-stu-id="db801-109">There are three concurrency modes available:</span></span>  
  
-   <span data-ttu-id="db801-110">`Single`: Každá instance služby zpracovává jednu zprávu najednou.</span><span class="sxs-lookup"><span data-stu-id="db801-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="db801-111">Toto je výchozí režim souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="db801-111">This is the default concurrency mode.</span></span>  
  
-   <span data-ttu-id="db801-112">`Multiple`: Každá instance služby zpracovává více zpráv současně.</span><span class="sxs-lookup"><span data-stu-id="db801-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="db801-113">Implementace služby musí být vláken pro použití tohoto režimu souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="db801-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
-   <span data-ttu-id="db801-114">`Reentrant`: Každá instance služby zpracovává jednu zprávu najednou, ale přijímá znovu zadaná volání.</span><span class="sxs-lookup"><span data-stu-id="db801-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="db801-115">Když se volají, služba přijímá pouze těchto volání. Vícenásobně přístupné ukazují [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="db801-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="db801-116">Použití souběžného zpracování se týká zřizování instancí režimu.</span><span class="sxs-lookup"><span data-stu-id="db801-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="db801-117">V <xref:System.ServiceModel.InstanceContextMode.PerCall> vytváření instancí, souběžnosti není relevantní, protože každá zpráva se zpracuje nové instance služby.</span><span class="sxs-lookup"><span data-stu-id="db801-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="db801-118">V <xref:System.ServiceModel.InstanceContextMode.Single> vytváření instancí buď <xref:System.ServiceModel.ConcurrencyMode.Single> nebo <xref:System.ServiceModel.ConcurrencyMode.Multiple> souběžnosti je relevantní, v závislosti na tom, jestli jediné instance zpracovává zprávy postupně nebo souběžně.</span><span class="sxs-lookup"><span data-stu-id="db801-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="db801-119">V <xref:System.ServiceModel.InstanceContextMode.PerSession> vytváření instancí, žádný z režimů souběžnosti nemusí být relevantní.</span><span class="sxs-lookup"><span data-stu-id="db801-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="db801-120">Třída služby určuje chování souběžnosti s `[ServiceBehavior(ConcurrencyMode=<setting>)]` atributu, jak je znázorněno v ukázce kódu, který následuje dále.</span><span class="sxs-lookup"><span data-stu-id="db801-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="db801-121">Změnou linky, které jsou označené jako komentář můžete vyzkoušet `Single` a `Multiple` režimy souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="db801-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="db801-122">Mějte na paměti, znovu sestavit službu po změně souběžný režim.</span><span class="sxs-lookup"><span data-stu-id="db801-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
```  
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
  
 <span data-ttu-id="db801-123">Příklad používá <xref:System.ServiceModel.ConcurrencyMode.Multiple> souběžnosti s <xref:System.ServiceModel.InstanceContextMode.Single> vytváření instancí ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="db801-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="db801-124">Kód klienta se změnilo používat asynchronní proxy server.</span><span class="sxs-lookup"><span data-stu-id="db801-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="db801-125">To umožňuje klientům provádět několik volání do služby bez čekání na odezvu mezi každé volání.</span><span class="sxs-lookup"><span data-stu-id="db801-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="db801-126">Rozdíl v chování souběžný režim služby můžete sledovat.</span><span class="sxs-lookup"><span data-stu-id="db801-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="db801-127">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="db801-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="db801-128">Souběžný režim, který služba běží pod se zobrazí, se nazývá každé operace a pak se zobrazí počet operací.</span><span class="sxs-lookup"><span data-stu-id="db801-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="db801-129">Všimněte si, že pokud je režim souběžnosti `Multiple`, budou vráceny výsledky v jiném pořadí než jak měla volat, protože služba zpracovává více zpráv současně.</span><span class="sxs-lookup"><span data-stu-id="db801-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="db801-130">Změnou souběžný režim `Single`, budou vráceny výsledky v pořadí se měla volat, protože služba zpracovává každou zprávu postupně.</span><span class="sxs-lookup"><span data-stu-id="db801-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="db801-131">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="db801-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="db801-132">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="db801-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="db801-133">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="db801-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="db801-134">Pokud používáte Svcutil.exe ke generování proxy serveru klienta, ujistěte se, jestli jste zahrnuli `/async` možnost.</span><span class="sxs-lookup"><span data-stu-id="db801-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3.  <span data-ttu-id="db801-135">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="db801-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="db801-136">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="db801-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="db801-137">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="db801-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="db801-138">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="db801-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="db801-139">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="db801-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="db801-140">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="db801-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
  
## <a name="see-also"></a><span data-ttu-id="db801-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="db801-141">See Also</span></span>
