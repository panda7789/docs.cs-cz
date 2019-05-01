---
title: Korelace zprávy
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: ed6fc8f5d16ae2d604cdbdf4659ecfaaa83bfa02
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989765"
---
# <a name="message-correlation"></a><span data-ttu-id="d747b-102">Korelace zprávy</span><span class="sxs-lookup"><span data-stu-id="d747b-102">Message Correlation</span></span>
<span data-ttu-id="d747b-103">Tato ukázka předvádí, jak služby Řízení front zpráv (MSMQ) aplikace může odesílat zprávy MSMQ do služby Windows Communication Foundation (WCF) a korelace zpráv mezi aplikacemi odesílatele a příjemce v případě požadavku nebo odpovědi.</span><span class="sxs-lookup"><span data-stu-id="d747b-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="d747b-104">Tato ukázka používá vazbu msmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="d747b-104">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="d747b-105">Služba není v tomto případě v místním prostředí konzolovou aplikaci, aby bylo možné sledovat, že služba, která bude přijímat zprávy zařazené do fronty.</span><span class="sxs-lookup"><span data-stu-id="d747b-105">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="d747b-106">k</span><span class="sxs-lookup"><span data-stu-id="d747b-106">k</span></span>  
  
 <span data-ttu-id="d747b-107">Služba zpracovává zprávu přijatou od odesílatele a odešle odpověď zpět do odesílatele.</span><span class="sxs-lookup"><span data-stu-id="d747b-107">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="d747b-108">Odesílatel koreluje odpovědí, žádost, u které původně odeslán přijaty.</span><span class="sxs-lookup"><span data-stu-id="d747b-108">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="d747b-109">`MessageID` a `CorrelationID` vlastnosti zprávy jsou používány ke korelaci zprávy požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="d747b-109">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>  
  
 <span data-ttu-id="d747b-110">`IOrderProcessor` Operace jednosměrné služby, který je vhodný pro použití se službou Řízení front definuje kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="d747b-110">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="d747b-111">Zprávy MSMQ nemá hlavičku akce, takže není možné automaticky mapovat různé zprávy služby MSMQ pro operaci smlouvy.</span><span class="sxs-lookup"><span data-stu-id="d747b-111">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="d747b-112">Proto může existovat pouze jeden kontrakt operace v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="d747b-112">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="d747b-113">Pokud chcete definovat další operace smluv týkajících se služby, aplikace musíte zadat informace jako záhlaví, které v služby MSMQ zprávy (třeba popisek, nebo ID korelace) umožňuje rozhodnout, kterou kontrakt k odeslání.</span><span class="sxs-lookup"><span data-stu-id="d747b-113">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span> 
  
 <span data-ttu-id="d747b-114">Zprávy služby MSMQ také neobsahuje informace ohledně toho, která hlavičky jsou namapovány na různé parametry kontrakt.</span><span class="sxs-lookup"><span data-stu-id="d747b-114">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="d747b-115">Proto může existovat jenom jeden parametr v kontrakt.</span><span class="sxs-lookup"><span data-stu-id="d747b-115">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="d747b-116">Parametr je typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, která obsahuje základní zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d747b-116">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, which contains the underlying MSMQ message.</span></span> <span data-ttu-id="d747b-117">Typ "T" v `MsmqMessage<T>` třída reprezentuje data, která je serializován do textu zprávy MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d747b-117">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="d747b-118">V této ukázce `PurchaseOrder` je typ serializován do textu zprávy MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d747b-118">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="d747b-119">Operace služby nákupní objednávku zpracovává a zobrazí se obsah nákupní objednávky a jeho stav v okně konzoly služby.</span><span class="sxs-lookup"><span data-stu-id="d747b-119">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="d747b-120"><xref:System.ServiceModel.OperationBehaviorAttribute> Nakonfiguruje operaci zařazení v transakci s frontou a označit dokončení transakce po návratu operaci.</span><span class="sxs-lookup"><span data-stu-id="d747b-120">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="d747b-121">`PurchaseOrder` Obsahuje podrobnosti objednávky, které musí být zpracovány služby.</span><span class="sxs-lookup"><span data-stu-id="d747b-121">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>

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

 <span data-ttu-id="d747b-122">Služba používá vlastní klienta `OrderResponseClient` do fronty odesílat zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d747b-122">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="d747b-123">Protože se aplikace, který přijímá a zpracovává zprávy služby MSMQ aplikace a aplikace WCF, neexistuje žádný implicitní smlouvu mezi těmito dvěma aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="d747b-123">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="d747b-124">Takže nemůžeme vytvořit proxy server pomocí nástroje Svcutil.exe v tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="d747b-124">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="d747b-125">Vlastní proxy server je v podstatě stejný pro všechny aplikace WCF, které používají `msmqIntegrationBinding` vazby pro odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="d747b-125">The custom proxy is essentially the same for all WCF applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="d747b-126">Na rozdíl od jiných proxy neobsahoval celou řadu operací služby.</span><span class="sxs-lookup"><span data-stu-id="d747b-126">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="d747b-127">Odeslat zprávu tato operace je pouze.</span><span class="sxs-lookup"><span data-stu-id="d747b-127">It is a submit message operation only.</span></span>

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

 <span data-ttu-id="d747b-128">Tato služba je vlastní hostované.</span><span class="sxs-lookup"><span data-stu-id="d747b-128">The service is self hosted.</span></span> <span data-ttu-id="d747b-129">Při použití transport integrace MSMQ fronty používají se musí vytvořit předem.</span><span class="sxs-lookup"><span data-stu-id="d747b-129">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="d747b-130">To můžete udělat ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="d747b-130">This can be done manually or through code.</span></span> <span data-ttu-id="d747b-131">V této ukázce obsahuje službu <xref:System.Messaging> kód pro provedení kontroly existence fronty a v případě potřeby ji vytvořit.</span><span class="sxs-lookup"><span data-stu-id="d747b-131">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="d747b-132">Název fronty načítají z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d747b-132">The queue name is read from the configuration file.</span></span>

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

 <span data-ttu-id="d747b-133">Fronta MSMQ, ke které se odesílají požadavky pořadí je definováno v sekci appSettings konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d747b-133">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="d747b-134">Koncové body klienta a služby jsou definovány v sekci system.serviceModel konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d747b-134">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="d747b-135">Jak určit `msmqIntegrationbinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="d747b-135">Both specify the `msmqIntegrationbinding` binding.</span></span>

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

 <span data-ttu-id="d747b-136">Klientská aplikace používá <xref:System.Messaging> odeslat odolné a transakční zprávu do fronty.</span><span class="sxs-lookup"><span data-stu-id="d747b-136">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="d747b-137">Tělo zprávy obsahuje nákupní objednávky.</span><span class="sxs-lookup"><span data-stu-id="d747b-137">The message's body contains the purchase order.</span></span>

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

 <span data-ttu-id="d747b-138">Fronta MSMQ, ze kterého jsou přijaty odpovědi pořadí je zadán v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d747b-138">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
>  <span data-ttu-id="d747b-139">Název fronty používá tečku (.) pro místní počítače a zpětné lomítko oddělovače v cestě.</span><span class="sxs-lookup"><span data-stu-id="d747b-139">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="d747b-140">Adresa koncového bodu WCF Určuje schéma msmq.formatname a používá "localhost" v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="d747b-140">The WCF endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="d747b-141">Název formátu správně vytvořená následuje msmq.formatname v identifikátoru URI podle pokynů služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d747b-141">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="d747b-142">Uloží klientské aplikace `messageID` zprávy s požadavkem pořadí, který odešle do služby a čeká na odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="d747b-142">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="d747b-143">Po přijetí odpovědi ve frontě klienta, koreluje ji s zpráv pořadí je odeslat pomocí `correlationID` vlastnosti zprávy, která obsahuje `messageID` pořadí, zprávy, které klient původně odeslána do služby.</span><span class="sxs-lookup"><span data-stu-id="d747b-143">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>

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

 <span data-ttu-id="d747b-144">Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="d747b-144">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="d747b-145">Zobrazí se služby přijmout zprávy z klienta a odešle odpověď zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="d747b-145">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="d747b-146">Klient se zobrazí odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="d747b-146">The client displays the response received from the service.</span></span> <span data-ttu-id="d747b-147">Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="d747b-147">Press ENTER in each console window to shut down the service and client.</span></span>

> [!NOTE]
>  <span data-ttu-id="d747b-148">Tato ukázka vyžaduje instalaci sady řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="d747b-148">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="d747b-149">MSMQ instalační pokyny naleznete v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="d747b-149">See the MSMQ installation instructions in the See Also section.</span></span>

### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="d747b-150">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d747b-150">To setup, build, and run the sample</span></span>

1. <span data-ttu-id="d747b-151">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d747b-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="d747b-152">Pokud je služba spuštěna první, zkontroluje se tak, aby byl do fronty k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d747b-152">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="d747b-153">Pokud fronta neexistuje, služba ho vytvoří.</span><span class="sxs-lookup"><span data-stu-id="d747b-153">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="d747b-154">Můžete spustit služba nejdřív vytvořte frontu nebo můžete vytvořit prostřednictvím Správce fronty MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d747b-154">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="d747b-155">Postupujte podle těchto kroků můžete vytvořit frontu Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="d747b-155">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="d747b-156">Otevřete správce serveru v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="d747b-156">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="d747b-157">Rozbalte **funkce** kartu.</span><span class="sxs-lookup"><span data-stu-id="d747b-157">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="d747b-158">Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="d747b-158">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="d747b-159">Zkontrolujte, **transakční** pole.</span><span class="sxs-lookup"><span data-stu-id="d747b-159">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="d747b-160">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="d747b-160">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="d747b-161">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d747b-161">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="d747b-162">Spusťte ukázku v jednom počítači konfiguraci, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d747b-162">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="d747b-163">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="d747b-163">To run the sample across computers</span></span>

1. <span data-ttu-id="d747b-164">Zkopírujte soubory programu služby ze složky \service\bin\ v rámci složky specifické pro jazyk, k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="d747b-164">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="d747b-165">Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="d747b-165">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="d747b-166">V souboru Client.exe.config změnit orderQueueName k zadání názvu počítače služba namísto ".".</span><span class="sxs-lookup"><span data-stu-id="d747b-166">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="d747b-167">V souboru Service.exe.config, změňte adresu koncového bodu klienta k určení názvu klientského počítače namísto ".".</span><span class="sxs-lookup"><span data-stu-id="d747b-167">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>

5. <span data-ttu-id="d747b-168">Na počítači se službou spusťte z příkazového řádku Service.exe.</span><span class="sxs-lookup"><span data-stu-id="d747b-168">On the service computer, launch Service.exe from a command prompt.</span></span>

6. <span data-ttu-id="d747b-169">Na klientském počítači spusťte Client.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d747b-169">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="d747b-170">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="d747b-170">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d747b-171">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d747b-171">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d747b-172">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d747b-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d747b-173">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d747b-173">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a><span data-ttu-id="d747b-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d747b-174">See also</span></span>

- [<span data-ttu-id="d747b-175">Zařazování do front ve WCF</span><span class="sxs-lookup"><span data-stu-id="d747b-175">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [<span data-ttu-id="d747b-176">Služba Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="d747b-176">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
