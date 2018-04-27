---
title: Aktivace MSMQ
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e0f8077e425464d5a9f33662366377d573719659
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="msmq-activation"></a><span data-ttu-id="16051-102">Aktivace MSMQ</span><span class="sxs-lookup"><span data-stu-id="16051-102">MSMQ Activation</span></span>
<span data-ttu-id="16051-103">Tento příklad ukazuje, jak pro hostování aplikací v procesu aktivace služby WAS (Windows), které se načítají z fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="16051-103">This sample demonstrates how to host applications in Windows Process Activation Service (WAS) that are read from a message queue.</span></span> <span data-ttu-id="16051-104">Této ukázce se používá `netMsmqBinding` a je založena na [obousměrné komunikace](../../../../docs/framework/wcf/samples/two-way-communication.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="16051-104">This sample uses the `netMsmqBinding` and is based on the [Two-Way Communication](../../../../docs/framework/wcf/samples/two-way-communication.md) sample.</span></span> <span data-ttu-id="16051-105">Služba je v tomto případě hostované webové aplikace a klient se hostuje sama a výstupy ke konzole sledovat stav nákupních objednávek odeslána.</span><span class="sxs-lookup"><span data-stu-id="16051-105">The service in this case is a Web-hosted application and the client is self-hosted and outputs to the console to observe the status of purchase orders submitted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16051-106">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="16051-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16051-107">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="16051-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="16051-108">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="16051-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  <span data-ttu-id="16051-109">\<InstallDrive >: \WF_WCF_Samples</span><span class="sxs-lookup"><span data-stu-id="16051-109">\<InstallDrive>:\WF_WCF_Samples</span></span>  
>   
>  <span data-ttu-id="16051-110">Pokud tento adresář neexistuje, přejděte na [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] HYPERLINK "http://go.microsoft.com/fwlink/?LinkId=150780" \t "_blank" a ukázky Windows Workflow Foundation (WF) pro [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] ke stažení všechny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="16051-110">If this directory does not exist, go to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] HYPERLINK "http://go.microsoft.com/fwlink/?LinkId=150780" \t "_blank"  and Windows Workflow Foundation (WF) Samples for [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] to download all [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="16051-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="16051-111">This sample is located in the following directory.</span></span>  
>   
>  <span data-ttu-id="16051-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span><span class="sxs-lookup"><span data-stu-id="16051-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span></span>  
  
 <span data-ttu-id="16051-113">Proces aktivace služby WAS (Windows), nový mechanismus aktivace procesů pro [!INCLUDE[lserver](../../../../includes/lserver-md.md)], poskytuje službě IIS jako funkce, které byly dřív dostupné jenom pro aplikace založené na protokolu HTTP pro aplikace, které pomocí jiných protokolů než HTTP.</span><span class="sxs-lookup"><span data-stu-id="16051-113">Windows Process Activation Service (WAS), the new process activation mechanism for [!INCLUDE[lserver](../../../../includes/lserver-md.md)], provides IIS-like features that were previously only available to HTTP-based applications to applications that use non-HTTP protocols.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="16051-114"> používá ke komunikaci žádosti o aktivaci, které jsou přijaty prostřednictvím protokolů než HTTP nepodporuje rozhraní adaptér naslouchání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], jako jsou například TCP, pojmenované kanály a služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="16051-114"> uses the Listener Adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], such as TCP, Named Pipes, and MSMQ.</span></span> <span data-ttu-id="16051-115">Funkce pro přijímání požadavků pomocí jiných protokolů než HTTP je hostován spravované služby systému Windows, které jsou spuštěny v SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="16051-115">The functionality for receiving requests over non-HTTP protocols is hosted by managed Windows services running in SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="16051-116">Adaptér naslouchání Net.Msmq služby (NetMsmqActivator) aktivuje zařazených do fronty aplikací založených na zprávy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="16051-116">The Net.Msmq Listener Adapter service (NetMsmqActivator) activates queued applications based on messages in the queue.</span></span>  
  
 <span data-ttu-id="16051-117">Klient odešle nákupních objednávek ke službě z v rámci oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="16051-117">The client sends purchase orders to the service from within the scope of a transaction.</span></span> <span data-ttu-id="16051-118">Služba přijímá objednávky v transakci a zpracovává je.</span><span class="sxs-lookup"><span data-stu-id="16051-118">The service receives the orders in a transaction and processes them.</span></span> <span data-ttu-id="16051-119">Služba zpět pak zavolá klienta se stav pořadí.</span><span class="sxs-lookup"><span data-stu-id="16051-119">The service then calls back the client with the status of the order.</span></span> <span data-ttu-id="16051-120">Pro usnadnění obousměrné komunikace klienta a služby používat fronty zařazování nákupních objednávek a stav pořadí.</span><span class="sxs-lookup"><span data-stu-id="16051-120">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="16051-121">Kontrakt služby `IOrderProcessor` definuje operace jednosměrné služby, které pracují s služby Řízení front.</span><span class="sxs-lookup"><span data-stu-id="16051-121">The service contract `IOrderProcessor` defines the one-way service operations that work with queuing.</span></span> <span data-ttu-id="16051-122">Operace služby používá k odesílání pořadí stavy klientovi odpovědi koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="16051-122">The service operation uses the reply endpoint to send order statuses to the client.</span></span> <span data-ttu-id="16051-123">Adresa koncového bodu odpovědi je identifikátor URI fronty používají k odesílání pořadí stavu zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="16051-123">The reply endpoint's address is the URI of the queue used to send the order status back to the client.</span></span> <span data-ttu-id="16051-124">Pořadí zpracování aplikace implementuje tuto smlouvu.</span><span class="sxs-lookup"><span data-stu-id="16051-124">The order processing application implements this contract.</span></span>  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 <span data-ttu-id="16051-125">Kontrakt odpověď k odeslání pořadí stav je zadat klientem.</span><span class="sxs-lookup"><span data-stu-id="16051-125">The reply contract to send order status to is specified by the client.</span></span> <span data-ttu-id="16051-126">Klient implementuje stav kontrakt pořadí.</span><span class="sxs-lookup"><span data-stu-id="16051-126">The client implements the order status contract.</span></span> <span data-ttu-id="16051-127">Služba používá k odeslání pořadí stavu zpět do klienta generovaného klienta této smlouvy.</span><span class="sxs-lookup"><span data-stu-id="16051-127">The service uses the generated client of this contract to send order status back to the client.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 <span data-ttu-id="16051-128">Operace služby zpracovává odeslaná nákupní objednávka.</span><span class="sxs-lookup"><span data-stu-id="16051-128">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="16051-129"><xref:System.ServiceModel.OperationBehaviorAttribute> Se použije pro operaci služby k určení automatických zařazení v transakci, která se používá k přijetí zprávy z fronty a automatického dokončování transakce na dokončení operace služby.</span><span class="sxs-lookup"><span data-stu-id="16051-129">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in the transaction that is used to receive the message from the queue and automatic completion of the transaction on completion of the service operation.</span></span> <span data-ttu-id="16051-130">`Orders` Třída zapouzdří funkce pořadí zpracování.</span><span class="sxs-lookup"><span data-stu-id="16051-130">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="16051-131">V takovém případě přidá nákupní objednávka do slovníku.</span><span class="sxs-lookup"><span data-stu-id="16051-131">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="16051-132">Je k dispozici pro operace v transakci, která v uvedené operaci služby `Orders` třídy.</span><span class="sxs-lookup"><span data-stu-id="16051-132">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="16051-133">Operace služby, kromě zpracování odeslaného nákupní objednávka, odpověď zpět do klienta o stavu pořadí.</span><span class="sxs-lookup"><span data-stu-id="16051-133">The service operation, in addition to processing the submitted purchase order, replies back to the client about the status of the order.</span></span>  
  
