---
title: Obousměrná komunikace
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 319b63ff1eefdab4c23932294c3f1970f204601e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786151"
---
# <a name="two-way-communication"></a><span data-ttu-id="723bb-102">Obousměrná komunikace</span><span class="sxs-lookup"><span data-stu-id="723bb-102">Two-Way Communication</span></span>
<span data-ttu-id="723bb-103">Tento příklad ukazuje, jak provádět transakční obousměrná komunikace ve frontě prostřednictvím služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="723bb-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="723bb-104">Tento příklad používá `netMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="723bb-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="723bb-105">V tomto případě služba není v místním prostředí konzolovou aplikaci, která umožňuje sledovat službu přijímání zpráv zařazených do fronty.</span><span class="sxs-lookup"><span data-stu-id="723bb-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="723bb-106">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="723bb-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="723bb-107">Tato ukázka je založena na [nepodporuje transakce vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="723bb-107">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="723bb-108">V komunikaci ve frontě klient komunikuje se služby pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="723bb-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="723bb-109">Klient odešle zprávy do fronty a služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="723bb-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="723bb-110">Klienta a služby, proto není potřeba běžet současně na komunikaci pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="723bb-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="723bb-111">V této ukázce 2 způsob komunikace pomocí front.</span><span class="sxs-lookup"><span data-stu-id="723bb-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="723bb-112">Klient odešle do fronty z v rámci oboru transakce nákupních objednávek.</span><span class="sxs-lookup"><span data-stu-id="723bb-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="723bb-113">Službu přijímá objednávky, objednávku zpracovává a pak zavolá zpět klientovi se stavem pořadí z fronty v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="723bb-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="723bb-114">Pro usnadnění obousměrná komunikace klienta a služby pomocí fronty zařadit nákupních objednávek a stav objednávky.</span><span class="sxs-lookup"><span data-stu-id="723bb-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="723bb-115">Kontrakt služby `IOrderProcessor` definuje operace jednosměrné služby, které vyhovují využívání služby Řízení front.</span><span class="sxs-lookup"><span data-stu-id="723bb-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="723bb-116">Operace služby obsahuje koncový bod odpověď pro odeslání objednávky stavy.</span><span class="sxs-lookup"><span data-stu-id="723bb-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="723bb-117">Koncový bod odpověď je identifikátor URI fronty pro odeslání objednávky stavu zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="723bb-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="723bb-118">Pořadí zpracování aplikace implementuje tento kontrakt.</span><span class="sxs-lookup"><span data-stu-id="723bb-118">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="723bb-119">Klient je uveden kontrakt odpověď k odeslání stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="723bb-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="723bb-120">Klient implementuje tento kontrakt stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="723bb-120">The client implements the order status contract.</span></span> <span data-ttu-id="723bb-121">Služba používá k odeslání objednávky stavu zpět do klienta vygenerovaný proxy server této smlouvy.</span><span class="sxs-lookup"><span data-stu-id="723bb-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="723bb-122">Operace služby odeslané nákupní objednávku zpracovává.</span><span class="sxs-lookup"><span data-stu-id="723bb-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="723bb-123"><xref:System.ServiceModel.OperationBehaviorAttribute> Se použije pro operace služby k určení automatické zařazení v transakci, která se používá k přijetí zprávy z fronty a automatické dokončování transakcí při dokončení operace služby.</span><span class="sxs-lookup"><span data-stu-id="723bb-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="723bb-124">`Orders` Třídy zapouzdřuje funkce zpracování objednávky.</span><span class="sxs-lookup"><span data-stu-id="723bb-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="723bb-125">V takovém případě nákupní objednávku přidá do slovníku.</span><span class="sxs-lookup"><span data-stu-id="723bb-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="723bb-126">Operace služby uveden v transakci je k dispozici s operacemi `Orders` třídy.</span><span class="sxs-lookup"><span data-stu-id="723bb-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="723bb-127">Operace služby, kromě odeslané nákupní objednávky, odešle odpověď zpět do klienta o stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="723bb-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

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

 <span data-ttu-id="723bb-128">Název fronty MSMQ je zadán v oddílu appSettings konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="723bb-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="723bb-129">Koncový bod služby je definován v oddíle System.ServiceModel konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="723bb-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="723bb-130">Adresa název a koncový bod fronty MSMQ používají mírně odlišná adresování konvence.</span><span class="sxs-lookup"><span data-stu-id="723bb-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="723bb-131">Název fronty MSMQ používá tečku (.) pro místní počítače a zpětné lomítko oddělovače v cestě.</span><span class="sxs-lookup"><span data-stu-id="723bb-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="723bb-132">Určuje adresu koncového bodu služby Windows Communication Foundation (WCF) net.msmq: schéma, používá "localhost" pro místní počítač a v jeho cesty používá lomítka.</span><span class="sxs-lookup"><span data-stu-id="723bb-132">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="723bb-133">Chcete-li načítají z fronty, která je hostována na vzdáleném počítači, nahraďte "." a "localhost" pro název vzdáleného počítače.</span><span class="sxs-lookup"><span data-stu-id="723bb-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="723bb-134">Tato služba je vlastní hostované.</span><span class="sxs-lookup"><span data-stu-id="723bb-134">The service is self hosted.</span></span> <span data-ttu-id="723bb-135">Při použití přenosu služby MSMQ, fronty, používá se musí vytvořit předem.</span><span class="sxs-lookup"><span data-stu-id="723bb-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="723bb-136">To můžete udělat ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="723bb-136">This can be done manually or through code.</span></span> <span data-ttu-id="723bb-137">V této ukázce služba zkontroluje existenci fronty a vytvoří, pokud je to nutné.</span><span class="sxs-lookup"><span data-stu-id="723bb-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="723bb-138">Název fronty načítají z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="723bb-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="723bb-139">Základní adresa je používána [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generovat proxy ke službě.</span><span class="sxs-lookup"><span data-stu-id="723bb-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

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

 <span data-ttu-id="723bb-140">Klient vytvoří transakci.</span><span class="sxs-lookup"><span data-stu-id="723bb-140">The client creates a transaction.</span></span> <span data-ttu-id="723bb-141">Komunikace s frontou probíhá v rámci oboru transakcí, vyvolá zacházet jako atomickou jednotku, kde všechny zprávy úspěch nebo neúspěch.</span><span class="sxs-lookup"><span data-stu-id="723bb-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

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

 <span data-ttu-id="723bb-142">Klientský kód implementuje `IOrderStatus` smlouvy získat ze služby stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="723bb-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="723bb-143">V takovém případě se vytiskne stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="723bb-143">In this case, it prints out the order status.</span></span>  

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

 <span data-ttu-id="723bb-144">Je vytvářena fronta stav objednávky v `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="723bb-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="723bb-145">Konfigurace klienta zahrnuje konfiguraci služby stavu objednávky pro hostování služby stavu objednávky, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="723bb-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="723bb-146">Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="723bb-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="723bb-147">Můžete zobrazit přijetí zprávy služby z klienta.</span><span class="sxs-lookup"><span data-stu-id="723bb-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="723bb-148">Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="723bb-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="723bb-149">Služba zobrazí informace o pořadí nákupu a indikuje, že se odesílá zpět stav objednávky do fronty stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="723bb-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
```  
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
  
 <span data-ttu-id="723bb-150">Klient se zobrazí informace o stavu objednávky prostřednictvím služby.</span><span class="sxs-lookup"><span data-stu-id="723bb-150">The client displays the order status information sent by the service.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="723bb-151">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="723bb-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="723bb-152">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="723bb-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="723bb-153">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="723bb-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="723bb-154">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="723bb-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="723bb-155">Pokud používáte Svcutil.exe k opětovnému vytvoření konfigurace pro tuto ukázku, nezapomeňte změnit názvy koncových bodů v konfiguraci klienta tak, aby odpovídaly klientský kód.</span><span class="sxs-lookup"><span data-stu-id="723bb-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="723bb-156">Ve výchozím nastavení se <xref:System.ServiceModel.NetMsmqBinding>, je povoleno zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="723bb-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="723bb-157">Existují dvě vlastnosti důležité pro zabezpečení přenosu služby MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` výchozí režim ověřování nastaven na `Windows` a aby úroveň ochrany je nastavená na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="723bb-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="723bb-158">Pro službu MSMQ. k ověřování a podepisování funkce musí být součástí domény a možnost integrace služby active directory pro službu MSMQ musí být nainstalována.</span><span class="sxs-lookup"><span data-stu-id="723bb-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="723bb-159">Pokud tuto ukázku spustit na počítači, který nevyhovuje těmto kritériím zobrazí chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="723bb-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="723bb-160">Ke spuštění ukázky na počítač připojen k pracovní skupině nebo bez integrace služby active directory</span><span class="sxs-lookup"><span data-stu-id="723bb-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="723bb-161">Pokud počítač není součástí domény nebo nemá nainstalované integrace služby active directory, vypněte zabezpečení přenosu nastavením úroveň ověření režimu a ochrany na `None` jak je znázorněno v následující ukázková konfigurace:</span><span class="sxs-lookup"><span data-stu-id="723bb-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
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
  
2.  <span data-ttu-id="723bb-162">Vypnutí zabezpečení pro konfiguraci klienta generuje následující:</span><span class="sxs-lookup"><span data-stu-id="723bb-162">Turning off security for a client configuration generates the following:</span></span>  
  
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
  
3.  <span data-ttu-id="723bb-163">Vytvoří vazbu ve službě pro tuto ukázku `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="723bb-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="723bb-164">Přidat řádek kódu po vazba je vytvořena instance pro nastavení režimu zabezpečení `None`.</span><span class="sxs-lookup"><span data-stu-id="723bb-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4.  <span data-ttu-id="723bb-165">Ujistěte se, že změníte konfiguraci na serveru a klienta, před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="723bb-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="723bb-166">Nastavení `security mode` k `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> nebo `Message` zabezpečení `None`.</span><span class="sxs-lookup"><span data-stu-id="723bb-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="723bb-167">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="723bb-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="723bb-168">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="723bb-168">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="723bb-169">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="723bb-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="723bb-170">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="723bb-170">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
  
## <a name="see-also"></a><span data-ttu-id="723bb-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="723bb-171">See Also</span></span>
