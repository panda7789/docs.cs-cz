---
title: Souběžnost
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 393c8a79cb60a33203b41a0778176a4d78a9b6ee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585308"
---
# <a name="concurrency"></a><span data-ttu-id="a7430-102">Souběžnost</span><span class="sxs-lookup"><span data-stu-id="a7430-102">Concurrency</span></span>
<span data-ttu-id="a7430-103">Ukázka souběžnosti ukazuje použití <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.ConcurrencyMode> prvku s výčtem, který určuje, zda instance služby zpracovává zprávy sekvenčně nebo souběžně.</span><span class="sxs-lookup"><span data-stu-id="a7430-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="a7430-104">Ukázka je založena na [Začínáme](getting-started-sample.md), která implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="a7430-104">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="a7430-105">Tato ukázka definuje nový kontrakt, `ICalculatorConcurrency` který dědí z `ICalculator` a poskytuje dvě další operace pro kontrolu stavu souběžnosti služby.</span><span class="sxs-lookup"><span data-stu-id="a7430-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="a7430-106">Změnou nastavení souběžnosti můžete sledovat změnu v chování spuštěním klienta.</span><span class="sxs-lookup"><span data-stu-id="a7430-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="a7430-107">V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="a7430-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7430-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="a7430-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a7430-109">K dispozici jsou tři režimy souběžnosti:</span><span class="sxs-lookup"><span data-stu-id="a7430-109">There are three concurrency modes available:</span></span>  
  
- <span data-ttu-id="a7430-110">`Single`: Každá instance služby zpracovává vždy jednu zprávu.</span><span class="sxs-lookup"><span data-stu-id="a7430-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="a7430-111">Toto je výchozí režim souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="a7430-111">This is the default concurrency mode.</span></span>  
  
- <span data-ttu-id="a7430-112">`Multiple`: Každá instance služby zpracovává více zpráv souběžně.</span><span class="sxs-lookup"><span data-stu-id="a7430-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="a7430-113">Aby bylo možné používat tento režim souběžnosti, musí být implementace služby bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="a7430-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
- <span data-ttu-id="a7430-114">`Reentrant`: Každá instance služby zpracovává jednu zprávu ve chvíli, ale přijímá znovu zadaná volání.</span><span class="sxs-lookup"><span data-stu-id="a7430-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="a7430-115">Služba akceptuje tato volání pouze při vyvolání. Znovu se zavedlo na výběr v ukázce režimu [ConcurrencyMode. revstupujícího](concurrencymode-reentrant.md) .</span><span class="sxs-lookup"><span data-stu-id="a7430-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="a7430-116">Použití souběžnosti souvisí s režimem vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="a7430-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="a7430-117">V rámci vytváření <xref:System.ServiceModel.InstanceContextMode.PerCall> instancí není souběžnost relevantní, protože každá zpráva je zpracována novou instancí služby.</span><span class="sxs-lookup"><span data-stu-id="a7430-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="a7430-118">V <xref:System.ServiceModel.InstanceContextMode.Single> rámci vytváření instancí, a to v <xref:System.ServiceModel.ConcurrencyMode.Single> <xref:System.ServiceModel.ConcurrencyMode.Multiple> závislosti na tom, zda jedna instance zpracovává zprávy sekvenčně nebo souběžně.</span><span class="sxs-lookup"><span data-stu-id="a7430-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="a7430-119">V <xref:System.ServiceModel.InstanceContextMode.PerSession> rámci vytváření instancí můžou být všechny režimy souběžnosti relevantní.</span><span class="sxs-lookup"><span data-stu-id="a7430-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="a7430-120">Třída služby určuje chování souběžnosti s `[ServiceBehavior(ConcurrencyMode=<setting>)]` atributem, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="a7430-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="a7430-121">Změnou řádků, které jsou zakomentovány, můžete experimentovat s `Single` režimy a `Multiple` souběžnost.</span><span class="sxs-lookup"><span data-stu-id="a7430-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="a7430-122">Nezapomeňte znovu sestavit službu po změně režimu souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="a7430-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
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
  
 <span data-ttu-id="a7430-123">Ukázka <xref:System.ServiceModel.ConcurrencyMode.Multiple> ve výchozím nastavení používá souběžnost se <xref:System.ServiceModel.InstanceContextMode.Single> vytvářením instancí.</span><span class="sxs-lookup"><span data-stu-id="a7430-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="a7430-124">Kód klienta byl změněn tak, aby používal asynchronní proxy server.</span><span class="sxs-lookup"><span data-stu-id="a7430-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="a7430-125">Díky tomu může klient uskutečnit více volání služby bez čekání na odezvu mezi jednotlivými voláními.</span><span class="sxs-lookup"><span data-stu-id="a7430-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="a7430-126">Můžete sledovat rozdíl v chování režimu souběžnosti služby.</span><span class="sxs-lookup"><span data-stu-id="a7430-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="a7430-127">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a7430-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a7430-128">Režim souběžnosti, ve kterém je služba spuštěna, se zobrazí při každé operaci a pak se zobrazí počet operací.</span><span class="sxs-lookup"><span data-stu-id="a7430-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="a7430-129">Všimněte si, že když je režim souběžnosti `Multiple` , výsledky se vrátí v jiném pořadí, než jak byly volány, protože služba zpracovává více zpráv souběžně.</span><span class="sxs-lookup"><span data-stu-id="a7430-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="a7430-130">Když změníte režim souběžnosti na `Single` , výsledky se vrátí v pořadí, ve kterém byly volány, protože služba zpracovává každou zprávu sekvenčně.</span><span class="sxs-lookup"><span data-stu-id="a7430-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="a7430-131">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="a7430-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a7430-132">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="a7430-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a7430-133">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a7430-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a7430-134">Pokud k vygenerování proxy klienta používáte Svcutil. exe, ujistěte se, že jste zahrnuli `/async` možnost.</span><span class="sxs-lookup"><span data-stu-id="a7430-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="a7430-135">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a7430-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="a7430-136">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a7430-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a7430-137">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="a7430-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a7430-138">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="a7430-138">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a7430-139">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="a7430-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a7430-140">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a7430-140">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