```csharp  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
        Console.WriteLine("Sending back order status information");  
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
        // please note that the same transaction that is used to dequeue purchase order is used  
        // to send back order status  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            client.OrderStatus(po.PONumber, po.Status);  
            scope.Complete();  
        }  
    }  
```  
  
 <span data-ttu-id="16051-134">Klient pro vytvoření vazby na použití je zadán pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="16051-134">The client binding to use is specified using a configuration file.</span></span>  
  
 <span data-ttu-id="16051-135">Název fronty služby MSMQ je zadán v oddílu appSettings konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="16051-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="16051-136">Koncový bod pro službu je definovaný v oddílu System.serviceModel konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="16051-136">The endpoint for the service is defined in the System.serviceModel section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16051-137">Adresu název a koncový bod služby MSMQ fronty pomocí mírně odlišné adresování konvence.</span><span class="sxs-lookup"><span data-stu-id="16051-137">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="16051-138">Název fronty služby MSMQ používá tečku (.) pro místní počítač a oddělovače zpětné lomítko, v jeho cesty.</span><span class="sxs-lookup"><span data-stu-id="16051-138">The MSMQ queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="16051-139">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Adresa koncového bodu určuje net.msmq: schéma, používá "localhost" pro místní počítač a v jeho cesty používá lomítka.</span><span class="sxs-lookup"><span data-stu-id="16051-139">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint address specifies a net.msmq: scheme, uses "localhost" for the local computer, and uses forward slashes in its path.</span></span> <span data-ttu-id="16051-140">Čtení z fronty, která je hostována na vzdáleném počítači, nahraďte "." a "localhost" pro název vzdáleného počítače.</span><span class="sxs-lookup"><span data-stu-id="16051-140">To read from a queue that is hosted on the remote computer, replace the "." and "localhost" to the remote computer name.</span></span>  
  
 <span data-ttu-id="16051-141">.Svc soubor s názvem třídy se používá k hostování kódu služby ve WAS.</span><span class="sxs-lookup"><span data-stu-id="16051-141">A .svc file with the name of the class is used to host the service code in WAS.</span></span>  
  
 <span data-ttu-id="16051-142">Samotný soubor Service.svc obsahuje direktivu vytvořit `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="16051-142">The Service.svc file itself contains a directive to create the `OrderProcessorService`.</span></span>  
  
```xml  
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 <span data-ttu-id="16051-143">Soubor Service.svc také obsahuje direktivu sestavení zajistit, že je načteno System.Transactions.dll.</span><span class="sxs-lookup"><span data-stu-id="16051-143">The Service.svc file also contains an assembly directive to ensure that System.Transactions.dll is loaded.</span></span>  
  
