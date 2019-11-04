---
title: Zacházení s nezpracovatelnými zprávami v MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 6f3ec0f097f1b18ca45333b7dc66431277816c60
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424314"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="4755b-102">Zacházení s nezpracovatelnými zprávami v MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="4755b-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="4755b-103">Tato ukázka předvádí, jak ve službě provádět zpracování nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="4755b-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="4755b-104">Tato ukázka je založená na ukázce s [transakčními vazbami služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) .</span><span class="sxs-lookup"><span data-stu-id="4755b-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="4755b-105">Tato ukázka používá `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="4755b-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="4755b-106">Služba je samoobslužná Konzolová aplikace, která vám umožní sledovat službu přijímající zprávy zařazené do fronty.</span><span class="sxs-lookup"><span data-stu-id="4755b-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="4755b-107">V komunikaci ve frontě klient komunikuje se službou pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="4755b-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="4755b-108">Klient přesněji odesílá zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="4755b-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="4755b-109">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="4755b-109">The service receives messages from the queue.</span></span> <span data-ttu-id="4755b-110">Službu a klient proto nemusí běžet současně, aby bylo možné komunikovat pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="4755b-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="4755b-111">Nezpracovatelná zpráva je zpráva, která se opakovaně čte z fronty, když služba čte zprávu, nemůže zprávu zpracovat, a proto ukončí transakci, pod kterou je zpráva přečtena.</span><span class="sxs-lookup"><span data-stu-id="4755b-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="4755b-112">V takových případech se zpráva znovu pokusí.</span><span class="sxs-lookup"><span data-stu-id="4755b-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="4755b-113">To se může teoreticky opakovat, pokud dojde k potížím se zprávou.</span><span class="sxs-lookup"><span data-stu-id="4755b-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="4755b-114">Všimněte si, že k tomu může dojít pouze v případě, že používáte transakce ke čtení z fronty a k vyvolání operace služby.</span><span class="sxs-lookup"><span data-stu-id="4755b-114">Note that this can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="4755b-115">V závislosti na verzi služby MSMQ podporuje NetMsmqBinding omezené zjišťování na úplnou detekci nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="4755b-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="4755b-116">Jakmile je zpráva zjištěna jako poškozená, může být zpracována několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="4755b-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="4755b-117">Na základě verze služby MSMQ podporuje NetMsmqBinding omezené zpracování na plné zpracování nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="4755b-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="4755b-118">Tato ukázka znázorňuje omezená zařízení, která jsou k dispozici na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platformě a úplném poškození poskytovaném na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4755b-118">This sample illustrates the limited poison facilities provided on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platform and the full poison facilities provided on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="4755b-119">V obou ukázkách je cílem přesunout nezpracovatelnou zprávu z fronty do jiné fronty, kterou pak může obsluhovat nezpracovatelná zpráva.</span><span class="sxs-lookup"><span data-stu-id="4755b-119">In both samples, the objective is move the poison message out of the queue to another queue which then can be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="4755b-120">Ukázka zpracování poškození služby MSMQ v 4.0</span><span class="sxs-lookup"><span data-stu-id="4755b-120">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="4755b-121">V [!INCLUDE[wv](../../../../includes/wv-md.md)]nabízí služba MSMQ zařízení s podfrontou nezpracovatele, které se dá použít k ukládání nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="4755b-121">In [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ provides a poison sub-queue facility that can be used to store poison messages.</span></span> <span data-ttu-id="4755b-122">Tato ukázka předvádí osvědčené postupy při práci s nepoškozenými zprávami pomocí [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4755b-122">This sample demonstrates the best practice of dealing with poison messages using [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="4755b-123">Detekce nepoškozených zpráv v [!INCLUDE[wv](../../../../includes/wv-md.md)] je poměrně sofistikovaná.</span><span class="sxs-lookup"><span data-stu-id="4755b-123">The poison message detection in [!INCLUDE[wv](../../../../includes/wv-md.md)] is quite sophisticated.</span></span> <span data-ttu-id="4755b-124">Existují tři vlastnosti, které vám pomůžou s detekcí.</span><span class="sxs-lookup"><span data-stu-id="4755b-124">There are 3 properties that help with detection.</span></span> <span data-ttu-id="4755b-125"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> je počet, kolikrát je daná zpráva znovu načtena z fronty a odeslána do aplikace ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="4755b-125">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="4755b-126">Zpráva je znovu načtena z fronty při návratu do fronty, protože zprávu nelze odeslat do aplikace nebo aplikace vrátí zpět transakci v rámci operace služby.</span><span class="sxs-lookup"><span data-stu-id="4755b-126">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="4755b-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> je počet přesunutí zprávy do fronty opakovaných pokusů.</span><span class="sxs-lookup"><span data-stu-id="4755b-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="4755b-128">Po dosažení <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> se zpráva přesune do fronty opakování.</span><span class="sxs-lookup"><span data-stu-id="4755b-128">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="4755b-129">Vlastnost <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> je časová prodleva, po jejímž uplynutí je zpráva přesunuta z fronty opakování zpět do hlavní fronty.</span><span class="sxs-lookup"><span data-stu-id="4755b-129">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="4755b-130"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> se resetuje na 0.</span><span class="sxs-lookup"><span data-stu-id="4755b-130">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="4755b-131">Zpráva se zopakuje.</span><span class="sxs-lookup"><span data-stu-id="4755b-131">The message is tried again.</span></span> <span data-ttu-id="4755b-132">Pokud se všechny pokusy o čtení zprávy nezdařily, zpráva je označena jako poškozená.</span><span class="sxs-lookup"><span data-stu-id="4755b-132">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="4755b-133">Jakmile je zpráva označena jako poškozená, zpráva se zabývá podle nastavení v <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> výčtu.</span><span class="sxs-lookup"><span data-stu-id="4755b-133">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="4755b-134">Chcete-li znovu iterovat možné hodnoty:</span><span class="sxs-lookup"><span data-stu-id="4755b-134">To reiterate the possible values:</span></span>

- <span data-ttu-id="4755b-135">Chyba (výchozí): pro selhání naslouchacího procesu a také hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="4755b-135">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="4755b-136">Drop: k vyřazení zprávy.</span><span class="sxs-lookup"><span data-stu-id="4755b-136">Drop: To drop the message.</span></span>

- <span data-ttu-id="4755b-137">Move: pro přesunutí zprávy do podfronty nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="4755b-137">Move: To move the message to the poison message sub-queue.</span></span> <span data-ttu-id="4755b-138">Tato hodnota je k dispozici pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4755b-138">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

- <span data-ttu-id="4755b-139">Odmítnout: Pokud chcete zprávu zamítnout, odešlete zprávu zpátky do fronty nedoručených zpráv odesilatele.</span><span class="sxs-lookup"><span data-stu-id="4755b-139">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="4755b-140">Tato hodnota je k dispozici pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4755b-140">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="4755b-141">Ukázka ukazuje použití dispoziční `Move` pro nezpracovatelnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="4755b-141">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="4755b-142">`Move` způsobí, že se zpráva přesune do podfronty nepoškozeného.</span><span class="sxs-lookup"><span data-stu-id="4755b-142">`Move` causes the message to move to the poison sub-queue.</span></span>

 <span data-ttu-id="4755b-143">Kontrakt služby je `IOrderProcessor`, který definuje jednosměrnou službu, která je vhodná pro použití s frontami.</span><span class="sxs-lookup"><span data-stu-id="4755b-143">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="4755b-144">Operace služby zobrazí zprávu informující o tom, že zpracovává objednávku.</span><span class="sxs-lookup"><span data-stu-id="4755b-144">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="4755b-145">Aby bylo možné předvést funkci nezpracovatelné zprávy, vyvolá operace `SubmitPurchaseOrder` služby výjimku pro vrácení transakce při náhodném volání služby.</span><span class="sxs-lookup"><span data-stu-id="4755b-145">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to rollback the transaction on a random invocation of the service.</span></span> <span data-ttu-id="4755b-146">Tím dojde k vrácení zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="4755b-146">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="4755b-147">Nakonec je zpráva označena jako nepoškozená.</span><span class="sxs-lookup"><span data-stu-id="4755b-147">Eventually the message is marked as poison.</span></span> <span data-ttu-id="4755b-148">Konfigurace je nastavená tak, aby se nezpracovatelná zpráva přesunula do podfronty otrav.</span><span class="sxs-lookup"><span data-stu-id="4755b-148">The configuration is set to move the poison message to the poison sub-queue.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    static Random r = new Random(137);

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {

        int randomNumber = r.Next(10);

        if (randomNumber % 2 == 0)
        {
            Orders.Add(po);
            Console.WriteLine("Processing {0} ", po);
        }
        else
        {
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);
            Console.WriteLine();
            throw new Exception("Cannot process purchase order: " + po.PONumber);
        }
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted");
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Get MSMQ queue name from app settings in configuration.
        string queueName = ConfigurationManager.AppSettings["queueName"];

        // Create the transacted MSMQ queue if necessary.
        if (!System.Messaging.MessageQueue.Exists(queueName))
            System.Messaging.MessageQueue.Create(queueName, true);

        // Get the base address that is used to listen for WS-MetaDataExchange requests.
        // This is useful to generate a proxy for the client.
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        // Open the ServiceHostBase to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        if(serviceHost.State != CommunicationState.Faulted) {
            serviceHost.Close();
        }

    }
}
```

 <span data-ttu-id="4755b-149">Konfigurace služby zahrnuje následující vlastnosti nezpracovatelné zprávy: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`a `receiveErrorHandling`, jak je znázorněno v následujícím konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="4755b-149">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>
  </appSettings>
  <system.serviceModel>
    <services>
      <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"
                  binding="netMsmqBinding"
                  bindingConfiguration="PoisonBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <bindings>
      <netMsmqBinding>
        <binding name="PoisonBinding"
                 receiveRetryCount="0"
                 maxRetryCycles="1"
                 retryCycleDelay="00:00:05"
                 receiveErrorHandling="Move">
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="4755b-150">Zpracování zpráv z fronty nezpracovatelných zpráv</span><span class="sxs-lookup"><span data-stu-id="4755b-150">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="4755b-151">Služba nepoškozených zpráv čte zprávy z konečné fronty zpráv o nepoškozených zprávách a zpracovává je.</span><span class="sxs-lookup"><span data-stu-id="4755b-151">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="4755b-152">Zprávy ve frontě nepoškozených zpráv jsou zprávy, které jsou adresovány službě, která zpracovává zprávu, což se může lišit od koncového bodu služby zprávy o nepoškozeném provozu.</span><span class="sxs-lookup"><span data-stu-id="4755b-152">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="4755b-153">Proto když služba nepoškozených zpráv přečte zprávy z fronty, vrstva kanálu WCF nalezne neshodu v koncových bodech a neodešle zprávu.</span><span class="sxs-lookup"><span data-stu-id="4755b-153">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="4755b-154">V tomto případě je zpráva adresována službě zpracování objednávky, ale je přijímána službou nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="4755b-154">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="4755b-155">Chcete-li nadále přijímat zprávy i v případě, že je zpráva adresována jinému koncovému bodu, je nutné přidat `ServiceBehavior` pro filtrování adres, kde kritérium shody odpovídá jakémukoli koncovému bodu služby, na který je zpráva adresována.</span><span class="sxs-lookup"><span data-stu-id="4755b-155">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="4755b-156">Tato operace je nutná k úspěšnému zpracování zpráv přečtených z fronty nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="4755b-156">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="4755b-157">Samotná implementace služby nepoškozených zpráv je velmi podobná implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="4755b-157">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="4755b-158">Implementuje kontrakt a zpracuje objednávky.</span><span class="sxs-lookup"><span data-stu-id="4755b-158">It implements the contract and processes the orders.</span></span> <span data-ttu-id="4755b-159">Příklad kódu je následující.</span><span class="sxs-lookup"><span data-stu-id="4755b-159">The code example is as follows.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted...exiting app");
        Environment.Exit(1);
    }

    // Host the service within this EXE console application.
    public static void Main()
    {

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The poison message service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHostBase to shutdown the service.
        if(serviceHost.State != CommunicationState.Faulted)
        {
            serviceHost.Close();
        }
    }
```

 <span data-ttu-id="4755b-160">Na rozdíl od služby zpracování objednávek, která čte zprávy z fronty objednávek, služba nepoškozených zpráv čte zprávy z podfronty nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="4755b-160">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison sub-queue.</span></span> <span data-ttu-id="4755b-161">Nezpracovatelná fronta je dílčí frontou hlavní fronty, má název "jed" a generuje se automaticky pomocí služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4755b-161">The poison queue is a sub-queue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="4755b-162">Pokud k němu chcete získat přístup, zadejte název hlavní fronty následovaný ";" a názvem podfronty, v tomto případě "jed", jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4755b-162">To access it, provide the main queue name followed by a ";" and the sub-queue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="4755b-163">V ukázce pro službu MSMQ v 3.0 není název fronty nefungují jako Podfronta, nikoli do fronty, do které jste zprávu přesunuli.</span><span class="sxs-lookup"><span data-stu-id="4755b-163">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >
        </endpoint>
      </service>
    </services>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="4755b-164">Když spustíte ukázku, aktivity služby klienta, služby a nepoškozená zpráva se zobrazí v oknech konzoly.</span><span class="sxs-lookup"><span data-stu-id="4755b-164">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="4755b-165">Můžete vidět, že služba přijímá zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="4755b-165">You can see the service receive messages from the client.</span></span> <span data-ttu-id="4755b-166">V každém okně konzoly stiskněte klávesu ENTER a ukončete služby.</span><span class="sxs-lookup"><span data-stu-id="4755b-166">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="4755b-167">Služba se spustí, pořadí zpracování a náhodně se spustí pro ukončení zpracování.</span><span class="sxs-lookup"><span data-stu-id="4755b-167">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="4755b-168">Pokud zpráva indikuje, že zpracovala objednávku, můžete spustit klienta znovu a odeslat další zprávu, dokud se nezobrazí zpráva, že služba skutečně ukončila zprávu.</span><span class="sxs-lookup"><span data-stu-id="4755b-168">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="4755b-169">V závislosti na nakonfigurovaných nastaveních poškození se zpráva před přesunem do konečné fronty nezpracovatele vyzkouší pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="4755b-169">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
