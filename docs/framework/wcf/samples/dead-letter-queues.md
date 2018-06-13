---
title: Fronty nedoručených zpráv
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: 9f92aeb02d997820fa2955419a3cdcf1c4369b45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33507978"
---
# <a name="dead-letter-queues"></a><span data-ttu-id="612b4-102">Fronty nedoručených zpráv</span><span class="sxs-lookup"><span data-stu-id="612b4-102">Dead Letter Queues</span></span>
<span data-ttu-id="612b4-103">Tento příklad znázorňuje postup zpracování a zpracování zpráv, které selhaly doručení.</span><span class="sxs-lookup"><span data-stu-id="612b4-103">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="612b4-104">Je založena na [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="612b4-104">It is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="612b4-105">V tomto příkladu `netMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="612b4-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="612b4-106">Služba je vlastním hostováním konzolové aplikace, které vám umožňují sledovat službu přijetí zprávy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="612b4-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="612b4-107">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="612b4-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="612b4-108">Tento příklad znázorňuje každou frontu nedoručených zpráv aplikace, která je dostupná pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="612b4-108">This sample demonstrates each application dead letter queue that is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="612b4-109">Ukázku můžete upravit tak, aby použít výchozí systémové fronty služby MSMQ 3.0 na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="612b4-109">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span></span>  
  
 <span data-ttu-id="612b4-110">V komunikaci ve frontě klient komunikuje se služby pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="612b4-110">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="612b4-111">Přesněji řečeno klient odešle zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="612b4-111">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="612b4-112">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="612b4-112">The service receives messages from the queue.</span></span> <span data-ttu-id="612b4-113">Služba a klient proto nemusíte používat současně na komunikaci pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="612b4-113">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="612b4-114">Vzhledem k tomu, že komunikace ve frontě zahrnuje množství dormanci; můžete přidružit hodnota time to live na zprávu zajistit, že zpráva není získat doručí aplikaci pokud je mimo po čase.</span><span class="sxs-lookup"><span data-stu-id="612b4-114">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="612b4-115">Existují také případy, kdy aplikace musí být informováni zda zprávu se nepovedlo doručení.</span><span class="sxs-lookup"><span data-stu-id="612b4-115">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="612b4-116">Ve všech těchto případech například když time-to-live na zprávu vypršela platnost nebo se nezdařilo, doručení, zpráva bude umístěna do fronty nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="612b4-116">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="612b4-117">Odesílající aplikací můžete číst zprávy do fronty nedoručených zpráv a provést opravné akce, které odešlete zprávu a odstranění příčiny selhání doručení v rozsahu od žádná akce.</span><span class="sxs-lookup"><span data-stu-id="612b4-117">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>  
  
 <span data-ttu-id="612b4-118">Frontu nedoručených zpráv v `NetMsmqBinding` vazba je vyjádřena v následujících vlastností:</span><span class="sxs-lookup"><span data-stu-id="612b4-118">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>  
  
-   <span data-ttu-id="612b4-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> Vlastnost express druh frontu nedoručených zpráv požadované klientem.</span><span class="sxs-lookup"><span data-stu-id="612b4-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="612b4-120">Tento výčet má následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="612b4-120">This enumeration has the following values:</span></span>  
  
-   <span data-ttu-id="612b4-121">`None`: Klient vyžaduje žádná fronta nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="612b4-121">`None`: No dead-letter queue is required by the client.</span></span>  
  
-   <span data-ttu-id="612b4-122">`System`: Fronty nedoručených zpráv systému se používá k ukládání neaktivní zprávy.</span><span class="sxs-lookup"><span data-stu-id="612b4-122">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="612b4-123">Fronty nedoručených zpráv systému sdílejí všechny aplikace spuštěné v počítači.</span><span class="sxs-lookup"><span data-stu-id="612b4-123">The system dead-letter queue is shared by all applications running on the computer.</span></span>  
  
-   <span data-ttu-id="612b4-124">`Custom`: Vlastní frontu nedoručených zpráv zadán pomocí <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> vlastnost se používá k ukládání neaktivní zprávy.</span><span class="sxs-lookup"><span data-stu-id="612b4-124">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="612b4-125">Tato funkce je dostupná pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="612b4-125">This feature is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="612b4-126">To se používá, když aplikace musí používat vlastní frontu nedoručených zpráv místo sdílení s dalších aplikací běžících na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="612b4-126">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>  
  
-   <span data-ttu-id="612b4-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> Vlastnost express konkrétní fronty, které chcete použít jako frontu nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="612b4-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="612b4-128">Toto je k dispozici pouze v [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="612b4-128">This is available only in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>  
  
 <span data-ttu-id="612b4-129">V této ukázce klient odešle dávku zpráv do služby z rozsahu transakce a určuje nahodile nízkou hodnotu "time-to-live" pro tyto zprávy (přibližně 2 sekundy).</span><span class="sxs-lookup"><span data-stu-id="612b4-129">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="612b4-130">Klient také určuje vlastní frontu nedoručených zpráv používat k zařazování zprávy, jejichž platnost vypršela.</span><span class="sxs-lookup"><span data-stu-id="612b4-130">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>  
  
 <span data-ttu-id="612b4-131">Klientská aplikace můžou číst zprávy do fronty nedoručených zpráv a buď opakování odesílání zprávy nebo opravte chybu, která způsobila, že na původní zprávu o umístit do fronty nedoručených zpráv a odeslat zprávu.</span><span class="sxs-lookup"><span data-stu-id="612b4-131">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="612b4-132">V ukázce klient se zobrazí chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="612b4-132">In the sample, the client displays an error message.</span></span>  
  
 <span data-ttu-id="612b4-133">Kontrakt služby je `IOrderProcessor`, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="612b4-133">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 <span data-ttu-id="612b4-134">Služba kód v ukázce je u [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="612b4-134">The service code in the sample is that of the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="612b4-135">Komunikace se službou probíhá v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="612b4-135">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="612b4-136">Tato služba čte zprávy z fronty, provede operaci a potom zobrazí výsledky operace.</span><span class="sxs-lookup"><span data-stu-id="612b4-136">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="612b4-137">Aplikace také vytvoří frontu nedoručených zpráv nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="612b4-137">The application also creates a dead-letter queue for dead-letter messages.</span></span>  

```csharp
//The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        // Get MSMQ queue name from app settings in configuration  
        string deadLetterQueueName = ConfigurationManager.AppSettings["deadLetterQueueName"];  
  
        // Create the transacted MSMQ queue for storing dead message if necessary.  
        if (!MessageQueue.Exists(deadLetterQueueName))  
            MessageQueue.Create(deadLetterQueueName, true);  
  
        // Create a proxy with given client endpoint configuration  
        OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
        // Create the purchase order  
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
  
        //Create a transaction scope.  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            // Make a queued call to submit the purchase order  
            client.SubmitPurchaseOrder(po);  
            // Complete the transaction.  
            scope.Complete();  
        }  
  
        client.Close();  
  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```

 <span data-ttu-id="612b4-138">Konfigurace klienta určuje krátká doba trvání pro zprávy cílové službě.</span><span class="sxs-lookup"><span data-stu-id="612b4-138">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="612b4-139">Pokud zpráva nemůže přenášených v rámci zadaná doba trvání, zprávy vyprší a je přesunuta do fronty nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="612b4-139">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="612b4-140">Je možné pro klienta pro doručení zprávy do fronty služby v rámci zadané doby.</span><span class="sxs-lookup"><span data-stu-id="612b4-140">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="612b4-141">Zajistit, že vidíte službu nedoručených zpráv v akci, byste měli spustit před spuštěním služby klienta.</span><span class="sxs-lookup"><span data-stu-id="612b4-141">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="612b4-142">Zpráva vyprší časový limit a doručí se do služby nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="612b4-142">The message times out and is delivered to the dead-letter service.</span></span>  
  
 <span data-ttu-id="612b4-143">Aplikace musí definovat fronty, které chcete použít jako jeho frontu nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="612b4-143">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="612b4-144">Pokud je zadána žádná fronta, výchozí systémové transakční fronty nedoručených zpráv se používá k neaktivní zprávy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="612b4-144">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="612b4-145">V tomto příkladu klientská aplikace určuje vlastní frontu nedoručených zpráv aplikace.</span><span class="sxs-lookup"><span data-stu-id="612b4-145">In this example, the client application specifies its own application dead-letter queue.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- use appSetting to configure MSMQ Dead Letter queue name -->  
    <add key="deadLetterQueueName" value=".\private$\ServiceModelSamplesOrdersAppDLQ"/>  
  </appSettings>  
  
  <system.serviceModel>  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"   
                binding="netMsmqBinding"   
                bindingConfiguration="PerAppDLQBinding"   
                contract="IOrderProcessor" />  
    </client>  
  
    <bindings>  
      <netMsmqBinding>  
        <binding name="PerAppDLQBinding"  
                 deadLetterQueue="Custom"  
                 customDeadLetterQueue="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"   
                 timeToLive="00:00:02"/>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="612b4-146">Služba nedoručených zpráv přečte zprávy z fronty nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="612b4-146">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="612b4-147">Implementuje služby nedoručených zpráv `IOrderProcessor` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="612b4-147">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="612b4-148">Jeho implementace ale není na proces objednávky.</span><span class="sxs-lookup"><span data-stu-id="612b4-148">Its implementation however is not to process orders.</span></span> <span data-ttu-id="612b4-149">Služba nedoručených zpráv je služba klienta a nemá zařízení při zpracování objednávky.</span><span class="sxs-lookup"><span data-stu-id="612b4-149">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="612b4-150">Frontu nedoručených zpráv je fronty klienta a místní účet správce klienta fronty.</span><span class="sxs-lookup"><span data-stu-id="612b4-150">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>  
  
 <span data-ttu-id="612b4-151">Implementace služby nedoručených zpráv kontroluje z důvodu, že se že zprávu nepodařilo doručení a trvá opravná opatření.</span><span class="sxs-lookup"><span data-stu-id="612b4-151">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="612b4-152">Důvod selhání zpráv zachytí ve dvou výčty <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> a <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span><span class="sxs-lookup"><span data-stu-id="612b4-152">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="612b4-153">Můžete získat <xref:System.ServiceModel.Channels.MsmqMessageProperty> z <xref:System.ServiceModel.OperationContext> jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="612b4-153">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>  

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)  
{  
    Console.WriteLine("Submitting purchase order did not succed ", po);  
    MsmqMessageProperty mqProp =   
                  OperationContext.Current.IncomingMessageProperties[  
                  MsmqMessageProperty.Name] as MsmqMessageProperty;  
    Console.WriteLine("Message Delivery Status: {0} ",   
                                                mqProp.DeliveryStatus);  
    Console.WriteLine("Message Delivery Failure: {0}",   
                                               mqProp.DeliveryFailure);  
    Console.WriteLine();  
    …  
}
```

 <span data-ttu-id="612b4-154">Zprávy do fronty nedoručených zpráv jsou zprávy adresované do služby, která je zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="612b4-154">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="612b4-155">Proto když služba nedoručených zpráv čte zprávy z fronty, vrstvy kanálu Windows Communication Foundation (WCF) najde neshody v koncových bodů a není odeslat zprávu.</span><span class="sxs-lookup"><span data-stu-id="612b4-155">Therefore, when the dead-letter message service reads messages from the queue, the Windows Communication Foundation (WCF) channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="612b4-156">V takovém případě zprávy je řešit pořadí zpracování služby, ale je přijatých službou nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="612b4-156">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="612b4-157">Pro příjem zprávy, která je určena k jinému koncovému bodu, filtr adres tak, aby odpovídaly libovolná adresa je uveden v `ServiceBehavior`.</span><span class="sxs-lookup"><span data-stu-id="612b4-157">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="612b4-158">To je nutné úspěšně zpracovat zprávy, které se načítají z fronty nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="612b4-158">This is required to successfully process messages that are read from the dead-letter queue.</span></span>  
  
 <span data-ttu-id="612b4-159">V této ukázce služba nedoručených zpráv znovu odešle zprávu Pokud z důvodu selhání je, že zpráva Vypršel časový limit. Z jiných důvodů zobrazí chyba doručení, jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="612b4-159">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>  

