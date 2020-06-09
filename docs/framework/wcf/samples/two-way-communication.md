---
title: Obousměrná komunikace
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 291380d656b0e22c7fdf1cb291c45d05359a95c8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591264"
---
# <a name="two-way-communication"></a><span data-ttu-id="26925-102">Obousměrná komunikace</span><span class="sxs-lookup"><span data-stu-id="26925-102">Two-Way Communication</span></span>
<span data-ttu-id="26925-103">Tato ukázka předvádí, jak provést transakční obousměrnou komunikaci přes službu MSMQ ve frontě.</span><span class="sxs-lookup"><span data-stu-id="26925-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="26925-104">Tato ukázka používá `netMsmqBinding` vazbu.</span><span class="sxs-lookup"><span data-stu-id="26925-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="26925-105">V tomto případě je tato služba samoobslužná Konzolová aplikace, která umožňuje sledovat službu přijímající zprávy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="26925-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26925-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="26925-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="26925-107">Tato ukázka je založená na [transakční vazbě služby MSMQ](transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="26925-107">This sample is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="26925-108">V komunikaci ve frontě klient komunikuje se službou pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="26925-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="26925-109">Klient odesílá zprávy do fronty a služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="26925-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="26925-110">Službu a klient proto nemusí běžet současně, aby bylo možné komunikovat pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="26925-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="26925-111">Tato ukázka předvádí obousměrnou komunikaci pomocí front.</span><span class="sxs-lookup"><span data-stu-id="26925-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="26925-112">Klient odesílá nákupní objednávky do fronty z rozsahu transakce.</span><span class="sxs-lookup"><span data-stu-id="26925-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="26925-113">Služba obdrží objednávky, zpracuje objednávku a pak zavolá zpět klienta se stavem pořadí z fronty v rámci rozsahu transakce.</span><span class="sxs-lookup"><span data-stu-id="26925-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="26925-114">Aby se usnadnila obousměrná komunikace klienta a služby, používají fronty k zařazování nákupních objednávek a stavu objednávek.</span><span class="sxs-lookup"><span data-stu-id="26925-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="26925-115">Kontrakt služby `IOrderProcessor` definuje jednosměrné operace služby, které vyhovují používání služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="26925-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="26925-116">Operace služby zahrnuje koncový bod odpovědi, který se použije k odeslání stavu objednávky na.</span><span class="sxs-lookup"><span data-stu-id="26925-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="26925-117">Koncový bod odpovědi je identifikátor URI fronty, který odesílá stav objednávky zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="26925-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="26925-118">Aplikace pro zpracování objednávek tuto smlouvu implementuje.</span><span class="sxs-lookup"><span data-stu-id="26925-118">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="26925-119">Klient zadá odpověď na odeslání stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="26925-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="26925-120">Klient implementuje kontrakt stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="26925-120">The client implements the order status contract.</span></span> <span data-ttu-id="26925-121">Služba používá vygenerovaný proxy server této smlouvy k odeslání stavu objednávky zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="26925-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="26925-122">Operace služby zpracuje odeslanou nákupní objednávku.</span><span class="sxs-lookup"><span data-stu-id="26925-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="26925-123">Se <xref:System.ServiceModel.OperationBehaviorAttribute> použije na operaci služby a určí automatické zařazení v transakci, která se používá k přijetí zprávy z fronty a automatickému dokončení transakcí při dokončení operace služby.</span><span class="sxs-lookup"><span data-stu-id="26925-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="26925-124">`Orders`Třída zapouzdřuje funkce zpracování objednávek.</span><span class="sxs-lookup"><span data-stu-id="26925-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="26925-125">V tomto případě přidá nákupní objednávku do slovníku.</span><span class="sxs-lookup"><span data-stu-id="26925-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="26925-126">Transakce, ve které je zapsána operace služby, je k dispozici pro operace ve `Orders` třídě.</span><span class="sxs-lookup"><span data-stu-id="26925-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="26925-127">Operace služby kromě zpracování odeslané nákupní objednávky odpoví zpátky na klienta ve stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="26925-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

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

 <span data-ttu-id="26925-128">Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="26925-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="26925-129">Koncový bod služby je definován v oddílu System. ServiceModel konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="26925-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26925-130">Název fronty MSMQ a adresa koncového bodu používají mírně odlišnou konvenci adres.</span><span class="sxs-lookup"><span data-stu-id="26925-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="26925-131">Název fronty MSMQ používá tečku (.) pro místní počítač a oddělovače zpětného lomítka v cestě.</span><span class="sxs-lookup"><span data-stu-id="26925-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="26925-132">Adresa koncového bodu služby Windows Communication Foundation (WCF) určuje položku NET. MSMQ: schéma, používá pro místní počítač localhost a v cestě používá lomítka.</span><span class="sxs-lookup"><span data-stu-id="26925-132">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="26925-133">Chcete-li číst z fronty hostované na vzdáleném počítači, nahraďte název vzdáleného počítače "." a "localhost".</span><span class="sxs-lookup"><span data-stu-id="26925-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="26925-134">Služba je hostována svým hostitelem.</span><span class="sxs-lookup"><span data-stu-id="26925-134">The service is self hosted.</span></span> <span data-ttu-id="26925-135">Při použití přenosu služby MSMQ musí být použitá fronta předem vytvořená.</span><span class="sxs-lookup"><span data-stu-id="26925-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="26925-136">To lze provést ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="26925-136">This can be done manually or through code.</span></span> <span data-ttu-id="26925-137">V této ukázce služba kontroluje existenci fronty a v případě potřeby ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="26925-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="26925-138">Název fronty se načte z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="26925-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="26925-139">Základní adresa je používána [nástrojem Svcutil. exe](../servicemodel-metadata-utility-tool-svcutil-exe.md) pro vygenerování proxy serveru ke službě.</span><span class="sxs-lookup"><span data-stu-id="26925-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

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

 <span data-ttu-id="26925-140">Klient vytvoří transakci.</span><span class="sxs-lookup"><span data-stu-id="26925-140">The client creates a transaction.</span></span> <span data-ttu-id="26925-141">Komunikace s frontou probíhá v rámci rozsahu transakce, což způsobuje, že se bude považovat za atomickou jednotku, ve které všechny zprávy budou úspěšné nebo neúspěšné.</span><span class="sxs-lookup"><span data-stu-id="26925-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

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

 <span data-ttu-id="26925-142">Klientský kód implementuje `IOrderStatus` kontrakt pro příjem stavu objednávky ze služby.</span><span class="sxs-lookup"><span data-stu-id="26925-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="26925-143">V tomto případě vytiskne stav objednávky.</span><span class="sxs-lookup"><span data-stu-id="26925-143">In this case, it prints out the order status.</span></span>  

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

 <span data-ttu-id="26925-144">V metodě je vytvořena fronta stavů pořadí `Main` .</span><span class="sxs-lookup"><span data-stu-id="26925-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="26925-145">Konfigurace klienta zahrnuje pořadí konfigurace stavové služby pro hostování služby stavu objednávky, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="26925-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="26925-146">Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta.</span><span class="sxs-lookup"><span data-stu-id="26925-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="26925-147">Můžete vidět, že služba přijímá zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="26925-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="26925-148">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="26925-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="26925-149">Služba zobrazí informace o objednávce nákupu a indikuje, že posílá zpět stav objednávky do fronty stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="26925-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
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
  
 <span data-ttu-id="26925-150">Klient zobrazí informace o stavu objednávky odesílané službou.</span><span class="sxs-lookup"><span data-stu-id="26925-150">The client displays the order status information sent by the service.</span></span>  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="26925-151">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="26925-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="26925-152">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="26925-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="26925-153">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="26925-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="26925-154">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="26925-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="26925-155">Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit názvy koncových bodů v konfiguraci klienta tak, aby odpovídaly kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="26925-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="26925-156">Ve výchozím nastavení <xref:System.ServiceModel.NetMsmqBinding> je zapnuto zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="26925-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="26925-157">Existují dvě důležité vlastnosti zabezpečení přenosu ve službě MSMQ <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` ve výchozím nastavení je režim ověřování nastaven na hodnotu `Windows` a úroveň ochrany je nastavena na hodnotu `Sign` .</span><span class="sxs-lookup"><span data-stu-id="26925-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="26925-158">Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény a musí být nainstalovaná možnost integrace služby Active Directory pro službu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="26925-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="26925-159">Pokud tuto ukázku spustíte na počítači, který nesplňuje tato kritéria, zobrazí se chyba.</span><span class="sxs-lookup"><span data-stu-id="26925-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="26925-160">Spuštění ukázky na počítači připojeném k pracovní skupině nebo bez integrace služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="26925-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="26925-161">Pokud počítač není součástí domény nebo nemáte nainstalovanou integraci služby Active Directory, vypněte zabezpečení přenosu nastavením režimu ověřování a úrovně ochrany tak, `None` jak je znázorněno v následující ukázkové konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="26925-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
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
  
2. <span data-ttu-id="26925-162">Vypnutí zabezpečení pro konfiguraci klienta generuje následující:</span><span class="sxs-lookup"><span data-stu-id="26925-162">Turning off security for a client configuration generates the following:</span></span>  
  
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
  
3. <span data-ttu-id="26925-163">Služba pro tuto ukázku vytvoří vazbu v `OrderProcessorService` .</span><span class="sxs-lookup"><span data-stu-id="26925-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="26925-164">Přidejte řádek kódu po vytvoření instance vazby pro nastavení režimu zabezpečení na `None` .</span><span class="sxs-lookup"><span data-stu-id="26925-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. <span data-ttu-id="26925-165">Před spuštěním ukázky se ujistěte, že jste změnili konfiguraci na serveru i v klientovi.</span><span class="sxs-lookup"><span data-stu-id="26925-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="26925-166">Nastavení `security mode` na `None` je ekvivalentní s nastavením <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> nebo `Message` zabezpečením na `None` .</span><span class="sxs-lookup"><span data-stu-id="26925-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="26925-167">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="26925-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="26925-168">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="26925-168">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="26925-169">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="26925-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="26925-170">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="26925-170">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
