---
title: Korelace zprávy
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: 9ded0886920f9f0b3d2f9b441061253b42a1c567
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747166"
---
# <a name="message-correlation"></a><span data-ttu-id="48ba9-102">Korelace zprávy</span><span class="sxs-lookup"><span data-stu-id="48ba9-102">Message Correlation</span></span>

<span data-ttu-id="48ba9-103">Tato ukázka předvádí, jak může aplikace služby Řízení front zpráv (MSMQ) odesílat zprávy MSMQ službě Windows Communication Foundation (WCF) a jak se dají mezi aplikacemi odesílatele a přijímače sladit zprávy ve scénáři požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="48ba9-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="48ba9-104">V této ukázce se používá vazba msmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="48ba9-104">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="48ba9-105">Tato služba je v tomto případě samoobslužná Konzolová aplikace, která umožňuje sledovat službu, která přijímá zprávy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="48ba9-105">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="48ba9-106">k</span><span class="sxs-lookup"><span data-stu-id="48ba9-106">k</span></span>

 <span data-ttu-id="48ba9-107">Služba zpracuje zprávu přijatou od odesílatele a pošle zprávu odpovědi zpět odesilateli.</span><span class="sxs-lookup"><span data-stu-id="48ba9-107">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="48ba9-108">Odesilatel koreluje odpověď, kterou obdržel, na žádost, kterou odeslal původně.</span><span class="sxs-lookup"><span data-stu-id="48ba9-108">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="48ba9-109">Vlastnosti `MessageID` a `CorrelationID` zprávy slouží ke korelaci požadavků a zpráv odpovědí.</span><span class="sxs-lookup"><span data-stu-id="48ba9-109">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>

 <span data-ttu-id="48ba9-110">Kontrakt služby `IOrderProcessor` definuje jednosměrnou operaci služby, která je vhodná pro použití při zařazování do fronty.</span><span class="sxs-lookup"><span data-stu-id="48ba9-110">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="48ba9-111">Zpráva služby MSMQ neobsahuje záhlaví akce, takže není možné automaticky mapovat různé zprávy MSMQ na provozní kontrakty.</span><span class="sxs-lookup"><span data-stu-id="48ba9-111">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="48ba9-112">V tomto případě může v tomto případě existovat pouze jedna kontrakt operace.</span><span class="sxs-lookup"><span data-stu-id="48ba9-112">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="48ba9-113">Chcete-li ve službě definovat více kontraktů operací, aplikace musí poskytnout informace o tom, které záhlaví ve zprávě služby MSMQ (například popisek nebo ID korelace) lze použít k rozhodnutí, který kontrakt operace se má odeslat.</span><span class="sxs-lookup"><span data-stu-id="48ba9-113">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span>

 <span data-ttu-id="48ba9-114">Zpráva služby MSMQ neobsahuje také informace o tom, která záhlaví jsou namapována na různé parametry kontraktu operace.</span><span class="sxs-lookup"><span data-stu-id="48ba9-114">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="48ba9-115">Proto může být v kontraktu operace pouze jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="48ba9-115">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="48ba9-116">Parametr je typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, který obsahuje podkladovou zprávu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="48ba9-116">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, which contains the underlying MSMQ message.</span></span> <span data-ttu-id="48ba9-117">Typ "T" ve třídě `MsmqMessage<T>` představuje data serializovaná do těla zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="48ba9-117">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="48ba9-118">V této ukázce je typ `PurchaseOrder` serializován do těla zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="48ba9-118">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="48ba9-119">Operace služby zpracuje objednávku nákupu a zobrazí obsah nákupní objednávky a její stav v okně konzoly služby.</span><span class="sxs-lookup"><span data-stu-id="48ba9-119">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="48ba9-120"><xref:System.ServiceModel.OperationBehaviorAttribute> nakonfiguruje operaci k zařazení do transakce s frontou a k označení transakce dokončené, když operace vrátí.</span><span class="sxs-lookup"><span data-stu-id="48ba9-120">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="48ba9-121">`PurchaseOrder` obsahuje podrobnosti objednávky, které musí služba zpracovat.</span><span class="sxs-lookup"><span data-stu-id="48ba9-121">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>

