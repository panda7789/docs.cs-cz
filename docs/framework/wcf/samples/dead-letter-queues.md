---
title: Fronty nedoručených zpráv
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: c8fea29fc420ea6bb922c93ea08e0e23d5bb941d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928669"
---
# <a name="dead-letter-queues"></a><span data-ttu-id="114ba-102">Fronty nedoručených zpráv</span><span class="sxs-lookup"><span data-stu-id="114ba-102">Dead Letter Queues</span></span>
<span data-ttu-id="114ba-103">Tato ukázka předvádí, jak zpracovávat a zpracovávat zprávy, které selhaly při doručování.</span><span class="sxs-lookup"><span data-stu-id="114ba-103">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="114ba-104">Vychází ze vzorových [vazeb v transakční službě MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) .</span><span class="sxs-lookup"><span data-stu-id="114ba-104">It is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="114ba-105">Tato ukázka používá `netMsmqBinding` vazbu.</span><span class="sxs-lookup"><span data-stu-id="114ba-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="114ba-106">Služba je samoobslužná Konzolová aplikace, která vám umožní sledovat službu přijímající zprávy zařazené do fronty.</span><span class="sxs-lookup"><span data-stu-id="114ba-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="114ba-107">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="114ba-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="114ba-108">Tato ukázka demonstruje každou frontu nedoručených zpráv aplikace [!INCLUDE[wv](../../../../includes/wv-md.md)], která je k dispozici pouze na.</span><span class="sxs-lookup"><span data-stu-id="114ba-108">This sample demonstrates each application dead letter queue that is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="114ba-109">Ukázku je možné upravit tak, aby používala výchozí systémové fronty pro službu MSMQ 3,0 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] zapnutou [!INCLUDE[wxp](../../../../includes/wxp-md.md)]a.</span><span class="sxs-lookup"><span data-stu-id="114ba-109">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span></span>

 <span data-ttu-id="114ba-110">V komunikaci ve frontě klient komunikuje se službou pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="114ba-110">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="114ba-111">Klient přesněji odesílá zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="114ba-111">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="114ba-112">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="114ba-112">The service receives messages from the queue.</span></span> <span data-ttu-id="114ba-113">Službu a klient proto nemusí běžet současně, aby bylo možné komunikovat pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="114ba-113">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="114ba-114">Vzhledem k tomu, že komunikace zařazená do fronty může zahrnovat určité množství dormancy, možná budete chtít ke zprávě přidružit hodnotu TTL (Time to Live), aby se zajistilo, že se zpráva nebude doručena do aplikace, pokud zmizela po čase.</span><span class="sxs-lookup"><span data-stu-id="114ba-114">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="114ba-115">Existují také případy, kdy musí být aplikace informována o tom, zda se nezdařila doručení zprávy.</span><span class="sxs-lookup"><span data-stu-id="114ba-115">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="114ba-116">Ve všech těchto případech, například když vypršel časový limit u zprávy nebo když zpráva selhala při doručování, je zpráva vložena do fronty nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="114ba-116">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="114ba-117">Odesílající aplikace potom může číst zprávy ve frontě nedoručených zpráv a provádět nápravné akce, které se nezdařily z důvodu opravy důvodů neúspěšného doručení a opětovného odeslání zprávy.</span><span class="sxs-lookup"><span data-stu-id="114ba-117">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>

 <span data-ttu-id="114ba-118">Fronta nedoručených zpráv ve `NetMsmqBinding` vazbě je vyjádřena v následujících vlastnostech:</span><span class="sxs-lookup"><span data-stu-id="114ba-118">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>

- <span data-ttu-id="114ba-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>vlastnost, která vyjadřuje druh fronty nedoručených zpráv, kterou klient vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="114ba-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="114ba-120">Tento výčet má následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="114ba-120">This enumeration has the following values:</span></span>

- <span data-ttu-id="114ba-121">`None`: Klient nepožaduje žádnou frontu nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="114ba-121">`None`: No dead-letter queue is required by the client.</span></span>

- <span data-ttu-id="114ba-122">`System`: Fronta nedoručených zpráv systému se používá k ukládání nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="114ba-122">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="114ba-123">Fronta nedoručených zpráv systému je sdílena všemi aplikacemi spuštěnými v počítači.</span><span class="sxs-lookup"><span data-stu-id="114ba-123">The system dead-letter queue is shared by all applications running on the computer.</span></span>

