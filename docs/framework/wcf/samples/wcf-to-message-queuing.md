---
title: Z WCF do Řízení front zpráv
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: 083e652a0924ffed272387a4974ec600073cef2f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966725"
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="5bc7e-102">Z WCF do Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="5bc7e-102">Windows Communication Foundation to Message Queuing</span></span>
<span data-ttu-id="5bc7e-103">Tato ukázka předvádí, jak může aplikace Windows Communication Foundation (WCF) odeslat zprávu do aplikace řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="5bc7e-103">This sample demonstrates how a Windows Communication Foundation (WCF) application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="5bc7e-104">Služba je samoobslužná Konzolová aplikace, která vám umožní sledovat službu přijímající zprávy zařazené do fronty.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="5bc7e-105">Službu a klienta nemusíte spouštět ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-105">The service and client do not have to be running at the same time.</span></span>

 <span data-ttu-id="5bc7e-106">Služba přijímá zprávy z objednávek front a procesů.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="5bc7e-107">Služba vytvoří transakční frontu a nastaví zprávu s oznámením o přijetí zprávy, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="5bc7e-108">Při přijetí zprávy ve frontě je vyvolána obslužná rutina `ProcessOrder` zprávy.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>

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

 <span data-ttu-id="5bc7e-109">Služba extrahuje `ProcessOrder` z těla zprávy služby MSMQ a zpracuje objednávku.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>

 <span data-ttu-id="5bc7e-110">Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="5bc7e-111">Název fronty pro místní počítač a oddělovače zpětného lomítka v cestě používá tečku (.).</span><span class="sxs-lookup"><span data-stu-id="5bc7e-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>

 <span data-ttu-id="5bc7e-112">Klient vytvoří nákupní objednávku a odešle nákupní objednávku v rámci oboru transakce, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="5bc7e-113">Klient pro odeslání zprávy služby MSMQ do fronty používá vlastního klienta.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="5bc7e-114">Vzhledem k tomu, že aplikace, která přijímá a zpracovává zprávu, je aplikace služby MSMQ a ne aplikace WCF, není mezi těmito dvěma aplikacemi žádný implicitní kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-114">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="5bc7e-115">Proto nemůžeme vytvořit proxy pomocí nástroje Svcutil. exe v tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="5bc7e-116">Vlastní klient je v podstatě stejný pro všechny aplikace WCF, které používají `MsmqIntegration` vazbu k posílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-116">The custom client is essentially the same for all WCF applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="5bc7e-117">Na rozdíl od jiných klientů nezahrnuje rozsah operací služby.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="5bc7e-118">Jedná se pouze o operaci Odeslat zprávu.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-118">It is a submit message operation only.</span></span>

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

 <span data-ttu-id="5bc7e-119">Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="5bc7e-120">Můžete vidět, že služba přijímá zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="5bc7e-121">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="5bc7e-122">Počítejte s tím, že protože se používá služba zařazování do fronty, klient a služba nemusí být spuštěny ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="5bc7e-123">Můžete třeba spustit klienta, vypnout ho a pak službu spustit a zároveň se jim budou zobrazovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

> [!NOTE]
> <span data-ttu-id="5bc7e-124">Tato ukázka vyžaduje instalaci služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="5bc7e-125">Projděte si pokyny k instalaci ve [službě Řízení front zpráv](https://go.microsoft.com/fwlink/?LinkId=94968).</span><span class="sxs-lookup"><span data-stu-id="5bc7e-125">See the installation instructions in [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968).</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="5bc7e-126">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="5bc7e-126">To setup, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5bc7e-127">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5bc7e-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5bc7e-128">Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="5bc7e-129">Pokud fronta není přítomna, služba ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="5bc7e-130">Službu můžete nejdřív spustit, abyste mohli vytvořit frontu, nebo ji můžete vytvořit pomocí Správce fronty MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="5bc7e-131">Pomocí těchto kroků vytvořte ve Windows 2008 frontu.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-131">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1. <span data-ttu-id="5bc7e-132">Otevřete Správce serveru v aplikaci Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-132">Open Server Manager in Visual Studio 2012.</span></span>  
  
    2. <span data-ttu-id="5bc7e-133">Rozbalte kartu **funkce** .</span><span class="sxs-lookup"><span data-stu-id="5bc7e-133">Expand the **Features** tab.</span></span>  
  
    3. <span data-ttu-id="5bc7e-134">Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **Nový**, **soukromá fronta**.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-134">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4. <span data-ttu-id="5bc7e-135">Zaškrtněte políčko **transakční** .</span><span class="sxs-lookup"><span data-stu-id="5bc7e-135">Check the **Transactional** box.</span></span>  
  
    5. <span data-ttu-id="5bc7e-136">Jako `ServiceModelSamplesTransacted` název nové fronty zadejte.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3. <span data-ttu-id="5bc7e-137">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5bc7e-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="5bc7e-138">Chcete-li spustit ukázku v konfiguraci s jedním počítačem, postupujte podle pokynů v [části spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5bc7e-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="5bc7e-139">Spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="5bc7e-139">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="5bc7e-140">Zkopírujte programové soubory služby ze složky \service\bin\ ve složce specifické pro daný jazyk do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2. <span data-ttu-id="5bc7e-141">Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3. <span data-ttu-id="5bc7e-142">V souboru Client. exe. config změňte adresu koncového bodu klienta tak, aby určovala název počítače služby místo ".".</span><span class="sxs-lookup"><span data-stu-id="5bc7e-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>  
  
4. <span data-ttu-id="5bc7e-143">Na počítači služby spusťte z příkazového řádku Service. exe.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-143">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="5bc7e-144">V klientském počítači spusťte z příkazového řádku soubor Client. exe.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-144">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5bc7e-145">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5bc7e-146">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5bc7e-147">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5bc7e-148">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5bc7e-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a><span data-ttu-id="5bc7e-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5bc7e-149">See also</span></span>

- [<span data-ttu-id="5bc7e-150">Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="5bc7e-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="5bc7e-151">Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="5bc7e-151">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
