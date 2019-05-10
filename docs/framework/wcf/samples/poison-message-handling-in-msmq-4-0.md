---
title: Zacházení s nezpracovatelnými zprávami v MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 86d42e567d6d0f2b306d4def6746d32bfe7c6ab4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664771"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="bdf97-102">Zacházení s nezpracovatelnými zprávami v MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="bdf97-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="bdf97-103">Tento příklad ukazuje, jak provádět zpracování ve službě nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="bdf97-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="bdf97-104">Tato ukázka je založena na [nepodporuje transakce vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="bdf97-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="bdf97-105">Tento příklad používá `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="bdf97-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="bdf97-106">Služba je v místním prostředí konzolovou aplikaci pro vám umožní sledovat službu přijímání zpráv zařazených do fronty.</span><span class="sxs-lookup"><span data-stu-id="bdf97-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="bdf97-107">V komunikaci ve frontě klient komunikuje se služby pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="bdf97-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="bdf97-108">Přesněji řečeno klient odešle zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="bdf97-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="bdf97-109">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="bdf97-109">The service receives messages from the queue.</span></span> <span data-ttu-id="bdf97-110">Klienta a služby, proto není potřeba běžet současně na komunikaci pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="bdf97-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="bdf97-111">Nezpracovatelná zpráva se zpráva, která opakovaně čte z fronty při čtení zprávy služby nelze zpracovat zprávu a proto ukončí transakce, pod kterým je pro čtení zprávy.</span><span class="sxs-lookup"><span data-stu-id="bdf97-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="bdf97-112">V takových případech je zpráva opakovat znovu.</span><span class="sxs-lookup"><span data-stu-id="bdf97-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="bdf97-113">To teoreticky přejít navždy Pokud dojde k nějakému problému s touto zprávou.</span><span class="sxs-lookup"><span data-stu-id="bdf97-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="bdf97-114">Všimněte si, že to může dojít pouze při použití transakcí čtení z fronty a vyvolat operaci služby.</span><span class="sxs-lookup"><span data-stu-id="bdf97-114">Note that this can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="bdf97-115">Založené na verzi služby MSMQ, NetMsmqBinding podporuje omezenou zjišťování pro úplné zjišťování nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="bdf97-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="bdf97-116">Po zprávy byl zjištěn, protože je poškozen, pak může být zpracována několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="bdf97-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="bdf97-117">Znovu založené na verzi služby MSMQ, NetMsmqBinding podporuje omezenou zpracování na úplné zpracování nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="bdf97-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="bdf97-118">Tato ukázka ilustruje omezený počet poškozených zařízení k dispozici na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platformy a úplné počet poškozených zařízení k dispozici na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bdf97-118">This sample illustrates the limited poison facilities provided on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platform and the full poison facilities provided on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="bdf97-119">V obou ukázky cílem je přesunout nezpracovatelná zpráva ven fronty do jiné fronty, který lze potom udržovat službou nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="bdf97-119">In both samples, the objective is move the poison message out of the queue to another queue which then can be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="bdf97-120">MSMQ 4.0 Poison zpracování vzorku</span><span class="sxs-lookup"><span data-stu-id="bdf97-120">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="bdf97-121">V [!INCLUDE[wv](../../../../includes/wv-md.md)], služby MSMQ obsahuje poškozené dílčí fronty zařízení, které slouží k ukládání nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="bdf97-121">In [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ provides a poison sub-queue facility that can be used to store poison messages.</span></span> <span data-ttu-id="bdf97-122">V této ukázce osvědčený postup řešení problémů s nezpracovatelných zpráv pomocí [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bdf97-122">This sample demonstrates the best practice of dealing with poison messages using [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="bdf97-123">Zjišťování nezpracovatelných zpráv v [!INCLUDE[wv](../../../../includes/wv-md.md)] je poměrně složité.</span><span class="sxs-lookup"><span data-stu-id="bdf97-123">The poison message detection in [!INCLUDE[wv](../../../../includes/wv-md.md)] is quite sophisticated.</span></span> <span data-ttu-id="bdf97-124">Existují 3 vlastností, které pomáhají s detekcí.</span><span class="sxs-lookup"><span data-stu-id="bdf97-124">There are 3 properties that help with detection.</span></span> <span data-ttu-id="bdf97-125"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Je málokdy danou zprávu je znovu čtení z fronty a odeslaného do aplikace pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="bdf97-125">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="bdf97-126">Opětovné načtení zprávy z fronty při přejde zpět do fronty, protože zprávu nelze odeslat do aplikace nebo aplikace vrátí zpět transakce v operaci služby.</span><span class="sxs-lookup"><span data-stu-id="bdf97-126">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="bdf97-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> je počet pokusů, které se zpráva bude přesunuta do fronty zkuste to znovu.</span><span class="sxs-lookup"><span data-stu-id="bdf97-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="bdf97-128">Když <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> je dosaženo, zpráva bude přesunuta do fronty zkuste to znovu.</span><span class="sxs-lookup"><span data-stu-id="bdf97-128">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="bdf97-129">Vlastnost <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> je časovou prodlevu, po jejímž uplynutí zpráva bude přesunuta z fronty opakování zpět do hlavní fronty.</span><span class="sxs-lookup"><span data-stu-id="bdf97-129">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="bdf97-130"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Nastaven na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="bdf97-130">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="bdf97-131">Zpráva se pokusilo znovu.</span><span class="sxs-lookup"><span data-stu-id="bdf97-131">The message is tried again.</span></span> <span data-ttu-id="bdf97-132">V případě, všechny pokusy o čtení zprávy, zprávu je označen jako poškozen.</span><span class="sxs-lookup"><span data-stu-id="bdf97-132">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="bdf97-133">Jakmile zprávu je označen jako poškozen, zprávu je řešeno podle nastavení v <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> výčtu.</span><span class="sxs-lookup"><span data-stu-id="bdf97-133">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="bdf97-134">Zdůrazňujeme možné hodnoty:</span><span class="sxs-lookup"><span data-stu-id="bdf97-134">To reiterate the possible values:</span></span>

- <span data-ttu-id="bdf97-135">Odolnost (výchozí): K selhání naslouchací proces a také hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="bdf97-135">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="bdf97-136">Přetažení: Chcete-li vyřadit zprávu.</span><span class="sxs-lookup"><span data-stu-id="bdf97-136">Drop: To drop the message.</span></span>

- <span data-ttu-id="bdf97-137">Přesuňte: Pro přesun zprávy do dílčí fronty nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="bdf97-137">Move: To move the message to the poison message sub-queue.</span></span> <span data-ttu-id="bdf97-138">Tato hodnota je dostupná jenom na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bdf97-138">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

- <span data-ttu-id="bdf97-139">Odmítnout: Odmítnout zprávu poslal zpět do fronty nedoručených zpráv odesílatele.</span><span class="sxs-lookup"><span data-stu-id="bdf97-139">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="bdf97-140">Tato hodnota je dostupná jenom na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bdf97-140">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="bdf97-141">Vzorek ukazuje použití `Move` dispozice pro nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="bdf97-141">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="bdf97-142">`Move` způsobí, že zpráva, kterou chcete přesunout do dílčí fronty poškozené.</span><span class="sxs-lookup"><span data-stu-id="bdf97-142">`Move` causes the message to move to the poison sub-queue.</span></span>

 <span data-ttu-id="bdf97-143">Kontrakt služby je `IOrderProcessor`, která definuje jednosměrné, který je vhodný pro použití s frontami služby.</span><span class="sxs-lookup"><span data-stu-id="bdf97-143">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="bdf97-144">Operace služby zobrazí zprávu s oznámením, že zpracování pořadí.</span><span class="sxs-lookup"><span data-stu-id="bdf97-144">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="bdf97-145">Abychom si předvedli funkci nezpracovatelná zpráva byla `SubmitPurchaseOrder` operace služby dojde k výjimce při vracení transakce na náhodných vyvolání služby.</span><span class="sxs-lookup"><span data-stu-id="bdf97-145">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to rollback the transaction on a random invocation of the service.</span></span> <span data-ttu-id="bdf97-146">To způsobí, že zpráva, kterou chcete vrátit zpět k frontě.</span><span class="sxs-lookup"><span data-stu-id="bdf97-146">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="bdf97-147">Nakonec zprávy je označena jako poison.</span><span class="sxs-lookup"><span data-stu-id="bdf97-147">Eventually the message is marked as poison.</span></span> <span data-ttu-id="bdf97-148">Nezpracovatelná zpráva přesunete nezpracovatelných dílčí fronta je nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="bdf97-148">The configuration is set to move the poison message to the poison sub-queue.</span></span>

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

 <span data-ttu-id="bdf97-149">Konfigurace služby obsahuje následující vlastnosti nezpracovatelných zpráv: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, a `receiveErrorHandling` jak je znázorněno v následující konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="bdf97-149">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

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

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="bdf97-150">Zpracování zpráv z fronty nezpracovatelných zpráv</span><span class="sxs-lookup"><span data-stu-id="bdf97-150">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="bdf97-151">Nezpracovatelná zpráva byla Služba čte zprávy z fronty konečné nezpracovatelných zpráv a zpracovává je.</span><span class="sxs-lookup"><span data-stu-id="bdf97-151">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="bdf97-152">Zprávy ve frontě nezpracovatelných zpráv jsou zprávy, které se tak vyřeší, službě, která zpracovává zprávu, která může být odlišné od koncového bodu služby nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="bdf97-152">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="bdf97-153">Proto když nezpracovatelná zpráva byla služba načte zprávy z fronty, vrstvy kanálu WCF vyhledá Neshoda v koncových bodů a není odeslání zprávy.</span><span class="sxs-lookup"><span data-stu-id="bdf97-153">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="bdf97-154">V tomto případě zprávy je určeno služba zpracování objednávky, ale je přijímáno službou nezpracovatelná zpráva byla.</span><span class="sxs-lookup"><span data-stu-id="bdf97-154">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="bdf97-155">Chcete-li pokračovat i v případě, že zprávy je určena k jinému koncovému bodu, zobrazí se zpráva, musí přidáme `ServiceBehavior` na filtr adresy, kde kritérium přiřazování je tak, aby odpovídaly libovolný koncový bod služby je určeno zprávy.</span><span class="sxs-lookup"><span data-stu-id="bdf97-155">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="bdf97-156">To se vyžaduje úspěšně zpracovávat zprávy, které načítají z fronty nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="bdf97-156">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="bdf97-157">Implementace služby nezpracovatelných zpráv, samotného je velmi podobný implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="bdf97-157">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="bdf97-158">Implementuje tento kontrakt a zpracovávat objednávky.</span><span class="sxs-lookup"><span data-stu-id="bdf97-158">It implements the contract and processes the orders.</span></span> <span data-ttu-id="bdf97-159">Příklad kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="bdf97-159">The code example is as follows.</span></span>

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

 <span data-ttu-id="bdf97-160">Na rozdíl od služby, která čte zprávy z fronty pořadí zpracování objednávek služba nezpracovatelných zpráv čte zprávy typu z nezpracovatelných dílčí fronty.</span><span class="sxs-lookup"><span data-stu-id="bdf97-160">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison sub-queue.</span></span> <span data-ttu-id="bdf97-161">Počet poškozených fronty je dílčí fronta hlavní fronty, má název "poison" a je automaticky generovaný službou MSMQ.</span><span class="sxs-lookup"><span data-stu-id="bdf97-161">The poison queue is a sub-queue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="bdf97-162">Chcete-li získat přístup, zadejte název hlavní frontou, za nímž následuje ";" a dílčí název fronty, v tomto případě – "nezpracovatelných", jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="bdf97-162">To access it, provide the main queue name followed by a ";" and the sub-queue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
>  <span data-ttu-id="bdf97-163">V ukázce pro službu MSMQ verze 3.0 název fronty nezpracovatelných není dílčí fronty, místo toho fronty, který jsme přesunuli zpráva, kterou chcete.</span><span class="sxs-lookup"><span data-stu-id="bdf97-163">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

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

 <span data-ttu-id="bdf97-164">Při spuštění ukázky klienta, služby a činnosti nezpracovatelná zpráva se zobrazí v oknech konzoly.</span><span class="sxs-lookup"><span data-stu-id="bdf97-164">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="bdf97-165">Můžete zobrazit přijetí zprávy služby z klienta.</span><span class="sxs-lookup"><span data-stu-id="bdf97-165">You can see the service receive messages from the client.</span></span> <span data-ttu-id="bdf97-166">Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí služby.</span><span class="sxs-lookup"><span data-stu-id="bdf97-166">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="bdf97-167">Spuštění spuštěný, zpracování objednávky a spustí náhodně k ukončení zpracování služby.</span><span class="sxs-lookup"><span data-stu-id="bdf97-167">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="bdf97-168">Pokud zpráva označuje, že nezpracuje pořadí, můžete spustit klienta znovu odeslat další zprávu, dokud neuvidíte, že služba byl ukončen ve skutečnosti zprávu.</span><span class="sxs-lookup"><span data-stu-id="bdf97-168">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="bdf97-169">Podle nakonfigurovaného nastavení nezpracovatelná zpráva zkusí se jednou pro zpracování před přesunutím do konečné nezpracovatelných fronty.</span><span class="sxs-lookup"><span data-stu-id="bdf97-169">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

```
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

 <span data-ttu-id="bdf97-170">Spusťte službu nezpracovatelná zpráva byla poškozená po zprávu z fronty nezpracovatelných číst.</span><span class="sxs-lookup"><span data-stu-id="bdf97-170">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="bdf97-171">V tomto příkladu služba nezpracovatelných zpráv přečte zprávu a zpracovává je.</span><span class="sxs-lookup"><span data-stu-id="bdf97-171">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="bdf97-172">Je možné, že uvidíte, že služba nezpracovatelných zpráv přečte nákupní objednávka, který byl ukončen a poškozen.</span><span class="sxs-lookup"><span data-stu-id="bdf97-172">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