- <span data-ttu-id="114ba-124">`Custom`: Vlastní fronta nedoručených zpráv určená pomocí <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> vlastnosti se používá k ukládání nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="114ba-124">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="114ba-125">Tato funkce je k dispozici [!INCLUDE[wv](../../../../includes/wv-md.md)]pouze v systému.</span><span class="sxs-lookup"><span data-stu-id="114ba-125">This feature is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="114ba-126">Tato část se používá, když aplikace musí používat vlastní frontu nedoručených zpráv místo jejího sdílení s jinými aplikacemi spuštěnými ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="114ba-126">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>

- <span data-ttu-id="114ba-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>vlastnost, která vyjadřuje konkrétní frontu, která se použije jako fronta nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="114ba-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="114ba-128">Tato je k dispozici [!INCLUDE[wv](../../../../includes/wv-md.md)]pouze v.</span><span class="sxs-lookup"><span data-stu-id="114ba-128">This is available only in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="114ba-129">V této ukázce klient pošle dávku zpráv službě v rámci rozsahu transakce a určí libovolně nízkou hodnotu "Time to Live" pro tyto zprávy (přibližně 2 sekundy).</span><span class="sxs-lookup"><span data-stu-id="114ba-129">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="114ba-130">Klient také určuje vlastní frontu nedoručených zpráv, která má být použita k zařazování zpráv, jejichž platnost vypršela.</span><span class="sxs-lookup"><span data-stu-id="114ba-130">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>

 <span data-ttu-id="114ba-131">Klientská aplikace může číst zprávy ve frontě nedoručených zpráv a buď znovu odeslat zprávu, nebo opravit chybu, která způsobila, že původní zpráva bude umístěna do fronty nedoručených zpráv, a odeslat zprávu.</span><span class="sxs-lookup"><span data-stu-id="114ba-131">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="114ba-132">V ukázce klient zobrazuje chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="114ba-132">In the sample, the client displays an error message.</span></span>

 <span data-ttu-id="114ba-133">Kontrakt služby je, `IOrderProcessor`jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="114ba-133">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="114ba-134">Kód služby v ukázce je výsledkem [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="114ba-134">The service code in the sample is that of the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>

 <span data-ttu-id="114ba-135">Komunikace se službou se uskutečňuje v rámci rozsahu transakce.</span><span class="sxs-lookup"><span data-stu-id="114ba-135">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="114ba-136">Služba přečte zprávy z fronty, provede operaci a potom zobrazí výsledky operace.</span><span class="sxs-lookup"><span data-stu-id="114ba-136">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="114ba-137">Aplikace také vytvoří frontu nedoručených zpráv pro zprávy s nedoručenými zprávami.</span><span class="sxs-lookup"><span data-stu-id="114ba-137">The application also creates a dead-letter queue for dead-letter messages.</span></span>

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

 <span data-ttu-id="114ba-138">Konfigurace klienta Určuje krátkou dobu trvání zprávy pro dosažení služby.</span><span class="sxs-lookup"><span data-stu-id="114ba-138">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="114ba-139">Pokud zprávu nelze přenést do zadané doby trvání, vyprší platnost zprávy a bude přesunuta do fronty nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="114ba-139">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>

> [!NOTE]
> <span data-ttu-id="114ba-140">Je možné, že klient doručí zprávu do fronty služby v určeném čase.</span><span class="sxs-lookup"><span data-stu-id="114ba-140">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="114ba-141">Abyste měli jistotu, že se služba nedoručených zpráv zobrazuje v akci, měli byste před spuštěním služby spustit klienta.</span><span class="sxs-lookup"><span data-stu-id="114ba-141">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="114ba-142">Vyprší časový limit zprávy a doručuje se do služby nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="114ba-142">The message times out and is delivered to the dead-letter service.</span></span>

 <span data-ttu-id="114ba-143">Aplikace musí definovat, kterou frontu použít jako svou frontu nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="114ba-143">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="114ba-144">Není-li zadána žádná fronta, je pro zařazení nedoručených zpráv použita výchozí fronta nedoručených transakčních zpráv v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="114ba-144">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="114ba-145">V tomto příkladu klientská aplikace určí svoji vlastní frontu nedoručených zpráv aplikace.</span><span class="sxs-lookup"><span data-stu-id="114ba-145">In this example, the client application specifies its own application dead-letter queue.</span></span>

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

 <span data-ttu-id="114ba-146">Nedoručená služba zpráv čte zprávy z fronty nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="114ba-146">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="114ba-147">Nedoručená služba zpráv implementuje `IOrderProcessor` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="114ba-147">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="114ba-148">Jeho implementace ale nezpracovává objednávky.</span><span class="sxs-lookup"><span data-stu-id="114ba-148">Its implementation however is not to process orders.</span></span> <span data-ttu-id="114ba-149">Nedoručená služba zpráv je klientská služba a nemá k dispozici zařízení pro zpracování objednávek.</span><span class="sxs-lookup"><span data-stu-id="114ba-149">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>

> [!NOTE]
> <span data-ttu-id="114ba-150">Fronta nedoručených zpráv je klientská fronta a je místní pro správce front klienta.</span><span class="sxs-lookup"><span data-stu-id="114ba-150">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>

 <span data-ttu-id="114ba-151">Nedoručená implementace služby zpráv s nedoručenými zprávami kontroluje důvod neúspěšného doručení zprávy a provádí nápravná opatření.</span><span class="sxs-lookup"><span data-stu-id="114ba-151">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="114ba-152">Důvod selhání zprávy je zachycen ve dvou výčtech <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> a. <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A></span><span class="sxs-lookup"><span data-stu-id="114ba-152">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="114ba-153">Můžete načíst <xref:System.ServiceModel.Channels.MsmqMessageProperty> z rozhraní <xref:System.ServiceModel.OperationContext> , jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="114ba-153">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succeed ", po);
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

 <span data-ttu-id="114ba-154">Zprávy ve frontě nedoručených zpráv jsou zprávy, které jsou adresovány službě, která zpracovává zprávu.</span><span class="sxs-lookup"><span data-stu-id="114ba-154">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="114ba-155">Proto když služba zpráv nedoručených zpráv přečte zprávy z fronty, vrstva kanálu Windows Communication Foundation (WCF) nalezne neshodu v koncových bodech a neodešle zprávu.</span><span class="sxs-lookup"><span data-stu-id="114ba-155">Therefore, when the dead-letter message service reads messages from the queue, the Windows Communication Foundation (WCF) channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="114ba-156">V tomto případě je zpráva adresována službě zpracování objednávky, ale je přijímána službou nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="114ba-156">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="114ba-157">Chcete-li získat zprávu adresovanou jinému koncovému bodu, je filtr adres shodný s libovolnou adresou uveden v `ServiceBehavior`.</span><span class="sxs-lookup"><span data-stu-id="114ba-157">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="114ba-158">Tato operace je nutná k úspěšnému zpracování zpráv, které jsou čteny z fronty nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="114ba-158">This is required to successfully process messages that are read from the dead-letter queue.</span></span>

 <span data-ttu-id="114ba-159">V této ukázce služba zasílání zpráv s nedoručenými zprávami znovu odešle zprávu, pokud příčinou chyby je, že došlo k vypršení časového limitu zprávy. Pro všechny ostatní důvody se zobrazí chyba doručení, jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="114ba-159">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>

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

 <span data-ttu-id="114ba-160">Následující příklad ukazuje konfiguraci pro zprávu s nedoručenými zprávami:</span><span class="sxs-lookup"><span data-stu-id="114ba-160">The following sample shows the configuration for a dead-letter message:</span></span>

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

 <span data-ttu-id="114ba-161">Při spuštění ukázky jsou k dispozici tři spustitelné soubory, abyste viděli, jak fronta nedoručených zpráv funguje pro každou aplikaci. klient, služba a služba nedoručených zpráv, která čte z fronty nedoručených zpráv pro každou aplikaci a odesílá zprávu službě.</span><span class="sxs-lookup"><span data-stu-id="114ba-161">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="114ba-162">Všechny jsou konzolové aplikace s výstupem v oknech konzoly.</span><span class="sxs-lookup"><span data-stu-id="114ba-162">All are console applications with output in console windows.</span></span>

> [!NOTE]
> <span data-ttu-id="114ba-163">Protože se služba Řízení front používá, není nutné, aby klient a služba běžely ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="114ba-163">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="114ba-164">Můžete spustit klienta, vypnout ho a pak spustit službu a nadále přijímat zprávy.</span><span class="sxs-lookup"><span data-stu-id="114ba-164">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="114ba-165">Službu je třeba spustit a vypnout, aby bylo možné vytvořit frontu.</span><span class="sxs-lookup"><span data-stu-id="114ba-165">You should start the service and shut it down so that the queue can be created.</span></span>

 <span data-ttu-id="114ba-166">Při spuštění klienta se zobrazí zpráva klienta:</span><span class="sxs-lookup"><span data-stu-id="114ba-166">When running the client, the client displays the message:</span></span>

```console
Press <ENTER> to terminate client.
```

 <span data-ttu-id="114ba-167">Klient se pokusil zprávu poslat, ale má krátký časový limit, zpráva vypršela a je nyní zařazena do fronty nedoručených zpráv pro každou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="114ba-167">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>

 <span data-ttu-id="114ba-168">Poté spustíte službu nedoručených zpráv, která přečte zprávu, zobrazí kód chyby a znovu odešle zprávu zpět do služby.</span><span class="sxs-lookup"><span data-stu-id="114ba-168">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>

```console
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 <span data-ttu-id="114ba-169">Služba se spustí a pak přečte zprávu o opakovaném odeslání a zpracuje ji.</span><span class="sxs-lookup"><span data-stu-id="114ba-169">The service starts and then reads the resent message and processes it.</span></span>

```console
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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="114ba-170">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="114ba-170">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="114ba-171">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="114ba-171">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="114ba-172">Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici.</span><span class="sxs-lookup"><span data-stu-id="114ba-172">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="114ba-173">Pokud fronta není přítomna, služba ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="114ba-173">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="114ba-174">Službu můžete nejdřív spustit, abyste mohli vytvořit frontu, nebo ji můžete vytvořit pomocí Správce fronty MSMQ.</span><span class="sxs-lookup"><span data-stu-id="114ba-174">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="114ba-175">Pomocí těchto kroků vytvořte ve Windows 2008 frontu.</span><span class="sxs-lookup"><span data-stu-id="114ba-175">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="114ba-176">Otevřete Správce serveru v aplikaci Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="114ba-176">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="114ba-177">Rozbalte kartu **funkce** .</span><span class="sxs-lookup"><span data-stu-id="114ba-177">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="114ba-178">Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **Nový**, **soukromá fronta**.</span><span class="sxs-lookup"><span data-stu-id="114ba-178">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="114ba-179">Zaškrtněte políčko **transakční** .</span><span class="sxs-lookup"><span data-stu-id="114ba-179">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="114ba-180">Jako `ServiceModelSamplesTransacted` název nové fronty zadejte.</span><span class="sxs-lookup"><span data-stu-id="114ba-180">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="114ba-181">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="114ba-181">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="114ba-182">Chcete-li ukázku spustit v jednom nebo několika počítačích ve frontě změny konfigurace, nahraďte localhost úplným názvem počítače a postupujte podle pokynů v [části spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="114ba-182">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="114ba-183">Spuštění ukázky na počítači připojeném k pracovní skupině</span><span class="sxs-lookup"><span data-stu-id="114ba-183">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="114ba-184">Pokud počítač není součástí domény, vypněte zabezpečení přenosu nastavením režimu ověřování a úrovně ochrany tak `None` , jak je znázorněno v následující ukázkové konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="114ba-184">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="114ba-185">Nastavením `bindingConfiguration` atributu koncového bodu zajistěte, aby byl koncový bod přidružen k vazbě.</span><span class="sxs-lookup"><span data-stu-id="114ba-185">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>

2. <span data-ttu-id="114ba-186">Před spuštěním ukázky se ujistěte, že jste změnili konfiguraci na DeadLetterService, serveru a klientovi.</span><span class="sxs-lookup"><span data-stu-id="114ba-186">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="114ba-187">Nastavení `security mode` `MsmqAuthenticationMode`na `None`jeekvivalent nastavení a`Message`zabezpečení na .`None` `MsmqProtectionLevel`</span><span class="sxs-lookup"><span data-stu-id="114ba-187">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

## <a name="comments"></a><span data-ttu-id="114ba-188">Komentáře</span><span class="sxs-lookup"><span data-stu-id="114ba-188">Comments</span></span>
 <span data-ttu-id="114ba-189">Ve výchozím nastavení se `netMsmqBinding` pro přenos vazeb povoluje zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="114ba-189">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="114ba-190">Dvě vlastnosti `MsmqAuthenticationMode` a `MsmqProtectionLevel`společně určují typ zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="114ba-190">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="114ba-191">Ve výchozím nastavení je režim ověřování nastaven na `Windows` hodnotu a úroveň ochrany je nastavena na `Sign`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="114ba-191">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="114ba-192">Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény.</span><span class="sxs-lookup"><span data-stu-id="114ba-192">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="114ba-193">Pokud tuto ukázku spustíte na počítači, který není součástí domény, zobrazí se následující chyba: "Vnitřní certifikát služby Řízení front zpráv" neexistuje ".</span><span class="sxs-lookup"><span data-stu-id="114ba-193">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="114ba-194">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="114ba-194">The samples may already be installed on your computer.</span></span> <span data-ttu-id="114ba-195">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="114ba-195">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="114ba-196">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="114ba-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="114ba-197">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="114ba-197">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
