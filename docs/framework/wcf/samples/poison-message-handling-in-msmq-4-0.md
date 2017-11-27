---
title: "Zacházení s nezpracovatelnými zprávami v MSMQ 4.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 910ebf0952d4a2399447de7442046eb0fe90060e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="7f892-102">Zacházení s nezpracovatelnými zprávami v MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="7f892-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="7f892-103">Tento příklad znázorňuje postup zpracování ve službě poškozených zpráv.</span><span class="sxs-lookup"><span data-stu-id="7f892-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="7f892-104">Tato ukázka je založena na [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="7f892-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="7f892-105">V tomto příkladu `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="7f892-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="7f892-106">Služba je vlastním hostováním konzolové aplikace, které vám umožňují sledovat službu přijetí zprávy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="7f892-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
 <span data-ttu-id="7f892-107">V komunikaci ve frontě klient komunikuje se služby pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="7f892-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="7f892-108">Přesněji řečeno klient odešle zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="7f892-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="7f892-109">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="7f892-109">The service receives messages from the queue.</span></span> <span data-ttu-id="7f892-110">Služba a klient proto nemusíte používat současně na komunikaci pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="7f892-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="7f892-111">Nezpracovatelná zpráva je zpráva, která je opakovaně pro čtení z fronty při čtení zprávy služby nelze zpracovat zprávu a proto ukončí transakce, pod kterým je zpráva pro čtení.</span><span class="sxs-lookup"><span data-stu-id="7f892-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="7f892-112">V takových případech je zpráva opakovat znovu.</span><span class="sxs-lookup"><span data-stu-id="7f892-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="7f892-113">To může teoreticky, přejděte na navždy Pokud došlo k potížím se zprávou.</span><span class="sxs-lookup"><span data-stu-id="7f892-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="7f892-114">Všimněte si, že to může dojít pouze při použití transakce čtení z fronty a volat operace služby.</span><span class="sxs-lookup"><span data-stu-id="7f892-114">Note that this can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>  
  
 <span data-ttu-id="7f892-115">Na základě verze služby MSMQ, – NetMsmqBinding podporuje omezenou zjišťování pro úplné zjišťování poškozených zpráv.</span><span class="sxs-lookup"><span data-stu-id="7f892-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="7f892-116">Po zpráva byla zjištěna jako poškozen, pak může ošetřit několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="7f892-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="7f892-117">Znovu podle verze služby MSMQ, – NetMsmqBinding podporuje omezenou zpracování úplné zpracování poškozených zpráv.</span><span class="sxs-lookup"><span data-stu-id="7f892-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>  
  
 <span data-ttu-id="7f892-118">Tato ukázka znázorňuje omezené poškozených zařízení, které jsou na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platformy a úplné poškozených zařízení, které jsou na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f892-118">This sample illustrates the limited poison facilities provided on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platform and the full poison facilities provided on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="7f892-119">V obou ukázky cílem je přesunout nezpracovatelná zpráva fronty do jiné fronty, která pak můžete obsloužení služba poškozených zpráv.</span><span class="sxs-lookup"><span data-stu-id="7f892-119">In both samples, the objective is move the poison message out of the queue to another queue which then can be serviced by a poison message service.</span></span>  
  
## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="7f892-120">MSMQ v4.0 Poison zpracování vzorku</span><span class="sxs-lookup"><span data-stu-id="7f892-120">MSMQ v4.0 Poison Handling Sample</span></span>  
 <span data-ttu-id="7f892-121">V [!INCLUDE[wv](../../../../includes/wv-md.md)], budovy poškozených dílčí fronty, který slouží k uložení poškozených zpráv poskytuje služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7f892-121">In [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ provides a poison sub-queue facility that can be used to store poison messages.</span></span> <span data-ttu-id="7f892-122">Tento příklad znázorňuje osvědčený postup, který se zabývá poškozených zpráv pomocí [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f892-122">This sample demonstrates the best practice of dealing with poison messages using [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>  
  
 <span data-ttu-id="7f892-123">Detekce nezpracovatelná zpráva v [!INCLUDE[wv](../../../../includes/wv-md.md)] je poměrně složité.</span><span class="sxs-lookup"><span data-stu-id="7f892-123">The poison message detection in [!INCLUDE[wv](../../../../includes/wv-md.md)] is quite sophisticated.</span></span> <span data-ttu-id="7f892-124">Existují 3 vlastností, které pomáhají s detekce.</span><span class="sxs-lookup"><span data-stu-id="7f892-124">There are 3 properties that help with detection.</span></span> <span data-ttu-id="7f892-125"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Je počet časech danou zprávu znovu čtení z fronty a odeslat do aplikace pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="7f892-125">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="7f892-126">Znovu načtení zprávy z fronty při jeho je vrátit zpět do fronty protože zprávu nelze odeslat do aplikace nebo aplikaci vrátí zpět transakci v operaci služby.</span><span class="sxs-lookup"><span data-stu-id="7f892-126">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="7f892-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>je počet, kolikrát zpráva bude přesunuta do fronty opakování.</span><span class="sxs-lookup"><span data-stu-id="7f892-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="7f892-128">Když <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> je dosaženo, zpráva bude přesunuta do fronty opakování.</span><span class="sxs-lookup"><span data-stu-id="7f892-128">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="7f892-129">Vlastnost <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> je prodlevu, po jejímž uplynutí zpráva bude přesunuta z fronty opakování zpět do hlavní fronty.</span><span class="sxs-lookup"><span data-stu-id="7f892-129">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="7f892-130"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Nastaven na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="7f892-130">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="7f892-131">Zpráva se pokus o znovu.</span><span class="sxs-lookup"><span data-stu-id="7f892-131">The message is tried again.</span></span> <span data-ttu-id="7f892-132">Pokud mají všechny pokusy o tuto zprávu přečíst, zprávy jsou označeny jako poškozen.</span><span class="sxs-lookup"><span data-stu-id="7f892-132">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>  
  
 <span data-ttu-id="7f892-133">Jakmile zprávy je označena jako poškozen, zpráva se zabývá podle nastavení v <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> výčtu.</span><span class="sxs-lookup"><span data-stu-id="7f892-133">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="7f892-134">Chcete-li znovu opakují možné hodnoty:</span><span class="sxs-lookup"><span data-stu-id="7f892-134">To reiterate the possible values:</span></span>  
  
-   <span data-ttu-id="7f892-135">Selhání (výchozí): na poruch naslouchací proces a taky hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="7f892-135">Fault (default): To fault the listener and also the service host.</span></span>  
  
-   <span data-ttu-id="7f892-136">Přetažení: Chcete-li vyřadit zprávu.</span><span class="sxs-lookup"><span data-stu-id="7f892-136">Drop: To drop the message.</span></span>  
  
-   <span data-ttu-id="7f892-137">Přesunutí: Přesunout zprávu do fronty dílčí poškozená zpráva.</span><span class="sxs-lookup"><span data-stu-id="7f892-137">Move: To move the message to the poison message sub-queue.</span></span> <span data-ttu-id="7f892-138">Tato hodnota je k dispozici pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f892-138">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>  
  
-   <span data-ttu-id="7f892-139">Odmítnutí: Tak, aby zamítal zprávy, poslal zpět do odesílatele je nedoručených zpráv fronty.</span><span class="sxs-lookup"><span data-stu-id="7f892-139">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="7f892-140">Tato hodnota je k dispozici pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f892-140">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>  
  
 <span data-ttu-id="7f892-141">Ukázka ukazuje, jak pomocí `Move` dispozice pro poškozená zpráva.</span><span class="sxs-lookup"><span data-stu-id="7f892-141">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="7f892-142">`Move`způsobí, že zpráva, kterou chcete přesunout do poškozených dílčí fronty.</span><span class="sxs-lookup"><span data-stu-id="7f892-142">`Move` causes the message to move to the poison sub-queue.</span></span>  
  
 <span data-ttu-id="7f892-143">Kontrakt služby je `IOrderProcessor`, která definuje jednosměrné služby, který je vhodný pro použití s front.</span><span class="sxs-lookup"><span data-stu-id="7f892-143">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 <span data-ttu-id="7f892-144">Operace služby zobrazí zprávu s oznámením, že pořadí zpracování.</span><span class="sxs-lookup"><span data-stu-id="7f892-144">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="7f892-145">K předvedení funkci nezpracovatelná zpráva `SubmitPurchaseOrder` operace služby vyvolá výjimku pro vrácení transakce u náhodných volání služby.</span><span class="sxs-lookup"><span data-stu-id="7f892-145">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to rollback the transaction on a random invocation of the service.</span></span> <span data-ttu-id="7f892-146">To způsobí, že zpráva, která má být vrátit zpět ve frontě.</span><span class="sxs-lookup"><span data-stu-id="7f892-146">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="7f892-147">Nakonec zprávy je označena jako poison.</span><span class="sxs-lookup"><span data-stu-id="7f892-147">Eventually the message is marked as poison.</span></span> <span data-ttu-id="7f892-148">Konfigurace je nastavena na poškozených zprávu přesunout do poškozených dílčí fronty.</span><span class="sxs-lookup"><span data-stu-id="7f892-148">The configuration is set to move the poison message to the poison sub-queue.</span></span>  
  
```  
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
  
 <span data-ttu-id="7f892-149">Konfigurace služby obsahuje následující vlastnosti nezpracovatelná zpráva: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, a `receiveErrorHandling` jak je znázorněno v následujícím souboru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7f892-149">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>  
  
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
  
## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="7f892-150">Zpracování zpráv z fronty poškozených zpráv</span><span class="sxs-lookup"><span data-stu-id="7f892-150">Processing messages from the poison message queue</span></span>  
 <span data-ttu-id="7f892-151">Služba poškozených zpráv čte zprávy z fronty konečné poškozených zpráv a zpracovává je.</span><span class="sxs-lookup"><span data-stu-id="7f892-151">The poison message service reads messages from the final poison message queue and processes them.</span></span>  
  
 <span data-ttu-id="7f892-152">Zprávy ve frontě nezpracovatelná zpráva jsou zprávy adresované do služby, která zpracovává zprávu, která může lišit od koncový bod služby nezpracovatelná zpráva.</span><span class="sxs-lookup"><span data-stu-id="7f892-152">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="7f892-153">Proto při službu nezpracovatelná zpráva čte zprávy z fronty [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vrstvy kanálu najde neshody v koncových bodů a není odeslat zprávu.</span><span class="sxs-lookup"><span data-stu-id="7f892-153">Therefore, when the poison message service reads messages from the queue, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="7f892-154">V takovém případě zprávy je řešit pořadí zpracování služby, ale je přijímání službou poškozená zpráva.</span><span class="sxs-lookup"><span data-stu-id="7f892-154">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="7f892-155">Pokud chcete pokračovat i v případě, že zpráva je určena k jinému koncovému bodu, zobrazí se zpráva, musí přidáme `ServiceBehavior` filtru adresy, kde je kritérium přiřazování tak, aby odpovídaly žádný koncový bod služby je určeno zprávy.</span><span class="sxs-lookup"><span data-stu-id="7f892-155">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="7f892-156">To je nutné úspěšně zpracovat zprávy, které můžete číst zprávy z fronty poškozená zpráva.</span><span class="sxs-lookup"><span data-stu-id="7f892-156">This is required to successfully process messages that you read from the poison message queue.</span></span>  
  
 <span data-ttu-id="7f892-157">Implementace služby nezpracovatelná zpráva, samotné je velmi podobné implementace služby.</span><span class="sxs-lookup"><span data-stu-id="7f892-157">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="7f892-158">Implementuje kontrakt a zpracovává objednávky.</span><span class="sxs-lookup"><span data-stu-id="7f892-158">It implements the contract and processes the orders.</span></span> <span data-ttu-id="7f892-159">Tady je příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="7f892-159">The code example is as follows.</span></span>  
  
```  
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
  
 <span data-ttu-id="7f892-160">Na rozdíl od pořadí služby, který čte zprávy z fronty pořadí zpracování služba poškozených zpráv čte zprávy typu z poškozených dílčí fronty.</span><span class="sxs-lookup"><span data-stu-id="7f892-160">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison sub-queue.</span></span> <span data-ttu-id="7f892-161">Poškozených fronty je dílčí fronta hlavní fronty, má název "poison" a je automaticky generovaný službou MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7f892-161">The poison queue is a sub-queue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="7f892-162">K přístupu, zadejte název fronty, za nímž následuje ";" a dílčí název fronty, v takovém případě-"poškozených", jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7f892-162">To access it, provide the main queue name followed by a ";" and the sub-queue name, in this case -"poison", as shown in the following sample configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f892-163">V ukázce pro MSMQ v3.0 název poškozených fronty není dílčí fronta, místo fronta, kterou jsme přesunout zprávu, která se.</span><span class="sxs-lookup"><span data-stu-id="7f892-163">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>  
  
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
  
 <span data-ttu-id="7f892-164">Při spuštění vzorového klienta, služby a služby aktivity nezpracovatelná zpráva se zobrazí v konzole windows.</span><span class="sxs-lookup"><span data-stu-id="7f892-164">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="7f892-165">Uvidíte služby přijmout zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="7f892-165">You can see the service receive messages from the client.</span></span> <span data-ttu-id="7f892-166">Stisknutím klávesy ENTER v každé okna konzoly vypnutí služby.</span><span class="sxs-lookup"><span data-stu-id="7f892-166">Press ENTER in each console window to shut down the services.</span></span>  
  
 <span data-ttu-id="7f892-167">Služba spustí spuštěna, zpracování objednávky a náhodně spustí ukončit zpracování.</span><span class="sxs-lookup"><span data-stu-id="7f892-167">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="7f892-168">Pokud zpráva indikuje, že zpracovala pořadí, můžete spustit klienta znovu odeslat další zprávu, až se, že služba byl ukončen ve skutečnosti zprávu.</span><span class="sxs-lookup"><span data-stu-id="7f892-168">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="7f892-169">Podle nakonfigurovaného nastavení poškozených, zpráva se pokus o jednou pro zpracování před přesunutím do konečné poškozených fronty.</span><span class="sxs-lookup"><span data-stu-id="7f892-169">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>  
  
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
  
 <span data-ttu-id="7f892-170">Spuštění služby nezpracovatelná zpráva poškozená po zprávu přečíst z poškozených fronty.</span><span class="sxs-lookup"><span data-stu-id="7f892-170">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="7f892-171">V tomto příkladu službu nezpracovatelná zpráva přečte zprávu a procesy.</span><span class="sxs-lookup"><span data-stu-id="7f892-171">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="7f892-172">By mohli zobrazit, že je služba nezpracovatelná zpráva pro čtení nákupní objednávka, která byla ukončena a poškozen.</span><span class="sxs-lookup"><span data-stu-id="7f892-172">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7f892-173">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="7f892-173">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7f892-174">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f892-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7f892-175">Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty.</span><span class="sxs-lookup"><span data-stu-id="7f892-175">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="7f892-176">Pokud fronta neexistuje, vytvoří služba jeden.</span><span class="sxs-lookup"><span data-stu-id="7f892-176">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="7f892-177">Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7f892-177">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="7f892-178">Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="7f892-178">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="7f892-179">Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f892-179">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="7f892-180">Rozbalte **funkce** kartě.</span><span class="sxs-lookup"><span data-stu-id="7f892-180">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="7f892-181">Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="7f892-181">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="7f892-182">Zkontrolujte **transakcí** pole.</span><span class="sxs-lookup"><span data-stu-id="7f892-182">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="7f892-183">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="7f892-183">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="7f892-184">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f892-184">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="7f892-185">Chcete-li v konfiguraci s jednou nebo mezi počítači spustit ukázku, změňte názvy fronty, aby odrážel skutečný název hostitele místo localhost a postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f892-185">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="7f892-186">Ve výchozím nastavení se `netMsmqBinding` vazby přenos, zabezpečení je povoleno.</span><span class="sxs-lookup"><span data-stu-id="7f892-186">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="7f892-187">Dvě vlastnosti `MsmqAuthenticationMode` a `MsmqProtectionLevel`, společně určují typ zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="7f892-187">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="7f892-188">Ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="7f892-188">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="7f892-189">Pro MSMQ k ověřování a podepisování funkce musí být součástí domény.</span><span class="sxs-lookup"><span data-stu-id="7f892-189">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="7f892-190">Pokud tuto ukázku spustit na počítači, který není součástí domény, můžete dojít k následující chybě: "Uživatele interní zpráv služby Řízení front certifikát neexistuje".</span><span class="sxs-lookup"><span data-stu-id="7f892-190">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>  
  
#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="7f892-191">Ke spuštění ukázky na počítače připojeného k pracovní skupině</span><span class="sxs-lookup"><span data-stu-id="7f892-191">To run the sample on a computer joined to a workgroup</span></span>  
  
1.  <span data-ttu-id="7f892-192">Pokud počítač není součástí domény, vypněte zabezpečení přenosu podle nastavení úrovně režim a ochrany ověřování na `None` jak je znázorněno v následující ukázka konfigurace:</span><span class="sxs-lookup"><span data-stu-id="7f892-192">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding name="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="7f892-193">Zajistěte, aby že koncový bod je přidružen vazby nastavením atributu bindingConfiguration pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="7f892-193">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>  
  
2.  <span data-ttu-id="7f892-194">Ujistěte se, že změníte konfiguraci PoisonMessageServer, serveru a klienta, před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="7f892-194">Ensure that you change the configuration on the PoisonMessageServer, server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7f892-195">Nastavení `security mode` k `None` je ekvivalentní nastavení `MsmqAuthenticationMode`, `MsmqProtectionLevel`, a `Message` zabezpečení `None`.</span><span class="sxs-lookup"><span data-stu-id="7f892-195">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3.  <span data-ttu-id="7f892-196">Aby výměny dat Meta pracovat jsme zaregistrovat adresu URL s vazbou http.</span><span class="sxs-lookup"><span data-stu-id="7f892-196">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="7f892-197">To vyžaduje, aby služba spuštěna v okně zvýšenými oprávněními příkaz.</span><span class="sxs-lookup"><span data-stu-id="7f892-197">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="7f892-198">Jinak dojde k výjimce, jako: neošetřená výjimka: System.ServiceModel.AddressAccessDeniedException: HTTP nebylo možné zaregistrovat http://+:8000/ServiceModelSamples/service/ adresy URL.</span><span class="sxs-lookup"><span data-stu-id="7f892-198">Otherwise, you get an exception such as: Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/.</span></span> <span data-ttu-id="7f892-199">Váš proces nemá přístupová práva na tento obor názvů (viz http://go.microsoft.com/fwlink/?LinkId=70353 podrobnosti).</span><span class="sxs-lookup"><span data-stu-id="7f892-199">Your process does not have access rights to this namespace (see http://go.microsoft.com/fwlink/?LinkId=70353 for details).</span></span> <span data-ttu-id="7f892-200">---> System.Net.HttpListenerException: přístup byl odepřen.</span><span class="sxs-lookup"><span data-stu-id="7f892-200">---> System.Net.HttpListenerException: Access is denied.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7f892-201">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="7f892-201">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7f892-202">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="7f892-202">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7f892-203">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="7f892-203">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7f892-204">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7f892-204">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`  
  
## <a name="see-also"></a><span data-ttu-id="7f892-205">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f892-205">See Also</span></span>
