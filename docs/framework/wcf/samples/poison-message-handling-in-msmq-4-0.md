---
title: Zacházení s nezpracovatelnými zprávami v MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 4b662094923c85e825edcc9025a73f1a1b42cb9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144237"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="61553-102">Zacházení s nezpracovatelnými zprávami v MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="61553-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="61553-103">Tato ukázka ukazuje, jak provádět zpracování poškozená zpráva ve službě.</span><span class="sxs-lookup"><span data-stu-id="61553-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="61553-104">Tato ukázka je založena na [transacted MSMQ binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="61553-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="61553-105">Tato ukázka `netMsmqBinding`používá .</span><span class="sxs-lookup"><span data-stu-id="61553-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="61553-106">Služba je aplikace konzoly s vlastním hostitelem, která umožňuje sledovat službu přijímající zprávy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="61553-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="61553-107">Ve frontové komunikaci klient komunikuje se službou pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="61553-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="61553-108">Přesněji řečeno, klient odesílá zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="61553-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="61553-109">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="61553-109">The service receives messages from the queue.</span></span> <span data-ttu-id="61553-110">Služba a klient proto nemusí být spuštěny současně komunikovat pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="61553-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="61553-111">Poškozená zpráva je zpráva, která je opakovaně číst z fronty, když služba čtení zprávy nemůže zpracovat zprávu a proto ukončí transakci, pod kterou je zpráva číst.</span><span class="sxs-lookup"><span data-stu-id="61553-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="61553-112">V takových případech je zpráva zopakována znovu.</span><span class="sxs-lookup"><span data-stu-id="61553-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="61553-113">To může teoreticky pokračovat navždy, pokud je problém se zprávou.</span><span class="sxs-lookup"><span data-stu-id="61553-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="61553-114">K tomu může dojít pouze v případě, že pomocí transakcí číst z fronty a vyvolat operaci služby.</span><span class="sxs-lookup"><span data-stu-id="61553-114">This can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="61553-115">Na základě verze služby MSMQ podporuje netmsmqbinding omezenou detekci na úplnou detekci poškozená zpráva.</span><span class="sxs-lookup"><span data-stu-id="61553-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="61553-116">Poté, co byla zpráva zjištěna jako poškozená, může být zpracována několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="61553-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="61553-117">Opět na základě verze služby MSMQ netmsmqbinding podporuje omezené zpracování na úplné zpracování poškozená zprávy.</span><span class="sxs-lookup"><span data-stu-id="61553-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="61553-118">Tato ukázka ilustruje omezené jedovaté zařízení poskytované na platformě Windows Server 2003 a Windows XP a zařízení s úplným jevem, která jsou k dispozici v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="61553-118">This sample illustrates the limited poison facilities provided on Windows Server 2003 and Windows XP platform and the full poison facilities provided on Windows Vista.</span></span> <span data-ttu-id="61553-119">V obou ukázkách je cílem přesunout poškozenou zprávu z fronty do jiné fronty.</span><span class="sxs-lookup"><span data-stu-id="61553-119">In both samples, the objective is to move the poison message out of the queue to another queue.</span></span> <span data-ttu-id="61553-120">Tato fronta pak může být obsluhována službou poškozená zpráva.</span><span class="sxs-lookup"><span data-stu-id="61553-120">That queue can then be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="61553-121">Ukázka zpracování jedů vSMQ v4.0</span><span class="sxs-lookup"><span data-stu-id="61553-121">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="61553-122">V systému Windows Vista poskytuje služba MSMQ jedovaté podfronty, které lze použít k ukládání jedovacích zpráv.</span><span class="sxs-lookup"><span data-stu-id="61553-122">In Windows Vista, MSMQ provides a poison subqueue facility that can be used to store poison messages.</span></span> <span data-ttu-id="61553-123">Tato ukázka ukazuje osvědčené postupy zpracování jedovaté zprávy pomocí systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="61553-123">This sample demonstrates the best practice of dealing with poison messages using Windows Vista.</span></span>

 <span data-ttu-id="61553-124">Detekce poškozená zpráva v systému Windows Vista je sofistikovaná.</span><span class="sxs-lookup"><span data-stu-id="61553-124">The poison message detection in Windows Vista is sophisticated.</span></span> <span data-ttu-id="61553-125">Existují 3 vlastnosti, které pomáhají s detekcí.</span><span class="sxs-lookup"><span data-stu-id="61553-125">There are 3 properties that help with detection.</span></span> <span data-ttu-id="61553-126">Je <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> počet, kolikrát je daná zpráva znovu přečtena z fronty a odeslána do aplikace ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="61553-126">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="61553-127">Zpráva je znovu číst z fronty při jeho vrácení zpět do fronty, protože zpráva nemůže být odeslána do aplikace nebo aplikace vrátí transakci v operaci služby.</span><span class="sxs-lookup"><span data-stu-id="61553-127">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="61553-128"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>je počet přesunů zprávy do fronty opakování.</span><span class="sxs-lookup"><span data-stu-id="61553-128"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="61553-129">Po <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> dosažení je zpráva přesunuta do fronty opakování.</span><span class="sxs-lookup"><span data-stu-id="61553-129">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="61553-130">Vlastnost <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> je časová prodleva, po jejímž uplynutí je zpráva přesunuta z fronty opakování zpět do hlavní fronty.</span><span class="sxs-lookup"><span data-stu-id="61553-130">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="61553-131">Je <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> nastaven na 0.</span><span class="sxs-lookup"><span data-stu-id="61553-131">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="61553-132">Zpráva je zopakována.</span><span class="sxs-lookup"><span data-stu-id="61553-132">The message is tried again.</span></span> <span data-ttu-id="61553-133">Pokud všechny pokusy o čtení zprávy se nezdařily, je zpráva označena jako poškozená.</span><span class="sxs-lookup"><span data-stu-id="61553-133">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="61553-134">Jakmile je zpráva označena jako poškozená, zpráva je zpracována podle nastavení ve výčtu. <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A></span><span class="sxs-lookup"><span data-stu-id="61553-134">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="61553-135">Chcete-li zopakovat možné hodnoty:</span><span class="sxs-lookup"><span data-stu-id="61553-135">To reiterate the possible values:</span></span>

