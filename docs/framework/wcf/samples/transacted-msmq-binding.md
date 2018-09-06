---
title: Zpracované vazby služby MSMQ
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: 381304bcef40245bac882a4fe4ae18a6998665cf
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43875720"
---
# <a name="transacted-msmq-binding"></a><span data-ttu-id="1b119-102">Zpracované vazby služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="1b119-102">Transacted MSMQ Binding</span></span>
<span data-ttu-id="1b119-103">Tento příklad znázorňuje způsob provedení transakčního komunikaci ve frontě pomocí služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="1b119-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b119-104">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="1b119-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1b119-105">V komunikaci ve frontě klient komunikuje se služby pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="1b119-105">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="1b119-106">Přesněji řečeno klient odešle zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="1b119-106">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="1b119-107">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="1b119-107">The service receives messages from the queue.</span></span> <span data-ttu-id="1b119-108">Služby a klienta, proto není potřeba běžet současně na komunikaci pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="1b119-108">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="1b119-109">Když transakce se používají k odesílání a příjem zpráv, se ve skutečnosti dvě samostatné transakce.</span><span class="sxs-lookup"><span data-stu-id="1b119-109">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="1b119-110">Když klient odešle zprávy v rámci oboru transakce, transakce je místní pro klienta a klient správce fronty.</span><span class="sxs-lookup"><span data-stu-id="1b119-110">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="1b119-111">Když služba přijímá zprávy v rámci oboru transakce, transakce je místní pro službu a využívá správce fronty.</span><span class="sxs-lookup"><span data-stu-id="1b119-111">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="1b119-112">Je velmi dobré si uvědomit, že klient a služba nenachází v rámci jedné transakce; Místo toho které využívají jiné transakce při provádění operací (například odesílání a příjem) s frontou.</span><span class="sxs-lookup"><span data-stu-id="1b119-112">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>  
  
 <span data-ttu-id="1b119-113">V této ukázce klient odešle dávku zpráv ke službě z v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="1b119-113">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="1b119-114">Služby v rámci oboru transakce definovány službou pak přijme zprávy odeslané do fronty.</span><span class="sxs-lookup"><span data-stu-id="1b119-114">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>  
  
 <span data-ttu-id="1b119-115">Kontrakt služby je `IOrderProcessor`, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="1b119-115">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="1b119-116">Rozhraní definuje jednosměrné, který je vhodný pro použití s frontami služby.</span><span class="sxs-lookup"><span data-stu-id="1b119-116">The interface defines a one-way service that is suitable for use with queues.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 <span data-ttu-id="1b119-117">Definuje chování služby na chování operace s `TransactionScopeRequired` nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="1b119-117">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="1b119-118">Tím se zajistí, že všechny správce prostředků přistupovat pomocí metody používají stejný obor transakcí, která se používá k načtení zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="1b119-118">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="1b119-119">Také zaručuje, že pokud metoda vyvolá výjimku, se vrátí zprávu do fronty.</span><span class="sxs-lookup"><span data-stu-id="1b119-119">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="1b119-120">Bez nastavení tohoto chování operace kanálu ve frontě vytvoří transakce čtení zprávy z fronty a potvrdí ji automaticky před odesláním tak, že pokud se operace nezdaří, dojde ke ztrátě zprávy.</span><span class="sxs-lookup"><span data-stu-id="1b119-120">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="1b119-121">Nejběžnější scénář je pro operace služby k zařazení v transakci, která slouží k načtení zprávy z fronty, jak je ukázáno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1b119-121">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>  

```csharp
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

 <span data-ttu-id="1b119-122">Tato služba je vlastní hostované.</span><span class="sxs-lookup"><span data-stu-id="1b119-122">The service is self hosted.</span></span> <span data-ttu-id="1b119-123">Při použití přenosu služby MSMQ, fronty, používá se musí vytvořit předem.</span><span class="sxs-lookup"><span data-stu-id="1b119-123">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="1b119-124">To můžete udělat ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="1b119-124">This can be done manually or through code.</span></span> <span data-ttu-id="1b119-125">V této ukázce služby obsahuje kód pro provedení kontroly existence fronty a vytvořit frontu, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="1b119-125">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="1b119-126">Název fronty načítají z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="1b119-126">The queue name is read from the configuration file.</span></span> <span data-ttu-id="1b119-127">Základní adresa je používána [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generovat proxy ke službě.</span><span class="sxs-lookup"><span data-stu-id="1b119-127">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

```csharp
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

 <span data-ttu-id="1b119-128">Název fronty MSMQ je zadat v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1b119-128">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="1b119-129">Název fronty používá tečku (.) pro místní počítače a zpětné lomítko oddělovače v cestě při vytvoření fronty pomocí <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="1b119-129">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="1b119-130">Koncový bod služby Windows Communication Foundation (WCF) používá adresa fronty s schéma net.msmq, používá "localhost" k označení místním počítači a používá lomítek v cestě.</span><span class="sxs-lookup"><span data-stu-id="1b119-130">The Windows Communication Foundation (WCF) endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>  
  
 <span data-ttu-id="1b119-131">Klient vytvoří obor transakce.</span><span class="sxs-lookup"><span data-stu-id="1b119-131">The client creates a transaction scope.</span></span> <span data-ttu-id="1b119-132">Komunikace s frontou probíhá v rámci oboru transakcí, vyvolá zacházet jako atomickou jednotku, kde jsou všechny zprávy odeslané do fronty nebo jsou žádné zprávy odeslané do fronty.</span><span class="sxs-lookup"><span data-stu-id="1b119-132">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="1b119-133">Transakce se potvrdí při volání <xref:System.Transactions.TransactionScope.Complete%2A> v oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="1b119-133">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>  

