---
title: Jednosměrný
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: e82034a79610ea7956b3ef07508295578461de1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008030"
---
# <a name="one-way"></a><span data-ttu-id="ff390-102">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="ff390-102">One-Way</span></span>
<span data-ttu-id="ff390-103">Tato ukázka předvádí, služba kontaktovat s operací jednosměrné služby.</span><span class="sxs-lookup"><span data-stu-id="ff390-103">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="ff390-104">Klient nečeká servisní operace dokončit, protože v případě obousměrné servisní operace.</span><span class="sxs-lookup"><span data-stu-id="ff390-104">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="ff390-105">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a používá `wsHttpBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="ff390-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="ff390-106">Služby v této ukázce je aplikace v místním prostředí konzoly, která vám umožní sledovat službu, která přijímá a zpracovává požadavky.</span><span class="sxs-lookup"><span data-stu-id="ff390-106">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="ff390-107">Klient je také konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ff390-107">The client is also a console application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff390-108">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ff390-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ff390-109">Vytvoření kontraktu služby jednosměrné, definování váš kontraktu služby, použije <xref:System.ServiceModel.OperationContractAttribute> třídy pro každou operaci a nastavte <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> k `true` jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="ff390-109">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="ff390-110">Abychom si předvedli, že klient nečeká na dokončení operací služby, implementuje kódu služby v této ukázce zpoždění pěti sekund, jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="ff390-110">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="ff390-111">Když klient zavolá službu, volání se vrátí bez čekání na dokončení operace služby.</span><span class="sxs-lookup"><span data-stu-id="ff390-111">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="ff390-112">Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="ff390-112">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ff390-113">Můžete zobrazit přijetí zprávy služby z klienta.</span><span class="sxs-lookup"><span data-stu-id="ff390-113">You can see the service receive messages from the client.</span></span> <span data-ttu-id="ff390-114">Stisknutím klávesy ENTER v okně konzoly se každý vypnout službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="ff390-114">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="ff390-115">Klient dokončí náskok před službu, představením toho, že klient nečeká na dokončení operací jednosměrné služby.</span><span class="sxs-lookup"><span data-stu-id="ff390-115">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="ff390-116">Výstup klienta vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="ff390-116">The client output is as follows:</span></span>  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="ff390-117">Se zobrazí následující výstup služby:</span><span class="sxs-lookup"><span data-stu-id="ff390-117">The following service output is shown:</span></span>  
  
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
>  <span data-ttu-id="ff390-118">HTTP je podle definice požadavků/odpovědí protokolu; Po provedení požadavku se vrátí odpověď.</span><span class="sxs-lookup"><span data-stu-id="ff390-118">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="ff390-119">To platí i pro operaci jednosměrné služby, která je přístupná přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="ff390-119">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="ff390-120">Při volání operace služby vrátí stavový kód HTTP 202 předtím, než se spustí operace služby.</span><span class="sxs-lookup"><span data-stu-id="ff390-120">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="ff390-121">Tímto stavovým kódem znamená, že požadavek přijal ke zpracování, ale zpracování nebyla dosud dokončena.</span><span class="sxs-lookup"><span data-stu-id="ff390-121">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="ff390-122">Klient, který volá operace blokuje až do obdržení odpovědi 202 ze služby.</span><span class="sxs-lookup"><span data-stu-id="ff390-122">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="ff390-123">Při více jednosměrné zprávy odesílat pomocí vazby, který je nakonfigurován pro použití relací to může způsobit nějaké neočekávané chování.</span><span class="sxs-lookup"><span data-stu-id="ff390-123">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="ff390-124">`wsHttpBinding` Vazba používané v tomto příkladu je nakonfigurována pro použití relací ve výchozím nastavení k vytvoření kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ff390-124">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="ff390-125">Ve výchozím nastavení je zaručena doručeny v pořadí, ve kterém jsou odesílány zprávy v relaci.</span><span class="sxs-lookup"><span data-stu-id="ff390-125">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="ff390-126">Z tohoto důvodu odeslání druhé zprávy v relaci není dokud byla zpracována na první zprávu zpracovat.</span><span class="sxs-lookup"><span data-stu-id="ff390-126">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="ff390-127">Výsledek tohoto je, že klient neobdrží odpovědi 202 zprávy dokud se nedokončí zpracování předchozí zprávu.</span><span class="sxs-lookup"><span data-stu-id="ff390-127">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="ff390-128">Klient se proto zobrazí do bloku na každé následné operace volání.</span><span class="sxs-lookup"><span data-stu-id="ff390-128">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="ff390-129">Chcete-li toto chování vyhnout, tento vzorovým kódem se nakonfiguruje runtime k odeslání zpráv souběžně, což umožňuje jedinečných instancí pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="ff390-129">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="ff390-130">Ukázka sady <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> k `PerCall` tak, aby každá zpráva mohou být zpracovány do jiné instance.</span><span class="sxs-lookup"><span data-stu-id="ff390-130">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="ff390-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> je nastavena na `Multiple` umožňuje více než jedno vlákno k odeslání zprávy v čase.</span><span class="sxs-lookup"><span data-stu-id="ff390-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ff390-132">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="ff390-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ff390-133">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ff390-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ff390-134">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ff390-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ff390-135">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ff390-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff390-136">Spusťte službu, před spuštěním klienta a vypnout klienta před ukončením služby.</span><span class="sxs-lookup"><span data-stu-id="ff390-136">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="ff390-137">Tím předejdete výjimka klienta, pokud nelze klienta ukončete relaci zabezpečení přímo, protože tato služba je pryč.</span><span class="sxs-lookup"><span data-stu-id="ff390-137">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff390-138">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="ff390-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ff390-139">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ff390-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ff390-140">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ff390-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ff390-141">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ff390-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
