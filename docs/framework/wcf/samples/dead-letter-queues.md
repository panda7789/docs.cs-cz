---
title: Fronty nedoručených zpráv
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: eab1c52f4d0b3d0f82cf561a9478ea8233598e1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144945"
---
# <a name="dead-letter-queues"></a><span data-ttu-id="f036e-102">Fronty nedoručených zpráv</span><span class="sxs-lookup"><span data-stu-id="f036e-102">Dead Letter Queues</span></span>
<span data-ttu-id="f036e-103">Tato ukázka ukazuje, jak zpracovat a zpracovat zprávy, které se nezdařilo doručení.</span><span class="sxs-lookup"><span data-stu-id="f036e-103">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="f036e-104">Je založen na [transacted MSMQ binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="f036e-104">It is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="f036e-105">Tato ukázka `netMsmqBinding` používá vazbu.</span><span class="sxs-lookup"><span data-stu-id="f036e-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="f036e-106">Služba je aplikace konzoly s vlastním hostitelem, která umožňuje sledovat službu přijímající zprávy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="f036e-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="f036e-107">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f036e-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="f036e-108">Tato ukázka ukazuje každou frontu nedoručených zpráv aplikace, která je k dispozici pouze v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="f036e-108">This sample demonstrates each application dead letter queue that is only available on Windows Vista.</span></span> <span data-ttu-id="f036e-109">Ukázku lze upravit tak, aby používala výchozí systémové fronty pro službu MSMQ 3.0 v systémech Windows Server 2003 a Windows XP.</span><span class="sxs-lookup"><span data-stu-id="f036e-109">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on Windows Server 2003 and Windows XP.</span></span>

 <span data-ttu-id="f036e-110">Ve frontové komunikaci klient komunikuje se službou pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="f036e-110">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="f036e-111">Přesněji řečeno, klient odesílá zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="f036e-111">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="f036e-112">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="f036e-112">The service receives messages from the queue.</span></span> <span data-ttu-id="f036e-113">Služba a klient proto nemusí být spuštěny současně komunikovat pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="f036e-113">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="f036e-114">Vzhledem k tomu, že komunikace ve frontě může zahrnovat určité množství klid, můžete přidružit hodnotu time-to-live na zprávu, abyste zajistili, že zpráva nebude doručena do aplikace, pokud uplynula.</span><span class="sxs-lookup"><span data-stu-id="f036e-114">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="f036e-115">Existují také případy, kdy aplikace musí být informováni, zda zpráva selhala doručení.</span><span class="sxs-lookup"><span data-stu-id="f036e-115">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="f036e-116">Ve všech těchto případech, například při vypršení doby do provozu na zprávu nebo zprávy se nezdařilo doručení, je zpráva umístěna do fronty nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="f036e-116">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="f036e-117">Odesílající aplikace pak můžete číst zprávy ve frontě nedoručených zpráv a přijmout nápravná opatření, která sahají od žádné akce k opravě důvodů pro neúspěšné doručení a opětovné odeslání zprávy.</span><span class="sxs-lookup"><span data-stu-id="f036e-117">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>

 <span data-ttu-id="f036e-118">Fronta nedoručených `NetMsmqBinding` zpráv ve vazbě je vyjádřena v následujících vlastnostech:</span><span class="sxs-lookup"><span data-stu-id="f036e-118">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>

- <span data-ttu-id="f036e-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>vlastnost vyjádřit druh fronty nedoručených zpráv vyžadované klientem.</span><span class="sxs-lookup"><span data-stu-id="f036e-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="f036e-120">Tento výčet má následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="f036e-120">This enumeration has the following values:</span></span>

- <span data-ttu-id="f036e-121">`None`: Klient nevyžaduje žádnou frontu nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="f036e-121">`None`: No dead-letter queue is required by the client.</span></span>

- <span data-ttu-id="f036e-122">`System`: Fronta nedoručených zpráv systému se používá k ukládání nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="f036e-122">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="f036e-123">Systémová fronta nedoručených zpráv je sdílena všemi aplikacemi spuštěnými v počítači.</span><span class="sxs-lookup"><span data-stu-id="f036e-123">The system dead-letter queue is shared by all applications running on the computer.</span></span>

- <span data-ttu-id="f036e-124">`Custom`: Vlastní fronta nedoručených <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> zpráv zadaná pomocí vlastnosti se používá k ukládání nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="f036e-124">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="f036e-125">Tato funkce je k dispozici pouze v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="f036e-125">This feature is only available on Windows Vista.</span></span> <span data-ttu-id="f036e-126">Používá se v případě, že aplikace musí používat vlastní frontu nedoručených zpráv namísto sdílení s jinými aplikacemi spuštěnými ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="f036e-126">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>

- <span data-ttu-id="f036e-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>vlastnost vyjádřit konkrétní fronty použít jako fronty nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="f036e-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="f036e-128">Tato možnost je k dispozici pouze v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="f036e-128">This is available only in Windows Vista.</span></span>

 <span data-ttu-id="f036e-129">V této ukázce klient odešle dávku zpráv do služby z rozsahu transakce a určuje libovolně nízkou hodnotu pro "time-to-live" pro tyto zprávy (asi 2 sekundy).</span><span class="sxs-lookup"><span data-stu-id="f036e-129">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="f036e-130">Klient také určuje vlastní frontu nedoručených zpráv, která se má použít k zařazení zpráv, jejichž platnost vypršela.</span><span class="sxs-lookup"><span data-stu-id="f036e-130">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>

 <span data-ttu-id="f036e-131">Klientská aplikace může číst zprávy ve frontě nedoručených zpráv a zkuste zprávu odeslat znovu nebo opravit chybu, která způsobila umístění původní zprávy do fronty nedoručených zpráv a odeslat zprávu.</span><span class="sxs-lookup"><span data-stu-id="f036e-131">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="f036e-132">V ukázce se zobrazí chybová zpráva klienta.</span><span class="sxs-lookup"><span data-stu-id="f036e-132">In the sample, the client displays an error message.</span></span>

 <span data-ttu-id="f036e-133">Servisní smlouva `IOrderProcessor`je , jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="f036e-133">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="f036e-134">Kód služby v ukázce je [kód transacted msmq vazby](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="f036e-134">The service code in the sample is that of the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>

 <span data-ttu-id="f036e-135">Komunikace se službou probíhá v rámci transakce.</span><span class="sxs-lookup"><span data-stu-id="f036e-135">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="f036e-136">Služba čte zprávy z fronty, provádí operaci a potom zobrazí výsledky operace.</span><span class="sxs-lookup"><span data-stu-id="f036e-136">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="f036e-137">Aplikace také vytvoří frontu nedoručených zpráv pro nedoručené zprávy.</span><span class="sxs-lookup"><span data-stu-id="f036e-137">The application also creates a dead-letter queue for dead-letter messages.</span></span>

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

 <span data-ttu-id="f036e-138">Konfigurace klienta určuje krátkou dobu trvání zprávy k dosažení služby.</span><span class="sxs-lookup"><span data-stu-id="f036e-138">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="f036e-139">Pokud zprávu nelze přenést v rámci zadané doby trvání, vyprší platnost zprávy a je přesunuta do fronty nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="f036e-139">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>

> [!NOTE]
> <span data-ttu-id="f036e-140">Je možné, aby klient doručit zprávu do fronty služeb v zadaném čase.</span><span class="sxs-lookup"><span data-stu-id="f036e-140">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="f036e-141">Chcete-li zajistit, že se služba nedoručených dat zobrazí v akci, měli byste před spuštěním služby spustit klienta.</span><span class="sxs-lookup"><span data-stu-id="f036e-141">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="f036e-142">Časový nebo poslední den zprávy a je doručena do služby nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="f036e-142">The message times out and is delivered to the dead-letter service.</span></span>

 <span data-ttu-id="f036e-143">Aplikace musí definovat, které fronty se mají použít jako frontu nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="f036e-143">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="f036e-144">Pokud není zadána žádná fronta, výchozí transakční fronta nedoručených zpráv pro celý systém se používá k zařazení nedoručených zpráv do fronty.</span><span class="sxs-lookup"><span data-stu-id="f036e-144">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="f036e-145">V tomto příkladu určuje klientská aplikace vlastní frontu nedoručených zpráv vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="f036e-145">In this example, the client application specifies its own application dead-letter queue.</span></span>

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

 <span data-ttu-id="f036e-146">Služba nedoručených zpráv čte zprávy z fronty nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="f036e-146">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="f036e-147">Služba nedoručených zpráv implementuje smlouvu. `IOrderProcessor`</span><span class="sxs-lookup"><span data-stu-id="f036e-147">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="f036e-148">Jeho realizace však není zpracování objednávek.</span><span class="sxs-lookup"><span data-stu-id="f036e-148">Its implementation however is not to process orders.</span></span> <span data-ttu-id="f036e-149">Služba nedoručených zpráv je klientská služba a nemá možnost zpracovávat objednávky.</span><span class="sxs-lookup"><span data-stu-id="f036e-149">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>

> [!NOTE]
> <span data-ttu-id="f036e-150">Fronta nedoručených zpráv je fronta klientů a je místní pro správce front klienta.</span><span class="sxs-lookup"><span data-stu-id="f036e-150">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>

 <span data-ttu-id="f036e-151">Implementace služby nedoručených zpráv z kontroluje z důvodu, že zpráva selhala doručení a přijímá nápravná opatření.</span><span class="sxs-lookup"><span data-stu-id="f036e-151">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="f036e-152">Důvod selhání zprávy je zachycen ve dvou <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> výčtů <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>a .</span><span class="sxs-lookup"><span data-stu-id="f036e-152">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="f036e-153">Můžete načíst <xref:System.ServiceModel.Channels.MsmqMessageProperty> z <xref:System.ServiceModel.OperationContext> jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="f036e-153">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>

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

 <span data-ttu-id="f036e-154">Zprávy ve frontě nedoručených zpráv jsou zprávy adresované službě, která zprávu zpracovává.</span><span class="sxs-lookup"><span data-stu-id="f036e-154">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="f036e-155">Proto při službě nedoručených zpráv čte zprávy z fronty, vrstva kanálu Windows Communication Foundation (WCF) najde neshodu v koncových bodech a neodešle zprávu.</span><span class="sxs-lookup"><span data-stu-id="f036e-155">Therefore, when the dead-letter message service reads messages from the queue, the Windows Communication Foundation (WCF) channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="f036e-156">V takovém případě je zpráva určena službě zpracování objednávek, ale je přijata službou nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="f036e-156">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="f036e-157">Chcete-li obdržet zprávu adresovanou jinému koncovému bodu, je v `ServiceBehavior`aplikaci zadán filtr adresy odpovídající libovolné adrese.</span><span class="sxs-lookup"><span data-stu-id="f036e-157">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="f036e-158">To je nutné úspěšně zpracovat zprávy, které jsou čteny z fronty nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="f036e-158">This is required to successfully process messages that are read from the dead-letter queue.</span></span>

 <span data-ttu-id="f036e-159">V této ukázce služba nedoručených zpráv znovu odešle zprávu, pokud důvodem selhání je, že časový čas zprávy. Ze všech ostatních důvodů zobrazuje selhání dodávky, jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="f036e-159">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>

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

 <span data-ttu-id="f036e-160">Následující ukázka ukazuje konfiguraci nedoručené zprávy:</span><span class="sxs-lookup"><span data-stu-id="f036e-160">The following sample shows the configuration for a dead-letter message:</span></span>

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

 <span data-ttu-id="f036e-161">Při spuštění ukázky existují 3 spustitelné soubory ke spuštění, aby viděli, jak funguje fronta nedoručených zpráv pro každou aplikaci; klient, služba a služba nedoručených zpráv, která čte z fronty nedoručených zpráv pro každou aplikaci a znovu odešle zprávu službě.</span><span class="sxs-lookup"><span data-stu-id="f036e-161">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="f036e-162">Všechny jsou konzolové aplikace s výstupem v konzolových oknech.</span><span class="sxs-lookup"><span data-stu-id="f036e-162">All are console applications with output in console windows.</span></span>

> [!NOTE]
> <span data-ttu-id="f036e-163">Vzhledem k tomu, že se používá fronty, klient a služba nemusí být současně spuštěni.</span><span class="sxs-lookup"><span data-stu-id="f036e-163">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="f036e-164">Můžete spustit klienta, vypnout a potom spustit službu a stále přijímá jeho zprávy.</span><span class="sxs-lookup"><span data-stu-id="f036e-164">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="f036e-165">Měli byste spustit službu a vypnout ji, aby bylo možné vytvořit frontu.</span><span class="sxs-lookup"><span data-stu-id="f036e-165">You should start the service and shut it down so that the queue can be created.</span></span>

 <span data-ttu-id="f036e-166">Při spuštění klienta se zobrazí zpráva:</span><span class="sxs-lookup"><span data-stu-id="f036e-166">When running the client, the client displays the message:</span></span>

```console
Press <ENTER> to terminate client.
```

 <span data-ttu-id="f036e-167">Klient se pokusil odeslat zprávu, ale s krátkým časovým limitem, zpráva vypršela a je nyní zařazena do fronty nedoručených zpráv pro každou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f036e-167">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>

 <span data-ttu-id="f036e-168">Potom spustíte službu nedoručených zpráv, která přečte zprávu a zobrazí kód chyby a znovu odešle zprávu zpět do služby.</span><span class="sxs-lookup"><span data-stu-id="f036e-168">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>

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

 <span data-ttu-id="f036e-169">Služba se spustí a potom přečte zprávu s opakováním a zpracuje ji.</span><span class="sxs-lookup"><span data-stu-id="f036e-169">The service starts and then reads the resent message and processes it.</span></span>

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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f036e-170">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="f036e-170">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="f036e-171">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f036e-171">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="f036e-172">Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f036e-172">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="f036e-173">Pokud fronta není k dispozici, služba ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="f036e-173">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="f036e-174">Nejprve můžete spustit službu a vytvořit frontu, nebo ji můžete vytvořit pomocí Správce front služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f036e-174">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="f036e-175">Vytvořenífronty v systému Windows 2008 postupujte takto.</span><span class="sxs-lookup"><span data-stu-id="f036e-175">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="f036e-176">Otevřete Správce serveru v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f036e-176">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="f036e-177">Rozbalte kartu **Funkce.**</span><span class="sxs-lookup"><span data-stu-id="f036e-177">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="f036e-178">Klepněte pravým tlačítkem myši na **položku Fronty soukromých zpráv**a vyberte příkaz **Nová**, **Soukromá fronta**.</span><span class="sxs-lookup"><span data-stu-id="f036e-178">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="f036e-179">Zaškrtněte políčko **Transakční** transakce.</span><span class="sxs-lookup"><span data-stu-id="f036e-179">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="f036e-180">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="f036e-180">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="f036e-181">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f036e-181">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="f036e-182">Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači změnit názvy fronty odpovídajícím způsobem, nahrazení localhost s úplný název počítače a postupujte podle pokynů v [spuštění windows communication foundation ukázky](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f036e-182">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="f036e-183">Spuštění ukázky v počítači připojovato k pracovní skupině</span><span class="sxs-lookup"><span data-stu-id="f036e-183">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="f036e-184">Pokud počítač není součástí domény, vypněte zabezpečení přenosu nastavením režimu `None` ověřování a úrovně ochrany na úroveň uvedenou v následující ukázkové konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="f036e-184">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="f036e-185">Ujistěte se, že koncový bod je přidružen `bindingConfiguration` k vazbě nastavením atributu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f036e-185">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>

2. <span data-ttu-id="f036e-186">Ujistěte se, že změníte konfiguraci na DeadLetterService, server a klient před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="f036e-186">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f036e-187">Nastavení `security mode` `None` na je `MsmqAuthenticationMode`ekvivalentní `MsmqProtectionLevel` `Message` nastavení `None`a zabezpečení .</span><span class="sxs-lookup"><span data-stu-id="f036e-187">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

## <a name="comments"></a><span data-ttu-id="f036e-188">Komentáře</span><span class="sxs-lookup"><span data-stu-id="f036e-188">Comments</span></span>
 <span data-ttu-id="f036e-189">Ve výchozím `netMsmqBinding` nastavení s přenosem vazby je povoleno zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f036e-189">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="f036e-190">Dvě `MsmqAuthenticationMode` vlastnosti `MsmqProtectionLevel`a společně určují typ zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="f036e-190">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="f036e-191">Ve výchozím nastavení je `Windows` režim ověřování nastaven na `Sign`hodnotu a úroveň ochrany je nastavena na hodnotu .</span><span class="sxs-lookup"><span data-stu-id="f036e-191">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="f036e-192">Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény.</span><span class="sxs-lookup"><span data-stu-id="f036e-192">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="f036e-193">Pokud spustíte tuto ukázku v počítači, který není součástí domény, zobrazí se následující chyba: "Interní certifikát fronty zpráv uživatele neexistuje".</span><span class="sxs-lookup"><span data-stu-id="f036e-193">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f036e-194">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="f036e-194">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f036e-195">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f036e-195">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f036e-196">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f036e-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f036e-197">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f036e-197">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