```xml  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 <span data-ttu-id="16051-144">Klient vytvoří oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="16051-144">The client creates a transaction scope.</span></span> <span data-ttu-id="16051-145">Komunikace se službou probíhá v rámci oboru transakce, příčinou je považován za atomické jednotky, kde všechny zprávy úspěch nebo neúspěch.</span><span class="sxs-lookup"><span data-stu-id="16051-145">Communication with the service takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="16051-146">Transakce se potvrdí voláním `Complete` v oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="16051-146">The transaction is committed by calling `Complete` on the transaction scope.</span></span>  
  
```csharp  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
    // Open the ServiceHostBase to create listeners and start listening   
    // for order status messages.  
    serviceHost.Open();  
  
    // Create a proxy with given client endpoint configuration  
    OrderProcessorClient client = new OrderProcessorClient();  
  
    // Create the purchase order  
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
  
    //Create a transaction scope.  
    using (TransactionScope scope = new   
        TransactionScope(TransactionScopeOption.Required))  
    {  
        // Make a queued call to submit the purchase order  
        client.SubmitPurchaseOrder(po,   
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Closing the client gracefully closes the connection and cleans up   
    //resources  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHostBase to shutdown the service.  
    serviceHost.Close();  
    }  
```  
  
 <span data-ttu-id="16051-147">Implementuje kód klienta `IOrderStatus` smlouvy přijímat pořadí stav ze služby.</span><span class="sxs-lookup"><span data-stu-id="16051-147">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="16051-148">V takovém případě vytiskne na stav pořadí.</span><span class="sxs-lookup"><span data-stu-id="16051-148">In this case, it prints out the order status.</span></span>  
  
```csharp  
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,   
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ",   
                                         poNumber , status);  
    }  
}  
```  
  
 <span data-ttu-id="16051-149">Je vytvářena fronta stavu pořadí v `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="16051-149">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="16051-150">Konfigurace klienta zahrnuje konfiguraci služby stavu pořadí k hostování služby stavu pořadí, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="16051-150">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
