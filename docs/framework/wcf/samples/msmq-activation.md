---
title: Aktivace MSMQ
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 0dbd24a612d56c0fe88066f625be2a8369b7df5b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602533"
---
# <a name="msmq-activation"></a><span data-ttu-id="d340f-102">Aktivace MSMQ</span><span class="sxs-lookup"><span data-stu-id="d340f-102">MSMQ Activation</span></span>

<span data-ttu-id="d340f-103">Tato ukázka předvádí, jak hostovat aplikace v aktivační službě procesů systému Windows (WAS), které se čtou z fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="d340f-103">This sample demonstrates how to host applications in Windows Process Activation Service (WAS) that are read from a message queue.</span></span> <span data-ttu-id="d340f-104">Tato ukázka používá `netMsmqBinding` a je založena na ukázce [obousměrné komunikace](two-way-communication.md) .</span><span class="sxs-lookup"><span data-stu-id="d340f-104">This sample uses the `netMsmqBinding` and is based on the [Two-Way Communication](two-way-communication.md) sample.</span></span> <span data-ttu-id="d340f-105">V tomto případě se jedná o aplikaci hostovanou v rámci webu a klient je v místním prostředí a výstupem do konzoly, aby bylo možné sledovat stav odeslaných nákupních objednávek.</span><span class="sxs-lookup"><span data-stu-id="d340f-105">The service in this case is a Web-hosted application and the client is self-hosted and outputs to the console to observe the status of purchase orders submitted.</span></span>

> [!NOTE]
> <span data-ttu-id="d340f-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d340f-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="d340f-107">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="d340f-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d340f-108">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d340f-108">Check for the following (default) directory before continuing.</span></span>
>
> <span data-ttu-id="d340f-109">\<InstallDrive>: \ WF_WCF_Samples</span><span class="sxs-lookup"><span data-stu-id="d340f-109">\<InstallDrive>:\WF_WCF_Samples</span></span>
>
> <span data-ttu-id="d340f-110">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech WCF a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="d340f-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all WCF and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d340f-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d340f-111">This sample is located in the following directory.</span></span>
>
> <span data-ttu-id="d340f-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span><span class="sxs-lookup"><span data-stu-id="d340f-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span></span>

<span data-ttu-id="d340f-113">Aktivační služba procesů systému Windows (WAS) nový mechanismus aktivace procesu pro Windows Server 2008 poskytuje funkce, které byly dříve dostupné jenom pro aplikace založené na protokolu HTTP, do aplikací, které používají protokoly jiného typu než HTTP.</span><span class="sxs-lookup"><span data-stu-id="d340f-113">Windows Process Activation Service (WAS), the new process activation mechanism for Windows Server 2008, provides IIS-like features that were previously only available to HTTP-based applications to applications that use non-HTTP protocols.</span></span> <span data-ttu-id="d340f-114">Windows Communication Foundation (WCF) používá rozhraní naslouchacího adaptéru k sdělování požadavků na aktivaci přijatých přes protokoly jiného typu než HTTP podporované službou WCF, jako je například TCP, pojmenované kanály a služba MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d340f-114">Windows Communication Foundation (WCF) uses the Listener Adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, Named Pipes, and MSMQ.</span></span> <span data-ttu-id="d340f-115">Funkce pro příjem požadavků přes protokoly jiné než HTTP je hostována spravovanými službami systému Windows, které jsou spuštěny v SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="d340f-115">The functionality for receiving requests over non-HTTP protocols is hosted by managed Windows services running in SMSvcHost.exe.</span></span>

<span data-ttu-id="d340f-116">Služba NET. MSMQ Listener Adapter (NetMsmqActivator) aktivuje aplikace zařazené do fronty na základě zpráv ve frontě.</span><span class="sxs-lookup"><span data-stu-id="d340f-116">The Net.Msmq Listener Adapter service (NetMsmqActivator) activates queued applications based on messages in the queue.</span></span>

