---
title: "Vytváření instancí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
caps.latest.revision: "40"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5b38d70a4f4c3938d6cc6116c94a009ec0f34dc0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="instancing"></a><span data-ttu-id="0103c-102">Vytváření instancí</span><span class="sxs-lookup"><span data-stu-id="0103c-102">Instancing</span></span>
<span data-ttu-id="0103c-103">Příklad Instancing znázorňuje zřizování instancí nastavení chování, který řídí vytváření instancí třídy služby v reakci na požadavky klientů.</span><span class="sxs-lookup"><span data-stu-id="0103c-103">The Instancing sample demonstrates the instancing behavior setting, which controls how instances of a service class are created in response to client requests.</span></span> <span data-ttu-id="0103c-104">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="0103c-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="0103c-105">Tento příklad definuje nové smlouvy, `ICalculatorInstance`, který dědí z `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="0103c-105">This sample defines a new contract, `ICalculatorInstance`, which inherits from `ICalculator`.</span></span> <span data-ttu-id="0103c-106">Kontrakt určený `ICalculatorInstance` poskytuje tři další operace pro kontroly stavu instance služby.</span><span class="sxs-lookup"><span data-stu-id="0103c-106">The contract specified by `ICalculatorInstance` provides three additional operations for inspecting the state of the service instance.</span></span> <span data-ttu-id="0103c-107">Změnou nastavení zřizování instancí, můžete sledovat změny v chování pomocí klienta.</span><span class="sxs-lookup"><span data-stu-id="0103c-107">By altering the instancing setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="0103c-108">V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="0103c-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0103c-109">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="0103c-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0103c-110">K dispozici jsou následující režimy zřizování instancí:</span><span class="sxs-lookup"><span data-stu-id="0103c-110">The following instancing modes are available:</span></span>  
  
-   <span data-ttu-id="0103c-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: Nové instance služby se vytvoří pro každý požadavek klienta.</span><span class="sxs-lookup"><span data-stu-id="0103c-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: A new service instance is created for each client request.</span></span>  
  
-   <span data-ttu-id="0103c-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: Novou instanci je vytvoří pro každou novou relaci klienta a udržovat po dobu jeho existence této relace (vyžaduje vazbu, která podporuje relace).</span><span class="sxs-lookup"><span data-stu-id="0103c-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: A new instance is created for each new client session, and maintained for the lifetime of that session (requires a binding that supports session).</span></span>  
  
-   <span data-ttu-id="0103c-113"><xref:System.ServiceModel.InstanceContextMode.Single>: Jednu instanci třídy služby zpracuje všechny žádosti klienta po dobu jeho existence aplikace.</span><span class="sxs-lookup"><span data-stu-id="0103c-113"><xref:System.ServiceModel.InstanceContextMode.Single>: A single instance of the service class handles all client requests for the lifetime of the application.</span></span>  
  
 <span data-ttu-id="0103c-114">Třída služby určuje chování zřizování instancí s `[ServiceBehavior(InstanceContextMode=<setting>)]` atributu, jak je znázorněno v ukázce kódu, který následuje dále.</span><span class="sxs-lookup"><span data-stu-id="0103c-114">The service class specifies instancing behavior with the `[ServiceBehavior(InstanceContextMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="0103c-115">Změnou linky, které jsou označené jako komentář, můžete sledovat chování oba režimy instance.</span><span class="sxs-lookup"><span data-stu-id="0103c-115">By changing which lines are commented out, you can observe the behavior of each of the instance modes.</span></span> <span data-ttu-id="0103c-116">Mějte na paměti, znovu sestavit po změně režimu zřizování instancí služby.</span><span class="sxs-lookup"><span data-stu-id="0103c-116">Remember to rebuild the service after changing the instancing mode.</span></span> <span data-ttu-id="0103c-117">Nejsou žádná vytváření instancí související nastavení k určení na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="0103c-117">There are no instancing-related settings to specify on the client.</span></span>  
  
```  
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed   
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="0103c-118">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="0103c-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0103c-119">Zobrazí se služba běží v režimu instance.</span><span class="sxs-lookup"><span data-stu-id="0103c-119">The instance mode the service is running under is displayed.</span></span> <span data-ttu-id="0103c-120">Po každé operaci zobrazí se počet instancí ID a operace tak, aby odrážela chování v režimu zřizování instancí.</span><span class="sxs-lookup"><span data-stu-id="0103c-120">After each operation, the instance ID and operation count are displayed to reflect the behavior of the instancing mode.</span></span> <span data-ttu-id="0103c-121">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="0103c-121">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0103c-122">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="0103c-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0103c-123">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0103c-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0103c-124">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0103c-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="0103c-125">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0103c-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0103c-126">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="0103c-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0103c-127">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0103c-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0103c-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="0103c-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0103c-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0103c-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
  
## <a name="see-also"></a><span data-ttu-id="0103c-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="0103c-130">See Also</span></span>