```csharp  
<appSettings>  
    <!-- use appSetting to configure MSMQ queue name -->  
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />  
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />  
  </appSettings>  
  
<system.serviceModel>  
  
    <services>  
      <service   
         name="Microsoft.ServiceModel.Samples.OrderStatusService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"  
                  binding="netMsmqBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
      </service>  
    </services>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"   
                binding="netMsmqBinding"   
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
    </client>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="16051-151">Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly klienta i serveru.</span><span class="sxs-lookup"><span data-stu-id="16051-151">When you run the sample, the client and service activities are displayed in both the server and client console windows.</span></span> <span data-ttu-id="16051-152">Můžete zobrazit server přijímat zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="16051-152">You can see the server receive messages from the client.</span></span> <span data-ttu-id="16051-153">Stisknutím klávesy ENTER v každé okno konzoly a ukončí se serverem a klientem.</span><span class="sxs-lookup"><span data-stu-id="16051-153">Press ENTER in each console window to shut down the server and client.</span></span>  
  
 <span data-ttu-id="16051-154">Klient se zobrazí informace o stavu pořadí odeslaných serverem:</span><span class="sxs-lookup"><span data-stu-id="16051-154">The client displays the order status information sent by the server:</span></span>  
  
```Output  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="16051-155">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="16051-155">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="16051-156">Ujistěte se, že [!INCLUDE[iisver](../../../../includes/iisver-md.md)] je nainstalovaná, jako je povinný aktivace WAS.</span><span class="sxs-lookup"><span data-stu-id="16051-156">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed, as it is required for WAS activation.</span></span>  
  
2.  <span data-ttu-id="16051-157">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16051-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span> <span data-ttu-id="16051-158">Kromě toho je nutné nainstalovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Aktivace jiným protokolem než HTTP součásti:</span><span class="sxs-lookup"><span data-stu-id="16051-158">In addition, you must install the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] non-HTTP activation components:</span></span>  
  
    1.  <span data-ttu-id="16051-159">Z **spustit** nabídce zvolte **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="16051-159">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="16051-160">Vyberte **programy a funkce**.</span><span class="sxs-lookup"><span data-stu-id="16051-160">Select **Programs and Features**.</span></span>  
  
    3.  <span data-ttu-id="16051-161">Klikněte na tlačítko **zapnout nebo vypnout funkce systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="16051-161">Click **Turn Windows Features on or off**.</span></span>  
  
    4.  <span data-ttu-id="16051-162">V části **Souhrn funkcí**, klikněte na tlačítko **přidat funkce**.</span><span class="sxs-lookup"><span data-stu-id="16051-162">Under **Features Summary**, click **Add Features**.</span></span>  
  
    5.  <span data-ttu-id="16051-163">Rozbalte **rozhraní Microsoft .NET Framework 3.0** uzlu a kontroly **Aktivace jiným protokolem než HTTP Windows Communication Foundation** funkce.</span><span class="sxs-lookup"><span data-stu-id="16051-163">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3.  <span data-ttu-id="16051-164">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16051-164">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="16051-165">Spusťte klienta spuštěním client.exe z příkazového okna.</span><span class="sxs-lookup"><span data-stu-id="16051-165">Run the client by executing client.exe from a command window.</span></span> <span data-ttu-id="16051-166">Tím se vytvoří frontu a odešle zprávu do ní.</span><span class="sxs-lookup"><span data-stu-id="16051-166">This creates the queue and sends a message to it.</span></span> <span data-ttu-id="16051-167">Nechte klienty v provozu zobrazíte výsledek službu čtení zprávy</span><span class="sxs-lookup"><span data-stu-id="16051-167">Leave the client running to see the result of the service reading the message</span></span>  
  
