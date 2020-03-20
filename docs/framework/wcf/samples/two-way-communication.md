---
title: Obousměrná komunikace
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 56f789fe185cb2885c215e9512e82ae2fbb64a36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143756"
---
# <a name="two-way-communication"></a><span data-ttu-id="7b760-102">Obousměrná komunikace</span><span class="sxs-lookup"><span data-stu-id="7b760-102">Two-Way Communication</span></span>
<span data-ttu-id="7b760-103">Tato ukázka ukazuje, jak provádět transakční obousměrnou komunikaci ve frontě přes službu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7b760-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="7b760-104">Tato ukázka `netMsmqBinding` používá vazbu.</span><span class="sxs-lookup"><span data-stu-id="7b760-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="7b760-105">V tomto případě je služba aplikace konzoly s vlastním hostitelem, která umožňuje sledovat službu přijímající zprávy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="7b760-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b760-106">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7b760-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7b760-107">Tato ukázka je založena na [transacted MSMQ vazby](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="7b760-107">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="7b760-108">Ve frontové komunikaci klient komunikuje se službou pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="7b760-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="7b760-109">Klient odesílá zprávy do fronty a služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="7b760-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="7b760-110">Služba a klient proto nemusí být spuštěny současně komunikovat pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="7b760-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="7b760-111">Tato ukázka ukazuje obousměrnou komunikaci pomocí front.</span><span class="sxs-lookup"><span data-stu-id="7b760-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="7b760-112">Klient odešle nákupní objednávky do fronty z rozsahu transakce.</span><span class="sxs-lookup"><span data-stu-id="7b760-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="7b760-113">Služba přijímá objednávky, zpracovává objednávku a pak zavolá zpět klientovi se stavem objednávky z fronty v rámci transakce.</span><span class="sxs-lookup"><span data-stu-id="7b760-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="7b760-114">Pro usnadnění obousměrné komunikace klient i služba používají fronty k zařazení nákupních objednávek do fronty a stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="7b760-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="7b760-115">Servisní smlouva `IOrderProcessor` definuje jednosměrné operace služeb, které vyhovují použití fronty.</span><span class="sxs-lookup"><span data-stu-id="7b760-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="7b760-116">Operace služby zahrnuje koncový bod odpovědi, který se má použít k odeslání stavů objednávek.</span><span class="sxs-lookup"><span data-stu-id="7b760-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="7b760-117">Koncový bod odpovědi je identifikátor URI fronty pro odeslání stavu objednávky zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="7b760-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="7b760-118">Aplikace zpracování objednávky implementuje tuto smlouvu.</span><span class="sxs-lookup"><span data-stu-id="7b760-118">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="7b760-119">Kontrakt odpovědi na odeslání stavu objednávky je určen klientem.</span><span class="sxs-lookup"><span data-stu-id="7b760-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="7b760-120">Klient implementuje kontrakt stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="7b760-120">The client implements the order status contract.</span></span> <span data-ttu-id="7b760-121">Služba používá generovaný proxy serveru této smlouvy k odeslání stavu objednávky zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="7b760-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="7b760-122">Operace služby zpracovává odeslanou nákupní objednávku.</span><span class="sxs-lookup"><span data-stu-id="7b760-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="7b760-123">Použije <xref:System.ServiceModel.OperationBehaviorAttribute> se na operaci služby k určení automatického zařazení do transakce, která se používá k přijetí zprávy z fronty a automatického dokončení transakcí po dokončení operace služby.</span><span class="sxs-lookup"><span data-stu-id="7b760-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="7b760-124">Třída `Orders` zapouzdřuje funkce zpracování objednávek.</span><span class="sxs-lookup"><span data-stu-id="7b760-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="7b760-125">V tomto případě přidá nákupní objednávku do slovníku.</span><span class="sxs-lookup"><span data-stu-id="7b760-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="7b760-126">Transakce, která operace služby zapsána v je `Orders` k dispozici operace ve třídě.</span><span class="sxs-lookup"><span data-stu-id="7b760-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="7b760-127">Operace servisu kromě zpracování odeslané nákupní objednávky odpovídá klientovi zpět na stav objednávky.</span><span class="sxs-lookup"><span data-stu-id="7b760-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
{  
    Orders.Add(po);  
    Console.WriteLine("Processing {0} ", po);  
    Console.WriteLine("Sending back order status information");  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding("ClientCallbackBinding");  
    OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
  
    // Please note that the same transaction that is used to dequeue the purchase order is used  
    // to send back order status.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        client.OrderStatus(po.PONumber, po.Status);  
        scope.Complete();  
    }  
    //Close the client.  
    client.Close();  
}  
```

 <span data-ttu-id="7b760-128">Název fronty služby MSMQ je určen v části appSettings konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="7b760-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="7b760-129">Koncový bod služby je definován v části System.ServiceModel konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="7b760-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b760-130">Název fronty a adresa koncového bodu msmq používají mírně odlišné konvence adresování.</span><span class="sxs-lookup"><span data-stu-id="7b760-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="7b760-131">Název fronty msmq používá tečku (.) pro místní počítač a oddělovače zpětného lomítka v jeho cestě.</span><span class="sxs-lookup"><span data-stu-id="7b760-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="7b760-132">Adresa koncového bodu WCF (Windows Communication Foundation) určuje schéma net.msmq:, používá "localhost" pro místní počítač a používá lomítka v cestě.</span><span class="sxs-lookup"><span data-stu-id="7b760-132">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="7b760-133">Chcete-li číst z fronty, která je hostována ve vzdáleném počítači, nahraďte "." a "localhost" na název vzdáleného počítače.</span><span class="sxs-lookup"><span data-stu-id="7b760-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="7b760-134">Služba je hostována samostatně.</span><span class="sxs-lookup"><span data-stu-id="7b760-134">The service is self hosted.</span></span> <span data-ttu-id="7b760-135">Při použití přenosu služby MSMQ musí být použitá fronta vytvořena předem.</span><span class="sxs-lookup"><span data-stu-id="7b760-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="7b760-136">To lze provést ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="7b760-136">This can be done manually or through code.</span></span> <span data-ttu-id="7b760-137">V této ukázce služba zkontroluje existenci fronty a v případě potřeby ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="7b760-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="7b760-138">Název fronty se čte z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="7b760-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="7b760-139">Základní adresa se používá [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generovat proxy služby.</span><span class="sxs-lookup"><span data-stu-id="7b760-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from appSettings in configuration.  
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
    }  
}  
```

 <span data-ttu-id="7b760-140">Klient vytvoří transakci.</span><span class="sxs-lookup"><span data-stu-id="7b760-140">The client creates a transaction.</span></span> <span data-ttu-id="7b760-141">Komunikace s frontou probíhá v rámci transakce, což způsobuje, že je považována za atomovou jednotku, kde všechny zprávy úspěšné nebo neúspěšné.</span><span class="sxs-lookup"><span data-stu-id="7b760-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

