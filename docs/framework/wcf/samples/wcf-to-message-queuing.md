---
title: Z WCF do Řízení front zpráv
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: 872632dc7d0a8a94f8829ffb3fe8eea2607697c8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602337"
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="1dc93-102">Z WCF do Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="1dc93-102">Windows Communication Foundation to Message Queuing</span></span>

<span data-ttu-id="1dc93-103">Tato ukázka předvádí, jak může aplikace Windows Communication Foundation (WCF) odeslat zprávu do aplikace řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="1dc93-103">This sample demonstrates how a Windows Communication Foundation (WCF) application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="1dc93-104">Služba je samoobslužná Konzolová aplikace, která vám umožní sledovat službu přijímající zprávy zařazené do fronty.</span><span class="sxs-lookup"><span data-stu-id="1dc93-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="1dc93-105">Službu a klienta nemusíte spouštět ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="1dc93-105">The service and client do not have to be running at the same time.</span></span>

 <span data-ttu-id="1dc93-106">Služba přijímá zprávy z objednávek front a procesů.</span><span class="sxs-lookup"><span data-stu-id="1dc93-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="1dc93-107">Služba vytvoří transakční frontu a nastaví zprávu s oznámením o přijetí zprávy, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="1dc93-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="1dc93-108">Při přijetí zprávy ve frontě je vyvolána obslužná rutina zprávy `ProcessOrder` .</span><span class="sxs-lookup"><span data-stu-id="1dc93-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>

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

 <span data-ttu-id="1dc93-109">Služba extrahuje `ProcessOrder` z těla zprávy služby MSMQ a zpracuje objednávku.</span><span class="sxs-lookup"><span data-stu-id="1dc93-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>

 <span data-ttu-id="1dc93-110">Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="1dc93-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="1dc93-111">Název fronty pro místní počítač a oddělovače zpětného lomítka v cestě používá tečku (.).</span><span class="sxs-lookup"><span data-stu-id="1dc93-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>

 <span data-ttu-id="1dc93-112">Klient vytvoří nákupní objednávku a odešle nákupní objednávku v rámci oboru transakce, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="1dc93-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="1dc93-113">Klient pro odeslání zprávy služby MSMQ do fronty používá vlastního klienta.</span><span class="sxs-lookup"><span data-stu-id="1dc93-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="1dc93-114">Vzhledem k tomu, že aplikace, která přijímá a zpracovává zprávu, je aplikace služby MSMQ a ne aplikace WCF, není mezi těmito dvěma aplikacemi žádný implicitní kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="1dc93-114">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="1dc93-115">Proto nemůžeme vytvořit proxy pomocí nástroje Svcutil. exe v tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="1dc93-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="1dc93-116">Vlastní klient je v podstatě stejný pro všechny aplikace WCF, které používají `MsmqIntegration` vazbu k posílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="1dc93-116">The custom client is essentially the same for all WCF applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="1dc93-117">Na rozdíl od jiných klientů nezahrnuje rozsah operací služby.</span><span class="sxs-lookup"><span data-stu-id="1dc93-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="1dc93-118">Jedná se pouze o operaci Odeslat zprávu.</span><span class="sxs-lookup"><span data-stu-id="1dc93-118">It is a submit message operation only.</span></span>

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

 <span data-ttu-id="1dc93-119">Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta.</span><span class="sxs-lookup"><span data-stu-id="1dc93-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="1dc93-120">Můžete vidět, že služba přijímá zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="1dc93-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="1dc93-121">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="1dc93-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="1dc93-122">Počítejte s tím, že protože se používá služba zařazování do fronty, klient a služba nemusí být spuštěny ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="1dc93-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="1dc93-123">Můžete třeba spustit klienta, vypnout ho a pak službu spustit a zároveň se jim budou zobrazovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="1dc93-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

> [!NOTE]
> <span data-ttu-id="1dc93-124">Tato ukázka vyžaduje instalaci služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="1dc93-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="1dc93-125">Projděte si pokyny k instalaci ve [službě Řízení front zpráv](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1dc93-125">See the installation instructions in [Message Queuing](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85)).</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="1dc93-126">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="1dc93-126">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="1dc93-127">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1dc93-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="1dc93-128">Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1dc93-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="1dc93-129">Pokud fronta není přítomna, služba ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="1dc93-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="1dc93-130">Službu můžete nejdřív spustit, abyste mohli vytvořit frontu, nebo ji můžete vytvořit pomocí Správce fronty MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1dc93-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="1dc93-131">Pomocí těchto kroků vytvořte ve Windows 2008 frontu.</span><span class="sxs-lookup"><span data-stu-id="1dc93-131">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="1dc93-132">Otevřete Správce serveru v aplikaci Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="1dc93-132">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="1dc93-133">Rozbalte kartu **funkce** .</span><span class="sxs-lookup"><span data-stu-id="1dc93-133">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="1dc93-134">Klikněte pravým tlačítkem na **fronty soukromých zpráv**a pak vyberte **Nová**  >  **soukromá fronta**.</span><span class="sxs-lookup"><span data-stu-id="1dc93-134">Right-click **Private Message Queues**, and then select **New** > **Private Queue**.</span></span>

    4. <span data-ttu-id="1dc93-135">Zaškrtněte políčko **transakční** .</span><span class="sxs-lookup"><span data-stu-id="1dc93-135">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="1dc93-136">`ServiceModelSamplesTransacted`Jako název nové fronty zadejte.</span><span class="sxs-lookup"><span data-stu-id="1dc93-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="1dc93-137">Chcete-li sestavit edici C# nebo Visual Basic, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1dc93-137">To build the C# or Visual Basic edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="1dc93-138">Chcete-li spustit ukázku v konfiguraci s jedním počítačem, postupujte podle pokynů v [části spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1dc93-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="1dc93-139">Spuštění ukázky napříč počítači</span><span class="sxs-lookup"><span data-stu-id="1dc93-139">Run the sample across computers</span></span>

1. <span data-ttu-id="1dc93-140">Zkopírujte programové soubory služby ze složky \service\bin\ ve složce specifické pro daný jazyk do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="1dc93-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="1dc93-141">Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="1dc93-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="1dc93-142">V souboru Client. exe. config změňte adresu koncového bodu klienta tak, aby určovala název počítače služby místo ".".</span><span class="sxs-lookup"><span data-stu-id="1dc93-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="1dc93-143">Na počítači služby spusťte z příkazového řádku Service. exe.</span><span class="sxs-lookup"><span data-stu-id="1dc93-143">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="1dc93-144">V klientském počítači spusťte z příkazového řádku soubor Client. exe.</span><span class="sxs-lookup"><span data-stu-id="1dc93-144">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1dc93-145">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="1dc93-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1dc93-146">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="1dc93-146">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="1dc93-147">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="1dc93-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1dc93-148">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1dc93-148">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`

## <a name="see-also"></a><span data-ttu-id="1dc93-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="1dc93-149">See also</span></span>

- [<span data-ttu-id="1dc93-150">Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front</span><span class="sxs-lookup"><span data-stu-id="1dc93-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- <span data-ttu-id="1dc93-151">[Služba Řízení front zpráv](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1dc93-151">[Message Queuing](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
