---
title: "Korelace zprávy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 95336c55b2c3e83e2bd68bb653bbaacc446d8934
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="message-correlation"></a><span data-ttu-id="5e4f4-102">Korelace zprávy</span><span class="sxs-lookup"><span data-stu-id="5e4f4-102">Message Correlation</span></span>
<span data-ttu-id="5e4f4-103">Tento příklad ukazuje, jak můžete k aplikaci služby Řízení front zpráv (MSMQ) odešle zprávu služby MSMQ pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby a korelace zpráv mezi aplikacemi odesílatele a příjemce v případě požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="5e4f4-104">Tato ukázka používá – msmqIntegrationBinding vazby.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-104">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="5e4f4-105">Služba je v tomto případě vlastním hostováním konzolovou aplikaci, abyste mohli pozorovat, že služby, která přijímá zprávy zařazené do fronty.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-105">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="5e4f4-106">K</span><span class="sxs-lookup"><span data-stu-id="5e4f4-106">k</span></span>  
  
 <span data-ttu-id="5e4f4-107">Služba zpracovává zprávu přijatou z odesílatele a odešle zprávu odpovědi zpátky do odesílatele.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-107">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="5e4f4-108">Odesílatel korelaci obdrženého na žádost, ke které původně odeslán odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-108">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="5e4f4-109">`MessageID` a `CorrelationID` vlastnosti zprávy, které se používají ke korelaci zprávy požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-109">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>  
  
 <span data-ttu-id="5e4f4-110">`IOrderProcessor` Operace jednosměrné služby, který je vhodný pro použití se službou Řízení front definuje kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-110">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="5e4f4-111">Zprávy MSMQ nemá hlavičku akce, takže není možné automaticky mapovat různé zprávy služby MSMQ kontrakty operaci.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-111">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="5e4f4-112">Proto může existovat pouze jedna smlouva operace v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-112">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="5e4f4-113">Pokud chcete definovat další operace měnící v rámci služby, aplikace musí poskytovat informace, které záhlaví v služby MSMQ zprávy (například štítek, nebo correlationID) slouží k rozhodnout, které operace kontrakt k odeslání.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-113">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span> <span data-ttu-id="5e4f4-114">Tento postup je znázorněn v [vlastní Demux](../../../../docs/framework/wcf/samples/custom-demux.md).</span><span class="sxs-lookup"><span data-stu-id="5e4f4-114">This is demonstrated in the [Custom Demux](../../../../docs/framework/wcf/samples/custom-demux.md).</span></span>  
  
 <span data-ttu-id="5e4f4-115">Zprávy služby MSMQ také neobsahuje informace o tom, které hlavičky jsou namapované na různé parametry operace kontrakt.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-115">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="5e4f4-116">Proto může existovat jenom jeden parametr v operaci kontraktu.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-116">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="5e4f4-117">Parametr je typu <!--zz <xref:System.ServiceModel.MSMQIntegration.MsmqMessage%601>`MsmqMessage<T>`--> , `System.ServiceModel.MSMQIntegration.MsmqMessage` obsahující základní zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-117">The parameter is of type <!--zz <xref:System.ServiceModel.MSMQIntegration.MsmqMessage%601>`MsmqMessage<T>`--> , `System.ServiceModel.MSMQIntegration.MsmqMessage` which contains the underlying MSMQ message.</span></span> <span data-ttu-id="5e4f4-118">Typ "T" v `MsmqMessage<T>` třída reprezentuje data, která je serializován do textu zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-118">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="5e4f4-119">V této ukázce `PurchaseOrder` typ serializován do textu zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-119">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```  
  
 <span data-ttu-id="5e4f4-120">Operace služby zpracovává nákupní objednávka a obsah nákupní objednávka a jeho stav se zobrazí v okně konzoly služby.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-120">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="5e4f4-121"><xref:System.ServiceModel.OperationBehaviorAttribute> Nakonfiguruje operaci zařazení v transakci s fronty a označit dokončení transakce po návratu operaci.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-121">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="5e4f4-122">`PurchaseOrder` Obsahuje podrobnosti o pořadí, které musí být služba.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-122">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>  
  
```  
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
  
 <span data-ttu-id="5e4f4-123">Služba používá vlastní klienta `OrderResponseClient` k odeslání zprávy služby MSMQ do fronty.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-123">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="5e4f4-124">Vzhledem k tomu, že je aplikace, který obdrží a zpracuje zprávy aplikací služby MSMQ a ne [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, neexistuje žádný kontrakt implicitní služby mezi těmito dvěma aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-124">Because the application that receives and processes the message is an MSMQ application and not a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="5e4f4-125">Proto nemůžeme vytvořit proxy server pomocí nástroje Svcutil.exe v tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-125">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>  
  
 <span data-ttu-id="5e4f4-126">Vlastní proxy server je v podstatě stejný pro všechny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, které používají `msmqIntegrationBinding` vazby k odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-126">The custom proxy is essentially the same for all [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="5e4f4-127">Na rozdíl od jiných proxy nebude obsahovat celou řadu operací služby.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-127">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="5e4f4-128">Je zpráva operaci odeslání jenom.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-128">It is a submit message operation only.</span></span>  
  
```  
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
  
 <span data-ttu-id="5e4f4-129">Služba je sám sebou hostované.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-129">The service is self hosted.</span></span> <span data-ttu-id="5e4f4-130">Pokud používáte transport integrace MSMQ, používá fronty musí být vytvořeny předem.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-130">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="5e4f4-131">Tento krok můžete provést ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-131">This can be done manually or through code.</span></span> <span data-ttu-id="5e4f4-132">V této ukázce služba obsahuje <xref:System.Messaging> kódu zkontrolujte existenci fronty a vytvořte ji v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-132">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="5e4f4-133">Název fronty je číst z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-133">The queue name is read from the configuration file.</span></span>  
  