```csharp
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Single, AddressFilterMode=AddressFilterMode.Any)]  
public class PurchaseOrderDLQService : IOrderProcessor  
{  
    OrderProcessorClient orderProcessorService;  
    public PurchaseOrderDLQService()  
    {  
        orderProcessorService = new OrderProcessorClient("OrderProcessorEndpoint");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Console.WriteLine("Submitting purchase order did not succeed ", po);  
        MsmqMessageProperty mqProp = OperationContext.Current.IncomingMessageProperties[MsmqMessageProperty.Name] as MsmqMessageProperty;  
  
        Console.WriteLine("Message Delivery Status: {0} ", mqProp.DeliveryStatus);  
        Console.WriteLine("Message Delivery Failure: {0}", mqProp.DeliveryFailure);  
        Console.WriteLine();  
  
        // resend the message if timed out  
        if (mqProp.DeliveryFailure == DeliveryFailure.ReachQueueTimeout ||  
            mqProp.DeliveryFailure == DeliveryFailure.ReceiveTimeout)  
        {  
            // re-send  
            Console.WriteLine("Purchase order Time To Live expired");  
            Console.WriteLine("Trying to resend the message");  
  
            // reuse the same transaction used to read the message from dlq to enqueue the message to app. queue  
            orderProcessorService.SubmitPurchaseOrder(po);  
            Console.WriteLine("Purchase order resent");  
        }  
    }  
  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the PurchaseOrderDLQService type.  
        using (ServiceHost serviceHost = new ServiceHost(typeof(PurchaseOrderDLQService)))  
        {  
            // Open the ServiceHostBase to create listeners and start listening for messages.  
            serviceHost.Open();  
  
            // The service can now be accessed.  
            Console.WriteLine("The dead letter service is ready.");  
            Console.WriteLine("Press <ENTER> to terminate service.");  
            Console.WriteLine();  
            Console.ReadLine();  
        }  
    }  
}   
```

 <span data-ttu-id="612b4-160">Následující příklad ukazuje konfiguraci nedoručených zpráv:</span><span class="sxs-lookup"><span data-stu-id="612b4-160">The following sample shows the configuration for a dead-letter message:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.PurchaseOrderDLQService">  
        <!-- Define NetMsmqEndpoint in this case, DLQ end point to read messages-->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"  
                  binding="netMsmqBinding"  
                  bindingConfiguration="DefaultBinding"   
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                 address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"   
                 binding="netMsmqBinding"   
                 bindingConfiguration="SystemDLQBinding"   
                 contract="IOrderProcessor" />  
    </client>  
  
    <bindings>  
      <netMsmqBinding>  
        <binding name="DefaultBinding" />  
        <binding name="SystemDLQBinding"  
                 deadLetterQueue="System"/>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="612b4-161">V běžícím ukázku, jsou 3 spustitelných souborů a zkontrolujte, jak funguje frontu nedoručených zpráv pro každou aplikaci; klienta, služby a služby nedoručených zpráv, který čte z fronty nedoručených zpráv pro každou aplikaci a znovu odešle zprávu do služby.</span><span class="sxs-lookup"><span data-stu-id="612b4-161">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="612b4-162">Všechny jsou konzolové aplikace s výstupem v oknech konzoly.</span><span class="sxs-lookup"><span data-stu-id="612b4-162">All are console applications with output in console windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="612b4-163">Protože služba Řízení front se používá, klient a služba nemusí být spuštěná ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="612b4-163">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="612b4-164">Spuštění klienta, vypněte ho a potom spuštění služby a stále přijímá jeho zprávy.</span><span class="sxs-lookup"><span data-stu-id="612b4-164">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="612b4-165">Doporučujeme spustit službu a vypnout, aby bylo možné vytvořit frontu.</span><span class="sxs-lookup"><span data-stu-id="612b4-165">You should start the service and shut it down so that the queue can be created.</span></span>  
  
 <span data-ttu-id="612b4-166">Při spuštění klienta, klient se zobrazí zpráva:</span><span class="sxs-lookup"><span data-stu-id="612b4-166">When running the client, the client displays the message:</span></span>  
  