```csharp
// Service class that implements the service contract.
public class OrderProcessorService : IOrderProcessor
{
   [OperationBehavior(TransactionScopeRequired = true,
          TransactionAutoComplete = true)]
   public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> ordermsg)
   {
       PurchaseOrder po = (PurchaseOrder)ordermsg.Body;
       Random statusIndexer = new Random();
       po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
       Console.WriteLine("Processing {0} ", po);
       //Send a response to the client that the order has been received
         and is pending fullfillment.
       SendResponse(ordermsg);
    }

    private void SendResponse(MsmqMessage<PurchaseOrder> ordermsg)
    {
        OrderResponseClient client = new OrderResponseClient("OrderResponseEndpoint");

        //Set the correlation ID such that the client can correlate the response to the order.
        MsmqMessage<PurchaseOrder> orderResponsemsg = new MsmqMessage<PurchaseOrder>(ordermsg.Body);
        orderResponsemsg.CorrelationId = ordermsg.Id;
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.SendOrderResponse(orderResponsemsg);
            scope.Complete();
        }

        client.Close();
    }
}
```

 <span data-ttu-id="48ba9-122">Služba používá vlastní `OrderResponseClient` klienta k odeslání zprávy služby MSMQ do fronty.</span><span class="sxs-lookup"><span data-stu-id="48ba9-122">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="48ba9-123">Vzhledem k tomu, že aplikace, která přijímá a zpracovává zprávu, je aplikace služby MSMQ a ne aplikace WCF, není mezi těmito dvěma aplikacemi žádný implicitní kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="48ba9-123">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="48ba9-124">Proto nemůžeme vytvořit proxy pomocí nástroje Svcutil. exe v tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="48ba9-124">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="48ba9-125">Vlastní proxy server je v podstatě stejný pro všechny aplikace WCF, které používají vazbu `msmqIntegrationBinding` k posílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="48ba9-125">The custom proxy is essentially the same for all WCF applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="48ba9-126">Na rozdíl od jiných proxy serverů nezahrnuje rozsah operací služby.</span><span class="sxs-lookup"><span data-stu-id="48ba9-126">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="48ba9-127">Jedná se pouze o operaci Odeslat zprávu.</span><span class="sxs-lookup"><span data-stu-id="48ba9-127">It is a submit message operation only.</span></span>

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderResponse
{

    [System.ServiceModel.OperationContractAttribute(IsOneWay = true, Action = "*")]
    void SendOrderResponse(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderResponseClient : System.ServiceModel.ClientBase<IOrderResponse>, IOrderResponse
{

    public OrderResponseClient()
    { }

    public OrderResponseClient(string configurationName)
        : base(configurationName)
    { }

    public OrderResponseClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SendOrderResponse(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SendOrderResponse(msg);
    }
}
```

 <span data-ttu-id="48ba9-128">Služba je hostována svým hostitelem.</span><span class="sxs-lookup"><span data-stu-id="48ba9-128">The service is self hosted.</span></span> <span data-ttu-id="48ba9-129">Při použití přenosu integrace služby MSMQ musí být použitá fronta předem vytvořena.</span><span class="sxs-lookup"><span data-stu-id="48ba9-129">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="48ba9-130">To lze provést ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="48ba9-130">This can be done manually or through code.</span></span> <span data-ttu-id="48ba9-131">V této ukázce služba obsahuje kód <xref:System.Messaging> pro kontrolu existence fronty a v případě potřeby ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="48ba9-131">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="48ba9-132">Název fronty se načte z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="48ba9-132">The queue name is read from the configuration file.</span></span>

```csharp
public static void Main()
{
       // Get the MSMQ queue name from application settings in configuration.
      string queueName =
                ConfigurationManager.AppSettings["orderQueueName"];
      // Create the transacted MSMQ queue if necessary.
      if (!MessageQueue.Exists(queueName))
                MessageQueue.Create(queueName, true);
     // Create a ServiceHost for the OrderProcessorService type.
     using (ServiceHost serviceHost = new
                   ServiceHost(typeof(OrderProcessorService)))
     {
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

 <span data-ttu-id="48ba9-133">Fronta MSMQ, na kterou jsou odesílány požadavky objednávky, je zadána v oddílu appSettings konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="48ba9-133">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="48ba9-134">Koncové body klienta a služby jsou definovány v oddílu System. serviceModel konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="48ba9-134">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="48ba9-135">Určete `msmqIntegrationbinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="48ba9-135">Both specify the `msmqIntegrationbinding` binding.</span></span>

```xml
<appSettings>
  <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>

<system.serviceModel>
  <client>
    <endpoint    name="OrderResponseEndpoint"
              address="msmq.formatname:DIRECT=OS:.\private$\OrderResponse"
              binding="msmqIntegrationBinding"
              bindingConfiguration="OrderProcessorBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderResponse">
    </endpoint>
  </client>

  <services>
    <service
      name="Microsoft.ServiceModel.Samples.OrderProcessorService">
      <endpoint address="msmq.formatname:DIRECT=OS:.\private$\Orders"
                            binding="msmqIntegrationBinding"
                bindingConfiguration="OrderProcessorBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor">
      </endpoint>
    </service>
  </services>

  <bindings>
    <msmqIntegrationBinding>
      <binding name="OrderProcessorBinding" >
        <security mode="None" />
      </binding>
    </msmqIntegrationBinding>
  </bindings>

</system.serviceModel>
```

 <span data-ttu-id="48ba9-136">Klientská aplikace používá <xref:System.Messaging> k odeslání trvalé a transakční zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="48ba9-136">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="48ba9-137">Tělo zprávy obsahuje nákupní objednávku.</span><span class="sxs-lookup"><span data-stu-id="48ba9-137">The message's body contains the purchase order.</span></span>

```csharp
static void PlaceOrder()
{
    //Connect to the queue
    MessageQueue orderQueue =
            new MessageQueue(
                    ConfigurationManager.AppSettings["orderQueueName"])
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

    Message msg = new Message();
    msg.UseDeadLetterQueue = true;
    msg.Body = po;

    //Create a transaction scope.
    using (TransactionScope scope = new
     TransactionScope(TransactionScopeOption.Required))
    {
        // Submit the purchase order.
        orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
        // Complete the transaction.
        scope.Complete();
    }
    //Save the messageID for order response correlation.
    orderMessageID = msg.Id;
    Console.WriteLine("Placed the order, waiting for response...");
}
```

 <span data-ttu-id="48ba9-138">Fronta MSMQ, ze které jsou přijímány odpovědi objednávek, je zadána v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="48ba9-138">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="48ba9-139">Název fronty pro místní počítač a oddělovače zpětného lomítka v cestě používá tečku (.).</span><span class="sxs-lookup"><span data-stu-id="48ba9-139">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="48ba9-140">Adresa koncového bodu WCF Určuje schéma služby MSMQ. formatname a pro místní počítač používá localhost.</span><span class="sxs-lookup"><span data-stu-id="48ba9-140">The WCF endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="48ba9-141">Název formátu správně vytvořeného v závislosti na pokynech služby MSMQ dodržuje formát MSMQ. FormatName v identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="48ba9-141">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="48ba9-142">Klientská aplikace uloží `messageID` zprávy žádosti o objednávku, kterou pošle službě, a počká na odpověď od služby.</span><span class="sxs-lookup"><span data-stu-id="48ba9-142">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="48ba9-143">Jakmile odpověď dorazí do fronty, bude ji klient korelovat se zprávou objednávky, kterou odeslal, pomocí vlastnosti `correlationID` zprávy, která obsahuje `messageID` zprávy objednávky, kterou klient původně odeslal službě.</span><span class="sxs-lookup"><span data-stu-id="48ba9-143">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>

```csharp
static void DisplayOrderStatus()
{
    MessageQueue orderResponseQueue = new
     MessageQueue(ConfigurationManager.AppSettings
                  ["orderResponseQueueName"]);
    //Create a transaction scope.
    bool responseReceived = false;
    orderResponseQueue.MessageReadPropertyFilter.CorrelationId = true;
    while (!responseReceived)
    {
       Message responseMsg;
       using (TransactionScope scope2 = new
         TransactionScope(TransactionScopeOption.Required))
       {
          //Receive the Order Response message.
          responseMsg =
              orderResponseQueue.Receive
                   (MessageQueueTransactionType.Automatic);
          scope2.Complete();
     }
     responseMsg.Formatter = new
     System.Messaging.XmlMessageFormatter(new Type[] {
         typeof(PurchaseOrder) });
     PurchaseOrder responsepo = (PurchaseOrder)responseMsg.Body;
    //Check if the response is for the order placed.
    if (orderMessageID == responseMsg.CorrelationId)
    {
       responseReceived = true;
       Console.WriteLine("Status of current Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
    else
    {
       Console.WriteLine("Status of previous Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
  }
}
```

 <span data-ttu-id="48ba9-144">Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta.</span><span class="sxs-lookup"><span data-stu-id="48ba9-144">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="48ba9-145">Můžete vidět, že služba přijímá zprávy z klienta a odesílá odpověď zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="48ba9-145">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="48ba9-146">Klient zobrazuje odpověď přijatou od služby.</span><span class="sxs-lookup"><span data-stu-id="48ba9-146">The client displays the response received from the service.</span></span> <span data-ttu-id="48ba9-147">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="48ba9-147">Press ENTER in each console window to shut down the service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="48ba9-148">Tato ukázka vyžaduje instalaci služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="48ba9-148">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="48ba9-149">Pokyny k instalaci služby MSMQ najdete v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="48ba9-149">See the MSMQ installation instructions in the See Also section.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="48ba9-150">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="48ba9-150">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="48ba9-151">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="48ba9-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="48ba9-152">Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici.</span><span class="sxs-lookup"><span data-stu-id="48ba9-152">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="48ba9-153">Pokud fronta není přítomna, služba ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="48ba9-153">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="48ba9-154">Službu můžete nejdřív spustit, abyste mohli vytvořit frontu, nebo ji můžete vytvořit pomocí Správce fronty MSMQ.</span><span class="sxs-lookup"><span data-stu-id="48ba9-154">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="48ba9-155">Pomocí těchto kroků vytvořte ve Windows 2008 frontu.</span><span class="sxs-lookup"><span data-stu-id="48ba9-155">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="48ba9-156">Otevřete Správce serveru v aplikaci Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="48ba9-156">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="48ba9-157">Rozbalte kartu **funkce** .</span><span class="sxs-lookup"><span data-stu-id="48ba9-157">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="48ba9-158">Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **Nový**, **soukromá fronta**.</span><span class="sxs-lookup"><span data-stu-id="48ba9-158">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="48ba9-159">Zaškrtněte políčko **transakční** .</span><span class="sxs-lookup"><span data-stu-id="48ba9-159">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="48ba9-160">Jako název nové fronty zadejte `ServiceModelSamplesTransacted`.</span><span class="sxs-lookup"><span data-stu-id="48ba9-160">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="48ba9-161">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="48ba9-161">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="48ba9-162">Chcete-li spustit ukázku v konfiguraci s jedním počítačem, postupujte podle pokynů v [části spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="48ba9-162">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="48ba9-163">Spuštění ukázky napříč počítači</span><span class="sxs-lookup"><span data-stu-id="48ba9-163">Run the sample across computers</span></span>

1. <span data-ttu-id="48ba9-164">Zkopírujte programové soubory služby ze složky \service\bin\ ve složce specifické pro daný jazyk do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="48ba9-164">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="48ba9-165">Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="48ba9-165">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="48ba9-166">V souboru Client. exe. config změňte orderQueueName a zadejte název počítače služby místo ".".</span><span class="sxs-lookup"><span data-stu-id="48ba9-166">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="48ba9-167">V souboru Service. exe. config změňte adresu koncového bodu klienta tak, aby určovala název klientského počítače místo ".".</span><span class="sxs-lookup"><span data-stu-id="48ba9-167">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>

5. <span data-ttu-id="48ba9-168">Na počítači služby spusťte z příkazového řádku Service. exe.</span><span class="sxs-lookup"><span data-stu-id="48ba9-168">On the service computer, launch Service.exe from a command prompt.</span></span>

6. <span data-ttu-id="48ba9-169">V klientském počítači spusťte z příkazového řádku soubor Client. exe.</span><span class="sxs-lookup"><span data-stu-id="48ba9-169">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="48ba9-170">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="48ba9-170">The samples may already be installed on your computer.</span></span> <span data-ttu-id="48ba9-171">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="48ba9-171">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="48ba9-172">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="48ba9-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="48ba9-173">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="48ba9-173">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`

## <a name="see-also"></a><span data-ttu-id="48ba9-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="48ba9-174">See also</span></span>

- [<span data-ttu-id="48ba9-175">Zařazování do front ve WCF</span><span class="sxs-lookup"><span data-stu-id="48ba9-175">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- <span data-ttu-id="48ba9-176">[Řízení front zpráv](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="48ba9-176">[Message Queuing](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
