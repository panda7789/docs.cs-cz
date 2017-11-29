---
title: "Obousměrná komunikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b9d55087eb46cc304fa2a42a3e64208d9a4fec5d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="two-way-communication"></a><span data-ttu-id="c2988-102">Obousměrná komunikace</span><span class="sxs-lookup"><span data-stu-id="c2988-102">Two-Way Communication</span></span>
<span data-ttu-id="c2988-103">Tento příklad ukazuje, jak provádět zpracovaných obousměrné komunikace ve frontě prostřednictvím služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c2988-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="c2988-104">V tomto příkladu `netMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="c2988-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="c2988-105">V takovém případě je služba vlastním hostováním konzolovou aplikaci, která umožňuje sledovat službu přijetí zprávy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="c2988-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2988-106">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="c2988-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c2988-107">Tato ukázka je založena na [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="c2988-107">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="c2988-108">V komunikaci ve frontě klient komunikuje se služby pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="c2988-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="c2988-109">Klient odešle zprávy do fronty, a služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="c2988-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="c2988-110">Služba a klient proto nemusíte používat současně na komunikaci pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="c2988-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="c2988-111">Tento příklad znázorňuje způsob 2 komunikaci pomocí front.</span><span class="sxs-lookup"><span data-stu-id="c2988-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="c2988-112">Klient odešle nákupních objednávek do fronty z v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="c2988-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="c2988-113">Tato služba přijímá objednávky, zpracuje pořadí a pak zavolá zpět na klienta se stav pořadí z fronty v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="c2988-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="c2988-114">Pro usnadnění obousměrné komunikace klienta a služby používat fronty zařazování nákupních objednávek a stav pořadí.</span><span class="sxs-lookup"><span data-stu-id="c2988-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="c2988-115">Kontrakt služby `IOrderProcessor` definuje operací jednosměrné služby, která vyhovuje použití služby Řízení front.</span><span class="sxs-lookup"><span data-stu-id="c2988-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="c2988-116">Operace služby obsahuje koncový odpovědi používat k odesílání stavy pořadí k.</span><span class="sxs-lookup"><span data-stu-id="c2988-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="c2988-117">Koncový bod odpovědi je identifikátor URI fronty pro odeslání pořadí stavu zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="c2988-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="c2988-118">Pořadí zpracování aplikace implementuje tuto smlouvu.</span><span class="sxs-lookup"><span data-stu-id="c2988-118">The order processing application implements this contract.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}  
```  
  
 <span data-ttu-id="c2988-119">Kontrakt odpověď k odeslání pořadí stav je určen klienta.</span><span class="sxs-lookup"><span data-stu-id="c2988-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="c2988-120">Klient implementuje stav kontrakt pořadí.</span><span class="sxs-lookup"><span data-stu-id="c2988-120">The client implements the order status contract.</span></span> <span data-ttu-id="c2988-121">Služba používá k odeslání pořadí stavu zpět do klienta vygenerovaný proxy server této smlouvy.</span><span class="sxs-lookup"><span data-stu-id="c2988-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  
  
