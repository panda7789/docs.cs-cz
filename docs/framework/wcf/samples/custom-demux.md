---
title: Vlastní demux
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
caps.latest.revision: 41
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 45184c2d884347baef4090ed496e22e77aab5423
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="custom-demux"></a><span data-ttu-id="871ac-102">Vlastní demux</span><span class="sxs-lookup"><span data-stu-id="871ac-102">Custom Demux</span></span>
<span data-ttu-id="871ac-103">Tento příklad ukazuje, jak hlavičky zpráv MSMQ lze mapovat na jinou službu operations tak, aby [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby využívající <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nejsou omezeny na použití jedné operace služby, jak je předvedeno v [služba Řízení front zpráv Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) a [Windows Communication Foundation do řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) ukázky.</span><span class="sxs-lookup"><span data-stu-id="871ac-103">This sample demonstrates how MSMQ message headers can be mapped to different service operations so that [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services that use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> are not limited to using one service operation as demonstrated in the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) and [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) samples.</span></span>  
  
 <span data-ttu-id="871ac-104">Služba v této ukázce je vlastním hostováním konzolové aplikace, které vám umožňují sledovat, že služby, která přijímá zprávy zařazené do fronty.</span><span class="sxs-lookup"><span data-stu-id="871ac-104">The service in this sample is a self-hosted console application to enable you to observe the service that receives queued messages.</span></span>  
  
 <span data-ttu-id="871ac-105">Kontrakt služby je `IOrderProcessor`a definuje jednosměrné služby, který je vhodný pro použití s front.</span><span class="sxs-lookup"><span data-stu-id="871ac-105">The service contract is `IOrderProcessor`, and defines a one-way service that is suitable for use with queues.</span></span>  

```csharp
[ServiceContract]  
[KnownType(typeof(PurchaseOrder))]  
[KnownType(typeof(String))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Name = "SubmitPurchaseOrder")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
  
    [OperationContract(IsOneWay = true, Name = "CancelPurchaseOrder")]  
    void CancelPurchaseOrder(MsmqMessage<string> ponumber);  
}  
```

 <span data-ttu-id="871ac-106">Zprávy MSMQ nemá hlavičku akce.</span><span class="sxs-lookup"><span data-stu-id="871ac-106">An MSMQ message does not have an Action header.</span></span> <span data-ttu-id="871ac-107">Není možné automaticky mapovat různé zprávy služby MSMQ kontrakty operaci.</span><span class="sxs-lookup"><span data-stu-id="871ac-107">It is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="871ac-108">Proto může být pouze jeden kontrakt operaci.</span><span class="sxs-lookup"><span data-stu-id="871ac-108">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="871ac-109">K překonání tohoto omezení služby implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> metodu <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="871ac-109">To overcome this limitation, the service implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method of the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface.</span></span> <span data-ttu-id="871ac-110"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> Metoda umožňuje službu, kterou chcete mapovat danou hlavičku zprávy pro konkrétní službu operaci.</span><span class="sxs-lookup"><span data-stu-id="871ac-110">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method enables the service to map a given header of the message to a particular service operation.</span></span> <span data-ttu-id="871ac-111">V této ukázce je záhlaví popisek zprávy je namapovaný k operacím služby.</span><span class="sxs-lookup"><span data-stu-id="871ac-111">In this sample, the message's label header is mapped to the service operations.</span></span> <span data-ttu-id="871ac-112">`Name` Parametr operaci kontrakt Určuje, které operace služby musí být odesílány pro danou zprávou štítek.</span><span class="sxs-lookup"><span data-stu-id="871ac-112">The `Name` parameter of the operation contract determines which service operation must be dispatched for a given message label.</span></span> <span data-ttu-id="871ac-113">Například pokud hlavička popisek zprávy obsahuje "SubmitPurchaseOrder", je volána operace služby "SubmitPurchaseOrder".</span><span class="sxs-lookup"><span data-stu-id="871ac-113">For example, if the message's label header contains "SubmitPurchaseOrder", the "SubmitPurchaseOrder" service operation is invoked.</span></span>  

```csharp
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```

 <span data-ttu-id="871ac-114">Služba musí implementovat <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> metodu <xref:System.ServiceModel.Description.IContractBehavior> rozhraní, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="871ac-114">The service must implement the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> method of the <xref:System.ServiceModel.Description.IContractBehavior> interface as shown in the following sample code.</span></span> <span data-ttu-id="871ac-115">To platí vlastní `OperationSelector` modulu runtime service framework odesílání.</span><span class="sxs-lookup"><span data-stu-id="871ac-115">This applies the custom `OperationSelector` to the service framework dispatch runtime.</span></span>  

```csharp
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```

 <span data-ttu-id="871ac-116">Zpráva musí projít dispečera <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> před získáním k třída OperationSelector.</span><span class="sxs-lookup"><span data-stu-id="871ac-116">A message must pass through the dispatcher's <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> before getting to the OperationSelector.</span></span> <span data-ttu-id="871ac-117">Ve výchozím nastavení je odmítnuta zprávu, pokud jeho akce nebyl nalezen na jakékoli smlouvy implementované službu.</span><span class="sxs-lookup"><span data-stu-id="871ac-117">By default a message is rejected if its action cannot be found on any contract implemented by the service.</span></span> <span data-ttu-id="871ac-118">Abyste se vyhnuli tuto kontrolu, můžeme implementovat <xref:System.ServiceModel.Description.IEndpointBehavior> s názvem `MatchAllFilterBehavior`, což umožňuje jakékoli zprávy předávat `ContractFilter` použitím <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="871ac-118">To avoid this check, we implement an <xref:System.ServiceModel.Description.IEndpointBehavior> named `MatchAllFilterBehavior`, which allows any message to pass through the `ContractFilter` by applying the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> as follows.</span></span>  

```csharp
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```
  
 <span data-ttu-id="871ac-119">Zpráva odeslaná službou, je odeslána operaci příslušnou službu pomocí informací uvedených v hlavičce popisek.</span><span class="sxs-lookup"><span data-stu-id="871ac-119">When a message is received by the service, the appropriate service operation is dispatched using the information provided by the label header.</span></span> <span data-ttu-id="871ac-120">Tělo zprávy je deserializovat do `PurchaseOrder` objektu, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="871ac-120">The body of the message is deserialized into a `PurchaseOrder` object, as shown in the following sample code.</span></span>  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```

 <span data-ttu-id="871ac-121">Služba se hostuje sama.</span><span class="sxs-lookup"><span data-stu-id="871ac-121">The service is self-hosted.</span></span> <span data-ttu-id="871ac-122">Při použití služby MSMQ, fronty, který se používá, musí být vytvořeny předem.</span><span class="sxs-lookup"><span data-stu-id="871ac-122">When using the MSMQ, the queue that is used must be created in advance.</span></span> <span data-ttu-id="871ac-123">Tento krok můžete provést ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="871ac-123">This can be done manually or through code.</span></span> <span data-ttu-id="871ac-124">V této ukázce služba obsahuje kód, zkontrolujte existenci fronty a ji vytvoří, pokud fronta neexistuje.</span><span class="sxs-lookup"><span data-stu-id="871ac-124">In this sample, the service contains code to check for the existence of the queue and creates it if the queue does not exist.</span></span> <span data-ttu-id="871ac-125">Název fronty je číst z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="871ac-125">The queue name is read from the configuration file.</span></span>  

```csharp
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration  
    string queueName = ConfigurationManager.AppSettings["orderQueueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {                 
        ServiceEndpoint endpoint = serviceHost.Description.Endpoints[0];  
        endpoint.Behaviors.Add(new MatchAllFilterBehavior());  
  
        //Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();  
    }  
}  
```

 <span data-ttu-id="871ac-126">Název fronty služby MSMQ je zadán v oddílu appSettings konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="871ac-126">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="871ac-127">Název fronty používá tečku (.) pro místní počítač a oddělovače zpětné lomítko, v jeho cesty.</span><span class="sxs-lookup"><span data-stu-id="871ac-127">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="871ac-128">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Adresa koncového bodu určuje schématu msmq.formatname a používá localhost pro místní počítač.</span><span class="sxs-lookup"><span data-stu-id="871ac-128">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="871ac-129">Následující schéma je adresa správně formátovaný fronty podle názvu formátu MSMQ adresování pokyny.</span><span class="sxs-lookup"><span data-stu-id="871ac-129">What follows the scheme is a properly formatted queue address according to the MSMQ Format name addressing guidelines.</span></span>  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="871ac-130">Tato ukázka vyžaduje instalaci [služby Řízení front zpráv](http://go.microsoft.com/fwlink/?LinkId=95143).</span><span class="sxs-lookup"><span data-stu-id="871ac-130">This sample requires the installation of [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=95143).</span></span>  
  
 <span data-ttu-id="871ac-131">Spusťte službu a spustit klienta.</span><span class="sxs-lookup"><span data-stu-id="871ac-131">Start the service and run the client.</span></span>  
  
 <span data-ttu-id="871ac-132">Tento výstup je vidět na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="871ac-132">The following output is seen on the client.</span></span>  
  
```  
Placed the order:Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
Canceled the Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="871ac-133">Tento výstup musí zobrazit na službu.</span><span class="sxs-lookup"><span data-stu-id="871ac-133">The following output must be seen on the service.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
Processing Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Shipped  
Purchase Order 28fc457a-1a56-4fe0-9dde-156965c21ed6 is canceled  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="871ac-134">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="871ac-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="871ac-135">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="871ac-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="871ac-136">Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty.</span><span class="sxs-lookup"><span data-stu-id="871ac-136">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="871ac-137">Pokud fronta neexistuje, vytvoří služba jeden.</span><span class="sxs-lookup"><span data-stu-id="871ac-137">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="871ac-138">Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="871ac-138">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="871ac-139">Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="871ac-139">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="871ac-140">Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="871ac-140">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="871ac-141">Rozbalte **funkce** kartě.</span><span class="sxs-lookup"><span data-stu-id="871ac-141">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="871ac-142">Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="871ac-142">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="871ac-143">Zkontrolujte **transakcí** pole.</span><span class="sxs-lookup"><span data-stu-id="871ac-143">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="871ac-144">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="871ac-144">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="871ac-145">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="871ac-145">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="871ac-146">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="871ac-146">To run the sample in a single- or cross- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="871ac-147">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="871ac-147">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="871ac-148">Zkopírujte soubory programu služby ve složce \service\bin\ ve složce pro specifický jazyk k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="871ac-148">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="871ac-149">Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.</span><span class="sxs-lookup"><span data-stu-id="871ac-149">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="871ac-150">V souboru Client.exe.config změnit orderQueueName k zadání názvu počítače služba místo ".".</span><span class="sxs-lookup"><span data-stu-id="871ac-150">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="871ac-151">Na počítači se službou spusťte z příkazového řádku Service.exe.</span><span class="sxs-lookup"><span data-stu-id="871ac-151">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="871ac-152">Na klientském počítači spusťte z příkazového řádku Client.exe.</span><span class="sxs-lookup"><span data-stu-id="871ac-152">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="871ac-153">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="871ac-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="871ac-154">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="871ac-154">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="871ac-155">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="871ac-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="871ac-156">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="871ac-156">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a><span data-ttu-id="871ac-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="871ac-157">See Also</span></span>  
 [<span data-ttu-id="871ac-158">Zařazování do front ve WCF</span><span class="sxs-lookup"><span data-stu-id="871ac-158">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="871ac-159">Služba Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="871ac-159">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=95143)
