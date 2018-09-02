---
title: Z WCF do Řízení front zpráv
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: ea0723d178b37b1ff2581981f8f49a6953c913cc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403617"
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="79267-102">Z WCF do Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="79267-102">Windows Communication Foundation to Message Queuing</span></span>
<span data-ttu-id="79267-103">Tato ukázka předvádí, jak můžete odeslat zprávu do aplikace služby Řízení front zpráv (MSMQ) aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="79267-103">This sample demonstrates how a Windows Communication Foundation (WCF) application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="79267-104">Služba je v místním prostředí konzolovou aplikaci pro vám umožní sledovat službu přijímání zpráv zařazených do fronty.</span><span class="sxs-lookup"><span data-stu-id="79267-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="79267-105">Klienta a služby nemusí být spuštěná ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="79267-105">The service and client do not have to be running at the same time.</span></span>  
  
 <span data-ttu-id="79267-106">Služba přijímá zprávy z fronty a zpracovávat objednávky.</span><span class="sxs-lookup"><span data-stu-id="79267-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="79267-107">Služba vytvoří transakční frontu a nastaví obslužné rutiny zpráv byla přijata zpráva, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="79267-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>  

```csharp
static void Main(string[] args)  
{  
    if (!MessageQueue.Exists(  
              ConfigurationManager.AppSettings["queueName"]))  
       MessageQueue.Create(  
           ConfigurationManager.AppSettings["queueName"], true);  
        //Connect to the queue  
        MessageQueue Queue = new   
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);  
    Queue.ReceiveCompleted +=   
                 new ReceiveCompletedEventHandler(ProcessOrder);  
    Queue.BeginReceive();  
    Console.WriteLine("Order Service is running");  
    Console.ReadLine();  
}  
```

 <span data-ttu-id="79267-108">Při doručení zprávy ve frontě, obslužná rutina zprávy `ProcessOrder` je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="79267-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>  

```csharp
public static void ProcessOrder(Object source,  
    ReceiveCompletedEventArgs asyncResult)  
{  
    try  
    {  
        // Connect to the queue.  
        MessageQueue Queue = (MessageQueue)source;  
        // End the asynchronous receive operation.  
        System.Messaging.Message msg =   
                     Queue.EndReceive(asyncResult.AsyncResult);  
        msg.Formatter = new System.Messaging.XmlMessageFormatter(  
                                new Type[] { typeof(PurchaseOrder) });  
        PurchaseOrder po = (PurchaseOrder) msg.Body;  
        Random statusIndexer = new Random();  
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];  
        Console.WriteLine("Processing {0} ", po);  
        Queue.BeginReceive();  
    }  
    catch (System.Exception ex)  
    {  
        Console.WriteLine(ex.Message);  
    }  
  
}  
```

 <span data-ttu-id="79267-109">Extrahuje služby `ProcessOrder` tělo zprávy ze služby MSMQ a objednávku zpracovává.</span><span class="sxs-lookup"><span data-stu-id="79267-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>  
  
 <span data-ttu-id="79267-110">Název fronty MSMQ je zadat v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="79267-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="79267-111">Název fronty používá tečku (.) pro místní počítače a zpětné lomítko oddělovače v cestě.</span><span class="sxs-lookup"><span data-stu-id="79267-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>  
  
 <span data-ttu-id="79267-112">Klient vytvoří nákupní objednávka a odešle nákupní objednávka v rámci oboru transakcí, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="79267-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>  