5.  <span data-ttu-id="16051-168">Aktivace služby MSMQ spouští jako síťová služba ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="16051-168">The MSMQ activation service runs as Network Service by default.</span></span> <span data-ttu-id="16051-169">Proto musí mít fronty, který se používá k aktivaci aplikace přijímat a prohlížet oprávnění pro síťovou službu.</span><span class="sxs-lookup"><span data-stu-id="16051-169">Therefore, the queue that is used to activate the application must have receive and peek permissions for Network Service.</span></span> <span data-ttu-id="16051-170">To lze přidat pomocí konzoly MMC služby Řízení front zpráv:</span><span class="sxs-lookup"><span data-stu-id="16051-170">This can be added by using the Message Queuing MMC:</span></span>  
  
    1.  <span data-ttu-id="16051-171">Z **spustit** nabídky, klikněte na tlačítko **spustit**, pak zadejte `Compmgmt.msc` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="16051-171">From the **Start** menu, click **Run**, then type `Compmgmt.msc` and press ENTER.</span></span>  
  
    2.  <span data-ttu-id="16051-172">V části **služeb a aplikací**, rozbalte položku **služby Řízení front zpráv**.</span><span class="sxs-lookup"><span data-stu-id="16051-172">Under **Services and Applications**, expand **Message Queuing**.</span></span>  
  
    3.  <span data-ttu-id="16051-173">Klikněte na tlačítko **soukromé fronty**.</span><span class="sxs-lookup"><span data-stu-id="16051-173">Click **Private Queues**.</span></span>  
  
    4.  <span data-ttu-id="16051-174">Klikněte pravým tlačítkem na fronty (servicemodelsamples/Service.svc) a zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="16051-174">Right-click the queue (servicemodelsamples/Service.svc) and choose **Properties**.</span></span>  
  
    5.  <span data-ttu-id="16051-175">Na **zabezpečení** , klikněte na **přidat** a poskytují funkce Náhled a obdrží oprávnění k síťové službě.</span><span class="sxs-lookup"><span data-stu-id="16051-175">On the **Security** tab, click **Add** and give peek and receive permissions to Network Service.</span></span>  
  
6.  <span data-ttu-id="16051-176">Konfigurace proces aktivace služby WAS (Windows) pro podporu aktivace MSMQ.</span><span class="sxs-lookup"><span data-stu-id="16051-176">Configure the Windows Process Activation Service (WAS) to support MSMQ activation.</span></span>  
  
     <span data-ttu-id="16051-177">Pro potřeby následující kroky jsou implementované v dávkovém souboru názvem AddMsmqSiteBinding.cmd umístěný v adresáři ukázka.</span><span class="sxs-lookup"><span data-stu-id="16051-177">As a convenience, the following steps are implemented in a batch file called AddMsmqSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="16051-178">Kvůli podpoře aktivace net.msmq, musí být nejprve vázána výchozí web na protokol net.msmq.</span><span class="sxs-lookup"><span data-stu-id="16051-178">To support net.msmq activation, the default Web site must first be bound to the net.msmq protocol.</span></span> <span data-ttu-id="16051-179">To lze provést pomocí appcmd.exe, která se instaluje s [!INCLUDE[iisver](../../../../includes/iisver-md.md)] sada nástrojů pro správu.</span><span class="sxs-lookup"><span data-stu-id="16051-179">This can be done using appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="16051-180">Z příkazového řádku s oprávněními zvýšenými na úroveň (správce) spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="16051-180">From an elevated (administrator) command prompt, run the following command.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="16051-181">Tento příkaz je na jednom řádku textu.</span><span class="sxs-lookup"><span data-stu-id="16051-181">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="16051-182">Tento příkaz přidá net.msmq vazba webu default Web site.</span><span class="sxs-lookup"><span data-stu-id="16051-182">This command adds a net.msmq site binding to the default Web site.</span></span>  
  
    2.  <span data-ttu-id="16051-183">Přestože všechny aplikace v rámci lokality sdílejí společné net.msmq vazbu, každá aplikace můžete povolit podporu net.msmq jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="16051-183">Although all applications within a site share a common net.msmq binding, each application can enable net.msmq support individually.</span></span> <span data-ttu-id="16051-184">Pokud chcete povolit net.msmq /servicemodelsamples aplikace, spusťte následující příkaz z příkazového řádku se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="16051-184">To enable net.msmq for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="16051-185">Tento příkaz je na jednom řádku textu.</span><span class="sxs-lookup"><span data-stu-id="16051-185">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="16051-186">Tento příkaz povolí aplikaci /servicemodelsamples získat přístup pomocí http://localhost/servicemodelsamples a net.msmq://localhost/servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="16051-186">This command enables the /servicemodelsamples application to be accessed using http://localhost/servicemodelsamples and net.msmq://localhost/servicemodelsamples.</span></span>  
  
