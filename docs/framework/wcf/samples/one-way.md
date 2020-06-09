---
title: Jednosměrný
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 07fc4ecf981acbad577758c943aa22405f528a52
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575249"
---
# <a name="one-way"></a><span data-ttu-id="e0b43-102">Jednosměrný</span><span class="sxs-lookup"><span data-stu-id="e0b43-102">One-Way</span></span>
<span data-ttu-id="e0b43-103">Tato ukázka demonstruje kontakt služby pomocí jednosměrných operací služby.</span><span class="sxs-lookup"><span data-stu-id="e0b43-103">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="e0b43-104">Klient nečeká na dokončení operací služby, protože se jedná o případ s obousměrnou operací služby.</span><span class="sxs-lookup"><span data-stu-id="e0b43-104">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="e0b43-105">Tato ukázka je založena na [Začínáme](getting-started-sample.md) a používá `wsHttpBinding` vazbu.</span><span class="sxs-lookup"><span data-stu-id="e0b43-105">This sample is based on the [Getting Started](getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="e0b43-106">Služba v této ukázce je samoobslužná Konzolová aplikace, která vám umožní sledovat službu, která přijímá a zpracovává požadavky.</span><span class="sxs-lookup"><span data-stu-id="e0b43-106">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="e0b43-107">Klient je také Konzolová aplikace.</span><span class="sxs-lookup"><span data-stu-id="e0b43-107">The client is also a console application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0b43-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e0b43-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e0b43-109">Chcete-li vytvořit jednosměrný kontrakt služby, definujte kontrakt služby, použijte <xref:System.ServiceModel.OperationContractAttribute> pro každou operaci třídu a nastavte <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> na `true` jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="e0b43-109">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="e0b43-110">Chcete-li předvést, že klient nečeká na dokončení operací služby, kód služby v této ukázce implementuje zpoždění pět sekund, jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="e0b43-110">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="e0b43-111">Když klient volá službu, volání se vrátí bez čekání na dokončení operace služby.</span><span class="sxs-lookup"><span data-stu-id="e0b43-111">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="e0b43-112">Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta.</span><span class="sxs-lookup"><span data-stu-id="e0b43-112">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="e0b43-113">Můžete vidět, že služba přijímá zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="e0b43-113">You can see the service receive messages from the client.</span></span> <span data-ttu-id="e0b43-114">V každém okně konzoly stiskněte klávesu ENTER a ukončete tak službu i klienta.</span><span class="sxs-lookup"><span data-stu-id="e0b43-114">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="e0b43-115">Klient se dokončí před službou a demonstruje, že klient nečeká na dokončení jednosměrných operací služby.</span><span class="sxs-lookup"><span data-stu-id="e0b43-115">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="e0b43-116">Výstup klienta je následující:</span><span class="sxs-lookup"><span data-stu-id="e0b43-116">The client output is as follows:</span></span>  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="e0b43-117">Zobrazí se následující výstup služby:</span><span class="sxs-lookup"><span data-stu-id="e0b43-117">The following service output is shown:</span></span>  
  
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
> <span data-ttu-id="e0b43-118">HTTP je, podle definice, protokolu požadavků a odpovědí. po podání žádosti se vrátí odpověď.</span><span class="sxs-lookup"><span data-stu-id="e0b43-118">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="e0b43-119">To platí i pro jednosměrnou operaci služby, která je vystavená přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="e0b43-119">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="e0b43-120">Při volání operace vrátí služba stavový kód HTTP 202 před provedením operace služby.</span><span class="sxs-lookup"><span data-stu-id="e0b43-120">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="e0b43-121">Tento stavový kód znamená, že žádost byla přijata ke zpracování, ale zpracování ještě nebylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="e0b43-121">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="e0b43-122">Klient, který se nazývá operace, zablokuje, dokud nepřijme odpověď 202 od služby.</span><span class="sxs-lookup"><span data-stu-id="e0b43-122">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="e0b43-123">To může způsobit neočekávané chování při posílání více jednosměrných zpráv pomocí vazby, která je nakonfigurována pro použití relací.</span><span class="sxs-lookup"><span data-stu-id="e0b43-123">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="e0b43-124">`wsHttpBinding`Vazba použitá v této ukázce je nakonfigurována tak, aby ve výchozím nastavení používala relace pro vytvoření kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e0b43-124">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="e0b43-125">Ve výchozím nastavení jsou zprávy v relaci zaručeny k doručení v pořadí, ve kterém jsou odesílány.</span><span class="sxs-lookup"><span data-stu-id="e0b43-125">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="e0b43-126">Z tohoto důvodu se při odeslání druhé zprávy v relaci nezpracovává, dokud se nezpracuje první zpráva.</span><span class="sxs-lookup"><span data-stu-id="e0b43-126">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="e0b43-127">Výsledkem je, že klient neobdrží odpověď 202 pro zprávu, dokud nebude dokončeno zpracování předchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="e0b43-127">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="e0b43-128">Klient se proto zobrazí při každém následném volání operace.</span><span class="sxs-lookup"><span data-stu-id="e0b43-128">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="e0b43-129">Chcete-li se tomuto chování vyhnout, Tato ukázka nakonfiguruje modul runtime tak, aby odesílal zprávy souběžně na samostatné instance pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="e0b43-129">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="e0b43-130">Ukázka nastaví <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> na `PerCall` tak, aby každá zpráva mohla být zpracována jinou instancí.</span><span class="sxs-lookup"><span data-stu-id="e0b43-130">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="e0b43-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>je nastaveno na `Multiple` , aby bylo možné odesílat zprávy najednou více než jedno vlákno.</span><span class="sxs-lookup"><span data-stu-id="e0b43-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e0b43-132">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="e0b43-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e0b43-133">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0b43-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e0b43-134">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0b43-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e0b43-135">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0b43-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0b43-136">Před ukončením služby spusťte službu před spuštěním klienta nástroje a vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="e0b43-136">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="e0b43-137">Tím se zabrání výjimka klienta, pokud klient nemůže relaci zabezpečení vyčistit, protože služba zmizela.</span><span class="sxs-lookup"><span data-stu-id="e0b43-137">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e0b43-138">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="e0b43-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e0b43-139">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="e0b43-139">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e0b43-140">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="e0b43-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e0b43-141">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e0b43-141">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