```csharp
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

 <span data-ttu-id="1b119-134">Pokud chcete ověřit, že transakce fungují, upravte klienta tak, že komentování obor transakcí, jak je znázorněno v následujícím ukázkovém kódu, znovu sestavte řešení a spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="1b119-134">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>  

```csharp
//scope.Complete();  
```

 <span data-ttu-id="1b119-135">Protože transakce není dokončena, nejsou odesílány zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="1b119-135">Because the transaction is not completed, the messages are not sent to the queue.</span></span>  
  
 <span data-ttu-id="1b119-136">Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="1b119-136">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="1b119-137">Můžete zobrazit přijetí zprávy služby z klienta.</span><span class="sxs-lookup"><span data-stu-id="1b119-137">You can see the service receive messages from the client.</span></span> <span data-ttu-id="1b119-138">Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="1b119-138">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="1b119-139">Mějte na paměti, protože služba Řízení front se používá, klient a služba nemusí být zprovoznit ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="1b119-139">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="1b119-140">Můžete spustit klienta, vypněte ho a spusťte službu a stále přijímá zprávy.</span><span class="sxs-lookup"><span data-stu-id="1b119-140">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1b119-141">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="1b119-141">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1b119-142">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1b119-142">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1b119-143">Pokud je služba spuštěna první, zkontroluje se tak, aby byl do fronty k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1b119-143">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="1b119-144">Pokud fronta neexistuje, služba ho vytvoří.</span><span class="sxs-lookup"><span data-stu-id="1b119-144">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="1b119-145">Můžete spustit služba nejdřív vytvořte frontu nebo můžete vytvořit prostřednictvím Správce fronty MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1b119-145">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="1b119-146">Postupujte podle těchto kroků můžete vytvořit frontu Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="1b119-146">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="1b119-147">Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b119-147">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="1b119-148">Rozbalte **funkce** kartu.</span><span class="sxs-lookup"><span data-stu-id="1b119-148">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="1b119-149">Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **nový**, **soukromou frontu**.</span><span class="sxs-lookup"><span data-stu-id="1b119-149">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="1b119-150">Zkontrolujte, **transakční** pole.</span><span class="sxs-lookup"><span data-stu-id="1b119-150">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="1b119-151">Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.</span><span class="sxs-lookup"><span data-stu-id="1b119-151">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="1b119-152">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1b119-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="1b119-153">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1b119-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="1b119-154">Ve výchozím nastavení se <xref:System.ServiceModel.NetMsmqBinding>, je povoleno zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="1b119-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="1b119-155">Existují dvě vlastnosti důležité pro zabezpečení přenosu služby MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="1b119-155">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="1b119-156">Ve výchozím nastavení, režim ověřování nastaven na `Windows` a aby úroveň ochrany je nastavená na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="1b119-156">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="1b119-157">Pro službu MSMQ. k ověřování a podepisování funkce musí být součástí domény a možnost integrace služby Active Directory pro službu MSMQ musí být nainstalována.</span><span class="sxs-lookup"><span data-stu-id="1b119-157">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="1b119-158">Pokud tuto ukázku spustit na počítači, který tato kritéria nesplňuje, zobrazí se chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="1b119-158">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="1b119-159">Ke spuštění ukázky na počítač připojen k pracovní skupině nebo bez integrace služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="1b119-159">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>  
  
1.  <span data-ttu-id="1b119-160">Pokud počítač není součástí domény nebo nemá nainstalované integrace služby Active Directory, vypněte zabezpečení přenosu nastavením úroveň ověření režimu a ochrany na `None` jak je znázorněno v následujícím ukázkovém kódu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1b119-160">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>  
  
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
  
2.  <span data-ttu-id="1b119-161">Ujistěte se, že změníte konfiguraci na serveru a klienta, před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="1b119-161">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1b119-162">Nastavení `security``mode` k `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, a `Message` zabezpečení `None`.</span><span class="sxs-lookup"><span data-stu-id="1b119-162">Setting `security``mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1b119-163">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="1b119-163">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1b119-164">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="1b119-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1b119-165">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="1b119-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1b119-166">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1b119-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`  
  
## <a name="see-also"></a><span data-ttu-id="1b119-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b119-167">See Also</span></span>