```  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 <span data-ttu-id="c2988-122">Operace služby zpracovává odeslaná nákupní objednávka.</span><span class="sxs-lookup"><span data-stu-id="c2988-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="c2988-123"><xref:System.ServiceModel.OperationBehaviorAttribute> Se použije pro operaci služby k určení automatických zařazení v transakci, která se používá k přijetí zprávy z fronty a automatické dokončování transakce na dokončení operace služby.</span><span class="sxs-lookup"><span data-stu-id="c2988-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="c2988-124">`Orders` Třída zapouzdří funkce pořadí zpracování.</span><span class="sxs-lookup"><span data-stu-id="c2988-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="c2988-125">V takovém případě přidá nákupní objednávka do slovníku.</span><span class="sxs-lookup"><span data-stu-id="c2988-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="c2988-126">Je k dispozici pro operace v transakci, která v uvedené operaci služby `Orders` třídy.</span><span class="sxs-lookup"><span data-stu-id="c2988-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="c2988-127">Operace služby, kromě zpracování odeslaného nákupní objednávka, odpoví klientovi na stav pořadí.</span><span class="sxs-lookup"><span data-stu-id="c2988-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  
  
```  
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
  
 <span data-ttu-id="c2988-128">Název fronty služby MSMQ je zadán v oddílu appSettings konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c2988-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="c2988-129">Koncový bod pro službu je definovaný v oddílu System.ServiceModel konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c2988-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2988-130">Adresu název a koncový bod služby MSMQ fronty pomocí mírně odlišné adresování konvence.</span><span class="sxs-lookup"><span data-stu-id="c2988-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="c2988-131">Název fronty služby MSMQ používá tečku (.) pro místní počítač a zpětné lomítko oddělovače v jeho cesty.</span><span class="sxs-lookup"><span data-stu-id="c2988-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="c2988-132">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Adresa koncového bodu určuje net.msmq: schéma, používá "localhost" pro místní počítač a lomítka v jeho cesty.</span><span class="sxs-lookup"><span data-stu-id="c2988-132">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="c2988-133">Čtení z fronty, který je hostován ve vzdáleném počítači, nahraďte "." a "localhost" na název vzdáleného počítače.</span><span class="sxs-lookup"><span data-stu-id="c2988-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="c2988-134">Služba je sám sebou hostované.</span><span class="sxs-lookup"><span data-stu-id="c2988-134">The service is self hosted.</span></span> <span data-ttu-id="c2988-135">Pokud používáte přenos MSMQ, používá fronty musí být vytvořeny předem.</span><span class="sxs-lookup"><span data-stu-id="c2988-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="c2988-136">Tento krok můžete provést ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="c2988-136">This can be done manually or through code.</span></span> <span data-ttu-id="c2988-137">V této ukázce služba zkontroluje existenci fronty a vytvoří, pokud je to nutné.</span><span class="sxs-lookup"><span data-stu-id="c2988-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="c2988-138">Název fronty je číst z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c2988-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="c2988-139">Základní adresa se používá [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování proxy ke službě.</span><span class="sxs-lookup"><span data-stu-id="c2988-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  
  
```  
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
  
 <span data-ttu-id="c2988-140">Klient vytvoří transakci.</span><span class="sxs-lookup"><span data-stu-id="c2988-140">The client creates a transaction.</span></span> <span data-ttu-id="c2988-141">Komunikace s fronty probíhá v rámci oboru transakce, příčinou je považován za atomické jednotky, kde všechny zprávy úspěch nebo neúspěch.</span><span class="sxs-lookup"><span data-stu-id="c2988-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  
  
```  
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
  
 <span data-ttu-id="c2988-142">Implementuje kód klienta `IOrderStatus` smlouvy přijímat pořadí stav ze služby.</span><span class="sxs-lookup"><span data-stu-id="c2988-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="c2988-143">V takovém případě vytiskne na stav pořadí.</span><span class="sxs-lookup"><span data-stu-id="c2988-143">In this case, it prints out the order status.</span></span>  
  
```  
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
  
 <span data-ttu-id="c2988-144">Je vytvářena fronta stavu pořadí v `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="c2988-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="c2988-145">Konfigurace klienta zahrnuje konfiguraci služby stavu pořadí k hostování služby stavu pořadí, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c2988-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="c2988-146">Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="c2988-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="c2988-147">Uvidíte služby přijmout zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="c2988-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="c2988-148">Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="c2988-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="c2988-149">Služba zobrazí informace o nákupu pořadí a znamená, že ji zpět odesílá stav objednávky do fronty stav pořadí.</span><span class="sxs-lookup"><span data-stu-id="c2988-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
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
  
 <span data-ttu-id="c2988-150">Klient se zobrazí informace o stavu pořadí odeslaných službou.</span><span class="sxs-lookup"><span data-stu-id="c2988-150">The client displays the order status information sent by the service.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c2988-151">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="c2988-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c2988-152">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2988-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c2988-153">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2988-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c2988-154">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2988-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c2988-155">Pokud používáte Svcutil.exe znovu vygenerovat konfigurace pro tuto ukázku, nezapomeňte změnit názvy koncových bodů v konfiguraci klienta tak, aby odpovídaly kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="c2988-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="c2988-156">Ve výchozím nastavení se <xref:System.ServiceModel.NetMsmqBinding>, je povoleno zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="c2988-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="c2988-157">Existují dvě vlastnosti důležité pro zabezpečení přenosu služby MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="c2988-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="c2988-158">Pro služby MSMQ k ověřování a podepisování funkce musí být součástí domény a možnost integrace služby active directory pro službu MSMQ musí být nainstalován.</span><span class="sxs-lookup"><span data-stu-id="c2988-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="c2988-159">Pokud tuto ukázku spustit na počítači, který nesplňuje tato kritéria obdržíte chybu.</span><span class="sxs-lookup"><span data-stu-id="c2988-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="c2988-160">Ke spuštění ukázky na počítač připojen k pracovní skupině nebo bez integrace služby active directory</span><span class="sxs-lookup"><span data-stu-id="c2988-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="c2988-161">Pokud počítač není součástí domény nebo nemá nainstalované integrační služby active directory, vypněte zabezpečení přenosu podle nastavení úrovně režim a ochrany ověřování na `None` jak je znázorněno v následující ukázka konfigurace:</span><span class="sxs-lookup"><span data-stu-id="c2988-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
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
  
2.  <span data-ttu-id="c2988-162">Vypnutí zabezpečení pro konfiguraci klienta generuje následující:</span><span class="sxs-lookup"><span data-stu-id="c2988-162">Turning off security for a client configuration generates the following:</span></span>  
  
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
  
3.  <span data-ttu-id="c2988-163">Služba pro tento příklad vytvoří vazbu v `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="c2988-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="c2988-164">Přidá řádek kódu po vytvoření vazby instance nastavení režimu zabezpečení na `None`.</span><span class="sxs-lookup"><span data-stu-id="c2988-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4.  <span data-ttu-id="c2988-165">Ujistěte se, změnit konfiguraci na serveru a klienta, před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="c2988-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c2988-166">Nastavení `security mode` k `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> nebo `Message` zabezpečení `None`.</span><span class="sxs-lookup"><span data-stu-id="c2988-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c2988-167">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="c2988-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c2988-168">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c2988-168">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c2988-169">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c2988-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c2988-170">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c2988-170">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
  
## <a name="see-also"></a><span data-ttu-id="c2988-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2988-171">See Also</span></span>