<span data-ttu-id="d340f-117">Klient odešle službě nákupní objednávky v rámci rozsahu transakce.</span><span class="sxs-lookup"><span data-stu-id="d340f-117">The client sends purchase orders to the service from within the scope of a transaction.</span></span> <span data-ttu-id="d340f-118">Služba obdrží objednávky v transakci a zpracuje je.</span><span class="sxs-lookup"><span data-stu-id="d340f-118">The service receives the orders in a transaction and processes them.</span></span> <span data-ttu-id="d340f-119">Služba pak zavolá zpět klienta se stavem pořadí.</span><span class="sxs-lookup"><span data-stu-id="d340f-119">The service then calls back the client with the status of the order.</span></span> <span data-ttu-id="d340f-120">Aby se usnadnila obousměrná komunikace klienta a služby, používají fronty k zařazování nákupních objednávek a stavu objednávek.</span><span class="sxs-lookup"><span data-stu-id="d340f-120">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>

<span data-ttu-id="d340f-121">Kontrakt služby `IOrderProcessor` definuje jednosměrné operace služby, které fungují s řazením do fronty.</span><span class="sxs-lookup"><span data-stu-id="d340f-121">The service contract `IOrderProcessor` defines the one-way service operations that work with queuing.</span></span> <span data-ttu-id="d340f-122">Operace služby používá koncový bod odpovědi k odeslání stavů objednávky klientovi.</span><span class="sxs-lookup"><span data-stu-id="d340f-122">The service operation uses the reply endpoint to send order statuses to the client.</span></span> <span data-ttu-id="d340f-123">Adresa koncového bodu odpovědi je identifikátor URI fronty, která byla použita k odeslání stavu objednávky zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="d340f-123">The reply endpoint's address is the URI of the queue used to send the order status back to the client.</span></span> <span data-ttu-id="d340f-124">Aplikace pro zpracování objednávek tuto smlouvu implementuje.</span><span class="sxs-lookup"><span data-stu-id="d340f-124">The order processing application implements this contract.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po,
                                           string reportOrderStatusTo);
}
```

<span data-ttu-id="d340f-125">Kontrakt odpovědi na odeslání stavu objednávky je určen klientem.</span><span class="sxs-lookup"><span data-stu-id="d340f-125">The reply contract to send order status to is specified by the client.</span></span> <span data-ttu-id="d340f-126">Klient implementuje kontrakt stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="d340f-126">The client implements the order status contract.</span></span> <span data-ttu-id="d340f-127">Služba používá vygenerovaný klient této smlouvy k odeslání stavu objednávky zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="d340f-127">The service uses the generated client of this contract to send order status back to the client.</span></span>

```csharp
[ServiceContract]
public interface IOrderStatus
{
    [OperationContract(IsOneWay = true)]
    void OrderStatus(string poNumber, string status);
}
```

<span data-ttu-id="d340f-128">Operace služby zpracuje odeslanou nákupní objednávku.</span><span class="sxs-lookup"><span data-stu-id="d340f-128">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="d340f-129">Se <xref:System.ServiceModel.OperationBehaviorAttribute> použije na operaci služby a určí automatické zařazení v transakci, která se používá k přijetí zprávy z fronty, a automatickému dokončení transakce při dokončení operace služby.</span><span class="sxs-lookup"><span data-stu-id="d340f-129">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in the transaction that is used to receive the message from the queue and automatic completion of the transaction on completion of the service operation.</span></span> <span data-ttu-id="d340f-130">`Orders`Třída zapouzdřuje funkce zpracování objednávek.</span><span class="sxs-lookup"><span data-stu-id="d340f-130">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="d340f-131">V tomto případě přidá nákupní objednávku do slovníku.</span><span class="sxs-lookup"><span data-stu-id="d340f-131">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="d340f-132">Transakce, ve které je zapsána operace služby, je k dispozici pro operace ve `Orders` třídě.</span><span class="sxs-lookup"><span data-stu-id="d340f-132">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>

<span data-ttu-id="d340f-133">Operace služby kromě zpracování odeslané nákupní objednávky odpoví zpátky na klienta o stavu objednávky.</span><span class="sxs-lookup"><span data-stu-id="d340f-133">The service operation, in addition to processing the submitted purchase order, replies back to the client about the status of the order.</span></span>

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
}
```