7.  <span data-ttu-id="16051-187">Pokud jste tak dosud neučinili dříve, ujistěte se, že je povolena služba Aktivace služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="16051-187">If you have not done so previously, ensure that the MSMQ activation service is enabled.</span></span> <span data-ttu-id="16051-188">Z **spustit** nabídky, klikněte na tlačítko **spustit**a typ `Services.msc`.</span><span class="sxs-lookup"><span data-stu-id="16051-188">From the **Start** menu, click **Run**, and type `Services.msc`.</span></span> <span data-ttu-id="16051-189">V seznamu služeb pro Hledat **adaptér naslouchání Net.Msmq**.</span><span class="sxs-lookup"><span data-stu-id="16051-189">Search the list of services for the **Net.Msmq Listener Adapter**.</span></span> <span data-ttu-id="16051-190">Klikněte pravým tlačítkem a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="16051-190">Right-click and select **Properties**.</span></span> <span data-ttu-id="16051-191">Nastavte **typ spuštění** k **automatické**, klikněte na tlačítko **použít** a klikněte na tlačítko **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="16051-191">Set the **Startup Type** to **Automatic**, click **Apply** and click the **Start** button.</span></span> <span data-ttu-id="16051-192">Tento krok je třeba provést pouze jednou před první využití služby Net.Msmq adaptér naslouchání.</span><span class="sxs-lookup"><span data-stu-id="16051-192">This step must only be done once prior to the first usage of the Net.Msmq Listener Adapter service.</span></span>  
  