```
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

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bdf97-173">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="bdf97-173">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="bdf97-174">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bdf97-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="bdf97-175">Pokud je služba spuštěna první, zkontroluje se tak, aby byl do fronty k dispozici.</span><span class="sxs-lookup"><span data-stu-id="bdf97-175">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="bdf97-176">Pokud fronta neexistuje, služba ho vytvoří.</span><span class="sxs-lookup"><span data-stu-id="bdf97-176">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="bdf97-177">Můžete spustit služba nejdřív vytvořte frontu nebo můžete vytvořit prostřednictvím Správce fronty MSMQ.</span><span class="sxs-lookup"><span data-stu-id="bdf97-177">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="bdf97-178">Postupujte podle těchto kroků můžete vytvořit frontu Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="bdf97-178">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="bdf97-179">Otevřete správce serveru v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="bdf97-179">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="bdf97-180">Rozbalte **funkce** kartu.</span><span class="sxs-lookup"><span data-stu-id="bdf97-180">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="bdf97-181">Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="bdf97-181">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="bdf97-182">Zkontrolujte, **transakční** pole.</span><span class="sxs-lookup"><span data-stu-id="bdf97-182">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="bdf97-183">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="bdf97-183">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="bdf97-184">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bdf97-184">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="bdf97-185">Spusťte ukázku v konfiguraci s jedním nebo více počítač, změňte názvy front, aby odrážel skutečný název hostitele, místo localhost a postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bdf97-185">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

 <span data-ttu-id="bdf97-186">Ve výchozím nastavení se `netMsmqBinding` vazby přenosu, zabezpečení je povolená.</span><span class="sxs-lookup"><span data-stu-id="bdf97-186">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="bdf97-187">Dvě vlastnosti `MsmqAuthenticationMode` a `MsmqProtectionLevel`, společně určují typ zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="bdf97-187">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="bdf97-188">Ve výchozím nastavení, režim ověřování nastaven na `Windows` a aby úroveň ochrany je nastavená na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="bdf97-188">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="bdf97-189">Pro službu MSMQ. k ověřování a podepisování funkce musí být součástí domény.</span><span class="sxs-lookup"><span data-stu-id="bdf97-189">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="bdf97-190">Pokud tuto ukázku spustit na počítači, který není součástí domény, zobrazí se následující chybová zpráva: "Certifikátu interní front uživatele neexistuje".</span><span class="sxs-lookup"><span data-stu-id="bdf97-190">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="bdf97-191">Ke spuštění ukázky na počítač připojen k pracovní skupině</span><span class="sxs-lookup"><span data-stu-id="bdf97-191">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="bdf97-192">Pokud počítač není součástí domény, vypněte zabezpečení přenosu nastavením úroveň ověření režimu a ochrany na `None` jak je znázorněno v následující ukázková konfigurace:</span><span class="sxs-lookup"><span data-stu-id="bdf97-192">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="bdf97-193">Zkontrolujte, že koncový bod je přidružen vazbu tak, že nastavíte atribut bindingConfiguration koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="bdf97-193">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="bdf97-194">Ujistěte se, že změníte konfiguraci PoisonMessageServer, server a klienta, před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="bdf97-194">Ensure that you change the configuration on the PoisonMessageServer, server and the client before you run the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="bdf97-195">Nastavení `security mode` k `None` je ekvivalentní nastavení `MsmqAuthenticationMode`, `MsmqProtectionLevel`, a `Message` zabezpečení `None`.</span><span class="sxs-lookup"><span data-stu-id="bdf97-195">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="bdf97-196">Aby Meta výměna dat pro práci můžeme zaregistrovat adresu URL s vazbou http.</span><span class="sxs-lookup"><span data-stu-id="bdf97-196">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="bdf97-197">To vyžaduje, že služba běžet v okně se zvýšenými oprávněními příkaz.</span><span class="sxs-lookup"><span data-stu-id="bdf97-197">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="bdf97-198">Jinak dojde k výjimce, jako: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span><span class="sxs-lookup"><span data-stu-id="bdf97-198">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bdf97-199">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="bdf97-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bdf97-200">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bdf97-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bdf97-201">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="bdf97-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bdf97-202">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="bdf97-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
