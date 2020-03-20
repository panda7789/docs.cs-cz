---
title: Jednosměrný
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 3203762e05c794ed28b65d8fded6972fac1f5820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183446"
---
# <a name="one-way"></a><span data-ttu-id="f7b63-102">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="f7b63-102">One-Way</span></span>
<span data-ttu-id="f7b63-103">Tato ukázka ukazuje kontakt služby s operacemi jednosměrné služby.</span><span class="sxs-lookup"><span data-stu-id="f7b63-103">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="f7b63-104">Klient nečeká na dokončení operací služby, jako je tomu v případě obousměrných operací služby.</span><span class="sxs-lookup"><span data-stu-id="f7b63-104">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="f7b63-105">Tato ukázka je založena na `wsHttpBinding` [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a používá vazbu.</span><span class="sxs-lookup"><span data-stu-id="f7b63-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="f7b63-106">Služba v této ukázce je aplikace konzoly s vlastním hostitelem, která umožňuje sledovat službu, která přijímá a zpracovává požadavky.</span><span class="sxs-lookup"><span data-stu-id="f7b63-106">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="f7b63-107">Klient je také konzolová aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7b63-107">The client is also a console application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7b63-108">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f7b63-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f7b63-109">Chcete-li vytvořit jednosměrnou servisní smlouvu, definujte servisní smlouvu, použijte třídu <xref:System.ServiceModel.OperationContractAttribute> pro každou operaci a nastavte <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> tak, jak je `true` znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="f7b63-109">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
```csharp
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
  
 <span data-ttu-id="f7b63-110">Chcete-li prokázat, že klient nečeká na dokončení operací služby, kód služby v této ukázce implementuje pětisekundové zpoždění, jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="f7b63-110">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
```csharp
// This service class implements the service contract.  
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
  
 <span data-ttu-id="f7b63-111">Když klient volá službu, volání vrátí bez čekání na dokončení operace služby.</span><span class="sxs-lookup"><span data-stu-id="f7b63-111">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="f7b63-112">Při spuštění ukázky jsou aktivity klienta a služby zobrazeny v systému Windows služby i klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="f7b63-112">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="f7b63-113">Můžete vidět službu přijímat zprávy od klienta.</span><span class="sxs-lookup"><span data-stu-id="f7b63-113">You can see the service receive messages from the client.</span></span> <span data-ttu-id="f7b63-114">Stisknutím klávesy ENTER v každém okně konzoly vypněte službu i klienta.</span><span class="sxs-lookup"><span data-stu-id="f7b63-114">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="f7b63-115">Klient dokončí před službou, což dokazuje, že klient nečeká na dokončení operací jednosměrné služby.</span><span class="sxs-lookup"><span data-stu-id="f7b63-115">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="f7b63-116">Výstup klienta je následující:</span><span class="sxs-lookup"><span data-stu-id="f7b63-116">The client output is as follows:</span></span>  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="f7b63-117">Zobrazí se následující výstup služby:</span><span class="sxs-lookup"><span data-stu-id="f7b63-117">The following service output is shown:</span></span>  
  
```console  
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
> <span data-ttu-id="f7b63-118">HTTP je ze své podstaty protokol požadavku/odpovědi; při požadavku je vrácena odpověď.</span><span class="sxs-lookup"><span data-stu-id="f7b63-118">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="f7b63-119">To platí i pro jednosměrné operace služby, která je vystavena přes HTTP.</span><span class="sxs-lookup"><span data-stu-id="f7b63-119">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="f7b63-120">Při volání operace vrátí služba stavový kód HTTP 202 před spuštěním operace služby.</span><span class="sxs-lookup"><span data-stu-id="f7b63-120">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="f7b63-121">Tento stavový kód znamená, že požadavek byl přijat ke zpracování, ale zpracování ještě nebylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="f7b63-121">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="f7b63-122">Klient, který volal bloky operace, dokud neobdrží odpověď 202 ze služby.</span><span class="sxs-lookup"><span data-stu-id="f7b63-122">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="f7b63-123">To může způsobit některé neočekávané chování při více jednosměrné zprávy jsou odesílány pomocí vazby, která je nakonfigurována pro použití relací.</span><span class="sxs-lookup"><span data-stu-id="f7b63-123">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="f7b63-124">Vazba použitá `wsHttpBinding` v této ukázce je nakonfigurována tak, aby ve výchozím nastavení používala relace k vytvoření kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f7b63-124">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="f7b63-125">Ve výchozím nastavení je zaručeno, že zprávy v relaci dorazí v pořadí, ve kterém jsou odesílány.</span><span class="sxs-lookup"><span data-stu-id="f7b63-125">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="f7b63-126">Z tohoto důvodu při odeslání druhé zprávy v relaci není zpracována, dokud první zpráva byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="f7b63-126">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="f7b63-127">Výsledkem je, že klient neobdrží odpověď 202 pro zprávu, dokud nebude dokončeno zpracování předchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="f7b63-127">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="f7b63-128">Klient se proto zobrazí blokovat při každém volání následující operace.</span><span class="sxs-lookup"><span data-stu-id="f7b63-128">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="f7b63-129">Chcete-li se tomuto chování vyhnout, tato ukázka konfiguruje runtime k odeslání zpráv současně na různé instance pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="f7b63-129">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="f7b63-130">Ukázka <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> se `PerCall` nastaví tak, aby každá zpráva může být zpracována jinou instancí.</span><span class="sxs-lookup"><span data-stu-id="f7b63-130">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="f7b63-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>je nastavena tak, aby `Multiple` více než jedno vlákno k odeslání zpráv najednou.</span><span class="sxs-lookup"><span data-stu-id="f7b63-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f7b63-132">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="f7b63-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f7b63-133">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7b63-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f7b63-134">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7b63-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f7b63-135">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f7b63-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7b63-136">Spusťte službu před spuštěním klienta a vypněte klienta před vypnutím služby.</span><span class="sxs-lookup"><span data-stu-id="f7b63-136">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="f7b63-137">Tím se vyhnete výjimce klienta, když klient nemůže zavřít relaci zabezpečení čistě, protože služba je pryč.</span><span class="sxs-lookup"><span data-stu-id="f7b63-137">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f7b63-138">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="f7b63-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f7b63-139">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f7b63-139">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f7b63-140">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f7b63-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f7b63-141">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f7b63-141">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