```csharp
// Create a ServiceHost for the OrderStatus service type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
  
    // Open the ServiceHostBase to create listeners and start listening for order status messages.  
    serviceHost.Open();  
  
    // Create the purchase order.  
    ...  
  
    // Create a client with given client endpoint configuration.  
    OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        string hostName = Dns.GetHostName();  
  
        // Make a queued call to submit the purchase order.  
        client.SubmitPurchaseOrder(po, "net.msmq://" + hostName + "/private/ServiceModelSamplesTwo-way/OrderStatus");  
  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Close down the client.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHost to shutdown the service.  
    serviceHost.Close();  
}  
```

 <span data-ttu-id="7b760-142">Kód klienta implementuje smlouvu `IOrderStatus` pro příjem stavu objednávky ze služby.</span><span class="sxs-lookup"><span data-stu-id="7b760-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="7b760-143">V tomto případě vytiskne stav objednávky.</span><span class="sxs-lookup"><span data-stu-id="7b760-143">In this case, it prints out the order status.</span></span>  

```csharp
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ", poNumber ,
                                                           status);  
    }  
}  
```

 <span data-ttu-id="7b760-144">V metodě je vytvořena `Main` fronta stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="7b760-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="7b760-145">Konfigurace klienta zahrnuje konfiguraci služby stavu objednávky pro hostování služby stavu objednávky, jak je znázorněno v následující vzorové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="7b760-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
</appSettings>  
  