<span data-ttu-id="d340f-134">Vazba klienta k použití je určena pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d340f-134">The client binding to use is specified using a configuration file.</span></span>

<span data-ttu-id="d340f-135">Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d340f-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="d340f-136">Koncový bod služby je definován v oddílu System. serviceModel konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d340f-136">The endpoint for the service is defined in the System.serviceModel section of the configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="d340f-137">Název fronty MSMQ a adresa koncového bodu používají mírně odlišnou konvenci adres.</span><span class="sxs-lookup"><span data-stu-id="d340f-137">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="d340f-138">Název fronty MSMQ používá tečku (.) pro místní počítač a oddělovače zpětného lomítka v cestě.</span><span class="sxs-lookup"><span data-stu-id="d340f-138">The MSMQ queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="d340f-139">Adresa koncového bodu WCF Určuje možnost NET. MSMQ:, používá pro místní počítač "localhost" a v cestě používá lomítka.</span><span class="sxs-lookup"><span data-stu-id="d340f-139">The WCF endpoint address specifies a net.msmq: scheme, uses "localhost" for the local computer, and uses forward slashes in its path.</span></span> <span data-ttu-id="d340f-140">Chcete-li číst z fronty hostované na vzdáleném počítači, nahraďte "." a "localhost" názvem vzdáleného počítače.</span><span class="sxs-lookup"><span data-stu-id="d340f-140">To read from a queue that is hosted on the remote computer, replace the "." and "localhost" to the remote computer name.</span></span>

<span data-ttu-id="d340f-141">Soubor. svc s názvem třídy slouží k hostování kódu služby v nástroji.</span><span class="sxs-lookup"><span data-stu-id="d340f-141">A .svc file with the name of the class is used to host the service code in WAS.</span></span>

<span data-ttu-id="d340f-142">Samotný soubor Service. svc obsahuje direktivu pro vytvoření `OrderProcessorService` .</span><span class="sxs-lookup"><span data-stu-id="d340f-142">The Service.svc file itself contains a directive to create the `OrderProcessorService`.</span></span>

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>`

<span data-ttu-id="d340f-143">Soubor Service. svc obsahuje také direktivu sestavení, aby bylo zajištěno, že je načten System. Transactions. dll.</span><span class="sxs-lookup"><span data-stu-id="d340f-143">The Service.svc file also contains an assembly directive to ensure that System.Transactions.dll is loaded.</span></span>

`<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>`

<span data-ttu-id="d340f-144">Klient vytvoří obor transakce.</span><span class="sxs-lookup"><span data-stu-id="d340f-144">The client creates a transaction scope.</span></span> <span data-ttu-id="d340f-145">Komunikace se službou probíhá v rámci rozsahu transakce, což způsobuje, že by byla považována za atomickou jednotku, ve které všechny zprávy jsou úspěšné nebo neúspěšné.</span><span class="sxs-lookup"><span data-stu-id="d340f-145">Communication with the service takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="d340f-146">Transakce je potvrzena voláním `Complete` v oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="d340f-146">The transaction is committed by calling `Complete` on the transaction scope.</span></span>

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

<span data-ttu-id="d340f-147">Klientský kód implementuje `IOrderStatus` kontrakt pro příjem stavu objednávky ze služby.</span><span class="sxs-lookup"><span data-stu-id="d340f-147">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="d340f-148">V tomto případě vytiskne stav objednávky.</span><span class="sxs-lookup"><span data-stu-id="d340f-148">In this case, it prints out the order status.</span></span>

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

<span data-ttu-id="d340f-149">V metodě je vytvořena fronta stavů pořadí `Main` .</span><span class="sxs-lookup"><span data-stu-id="d340f-149">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="d340f-150">Konfigurace klienta zahrnuje pořadí konfigurace stavové služby pro hostování služby stavu objednávky, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d340f-150">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>

```xml
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

