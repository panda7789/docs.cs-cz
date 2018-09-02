---
title: Řízení front zpráv do WCF
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 983fd2ef7338e24c67e3556849e73c2feaf97a60
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423371"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="5e416-102">Řízení front zpráv do WCF</span><span class="sxs-lookup"><span data-stu-id="5e416-102">Message Queuing to Windows Communication Foundation</span></span>
<span data-ttu-id="5e416-103">Tato ukázka předvádí, jak aplikace služby Řízení front zpráv (MSMQ) zprávy MSMQ odeslat do služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5e416-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="5e416-104">Služba je v místním prostředí konzolovou aplikaci pro vám umožní sledovat službu přijímání zpráv zařazených do fronty.</span><span class="sxs-lookup"><span data-stu-id="5e416-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
 <span data-ttu-id="5e416-105">Kontrakt služby je `IOrderProcessor`, která definuje jednosměrné, který je vhodný pro použití s frontami služby.</span><span class="sxs-lookup"><span data-stu-id="5e416-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="5e416-106">Zprávy MSMQ nemá hlavičku akce, takže není možné automaticky mapovat různé zprávy služby MSMQ pro operaci smlouvy.</span><span class="sxs-lookup"><span data-stu-id="5e416-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="5e416-107">Proto může být pouze jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="5e416-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="5e416-108">Pokud chcete definovat více než jeden kontrakt služby, aplikace musí poskytovat informace ohledně toho, která záhlaví zprávy služby MSMQ (například popisku nebo ID korelace) umožňuje rozhodnout, kterou kontrakt k odeslání.</span><span class="sxs-lookup"><span data-stu-id="5e416-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span> <span data-ttu-id="5e416-109">To je patrné [vlastní Demux](../../../../docs/framework/wcf/samples/custom-demux.md).</span><span class="sxs-lookup"><span data-stu-id="5e416-109">This is demonstrated in the [Custom Demux](../../../../docs/framework/wcf/samples/custom-demux.md).</span></span>  
  
 <span data-ttu-id="5e416-110">Zprávy služby MSMQ neobsahuje informace ohledně toho, která hlavičky jsou namapovány na různé parametry kontrakt.</span><span class="sxs-lookup"><span data-stu-id="5e416-110">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="5e416-111">Parametr je typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), která obsahuje základní zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5e416-111">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="5e416-112">Typ "T" v <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) třída reprezentuje data, která je serializován do textu zprávy MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5e416-112">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="5e416-113">V této ukázce `PurchaseOrder` je typ serializován do textu zprávy MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5e416-113">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  
  
 <span data-ttu-id="5e416-114">Následující ukázkový kód ukazuje kontrakt služby služba zpracování objednávky.</span><span class="sxs-lookup"><span data-stu-id="5e416-114">The following sample code shows the service contract of the order processing service.</span></span>  

```csharp
// Define a service contract.  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```

 <span data-ttu-id="5e416-115">Tato služba je vlastní hostované.</span><span class="sxs-lookup"><span data-stu-id="5e416-115">The service is self hosted.</span></span> <span data-ttu-id="5e416-116">Při použití služby MSMQ, fronty, používá se musí vytvořit předem.</span><span class="sxs-lookup"><span data-stu-id="5e416-116">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="5e416-117">To můžete udělat ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="5e416-117">This can be done manually or through code.</span></span> <span data-ttu-id="5e416-118">V této ukázce služba zkontroluje existenci fronty a v případě potřeby ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="5e416-118">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="5e416-119">Název fronty načítají z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5e416-119">The queue name is read from the configuration file.</span></span>  

```csharp
public static void Main()  
{  
    // Get the MSMQ queue name from the application settings in   
    // configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
    // Create the MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
    …  
}  
```

 <span data-ttu-id="5e416-120">Služba vytvoří a otevře <xref:System.ServiceModel.ServiceHost> pro `OrderProcessorService`, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="5e416-120">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>  

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
{  
    serviceHost.Open();  
    Console.WriteLine("The service is ready.");  
    Console.WriteLine("Press <ENTER> to terminate service.");  
    Console.ReadLine();  
    serviceHost.Close();  
}  
```

 <span data-ttu-id="5e416-121">Název fronty MSMQ je zadat v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5e416-121">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e416-122">Název fronty používá tečku (.) pro místní počítače a zpětné lomítko oddělovače v cestě.</span><span class="sxs-lookup"><span data-stu-id="5e416-122">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="5e416-123">Adresa koncového bodu WCF Určuje schéma msmq.formatname a používá localhost pro místní počítač.</span><span class="sxs-lookup"><span data-stu-id="5e416-123">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="5e416-124">Adresa fronty pro každý název formátu MSMQ adresování pokyny následuje schéma msmq.formatname.</span><span class="sxs-lookup"><span data-stu-id="5e416-124">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 <span data-ttu-id="5e416-125">Klientská aplikace je aplikace služby MSMQ, která se používá <xref:System.Messaging.MessageQueue.Send%2A> metodu pro odeslání odolné a transakční zprávy do fronty, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="5e416-125">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>  

```csharp
//Connect to the queue.  
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);  
  