```

 <span data-ttu-id="4755b-170">Spusťte službu nezpracovatelných zpráv pro čtení poškozené zprávy z fronty poškození.</span><span class="sxs-lookup"><span data-stu-id="4755b-170">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="4755b-171">V tomto příkladu služba nepoškozených zpráv přečte zprávu a zpracuje ji.</span><span class="sxs-lookup"><span data-stu-id="4755b-171">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="4755b-172">Je možné, že se v případě nezpracovatele přečte objednávka, která byla ukončena a poškozená.</span><span class="sxs-lookup"><span data-stu-id="4755b-172">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4755b-173">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4755b-173">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="4755b-174">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4755b-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="4755b-175">Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4755b-175">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="4755b-176">Pokud fronta není přítomna, služba ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="4755b-176">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="4755b-177">Službu můžete nejdřív spustit, abyste mohli vytvořit frontu, nebo ji můžete vytvořit pomocí Správce fronty MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4755b-177">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="4755b-178">Pomocí těchto kroků vytvořte ve Windows 2008 frontu.</span><span class="sxs-lookup"><span data-stu-id="4755b-178">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="4755b-179">Otevřete Správce serveru v aplikaci Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="4755b-179">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="4755b-180">Rozbalte kartu **funkce** .</span><span class="sxs-lookup"><span data-stu-id="4755b-180">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="4755b-181">Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **Nový**, **soukromá fronta**.</span><span class="sxs-lookup"><span data-stu-id="4755b-181">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="4755b-182">Zaškrtněte políčko **transakční** .</span><span class="sxs-lookup"><span data-stu-id="4755b-182">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="4755b-183">Jako název nové fronty zadejte `ServiceModelSamplesTransacted`.</span><span class="sxs-lookup"><span data-stu-id="4755b-183">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="4755b-184">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4755b-184">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="4755b-185">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, změňte názvy front tak, aby odrážely skutečný název hostitele namísto názvu localhost, a postupujte podle pokynů v [části spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4755b-185">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

 <span data-ttu-id="4755b-186">Ve výchozím nastavení se u `netMsmqBinding` vazby vazeb povoluje zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4755b-186">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="4755b-187">Dvě vlastnosti, `MsmqAuthenticationMode` a `MsmqProtectionLevel`, společně určují typ zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="4755b-187">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="4755b-188">Ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="4755b-188">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="4755b-189">Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény.</span><span class="sxs-lookup"><span data-stu-id="4755b-189">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="4755b-190">Pokud tuto ukázku spustíte na počítači, který není součástí domény, zobrazí se následující chyba: "vnitřní certifikát služby Řízení front zpráv" neexistuje.</span><span class="sxs-lookup"><span data-stu-id="4755b-190">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="4755b-191">Spuštění ukázky na počítači připojeném k pracovní skupině</span><span class="sxs-lookup"><span data-stu-id="4755b-191">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="4755b-192">Pokud počítač není součástí domény, vypněte zabezpečení přenosu nastavením režimu ověřování a úrovně ochrany tak, aby `None`, jak je znázorněno v následující ukázkové konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="4755b-192">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="4755b-193">Nastavením atributu bindingConfiguration koncového bodu zajistěte, aby byl koncový bod přidružen k vazbě.</span><span class="sxs-lookup"><span data-stu-id="4755b-193">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="4755b-194">Před spuštěním ukázky se ujistěte, že jste změnili konfiguraci na PoisonMessageServer, serveru a klientovi.</span><span class="sxs-lookup"><span data-stu-id="4755b-194">Ensure that you change the configuration on the PoisonMessageServer, server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4755b-195">Nastavení `security mode` na `None` je ekvivalentem nastavení `MsmqAuthenticationMode`, `MsmqProtectionLevel`a `Message` zabezpečení na `None`.</span><span class="sxs-lookup"><span data-stu-id="4755b-195">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="4755b-196">Aby výměna metadat mohla fungovat, zaregistrujeme adresu URL s vazbou http.</span><span class="sxs-lookup"><span data-stu-id="4755b-196">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="4755b-197">To vyžaduje, aby se služba spouštěla v okně příkazového řádku se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="4755b-197">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="4755b-198">V opačném případě získáte výjimku, například: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span><span class="sxs-lookup"><span data-stu-id="4755b-198">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4755b-199">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="4755b-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4755b-200">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="4755b-200">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="4755b-201">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="4755b-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4755b-202">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4755b-202">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