```csharp
// Create the purchase order  
PurchaseOrder po = new PurchaseOrder();  
// Fill in the details  
...  
  
OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");  
  
MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    client.SubmitPurchaseOrder(ordermsg);  
    scope.Complete();  
}  
Console.WriteLine("Order has been submitted:{0}", po);  
  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```

 <span data-ttu-id="79267-113">Klient použije vlastní klienta v daném pořadí do fronty odesílat zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="79267-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="79267-114">Protože se aplikace, který přijímá a zpracovává zprávy služby MSMQ aplikace a aplikace WCF, neexistuje žádný implicitní smlouvu mezi těmito dvěma aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="79267-114">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="79267-115">Takže nemůžeme vytvořit proxy server pomocí nástroje Svcutil.exe v tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="79267-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>  
  
 <span data-ttu-id="79267-116">Vlastní klient je v podstatě stejný pro všechny aplikace WCF, které používají `MsmqIntegration` vazby pro odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="79267-116">The custom client is essentially the same for all WCF applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="79267-117">Na rozdíl od jiných klientů neobsahoval celou řadu operací služby.</span><span class="sxs-lookup"><span data-stu-id="79267-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="79267-118">Odeslat zprávu tato operace je pouze.</span><span class="sxs-lookup"><span data-stu-id="79267-118">It is a submit message operation only.</span></span>  

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
  
public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor  
{  
    public OrderProcessorClient(){}  
  
    public OrderProcessorClient(string configurationName)  
        : base(configurationName)  
    { }  
  
    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)  
        : base(binding, address)  
    { }  
  
    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
    {  
        base.Channel.SubmitPurchaseOrder(msg);  
    }  
}  
```

 <span data-ttu-id="79267-119">Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="79267-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="79267-120">Můžete zobrazit přijetí zprávy služby z klienta.</span><span class="sxs-lookup"><span data-stu-id="79267-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="79267-121">Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="79267-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="79267-122">Mějte na paměti, protože služba Řízení front se používá, klient a služba nemusí být zprovoznit ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="79267-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="79267-123">Například může spustit klienta, vypněte ho a potom spusťte službu a pak by stále přijímat zprávy.</span><span class="sxs-lookup"><span data-stu-id="79267-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79267-124">Tato ukázka vyžaduje instalaci služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="79267-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="79267-125">Pokyny k instalaci v [služby Řízení front zpráv](https://go.microsoft.com/fwlink/?LinkId=94968).</span><span class="sxs-lookup"><span data-stu-id="79267-125">See the installation instructions in [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968).</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="79267-126">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="79267-126">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="79267-127">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="79267-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="79267-128">Pokud je služba spuštěna první, zkontroluje se tak, aby byl do fronty k dispozici.</span><span class="sxs-lookup"><span data-stu-id="79267-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="79267-129">Pokud fronta neexistuje, služba ho vytvoří.</span><span class="sxs-lookup"><span data-stu-id="79267-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="79267-130">Můžete spustit služba nejdřív vytvořte frontu nebo můžete vytvořit prostřednictvím Správce fronty MSMQ.</span><span class="sxs-lookup"><span data-stu-id="79267-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="79267-131">Postupujte podle těchto kroků můžete vytvořit frontu Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="79267-131">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="79267-132">Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="79267-132">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="79267-133">Rozbalte **funkce** kartu.</span><span class="sxs-lookup"><span data-stu-id="79267-133">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="79267-134">Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="79267-134">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="79267-135">Zkontrolujte, **transakční** pole.</span><span class="sxs-lookup"><span data-stu-id="79267-135">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="79267-136">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="79267-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="79267-137">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="79267-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="79267-138">Spusťte ukázku v jednom počítači konfiguraci, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="79267-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="79267-139">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="79267-139">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="79267-140">Zkopírujte soubory programu služby ze složky \service\bin\ v rámci složky specifické pro jazyk, k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="79267-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="79267-141">Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="79267-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="79267-142">V souboru Client.exe.config, změňte adresu koncového bodu klienta k zadání názvu počítače služba namísto ".".</span><span class="sxs-lookup"><span data-stu-id="79267-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="79267-143">Na počítači se službou spusťte z příkazového řádku Service.exe.</span><span class="sxs-lookup"><span data-stu-id="79267-143">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="79267-144">Na klientském počítači spusťte Client.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="79267-144">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="79267-145">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="79267-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="79267-146">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="79267-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="79267-147">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="79267-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="79267-148">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="79267-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a><span data-ttu-id="79267-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="79267-149">See Also</span></span>  
 [<span data-ttu-id="79267-150">Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front</span><span class="sxs-lookup"><span data-stu-id="79267-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="79267-151">Služba Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="79267-151">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