<span data-ttu-id="d340f-151">Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzole serveru i klienta.</span><span class="sxs-lookup"><span data-stu-id="d340f-151">When you run the sample, the client and service activities are displayed in both the server and client console windows.</span></span> <span data-ttu-id="d340f-152">Můžete vidět, že server obdrží zprávy od klienta.</span><span class="sxs-lookup"><span data-stu-id="d340f-152">You can see the server receive messages from the client.</span></span> <span data-ttu-id="d340f-153">Pro vypnutí serveru a klienta stiskněte klávesu ENTER v každém okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="d340f-153">Press ENTER in each console window to shut down the server and client.</span></span>

<span data-ttu-id="d340f-154">Klient zobrazí informace o stavu objednávky odeslané serverem:</span><span class="sxs-lookup"><span data-stu-id="d340f-154">The client displays the order status information sent by the server:</span></span>

```console
Press <ENTER> to terminate client.
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d340f-155">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d340f-155">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d340f-156">Ujistěte se, že je nainstalovaná služba IIS 7,0, jak je potřeba pro aktivaci.</span><span class="sxs-lookup"><span data-stu-id="d340f-156">Ensure that IIS 7.0 is installed, as it is required for WAS activation.</span></span>

2. <span data-ttu-id="d340f-157">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d340f-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span> <span data-ttu-id="d340f-158">Kromě toho musíte nainstalovat komponenty WCF, které nejsou součástí aktivace přes protokol HTTP:</span><span class="sxs-lookup"><span data-stu-id="d340f-158">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="d340f-159">V nabídce **Start** klikněte na položku **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="d340f-159">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="d340f-160">Vyberte **programy a funkce**.</span><span class="sxs-lookup"><span data-stu-id="d340f-160">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="d340f-161">Klikněte na **zapnout nebo vypnout funkce systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="d340f-161">Click **Turn Windows Features on or off**.</span></span>

    4. <span data-ttu-id="d340f-162">V části **Souhrn funkcí**klikněte na **Přidat funkce**.</span><span class="sxs-lookup"><span data-stu-id="d340f-162">Under **Features Summary**, click **Add Features**.</span></span>

    5. <span data-ttu-id="d340f-163">Rozbalte uzel **Microsoft .NET Framework 3,0** a podívejte se na funkci **Windows Communication Foundation aktivace jiným protokolem než http** .</span><span class="sxs-lookup"><span data-stu-id="d340f-163">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="d340f-164">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d340f-164">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="d340f-165">Spusťte klienta spuštěním příkazu Client. exe z příkazového okna.</span><span class="sxs-lookup"><span data-stu-id="d340f-165">Run the client by executing client.exe from a command window.</span></span> <span data-ttu-id="d340f-166">Tím se vytvoří fronta a pošle se do ní zpráva.</span><span class="sxs-lookup"><span data-stu-id="d340f-166">This creates the queue and sends a message to it.</span></span> <span data-ttu-id="d340f-167">Ponechte spuštěného klienta, aby se zobrazil výsledek služby, která čte zprávu.</span><span class="sxs-lookup"><span data-stu-id="d340f-167">Leave the client running to see the result of the service reading the message</span></span>

5. <span data-ttu-id="d340f-168">Aktivační služba MSMQ je ve výchozím nastavení spuštěna jako síťová služba.</span><span class="sxs-lookup"><span data-stu-id="d340f-168">The MSMQ activation service runs as Network Service by default.</span></span> <span data-ttu-id="d340f-169">Proto fronta, která se používá k aktivaci aplikace, musí mít oprávnění Receive a prohlížet pro síťovou službu.</span><span class="sxs-lookup"><span data-stu-id="d340f-169">Therefore, the queue that is used to activate the application must have receive and peek permissions for Network Service.</span></span> <span data-ttu-id="d340f-170">Dá se přidat pomocí konzoly MMC služby Řízení front zpráv:</span><span class="sxs-lookup"><span data-stu-id="d340f-170">This can be added by using the Message Queuing MMC:</span></span>

    1. <span data-ttu-id="d340f-171">V nabídce **Start** klikněte na tlačítko **Spustit**a zadejte příkaz `Compmgmt.msc` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="d340f-171">From the **Start** menu, click **Run**, then type `Compmgmt.msc` and press ENTER.</span></span>

    2. <span data-ttu-id="d340f-172">V části **služby a aplikace**rozbalte položku **Řízení front zpráv**.</span><span class="sxs-lookup"><span data-stu-id="d340f-172">Under **Services and Applications**, expand **Message Queuing**.</span></span>

    3. <span data-ttu-id="d340f-173">Klikněte na **soukromé fronty**.</span><span class="sxs-lookup"><span data-stu-id="d340f-173">Click **Private Queues**.</span></span>

    4. <span data-ttu-id="d340f-174">Klikněte pravým tlačítkem na frontu (ServiceModelSamples/service. svc) a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d340f-174">Right-click the queue (servicemodelsamples/Service.svc) and choose **Properties**.</span></span>

    5. <span data-ttu-id="d340f-175">Na kartě **zabezpečení** klikněte na **Přidat** a poskytněte síťové službě oprávnění k prohlížení a příjmu.</span><span class="sxs-lookup"><span data-stu-id="d340f-175">On the **Security** tab, click **Add** and give peek and receive permissions to Network Service.</span></span>

6. <span data-ttu-id="d340f-176">Nakonfigurujte aktivační službu procesů systému Windows (WAS), aby podporovala aktivaci služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d340f-176">Configure the Windows Process Activation Service (WAS) to support MSMQ activation.</span></span>

    <span data-ttu-id="d340f-177">V rámci pohodlí jsou v dávkovém souboru s názvem AddMsmqSiteBinding. cmd, který je umístěn v ukázkovém adresáři, implementovány následující kroky.</span><span class="sxs-lookup"><span data-stu-id="d340f-177">As a convenience, the following steps are implemented in a batch file called AddMsmqSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="d340f-178">Aby bylo možné podporovat aktivaci NET. MSMQ, výchozí web musí být nejprve svázán s protokolem NET. MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d340f-178">To support net.msmq activation, the default Web site must first be bound to the net.msmq protocol.</span></span> <span data-ttu-id="d340f-179">To lze provést pomocí nástroje Appcmd. exe, který je nainstalován se sadou nástrojů pro správu služby IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="d340f-179">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="d340f-180">Na příkazovém řádku se zvýšenými oprávněními (správce) spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="d340f-180">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > <span data-ttu-id="d340f-181">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="d340f-181">This command is a single line of text.</span></span>

        <span data-ttu-id="d340f-182">Tento příkaz přidá na výchozí web vazbu lokality NET. MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d340f-182">This command adds a net.msmq site binding to the default Web site.</span></span>

    2. <span data-ttu-id="d340f-183">I když všechny aplikace v rámci lokality sdílejí společnou vazbu NET. MSMQ, každá aplikace může povolit podporu NET. msmq samostatně.</span><span class="sxs-lookup"><span data-stu-id="d340f-183">Although all applications within a site share a common net.msmq binding, each application can enable net.msmq support individually.</span></span> <span data-ttu-id="d340f-184">Pokud chcete pro aplikaci/ServiceModelSamples povolit NET. MSMQ, spusťte z příkazového řádku se zvýšenými oprávněními následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="d340f-184">To enable net.msmq for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq
        ```

        > [!NOTE]
        > <span data-ttu-id="d340f-185">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="d340f-185">This command is a single line of text.</span></span>

        <span data-ttu-id="d340f-186">Tento příkaz umožňuje, aby byla aplikace/ServiceModelSamples k dispozici pomocí `http://localhost/servicemodelsamples` a `net.msmq://localhost/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="d340f-186">This command enables the /servicemodelsamples application to be accessed using `http://localhost/servicemodelsamples` and `net.msmq://localhost/servicemodelsamples`.</span></span>