// Create the purchase order.  
PurchaseOrder po = new PurchaseOrder();  
po.CustomerId = "somecustomer.com";  
po.PONumber = Guid.NewGuid().ToString();  
  
PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
lineItem1.ProductId = "Blue Widget";  
lineItem1.Quantity = 54;  
lineItem1.UnitCost = 29.99F;  
  
PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
lineItem2.ProductId = "Red Widget";  
lineItem2.Quantity = 890;  
lineItem2.UnitCost = 45.89F;  
  
po.orderLineItems = new PurchaseOrderLineItem[2];  
po.orderLineItems[0] = lineItem1;  
po.orderLineItems[1] = lineItem2;  
  
// Submit the purchase order.  
Message msg = new Message();  
msg.Body = po;  
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
  
    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);  
    // Complete the transaction.  
    scope.Complete();  
  
}  
Console.WriteLine("Placed the order:{0}", po);  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```

 <span data-ttu-id="5e416-126">Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="5e416-126">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="5e416-127">Můžete zobrazit přijetí zprávy služby z klienta.</span><span class="sxs-lookup"><span data-stu-id="5e416-127">You can see the service receive messages from the client.</span></span> <span data-ttu-id="5e416-128">Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="5e416-128">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="5e416-129">Mějte na paměti, protože služba Řízení front se používá, klient a služba nemusí být zprovoznit ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="5e416-129">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="5e416-130">Například může spustit klienta, vypněte ho a potom spusťte službu a pak by stále přijímat zprávy.</span><span class="sxs-lookup"><span data-stu-id="5e416-130">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="5e416-131">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="5e416-131">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5e416-132">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e416-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5e416-133">Pokud je služba spuštěna první, zkontroluje se tak, aby byl do fronty k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5e416-133">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="5e416-134">Pokud fronta neexistuje, služba ho vytvoří.</span><span class="sxs-lookup"><span data-stu-id="5e416-134">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="5e416-135">Můžete spustit služba nejdřív vytvořte frontu nebo můžete vytvořit prostřednictvím Správce fronty MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5e416-135">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="5e416-136">Postupujte podle těchto kroků můžete vytvořit frontu Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="5e416-136">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="5e416-137">Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e416-137">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="5e416-138">Rozbalte **funkce** kartu.</span><span class="sxs-lookup"><span data-stu-id="5e416-138">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="5e416-139">Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="5e416-139">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="5e416-140">Zkontrolujte, **transakční** pole.</span><span class="sxs-lookup"><span data-stu-id="5e416-140">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="5e416-141">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="5e416-141">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="5e416-142">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e416-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="5e416-143">Spusťte ukázku v jednom počítači konfiguraci, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e416-143">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="5e416-144">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="5e416-144">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="5e416-145">Zkopírujte soubory programu služby ze složky \service\bin\ v rámci složky specifické pro jazyk, k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="5e416-145">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="5e416-146">Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="5e416-146">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="5e416-147">V souboru Client.exe.config změnit orderQueueName k zadání názvu počítače služba namísto ".".</span><span class="sxs-lookup"><span data-stu-id="5e416-147">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="5e416-148">Na počítači se službou spusťte z příkazového řádku Service.exe.</span><span class="sxs-lookup"><span data-stu-id="5e416-148">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="5e416-149">Na klientském počítači spusťte Client.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5e416-149">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5e416-150">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="5e416-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5e416-151">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="5e416-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5e416-152">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="5e416-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5e416-153">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5e416-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a><span data-ttu-id="5e416-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e416-154">See Also</span></span>  
 [<span data-ttu-id="5e416-155">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="5e416-155">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="5e416-156">Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front</span><span class="sxs-lookup"><span data-stu-id="5e416-156">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="5e416-157">Služba Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="5e416-157">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
