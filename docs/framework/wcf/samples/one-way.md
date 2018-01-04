---
title: "Jednosměrný"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a781963205f260c82d3db316680c9e8c33045434
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="one-way"></a><span data-ttu-id="e06bf-102">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="e06bf-102">One-Way</span></span>
<span data-ttu-id="e06bf-103">Tento příklad znázorňuje služby kontaktu s operací jednosměrné služby.</span><span class="sxs-lookup"><span data-stu-id="e06bf-103">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="e06bf-104">Klient není počkejte na dokončení stejně jako v případě s operací obousměrné služby operací služby.</span><span class="sxs-lookup"><span data-stu-id="e06bf-104">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="e06bf-105">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a používá `wsHttpBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="e06bf-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="e06bf-106">Služba v této ukázce je vlastním hostováním konzolové aplikace, které vám umožňují sledovat službu, která přijímá a zpracovává požadavky.</span><span class="sxs-lookup"><span data-stu-id="e06bf-106">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="e06bf-107">Klient je také konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="e06bf-107">The client is also a console application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e06bf-108">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e06bf-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e06bf-109">K vytvoření kontraktu jednosměrné služby, zadejte své smlouvy, použít <xref:System.ServiceModel.OperationContractAttribute> na každou operaci a nastavit <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> k `true` jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="e06bf-109">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="e06bf-110">K prokázání, že klient čekat na dokončení operací služby, implementuje kódu služby v této ukázce pěti sekund zpoždění, jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="e06bf-110">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
```  
/ This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="e06bf-111">Když klient zavolá službu, volání se vrátí bez čekání na dokončení operace služby.</span><span class="sxs-lookup"><span data-stu-id="e06bf-111">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="e06bf-112">Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="e06bf-112">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="e06bf-113">Uvidíte služby přijmout zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="e06bf-113">You can see the service receive messages from the client.</span></span> <span data-ttu-id="e06bf-114">Stisknutím klávesy ENTER v každé okna konzoly vypněte službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="e06bf-114">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="e06bf-115">Klient dokončí před službu, demonstraci toho, že klient čekat na dokončení operací jednosměrné služby.</span><span class="sxs-lookup"><span data-stu-id="e06bf-115">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="e06bf-116">Výstup klienta vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="e06bf-116">The client output is as follows:</span></span>  
  
```  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="e06bf-117">Tento výstup služby se zobrazí:</span><span class="sxs-lookup"><span data-stu-id="e06bf-117">The following service output is shown:</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
```  
  
> [!NOTE]
>  <span data-ttu-id="e06bf-118">HTTP je podle definice požadavků a odpovědí protokolu; Když je žádosti se vrátí odpověď.</span><span class="sxs-lookup"><span data-stu-id="e06bf-118">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="e06bf-119">To platí i pro operaci jednosměrné služby, který je zveřejněný prostřednictvím protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="e06bf-119">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="e06bf-120">Při volání operace služby vrátí kód stavu HTTP 202, předtím, než se spustí operace služby.</span><span class="sxs-lookup"><span data-stu-id="e06bf-120">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="e06bf-121">Tento kód stavu znamená, že žádost byla přijata pro zpracování, ale zpracování dosud nebyl dokončen.</span><span class="sxs-lookup"><span data-stu-id="e06bf-121">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="e06bf-122">Klient, který volal operaci bloky, dokud neobdrží 202 odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="e06bf-122">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="e06bf-123">To může způsobit některé neočekávanému chování při odesílání více jednosměrný zpráv pomocí vazby, který je nakonfigurován pro použití relací.</span><span class="sxs-lookup"><span data-stu-id="e06bf-123">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="e06bf-124">`wsHttpBinding` Vazba použitá v této ukázce je nakonfigurovaný na použití relací ve výchozím nastavení k vytvoření kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e06bf-124">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="e06bf-125">Ve výchozím nastavení jsou zaručené doručení v pořadí, v níž jsou odesílány zprávy v relaci.</span><span class="sxs-lookup"><span data-stu-id="e06bf-125">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="e06bf-126">Z toho důvodu je odeslání o druhou zprávu v relaci není dokud zpracovala první zprávu zpracovat.</span><span class="sxs-lookup"><span data-stu-id="e06bf-126">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="e06bf-127">Důsledkem je, klient až do dokončení zpracování v předchozí zprávě neobdrží 202 odpovědi na zprávy.</span><span class="sxs-lookup"><span data-stu-id="e06bf-127">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="e06bf-128">Klient proto pravděpodobně bloku při každém volání další operace.</span><span class="sxs-lookup"><span data-stu-id="e06bf-128">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="e06bf-129">Chcete-li tomu zabránit, nakonfiguruje této ukázky modulu runtime odesílání zpráv souběžně na různých instancí pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="e06bf-129">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="e06bf-130">Ukázka sady <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> k `PerCall` tak, aby každá zpráva může zpracovat jiné instance.</span><span class="sxs-lookup"><span data-stu-id="e06bf-130">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="e06bf-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>je nastavena na `Multiple` umožňuje více než jedno vlákno k odesílání zpráv v čase.</span><span class="sxs-lookup"><span data-stu-id="e06bf-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e06bf-132">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="e06bf-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e06bf-133">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e06bf-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e06bf-134">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e06bf-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="e06bf-135">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e06bf-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e06bf-136">Spusťte službu před spuštěním klienta a vypnout klienta před ukončením služby.</span><span class="sxs-lookup"><span data-stu-id="e06bf-136">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="e06bf-137">Tím je zabráněno výjimka klienta, pokud nelze klienta ukončení relace zabezpečení ještě jednou, protože služba není pryč.</span><span class="sxs-lookup"><span data-stu-id="e06bf-137">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e06bf-138">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="e06bf-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e06bf-139">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e06bf-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e06bf-140">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e06bf-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e06bf-141">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e06bf-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
  
## <a name="see-also"></a><span data-ttu-id="e06bf-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="e06bf-142">See Also</span></span>