7. <span data-ttu-id="d340f-187">Pokud jste tak dosud neučinili, ujistěte se, že je povolená aktivační služba MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d340f-187">If you have not done so previously, ensure that the MSMQ activation service is enabled.</span></span> <span data-ttu-id="d340f-188">V nabídce **Start** klikněte na **Spustit**a zadejte `Services.msc` .</span><span class="sxs-lookup"><span data-stu-id="d340f-188">From the **Start** menu, click **Run**, and type `Services.msc`.</span></span> <span data-ttu-id="d340f-189">Vyhledejte v seznamu služeb **adaptér naslouchání NET. MSMQ**.</span><span class="sxs-lookup"><span data-stu-id="d340f-189">Search the list of services for the **Net.Msmq Listener Adapter**.</span></span> <span data-ttu-id="d340f-190">Klikněte pravým tlačítkem a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d340f-190">Right-click and select **Properties**.</span></span> <span data-ttu-id="d340f-191">Nastavte **Typ spouštění** na **automaticky**, klikněte na **použít** a klikněte na tlačítko **Spustit** .</span><span class="sxs-lookup"><span data-stu-id="d340f-191">Set the **Startup Type** to **Automatic**, click **Apply** and click the **Start** button.</span></span> <span data-ttu-id="d340f-192">Tento krok je potřeba provést jenom jednou před prvním použitím služby NET. MSMQ Listener Adapter.</span><span class="sxs-lookup"><span data-stu-id="d340f-192">This step must only be done once prior to the first usage of the Net.Msmq Listener Adapter service.</span></span>