<system.serviceModel>  
  
  <services>  
    <service
       name="Microsoft.ServiceModel.Samples.OrderStatusService">  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
    </service>  
  </services>  
  
  <client>  
    <!-- Define NetMsmqEndpoint -->  
    <endpoint name="OrderProcessorEndpoint"  
              address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
              binding="netMsmqBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
  </client>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="7b760-146">Při spuštění ukázky jsou aktivity klienta a služby zobrazeny v systému Windows služby i klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="7b760-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="7b760-147">Můžete vidět službu přijímat zprávy od klienta.</span><span class="sxs-lookup"><span data-stu-id="7b760-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="7b760-148">Stisknutím klávesy ENTER v každém okně konzoly vypněte službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="7b760-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="7b760-149">Služba zobrazí informace o nákupní objednávce a označuje, že odesílá zpět stav objednávky do fronty stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="7b760-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 124a1f69-3699-4b16-9bcc-43147a8756fc  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Sending back order status information  
```  
  
 <span data-ttu-id="7b760-150">Klient zobrazí informace o stavu objednávky odeslané službou.</span><span class="sxs-lookup"><span data-stu-id="7b760-150">The client displays the order status information sent by the service.</span></span>  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7b760-151">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="7b760-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7b760-152">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7b760-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7b760-153">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7b760-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7b760-154">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7b760-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7b760-155">Pokud používáte Svcutil.exe k obnovení konfigurace pro tuto ukázku, nezapomeňte upravit názvy koncových bodů v konfiguraci klienta tak, aby odpovídaly kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="7b760-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="7b760-156">Ve výchozím <xref:System.ServiceModel.NetMsmqBinding>nastavení je povoleno zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="7b760-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="7b760-157">Existují dvě relevantní vlastnosti zabezpečení přenosu <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> služby MSMQ a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` `Windows` ve výchozím nastavení je `Sign`režim ověřování nastaven na a úroveň ochrany je nastavena na hodnotu .</span><span class="sxs-lookup"><span data-stu-id="7b760-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="7b760-158">Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény a musí být nainstalována možnost integrace služby Active Directory pro službu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7b760-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="7b760-159">Pokud spustíte tuto ukázku v počítači, který nesplňuje tato kritéria, zobrazí se chyba.</span><span class="sxs-lookup"><span data-stu-id="7b760-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="7b760-160">Spuštění ukázky v počítači připojovat se k pracovní skupině nebo bez integrace služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="7b760-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="7b760-161">Pokud počítač není součástí domény nebo není nainstalována integrace služby Active Directory, vypněte zabezpečení `None` přenosu nastavením režimu ověřování a úrovně ochrany na úroveň uvedenou v následující ukázkové konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="7b760-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <configuration>  
  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderProcessor" />  
      </appSettings>  
  
      <system.serviceModel>  
        <services>  
          <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding"
                      contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
2. <span data-ttu-id="7b760-162">Vypnutí zabezpečení konfigurace klienta generuje následující:</span><span class="sxs-lookup"><span data-stu-id="7b760-162">Turning off security for a client configuration generates the following:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
      </appSettings>  
  
      <system.serviceModel>  
  
        <services>  
          <service
             name="Microsoft.ServiceModel.Samples.OrderStatusService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding" contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
          </service>  
        </services>  
  
        <client>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint name="OrderProcessorEndpoint"  
                    address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
                    binding="netMsmqBinding"
                    bindingConfiguration="TransactedBinding"  
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        </client>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
3. <span data-ttu-id="7b760-163">Služba pro tuto ukázku vytvoří `OrderProcessorService`vazbu v .</span><span class="sxs-lookup"><span data-stu-id="7b760-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="7b760-164">Přidejte řádek kódu po vytvoření instance vazby pro nastavení `None`režimu zabezpečení na .</span><span class="sxs-lookup"><span data-stu-id="7b760-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. <span data-ttu-id="7b760-165">Před spuštěním ukázky se ujistěte, že změníte konfiguraci na serveru i na klientovi.</span><span class="sxs-lookup"><span data-stu-id="7b760-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7b760-166">Nastavení `security mode` `None` na je <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>ekvivalentní <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `Message` nastavení `None`nebo zabezpečení .</span><span class="sxs-lookup"><span data-stu-id="7b760-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7b760-167">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="7b760-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7b760-168">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="7b760-168">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7b760-169">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="7b760-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b760-170">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7b760-170">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