8.  <span data-ttu-id="16051-193">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16051-193">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="16051-194">Kromě toho změňte kód v klientovi, který odešle nákupní objednávka podle názvu počítače v identifikátoru URI fronty při odesílání nákupní objednávka.</span><span class="sxs-lookup"><span data-stu-id="16051-194">Additionally, change the code on the client that submits the purchase order to reflect the computer name in the URI of the queue when submitting the purchase order.</span></span> <span data-ttu-id="16051-195">Použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="16051-195">Use the following code:</span></span>  
  
    ```  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. <span data-ttu-id="16051-196">Odeberte net.msmq vazby webu, který jste přidali Tato ukázka.</span><span class="sxs-lookup"><span data-stu-id="16051-196">Remove the net.msmq site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="16051-197">Pro potřeby následující kroky jsou implementované v dávkovém souboru názvem RemoveMsmqSiteBinding.cmd umístěný v adresáři ukázka:</span><span class="sxs-lookup"><span data-stu-id="16051-197">As a convenience, the following steps are implemented in a batch file called RemoveMsmqSiteBinding.cmd located in the sample directory:</span></span>  
  
    1.  <span data-ttu-id="16051-198">Odeberte net.msmq ze seznamu povolených protokolů spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="16051-198">Remove net.msmq from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="16051-199">Tento příkaz je na jednom řádku textu.</span><span class="sxs-lookup"><span data-stu-id="16051-199">This command is a single line of text.</span></span>  
  
    2.  <span data-ttu-id="16051-200">Odeberte vazbu webu net.msmq spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="16051-200">Remove the net.msmq site binding by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="16051-201">Tento příkaz je na jednom řádku textu.</span><span class="sxs-lookup"><span data-stu-id="16051-201">This command is a single line of text.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="16051-202">Spuštění dávkového souboru obnoví DefaultAppPool běžely pomocí rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="16051-202">Running the batch file will reset the DefaultAppPool to run using .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="16051-203">Ve výchozím nastavení se `netMsmqBinding` vazby přenos, zabezpečení je povoleno.</span><span class="sxs-lookup"><span data-stu-id="16051-203">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="16051-204">Dvě vlastnosti `MsmqAuthenticationMode` a `MsmqProtectionLevel`, společně určují typ zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="16051-204">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="16051-205">Ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="16051-205">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="16051-206">Pro MSMQ k ověřování a podepisování funkce musí být součástí domény.</span><span class="sxs-lookup"><span data-stu-id="16051-206">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="16051-207">Pokud tuto ukázku spustit na počítači, který není součástí domény, je přijatých k následující chybě: "Uživatele interní zpráv služby Řízení front certifikát neexistuje".</span><span class="sxs-lookup"><span data-stu-id="16051-207">If you run this sample on a computer that is not part of a domain, the following error is received: "User's internal message queuing certificate does not exist".</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="16051-208">Ke spuštění ukázky na počítače připojeného k pracovní skupině</span><span class="sxs-lookup"><span data-stu-id="16051-208">To run the sample on a computer joined to a workgroup</span></span>  
  
1.  <span data-ttu-id="16051-209">Pokud počítač není součástí domény, vypněte podle nastavení úrovně ověřování režimu a ochrany na hodnotu none, jak je znázorněno v následující ukázka konfigurace zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="16051-209">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to none as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2.  <span data-ttu-id="16051-210">Změňte konfiguraci na serveru a klienta, před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="16051-210">Change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="16051-211">Nastavení `security mode` k `None` je ekvivalentní nastavení `MsmqAuthenticationMode`, `MsmqProtectionLevel` a `Message` zabezpečení `None`.</span><span class="sxs-lookup"><span data-stu-id="16051-211">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>  
  
3.  <span data-ttu-id="16051-212">Povolit aktivace v počítače připojeného k pracovní skupině, je potřeba spustit službu Aktivace a pracovní proces s konkrétní uživatelský účet (musí být stejné pro obě) a fronty musí mít seznamy řízení přístupu pro konkrétní uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="16051-212">To enable activation in a computer joined to a workgroup, both the activation service and the worker process must be run with a specific user account (must be same for both) and the queue must have ACLs for the specific user account.</span></span>  
  
     <span data-ttu-id="16051-213">Změna identity kompatibilní se pracovní proces:</span><span class="sxs-lookup"><span data-stu-id="16051-213">To change the identity that the worker process runs under:</span></span>  
  
    1.  <span data-ttu-id="16051-214">Spusťte Inetmgr.exe.</span><span class="sxs-lookup"><span data-stu-id="16051-214">Run Inetmgr.exe.</span></span>  
  
    2.  <span data-ttu-id="16051-215">V části **fondy aplikací**, klikněte pravým tlačítkem myši **AppPool** (obvykle **DefaultAppPool**) a zvolte **nastavit výchozí nastavení fondu aplikací...** .</span><span class="sxs-lookup"><span data-stu-id="16051-215">Under **Application Pools**, right-click the **AppPool** (typically **DefaultAppPool**) and choose **Set Application Pool Defaults…**.</span></span>  
  
    3.  <span data-ttu-id="16051-216">Změňte vlastnosti Identity pro použití účtu pro konkrétního uživatele.</span><span class="sxs-lookup"><span data-stu-id="16051-216">Change the Identity properties to use the specific user account.</span></span>  
  
     <span data-ttu-id="16051-217">Změna identity kompatibilní se službu Aktivace:</span><span class="sxs-lookup"><span data-stu-id="16051-217">To change the identity that the Activation Service runs under:</span></span>  
  
    1.  <span data-ttu-id="16051-218">Run Services.msc.</span><span class="sxs-lookup"><span data-stu-id="16051-218">Run Services.msc.</span></span>  
  
    2.  <span data-ttu-id="16051-219">Klikněte pravým tlačítkem myši **Net.MsmqListener adaptér**a zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="16051-219">Right-click the **Net.MsmqListener Adapter**, and choose **Properties**.</span></span>  
  
4.  <span data-ttu-id="16051-220">Změňte účet v **přihlášení** kartě.</span><span class="sxs-lookup"><span data-stu-id="16051-220">Change the account in the **LogOn** tab.</span></span>  
  
5.  <span data-ttu-id="16051-221">V pracovní skupině se musí taky spustit služba pomocí neomezený tokenu.</span><span class="sxs-lookup"><span data-stu-id="16051-221">In workgroup, the service must also run using an unrestricted token.</span></span> <span data-ttu-id="16051-222">K tomu, spusťte následující příkazy v příkazovém okně:</span><span class="sxs-lookup"><span data-stu-id="16051-222">To do this, run the following in a command window:</span></span>  
  
    ```  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="16051-223">Viz také</span><span class="sxs-lookup"><span data-stu-id="16051-223">See Also</span></span>  
 [<span data-ttu-id="16051-224">Ukázky trvalosti a hostování AppFabric</span><span class="sxs-lookup"><span data-stu-id="16051-224">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
