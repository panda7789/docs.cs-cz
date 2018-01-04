---
title: "Zpracované vazby služby MSMQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
caps.latest.revision: "50"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 702f3ac45ade5fcd2f37d256ce1213a79f012ae3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="transacted-msmq-binding"></a><span data-ttu-id="5ee16-102">Zpracované vazby služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="5ee16-102">Transacted MSMQ Binding</span></span>
<span data-ttu-id="5ee16-103">Tento příklad ukazuje, jak provést zpracovaných komunikace ve frontě pomocí služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="5ee16-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ee16-104">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="5ee16-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5ee16-105">V komunikaci ve frontě klient komunikuje se služby pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="5ee16-105">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="5ee16-106">Přesněji řečeno klient odešle zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="5ee16-106">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="5ee16-107">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="5ee16-107">The service receives messages from the queue.</span></span> <span data-ttu-id="5ee16-108">Službu a klienta, proto nemusíte používat současně na komunikaci pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="5ee16-108">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="5ee16-109">Pokud transakce se používají k odesílání a přijímání zpráv, jsou ve skutečnosti dvě samostatné transakce.</span><span class="sxs-lookup"><span data-stu-id="5ee16-109">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="5ee16-110">Když klient odešle zprávy v rámci oboru transakce, transakce je místní pro klienta a fronty správce klienta.</span><span class="sxs-lookup"><span data-stu-id="5ee16-110">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="5ee16-111">Když služba přijímá zprávy v rámci oboru transakce, transakce je místní služby a využívá správce fronty.</span><span class="sxs-lookup"><span data-stu-id="5ee16-111">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="5ee16-112">Je důležité si pamatovat, klient a služba nejsou součástí stejné transakci; různé transakce místo toho používají při provádění operací (například odesílat a přijímat) s fronty.</span><span class="sxs-lookup"><span data-stu-id="5ee16-112">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>  
  
 <span data-ttu-id="5ee16-113">V této ukázce klient odešle dávku zpráv do služby z v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="5ee16-113">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="5ee16-114">Služba v rámci oboru transakce definované ve službě jsou pak přijímá zprávy odeslané do fronty.</span><span class="sxs-lookup"><span data-stu-id="5ee16-114">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>  
  
 <span data-ttu-id="5ee16-115">Kontrakt služby je `IOrderProcessor`, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="5ee16-115">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="5ee16-116">Rozhraní definuje jednosměrné služby, který je vhodný pro použití s front.</span><span class="sxs-lookup"><span data-stu-id="5ee16-116">The interface defines a one-way service that is suitable for use with queues.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 <span data-ttu-id="5ee16-117">Chování služby definuje chování operaci s `TransactionScopeRequired` nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="5ee16-117">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="5ee16-118">To zajistí, že je žádné správci prostředků přístup metodu použít stejný obor transakce, který se používá k načtení zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="5ee16-118">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="5ee16-119">Také zaručuje, že pokud metoda vyvolá výjimku, bude vráceno do fronty.</span><span class="sxs-lookup"><span data-stu-id="5ee16-119">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="5ee16-120">Bez nastavení toto chování operace, zařazených do fronty kanál vytvoří transakci čtení zprávy ve frontě a provede ji automaticky před odesláním tak, že pokud se operace nezdaří, dojde ke ztrátě zprávy.</span><span class="sxs-lookup"><span data-stu-id="5ee16-120">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="5ee16-121">Nejběžnější scénáře je pro operace služby zařazení v transakci, která slouží k načtení zprávy z fronty, jak je ukázáno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5ee16-121">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>  
  
```  
 // This service class that implements the service contract.  
 // This added code writes output to the console window.  
 public class OrderProcessorService : IOrderProcessor  
 {  
     [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
     public void SubmitPurchaseOrder(PurchaseOrder po)  
     {  
         Orders.Add(po);  
         Console.WriteLine("Processing {0} ", po);  
     }  
  …  
}  
```  
  
 <span data-ttu-id="5ee16-122">Služba je sám sebou hostované.</span><span class="sxs-lookup"><span data-stu-id="5ee16-122">The service is self hosted.</span></span> <span data-ttu-id="5ee16-123">Pokud používáte přenos MSMQ, používá fronty musí být vytvořeny předem.</span><span class="sxs-lookup"><span data-stu-id="5ee16-123">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="5ee16-124">Tento krok můžete provést ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="5ee16-124">This can be done manually or through code.</span></span> <span data-ttu-id="5ee16-125">V této ukázce služby obsahuje kód kontrolovat existenci fronty a vytvořit frontu, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="5ee16-125">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="5ee16-126">Název fronty je číst z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5ee16-126">The queue name is read from the configuration file.</span></span> <span data-ttu-id="5ee16-127">Základní adresa se používá [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování proxy ke službě.</span><span class="sxs-lookup"><span data-stu-id="5ee16-127">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  
  