```  
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
  
 <span data-ttu-id="5e4f4-134">Frontu MSMQ, ke které se odesílají žádosti pořadí je zadána v oddílu appSettings konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-134">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="5e4f4-135">Koncové body klienta a služby jsou definovány v sekci system.serviceModel konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-135">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="5e4f4-136">Zadejte oba `msmqIntegrationbinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-136">Both specify the `msmqIntegrationbinding` binding.</span></span>  
  
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
  
 <span data-ttu-id="5e4f4-137">Klientská aplikace používá <xref:System.Messaging> k odeslání odolné a transakční zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-137">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="5e4f4-138">Tělo zprávy obsahuje nákupní objednávka.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-138">The message's body contains the purchase order.</span></span>  
  
```  
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
  
 <span data-ttu-id="5e4f4-139">Frontu MSMQ, ve kterém jsou přijaty odpovědi pořadí je zadána v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-139">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e4f4-140">Název fronty používá tečku (.) pro místní počítač a oddělovače zpětné lomítko, v jeho cesty.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-140">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="5e4f4-141">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Adresa koncového bodu určuje schématu msmq.formatname a používá "localhost" pro místní počítač.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-141">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="5e4f4-142">Název formátu správně vytvořená následuje msmq.formatname v identifikátoru URI podle pokynů služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-142">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>  
  
```xml  
<appSettings>  
    <add key=" orderResponseQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 <span data-ttu-id="5e4f4-143">Uloží aplikace klienta `messageID` pořadí zprávě požadavku, která ji odešle do služby a čeká na odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-143">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="5e4f4-144">Po odpověď dorazí ve frontě, klient ji koreluje s pořadí zpráva se odešle pomocí `correlationID` vlastnosti zprávy, která obsahuje `messageID` objednávky zprávou, která klient odešle do služby původně.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-144">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>  
  
```  
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
  
 <span data-ttu-id="5e4f4-145">Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-145">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="5e4f4-146">Zobrazí se službu přijmout zprávy z klienta a odešle odpověď zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-146">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="5e4f4-147">Klient se zobrazí odpověď přijal od služby.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-147">The client displays the response received from the service.</span></span> <span data-ttu-id="5e4f4-148">Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e4f4-149">Tato ukázka vyžaduje instalaci služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="5e4f4-149">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="5e4f4-150">Najdete v pokynech k instalaci služby MSMQ v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-150">See the MSMQ installation instructions in the See Also section.</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="5e4f4-151">Instalační program, sestavení a spuštění vzorku</span><span class="sxs-lookup"><span data-stu-id="5e4f4-151">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5e4f4-152">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e4f4-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5e4f4-153">Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-153">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="5e4f4-154">Pokud fronta neexistuje, vytvoří služba jeden.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-154">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="5e4f4-155">Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-155">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="5e4f4-156">Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-156">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="5e4f4-157">Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e4f4-157">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="5e4f4-158">Rozbalte **funkce** kartě.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-158">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="5e4f4-159">Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-159">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="5e4f4-160">Zkontrolujte **transakcí** pole.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-160">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="5e4f4-161">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-161">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="5e4f4-162">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e4f4-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="5e4f4-163">Spustit ukázku v konfiguraci jednoho počítače, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e4f4-163">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="5e4f4-164">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="5e4f4-164">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="5e4f4-165">Zkopírujte soubory programu služby ve složce \service\bin\ ve složce pro specifický jazyk k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-165">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="5e4f4-166">Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-166">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="5e4f4-167">V souboru Client.exe.config změnit orderQueueName k zadání názvu počítače služba místo ".".</span><span class="sxs-lookup"><span data-stu-id="5e4f4-167">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="5e4f4-168">V souboru Service.exe.config změnit adresa koncového bodu klienta k zadání názvu počítače klienta místo ".".</span><span class="sxs-lookup"><span data-stu-id="5e4f4-168">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>  
  
5.  <span data-ttu-id="5e4f4-169">Na počítači se službou spusťte z příkazového řádku Service.exe.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-169">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
6.  <span data-ttu-id="5e4f4-170">Na klientském počítači spusťte z příkazového řádku Client.exe.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-170">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5e4f4-171">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-171">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5e4f4-172">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="5e4f4-172">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5e4f4-173">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5e4f4-174">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5e4f4-174">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a><span data-ttu-id="5e4f4-175">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e4f4-175">See Also</span></span>  
 [<span data-ttu-id="5e4f4-176">Zařazování do front ve WCF</span><span class="sxs-lookup"><span data-stu-id="5e4f4-176">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="5e4f4-177">Služba Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="5e4f4-177">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=94968)
