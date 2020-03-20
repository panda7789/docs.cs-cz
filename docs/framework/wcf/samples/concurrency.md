---
title: Souběžnost
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: eb6140895bb922bd159f1abf536a0d0b12d4f96c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183936"
---
# <a name="concurrency"></a><span data-ttu-id="be764-102">Souběžnost</span><span class="sxs-lookup"><span data-stu-id="be764-102">Concurrency</span></span>
<span data-ttu-id="be764-103">Ukázka souběžnosti ukazuje <xref:System.ServiceModel.ServiceBehaviorAttribute> použití <xref:System.ServiceModel.ConcurrencyMode> s výčtu, který řídí, zda instance služby zpracovává zprávy postupně nebo souběžně.</span><span class="sxs-lookup"><span data-stu-id="be764-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="be764-104">Ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` který implementuje servisní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="be764-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="be764-105">Tato ukázka definuje novou `ICalculatorConcurrency`smlouvu , `ICalculator`která dědí z , poskytuje dvě další operace pro kontrolu stavu souběžnosti služby.</span><span class="sxs-lookup"><span data-stu-id="be764-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="be764-106">Změnou nastavení souběžnosti můžete sledovat změnu v chování spuštěním klienta.</span><span class="sxs-lookup"><span data-stu-id="be764-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="be764-107">V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="be764-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be764-108">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="be764-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="be764-109">K dispozici jsou tři režimy souběžnosti:</span><span class="sxs-lookup"><span data-stu-id="be764-109">There are three concurrency modes available:</span></span>  
  
- <span data-ttu-id="be764-110">`Single`: Každá instance služby zpracovává jednu zprávu najednou.</span><span class="sxs-lookup"><span data-stu-id="be764-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="be764-111">Toto je výchozí režim souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="be764-111">This is the default concurrency mode.</span></span>  
  
- <span data-ttu-id="be764-112">`Multiple`: Každá instance služby zpracovává více zpráv současně.</span><span class="sxs-lookup"><span data-stu-id="be764-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="be764-113">Implementace služby musí být bezpečné pro přístup z více vláken, aby bylo možné použít tento režim souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="be764-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
- <span data-ttu-id="be764-114">`Reentrant`: Každá instance služby zpracovává jednu zprávu najednou, ale přijímá reentrant volání.</span><span class="sxs-lookup"><span data-stu-id="be764-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="be764-115">Služba přijímá tato volání pouze při volání. Reentrant je prokázáno v [Ukázce ConcurrencyMode.Reentrant.](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md)</span><span class="sxs-lookup"><span data-stu-id="be764-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="be764-116">Použití souběžnosti souvisí s instance režimu.</span><span class="sxs-lookup"><span data-stu-id="be764-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="be764-117">V <xref:System.ServiceModel.InstanceContextMode.PerCall> instance souběžnosti není relevantní, protože každá zpráva je zpracována novou instancí služby.</span><span class="sxs-lookup"><span data-stu-id="be764-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="be764-118">V <xref:System.ServiceModel.InstanceContextMode.Single> instance buď <xref:System.ServiceModel.ConcurrencyMode.Single> nebo <xref:System.ServiceModel.ConcurrencyMode.Multiple> souběžnost je relevantní, v závislosti na tom, zda jedna instance zpracovává zprávy postupně nebo souběžně.</span><span class="sxs-lookup"><span data-stu-id="be764-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="be764-119">V <xref:System.ServiceModel.InstanceContextMode.PerSession> instance může být relevantní kterýkoli z režimů souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="be764-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="be764-120">Třída service určuje chování souběžnosti `[ServiceBehavior(ConcurrencyMode=<setting>)]` s atributem, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="be764-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="be764-121">Změnou, které řádky jsou zakomentovány, můžete experimentovat s režimy `Single` a `Multiple` souběžnost.</span><span class="sxs-lookup"><span data-stu-id="be764-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="be764-122">Nezapomeňte znovu sestavit službu po změně režimu souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="be764-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
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
  
 <span data-ttu-id="be764-123">Ukázka <xref:System.ServiceModel.ConcurrencyMode.Multiple> používá souběžnost s <xref:System.ServiceModel.InstanceContextMode.Single> instance ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="be764-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="be764-124">Kód klienta byl upraven tak, aby používal asynchronní proxy server.</span><span class="sxs-lookup"><span data-stu-id="be764-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="be764-125">To umožňuje klientovi provádět více volání služby bez čekání na odpověď mezi jednotlivými volání.</span><span class="sxs-lookup"><span data-stu-id="be764-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="be764-126">Můžete sledovat rozdíl v chování režimu souběžnosti služby.</span><span class="sxs-lookup"><span data-stu-id="be764-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="be764-127">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="be764-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="be764-128">Je zobrazen režim souběžnosti, pod kterým je služba spuštěna, každá operace je volána a poté se zobrazí počet operací.</span><span class="sxs-lookup"><span data-stu-id="be764-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="be764-129">Všimněte si, že `Multiple`pokud je režim souběžnosti , výsledky jsou vráceny v jiném pořadí, než jak byly volány, protože služba zpracovává více zpráv současně.</span><span class="sxs-lookup"><span data-stu-id="be764-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="be764-130">Změnou režimu souběžnosti na `Single`, jsou výsledky vráceny v pořadí, v jakém byly volány, protože služba zpracovává každou zprávu postupně.</span><span class="sxs-lookup"><span data-stu-id="be764-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="be764-131">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="be764-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="be764-132">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="be764-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="be764-133">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="be764-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="be764-134">Pokud používáte Svcutil.exe ke generování proxy klienta, ujistěte se, že zahrnete `/async` možnost.</span><span class="sxs-lookup"><span data-stu-id="be764-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="be764-135">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="be764-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="be764-136">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="be764-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="be764-137">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="be764-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="be764-138">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="be764-138">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="be764-139">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="be764-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="be764-140">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="be764-140">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