```  
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get the MSMQ queue name from appSettings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderProcessorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shut down the service.  
        serviceHost.Close();  
    }  
}  
```  
  
 <span data-ttu-id="5ee16-128">Název fronty služby MSMQ je zadaný v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5ee16-128">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="5ee16-129">Název fronty používá tečku (.) pro místní počítač a oddělovačů zpětné lomítko, v cestě, při vytváření fronty pomocí <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="5ee16-129">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="5ee16-130">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Koncový bod používá adresu fronty s schéma net.msmq, používá "localhost" k označení místního počítače, a používá předávání lomítka v jeho cesty.</span><span class="sxs-lookup"><span data-stu-id="5ee16-130">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>  
  
 <span data-ttu-id="5ee16-131">Klient vytvoří oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="5ee16-131">The client creates a transaction scope.</span></span> <span data-ttu-id="5ee16-132">Komunikace s fronty probíhá v rámci oboru transakce, příčinou je považován za atomické jednotky, kde jsou všechny zprávy odeslané do fronty nebo žádné zprávy jsou odesílány do fronty.</span><span class="sxs-lookup"><span data-stu-id="5ee16-132">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="5ee16-133">Transakce se potvrdí voláním <xref:System.Transactions.TransactionScope.Complete%2A> v oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="5ee16-133">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>  
  
```  
// Create a client.  
OrderProcessorClient client = new OrderProcessorClient();  
  
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
  
// Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Make a queued call to submit the purchase order.  
    client.SubmitPurchaseOrder(po);  
    // Complete the transaction.  
    scope.Complete();  
}  
  
// Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="5ee16-134">Pokud chcete ověřit, že transakce funguje, měnit klienta, a jak je znázorněno v následujícím ukázkovém kódu komentářů oboru transakce, znovu sestavte řešení a spuštění klienta.</span><span class="sxs-lookup"><span data-stu-id="5ee16-134">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>  
  
```  
//scope.Complete();  
```  
  
 <span data-ttu-id="5ee16-135">Protože transakce není dokončena, nejsou zprávy odeslané do fronty.</span><span class="sxs-lookup"><span data-stu-id="5ee16-135">Because the transaction is not completed, the messages are not sent to the queue.</span></span>  
  
 <span data-ttu-id="5ee16-136">Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="5ee16-136">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="5ee16-137">Uvidíte služby přijmout zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="5ee16-137">You can see the service receive messages from the client.</span></span> <span data-ttu-id="5ee16-138">Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="5ee16-138">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="5ee16-139">Všimněte si, že vzhledem k tomu, že služby Řízení front se používá, klient a služba nemusí být spuštěná ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="5ee16-139">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="5ee16-140">Spuštění klienta, vypněte ho a potom spuštění služby a stále obdrží zprávy.</span><span class="sxs-lookup"><span data-stu-id="5ee16-140">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 7b31ce51-ae7c-4def-9b8b-617e4288eafd  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5ee16-141">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="5ee16-141">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5ee16-142">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5ee16-142">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5ee16-143">Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty.</span><span class="sxs-lookup"><span data-stu-id="5ee16-143">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="5ee16-144">Pokud fronta neexistuje, vytvoří služba jeden.</span><span class="sxs-lookup"><span data-stu-id="5ee16-144">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="5ee16-145">Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5ee16-145">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="5ee16-146">Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="5ee16-146">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="5ee16-147">Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5ee16-147">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="5ee16-148">Rozbalte **funkce** kartě.</span><span class="sxs-lookup"><span data-stu-id="5ee16-148">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="5ee16-149">Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="5ee16-149">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="5ee16-150">Zkontrolujte **transakcí** pole.</span><span class="sxs-lookup"><span data-stu-id="5ee16-150">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="5ee16-151">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="5ee16-151">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="5ee16-152">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5ee16-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="5ee16-153">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5ee16-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="5ee16-154">Ve výchozím nastavení se <xref:System.ServiceModel.NetMsmqBinding>, je povoleno zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="5ee16-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="5ee16-155">Existují dvě vlastnosti důležité pro zabezpečení přenosu služby MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="5ee16-155">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="5ee16-156">Ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="5ee16-156">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="5ee16-157">Pro služby MSMQ k ověřování a podepisování funkce musí být součástí domény a možnost integrace služby Active Directory pro službu MSMQ musí být nainstalován.</span><span class="sxs-lookup"><span data-stu-id="5ee16-157">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="5ee16-158">Pokud tuto ukázku spustit na počítači, který nesplňuje tato kritéria, obdržíte chybu.</span><span class="sxs-lookup"><span data-stu-id="5ee16-158">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="5ee16-159">Ke spuštění ukázky na počítač připojen k pracovní skupině nebo bez integrace služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="5ee16-159">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>  
  
1.  <span data-ttu-id="5ee16-160">Pokud počítač není součástí domény nebo nemá nainstalované integrační služby Active Directory, vypněte zabezpečení přenosu podle nastavení úrovně režim a ochrany ověřování na `None` jak je znázorněno v následujícím ukázkovém kódu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5ee16-160">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderProcessorService"  
                 behaviorConfiguration="OrderProcessorServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint. -->  
          <endpoint  
              address="net.msmq://localhost/private/ServiceModelSamplesTransacted"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <!-- The mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex. -->  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="OrderProcessorServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="5ee16-161">Ujistěte se, změnit konfiguraci na serveru a klienta, před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="5ee16-161">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5ee16-162">Nastavení `security``mode` k `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, a `Message` zabezpečení `None`.</span><span class="sxs-lookup"><span data-stu-id="5ee16-162">Setting `security``mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5ee16-163">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="5ee16-163">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5ee16-164">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="5ee16-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5ee16-165">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="5ee16-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5ee16-166">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5ee16-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`  
  
## <a name="see-also"></a><span data-ttu-id="5ee16-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ee16-167">See Also</span></span>