8. <span data-ttu-id="d340f-193">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d340f-193">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="d340f-194">Navíc můžete změnit kód v klientovi, který odešle nákupní objednávku tak, aby odrážel název počítače v identifikátoru URI fronty při odeslání nákupní objednávky.</span><span class="sxs-lookup"><span data-stu-id="d340f-194">Additionally, change the code on the client that submits the purchase order to reflect the computer name in the URI of the queue when submitting the purchase order.</span></span> <span data-ttu-id="d340f-195">Použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="d340f-195">Use the following code:</span></span>

    ```csharp
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");
    ```

9. <span data-ttu-id="d340f-196">Odeberte vazbu na lokalitu NET. MSMQ, kterou jste přidali pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="d340f-196">Remove the net.msmq site binding you added for this sample.</span></span>

    <span data-ttu-id="d340f-197">Pro usnadnění jsou v dávkovém souboru s názvem RemoveMsmqSiteBinding. cmd, který se nachází v ukázkovém adresáři, implementované následující kroky:</span><span class="sxs-lookup"><span data-stu-id="d340f-197">As a convenience, the following steps are implemented in a batch file called RemoveMsmqSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="d340f-198">Ze seznamu povolených protokolů odeberte NET. MSMQ spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="d340f-198">Remove net.msmq from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="d340f-199">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="d340f-199">This command is a single line of text.</span></span>

    2. <span data-ttu-id="d340f-200">Odeberte vazbu lokality NET. MSMQ spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="d340f-200">Remove the net.msmq site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > <span data-ttu-id="d340f-201">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="d340f-201">This command is a single line of text.</span></span>

    > [!WARNING]
    > <span data-ttu-id="d340f-202">Spuštěním dávkového souboru resetujete službu DefaultAppPool tak, aby běžela pomocí .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="d340f-202">Running the batch file will reset the DefaultAppPool to run using .NET Framework version 2.0.</span></span>

<span data-ttu-id="d340f-203">Ve výchozím nastavení se pro `netMsmqBinding` přenos vazeb povoluje zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d340f-203">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="d340f-204">Dvě vlastnosti `MsmqAuthenticationMode` a `MsmqProtectionLevel` společně určují typ zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="d340f-204">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="d340f-205">Ve výchozím nastavení je režim ověřování nastaven na hodnotu `Windows` a úroveň ochrany je nastavena na hodnotu `Sign` .</span><span class="sxs-lookup"><span data-stu-id="d340f-205">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="d340f-206">Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény.</span><span class="sxs-lookup"><span data-stu-id="d340f-206">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="d340f-207">Pokud tuto ukázku spustíte na počítači, který není součástí domény, obdrží se následující chyba: "vnitřní certifikát služby Řízení front zpráv" neexistuje.</span><span class="sxs-lookup"><span data-stu-id="d340f-207">If you run this sample on a computer that is not part of a domain, the following error is received: "User's internal message queuing certificate does not exist".</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="d340f-208">Spuštění ukázky na počítači připojeném k pracovní skupině</span><span class="sxs-lookup"><span data-stu-id="d340f-208">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="d340f-209">Pokud počítač není součástí domény, vypněte zabezpečení přenosu nastavením režimu ověřování a úrovně ochrany na žádné, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d340f-209">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to none as shown in the following sample configuration.</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding configurationName="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