- <span data-ttu-id="61553-136">Chyba (výchozí): Chyba naslouchací proces a také hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="61553-136">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="61553-137">Přetažení: Chcete-li zprávu přetáhnout.</span><span class="sxs-lookup"><span data-stu-id="61553-137">Drop: To drop the message.</span></span>

- <span data-ttu-id="61553-138">Přesunout: Chcete-li přesunout zprávu do podfronty poškozená zpráva.</span><span class="sxs-lookup"><span data-stu-id="61553-138">Move: To move the message to the poison message subqueue.</span></span> <span data-ttu-id="61553-139">Tato hodnota je k dispozici pouze v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="61553-139">This value is available only on Windows Vista.</span></span>

- <span data-ttu-id="61553-140">Odmítnout: Chcete-li zprávu odmítnout, odešlete zprávu zpět do fronty nedoručených zpráv odesílatele.</span><span class="sxs-lookup"><span data-stu-id="61553-140">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="61553-141">Tato hodnota je k dispozici pouze v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="61553-141">This value is available only on Windows Vista.</span></span>

 <span data-ttu-id="61553-142">Ukázka ukazuje použití `Move` dispozice pro zprávu poison.</span><span class="sxs-lookup"><span data-stu-id="61553-142">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="61553-143">`Move`způsobí, že zpráva přesunout do podfronty poison.</span><span class="sxs-lookup"><span data-stu-id="61553-143">`Move` causes the message to move to the poison subqueue.</span></span>

 <span data-ttu-id="61553-144">Servisní smlouva `IOrderProcessor`je , která definuje jednosměrnou službu, která je vhodná pro použití s frontami.</span><span class="sxs-lookup"><span data-stu-id="61553-144">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="61553-145">Operace služby zobrazí zprávu oznamující, že zpracovává objednávku.</span><span class="sxs-lookup"><span data-stu-id="61553-145">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="61553-146">Chcete-li demonstrovat funkce `SubmitPurchaseOrder` poškozená zpráva, operace služby vyvolá výjimku vrátit zpět transakce na náhodné vyvolání služby.</span><span class="sxs-lookup"><span data-stu-id="61553-146">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to roll back the transaction on a random invocation of the service.</span></span> <span data-ttu-id="61553-147">To způsobí, že zpráva, která má být umístěna zpět do fronty.</span><span class="sxs-lookup"><span data-stu-id="61553-147">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="61553-148">Nakonec je zpráva označena jako jed.</span><span class="sxs-lookup"><span data-stu-id="61553-148">Eventually the message is marked as poison.</span></span> <span data-ttu-id="61553-149">Konfigurace je nastavena na přesunutí poškozená zpráva poison podfronty.</span><span class="sxs-lookup"><span data-stu-id="61553-149">The configuration is set to move the poison message to the poison subqueue.</span></span>

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

 <span data-ttu-id="61553-150">Konfigurace služby obsahuje následující vlastnosti `retryCycleDelay`poškozená `receiveErrorHandling` zpráva: `receiveRetryCount`, `maxRetryCycles`, a jak je znázorněno v následujícím konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="61553-150">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

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

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="61553-151">Zpracování zpráv z fronty poškozená zpráva</span><span class="sxs-lookup"><span data-stu-id="61553-151">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="61553-152">Služba poškozená zpráva čte zprávy z fronty konečných poškozená zpráva a zpracuje je.</span><span class="sxs-lookup"><span data-stu-id="61553-152">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="61553-153">Zprávy ve frontě poškozená zpráva jsou zprávy, které jsou určeny pro službu, která zpracovává zprávu, které se mohou lišit od koncového bodu služby poškozená zpráva.</span><span class="sxs-lookup"><span data-stu-id="61553-153">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="61553-154">Proto při službě poškozená zpráva čte zprávy z fronty, vrstva kanálu WCF najde neshodu v koncových bodech a neodešle zprávu.</span><span class="sxs-lookup"><span data-stu-id="61553-154">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="61553-155">V takovém případě je zpráva určena službě zpracování objednávek, ale je přijímána službou poškozená zpráva.</span><span class="sxs-lookup"><span data-stu-id="61553-155">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="61553-156">Chcete-li i nadále přijímat zprávy i v případě, že zpráva `ServiceBehavior` je určena k jinému koncovému bodu, musíme přidat do filtru adresy, kde je kritérium shody tak, aby odpovídaly všechny koncového bodu služby zpráva je určena.</span><span class="sxs-lookup"><span data-stu-id="61553-156">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="61553-157">To je nutné úspěšně zpracovat zprávy, které čtete z fronty poškozená zpráva.</span><span class="sxs-lookup"><span data-stu-id="61553-157">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="61553-158">Samotná implementace služby poškozená zpráva je velmi podobná implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="61553-158">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="61553-159">Implementuje smlouvu a zpracovává objednávky.</span><span class="sxs-lookup"><span data-stu-id="61553-159">It implements the contract and processes the orders.</span></span> <span data-ttu-id="61553-160">Příklad kódu je následující.</span><span class="sxs-lookup"><span data-stu-id="61553-160">The code example is as follows.</span></span>

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

 <span data-ttu-id="61553-161">Na rozdíl od služby zpracování objednávek, která čte zprávy z fronty objednávek, služba poškozená zpráva čte zprávy z podfronty poison.</span><span class="sxs-lookup"><span data-stu-id="61553-161">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison subqueue.</span></span> <span data-ttu-id="61553-162">Fronty je podfronty hlavní fronty, je s názvem "poison" a je automaticky generována služba MSMQ.</span><span class="sxs-lookup"><span data-stu-id="61553-162">The poison queue is a subqueue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="61553-163">Chcete-li k němu získat přístup, zadejte název hlavní fronty následovaný ";" a název podfronty, v tomto případě "poison", jak je znázorněno na následující ukázce konfigurace.</span><span class="sxs-lookup"><span data-stu-id="61553-163">To access it, provide the main queue name followed by a ";" and the subqueue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="61553-164">V ukázce pro službu MSMQ v3.0 není název fronty poison dílčí frontou, spíše frontou, do které jsme zprávu přesunuli.</span><span class="sxs-lookup"><span data-stu-id="61553-164">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

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

 <span data-ttu-id="61553-165">Při spuštění ukázky jsou v oknech konzoly zobrazeny aktivity služby klienta, služby a služby poškozená zpráva.</span><span class="sxs-lookup"><span data-stu-id="61553-165">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="61553-166">Můžete vidět službu přijímat zprávy od klienta.</span><span class="sxs-lookup"><span data-stu-id="61553-166">You can see the service receive messages from the client.</span></span> <span data-ttu-id="61553-167">Chcete-li služby vypnout stisknutím klávesy ENTER v každém okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="61553-167">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="61553-168">Služba se spustí, zpracování objednávek a náhodně začne ukončit zpracování.</span><span class="sxs-lookup"><span data-stu-id="61553-168">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="61553-169">Pokud zpráva označuje, že objednávku zpracoval, můžete klienta znovu spustit a odeslat další zprávu, dokud se nezobrazí, že služba skutečně ukončila zprávu.</span><span class="sxs-lookup"><span data-stu-id="61553-169">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="61553-170">Na základě nakonfigurované nastavení jepoškozen, zpráva se pokusí jednou pro zpracování před přesunutím do konečné fronty jed.</span><span class="sxs-lookup"><span data-stu-id="61553-170">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

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

 <span data-ttu-id="61553-171">Spusťte službu poškozená zpráva číst poškozenou zprávu z fronty poškozen.</span><span class="sxs-lookup"><span data-stu-id="61553-171">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="61553-172">V tomto příkladu služba poškozená zpráva přečte zprávu a zpracuje ji.</span><span class="sxs-lookup"><span data-stu-id="61553-172">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="61553-173">Můžete vidět, že nákupní objednávka, která byla ukončena a otrávena, je přečtena službou poškozená zpráva.</span><span class="sxs-lookup"><span data-stu-id="61553-173">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

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

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="61553-174">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="61553-174">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="61553-175">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="61553-175">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="61553-176">Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici.</span><span class="sxs-lookup"><span data-stu-id="61553-176">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="61553-177">Pokud fronta není k dispozici, služba ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="61553-177">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="61553-178">Nejprve můžete spustit službu a vytvořit frontu, nebo ji můžete vytvořit pomocí Správce front služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="61553-178">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="61553-179">Vytvořenífronty v systému Windows 2008 postupujte takto.</span><span class="sxs-lookup"><span data-stu-id="61553-179">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="61553-180">Otevřete Správce serveru v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="61553-180">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="61553-181">Rozbalte kartu **Funkce.**</span><span class="sxs-lookup"><span data-stu-id="61553-181">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="61553-182">Klepněte pravým tlačítkem myši na **položku Fronty soukromých zpráv**a vyberte příkaz **Nová**, **Soukromá fronta**.</span><span class="sxs-lookup"><span data-stu-id="61553-182">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="61553-183">Zaškrtněte políčko **Transakční** transakce.</span><span class="sxs-lookup"><span data-stu-id="61553-183">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="61553-184">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="61553-184">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="61553-185">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="61553-185">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="61553-186">Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, změňte názvy front tak, aby odrážely skutečný název hostitele namísto localhost a postupujte podle pokynů v [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="61553-186">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

 <span data-ttu-id="61553-187">Ve výchozím `netMsmqBinding` nastavení s přenosem vazby je povoleno zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="61553-187">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="61553-188">Dvě `MsmqAuthenticationMode` vlastnosti `MsmqProtectionLevel`a společně určují typ zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="61553-188">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="61553-189">Ve výchozím nastavení je režim `Windows` ověřování nastaven na `Sign`hodnotu a úroveň ochrany je nastavena na hodnotu .</span><span class="sxs-lookup"><span data-stu-id="61553-189">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="61553-190">Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény.</span><span class="sxs-lookup"><span data-stu-id="61553-190">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="61553-191">Pokud spustíte tuto ukázku v počítači, který není součástí domény, zobrazí se následující chyba: "Interní certifikát fronty zpráv uživatele neexistuje".</span><span class="sxs-lookup"><span data-stu-id="61553-191">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="61553-192">Spuštění ukázky v počítači připojovato k pracovní skupině</span><span class="sxs-lookup"><span data-stu-id="61553-192">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="61553-193">Pokud počítač není součástí domény, vypněte zabezpečení přenosu nastavením režimu `None` ověřování a úrovně ochrany na úroveň uvedenou v následující ukázkové konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="61553-193">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="61553-194">Ujistěte se, že koncový bod je přidružen k vazbě nastavením atributu vazby koncového boduConfiguration.</span><span class="sxs-lookup"><span data-stu-id="61553-194">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="61553-195">Ujistěte se, že změníte konfiguraci na PoisonMessageServer, server a klient před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="61553-195">Ensure that you change the configuration on the PoisonMessageServer, server, and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="61553-196">Nastavení `security mode` `None` na je `MsmqAuthenticationMode`ekvivalentní `MsmqProtectionLevel`nastavení `Message` a `None`zabezpečení .</span><span class="sxs-lookup"><span data-stu-id="61553-196">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="61553-197">Aby Meta Data Exchange fungovala, zaregistrujeme adresu URL s vazbou http.</span><span class="sxs-lookup"><span data-stu-id="61553-197">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="61553-198">To vyžaduje, aby služba spuštěna v okně příkazu se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="61553-198">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="61553-199">V opačném případě se dostanete `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`výjimku, například: .</span><span class="sxs-lookup"><span data-stu-id="61553-199">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="61553-200">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="61553-200">The samples may already be installed on your computer.</span></span> <span data-ttu-id="61553-201">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="61553-201">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="61553-202">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="61553-202">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="61553-203">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="61553-203">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