```  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="612b4-167">Klient se pokusil o odeslání zprávy, ale s krátkou vypršení časového limitu, zpráva vypršela a je nyní zařazeny do fronty nedoručených zpráv pro každou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="612b4-167">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>  
  
 <span data-ttu-id="612b4-168">Pak spusťte službu nedoručených zpráv, která čte zprávy a zobrazí kód chyby a znovu odešle zprávu zpět ke službě.</span><span class="sxs-lookup"><span data-stu-id="612b4-168">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>  
  
```  
The dead letter service is ready.  
Press <ENTER> to terminate service.  
  
Submitting purchase order did not succeed  
Message Delivery Status: InDoubt  
Message Delivery Failure: ReachQueueTimeout  
  
Purchase order Time To Live expired  
Trying to resend the message  
Purchase order resent  
```  
  
 <span data-ttu-id="612b4-169">Služba spustí a pak přečte zprávu opětovného odeslání a procesy.</span><span class="sxs-lookup"><span data-stu-id="612b4-169">The service starts and then reads the resent message and processes it.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 97897eff-f926-4057-a32b-af8fb11b9bf9  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="612b4-170">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="612b4-170">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="612b4-171">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="612b4-171">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="612b4-172">Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty.</span><span class="sxs-lookup"><span data-stu-id="612b4-172">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="612b4-173">Pokud fronta neexistuje, vytvoří služba jeden.</span><span class="sxs-lookup"><span data-stu-id="612b4-173">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="612b4-174">Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="612b4-174">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="612b4-175">Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="612b4-175">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="612b4-176">Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="612b4-176">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="612b4-177">Rozbalte **funkce** kartě.</span><span class="sxs-lookup"><span data-stu-id="612b4-177">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="612b4-178">Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="612b4-178">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="612b4-179">Zkontrolujte **transakcí** pole.</span><span class="sxs-lookup"><span data-stu-id="612b4-179">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="612b4-180">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="612b4-180">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="612b4-181">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="612b4-181">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="612b4-182">Ke spuštění ukázky ve frontě změnit konfiguraci jednoho nebo více počítače názvy správně, nahraďte localhost úplný název počítače a postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="612b4-182">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="612b4-183">Ke spuštění ukázky na počítače připojeného k pracovní skupině</span><span class="sxs-lookup"><span data-stu-id="612b4-183">To run the sample on a computer joined to a workgroup</span></span>  
  
1.  <span data-ttu-id="612b4-184">Pokud počítač není součástí domény, vypněte zabezpečení přenosu podle nastavení úrovně režim a ochrany ověřování na `None` jak je znázorněno v následující ukázka konfigurace:</span><span class="sxs-lookup"><span data-stu-id="612b4-184">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding name="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="612b4-185">Ujistěte se, koncový bod je přidružen vazbu pomocí nastavení pro koncový bod `bindingConfiguration` atribut.</span><span class="sxs-lookup"><span data-stu-id="612b4-185">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>  
  
2.  <span data-ttu-id="612b4-186">Ujistěte se, že změníte konfiguraci DeadLetterService, serveru a klienta, před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="612b4-186">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="612b4-187">Nastavení `security mode` k `None` je ekvivalentní nastavení `MsmqAuthenticationMode`, `MsmqProtectionLevel` a `Message` zabezpečení `None`.</span><span class="sxs-lookup"><span data-stu-id="612b4-187">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="612b4-188">Komentáře</span><span class="sxs-lookup"><span data-stu-id="612b4-188">Comments</span></span>  
 <span data-ttu-id="612b4-189">Ve výchozím nastavení se `netMsmqBinding` vazby přenos, zabezpečení je povoleno.</span><span class="sxs-lookup"><span data-stu-id="612b4-189">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="612b4-190">Dvě vlastnosti `MsmqAuthenticationMode` a `MsmqProtectionLevel`, společně určují typ zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="612b4-190">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="612b4-191">Ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="612b4-191">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="612b4-192">Pro MSMQ k ověřování a podepisování funkce musí být součástí domény.</span><span class="sxs-lookup"><span data-stu-id="612b4-192">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="612b4-193">Pokud tuto ukázku spustit na počítači, který není součástí domény, můžete dojít k následující chybě: "Uživatele interní zpráv služby Řízení front certifikát neexistuje".</span><span class="sxs-lookup"><span data-stu-id="612b4-193">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="612b4-194">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="612b4-194">The samples may already be installed on your computer.</span></span> <span data-ttu-id="612b4-195">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="612b4-195">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="612b4-196">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="612b4-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="612b4-197">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="612b4-197">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
  
## <a name="see-also"></a><span data-ttu-id="612b4-198">Viz také</span><span class="sxs-lookup"><span data-stu-id="612b4-198">See Also</span></span>