2. <span data-ttu-id="d340f-210">Před spuštěním ukázky změňte konfiguraci na serveru i v klientovi.</span><span class="sxs-lookup"><span data-stu-id="d340f-210">Change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d340f-211">Nastavení `security mode` na `None` je ekvivalent nastavení `MsmqAuthenticationMode` `MsmqProtectionLevel` a `Message` zabezpečení na `None` .</span><span class="sxs-lookup"><span data-stu-id="d340f-211">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

3. <span data-ttu-id="d340f-212">Chcete-li povolit aktivaci na počítači připojeném k pracovní skupině, musí být aktivační služba i pracovní proces spuštěny s konkrétním uživatelským účtem (musí být u obou) spuštěné a fronta musí mít pro konkrétní uživatelský účet seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="d340f-212">To enable activation in a computer joined to a workgroup, both the activation service and the worker process must be run with a specific user account (must be same for both) and the queue must have ACLs for the specific user account.</span></span>

     <span data-ttu-id="d340f-213">Chcete-li změnit identitu, pod kterou běží pracovní proces:</span><span class="sxs-lookup"><span data-stu-id="d340f-213">To change the identity that the worker process runs under:</span></span>

    1. <span data-ttu-id="d340f-214">Spusťte příkaz inetmgr. exe.</span><span class="sxs-lookup"><span data-stu-id="d340f-214">Run Inetmgr.exe.</span></span>

    2. <span data-ttu-id="d340f-215">V části **fondy aplikací**klikněte pravým tlačítkem na **AppPool** (obvykle **DefaultAppPool**) a vyberte **nastavit výchozí nastavení fondu aplikací..**.</span><span class="sxs-lookup"><span data-stu-id="d340f-215">Under **Application Pools**, right-click the **AppPool** (typically **DefaultAppPool**) and choose **Set Application Pool Defaults…**.</span></span>

    3. <span data-ttu-id="d340f-216">Změňte vlastnosti identity tak, aby používaly konkrétní uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="d340f-216">Change the Identity properties to use the specific user account.</span></span>

     <span data-ttu-id="d340f-217">Chcete-li změnit identitu, pod kterou se aktivační služba spouští:</span><span class="sxs-lookup"><span data-stu-id="d340f-217">To change the identity that the Activation Service runs under:</span></span>

    1. <span data-ttu-id="d340f-218">Spusťte Services. msc.</span><span class="sxs-lookup"><span data-stu-id="d340f-218">Run Services.msc.</span></span>

    2. <span data-ttu-id="d340f-219">Klikněte pravým tlačítkem na **adaptér NET. MsmqListener**a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d340f-219">Right-click the **Net.MsmqListener Adapter**, and choose **Properties**.</span></span>

4. <span data-ttu-id="d340f-220">Změňte účet na kartě **přihlášení** .</span><span class="sxs-lookup"><span data-stu-id="d340f-220">Change the account in the **LogOn** tab.</span></span>

5. <span data-ttu-id="d340f-221">V pracovní skupině musí služba také běžet pomocí neomezeného tokenu.</span><span class="sxs-lookup"><span data-stu-id="d340f-221">In workgroup, the service must also run using an unrestricted token.</span></span> <span data-ttu-id="d340f-222">Uděláte to tak, že v příkazovém okně spustíte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="d340f-222">To do this, run the following in a command window:</span></span>

    ```console
    sc sidtype netmsmqactivator unrestricted
    ```

## <a name="see-also"></a><span data-ttu-id="d340f-223">Viz také</span><span class="sxs-lookup"><span data-stu-id="d340f-223">See also</span></span>

- <span data-ttu-id="d340f-224">[Hostování technologie AppFabric a ukázky trvalosti](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d340f-224">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
