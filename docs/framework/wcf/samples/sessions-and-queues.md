---
title: Relace a fronty
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: aaba55ac3eec5ae4ec36fc449c0b211cb36619d2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964510"
---
# <a name="sessions-and-queues"></a><span data-ttu-id="73fe6-102">Relace a fronty</span><span class="sxs-lookup"><span data-stu-id="73fe6-102">Sessions and Queues</span></span>
<span data-ttu-id="73fe6-103">Tato ukázka předvádí, jak odeslat a přijmout sadu souvisejících zpráv v komunikaci ve frontě prostřednictvím přenosu služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="73fe6-103">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="73fe6-104">Tato ukázka používá `netMsmqBinding` vazbu.</span><span class="sxs-lookup"><span data-stu-id="73fe6-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="73fe6-105">Služba je samoobslužná Konzolová aplikace, která vám umožní sledovat službu přijímající zprávy zařazené do fronty.</span><span class="sxs-lookup"><span data-stu-id="73fe6-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73fe6-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="73fe6-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="73fe6-107">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="73fe6-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="73fe6-108">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="73fe6-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="73fe6-109">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="73fe6-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="73fe6-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="73fe6-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="73fe6-111">V komunikaci ve frontě klient komunikuje se službou pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="73fe6-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="73fe6-112">Klient přesněji odesílá zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="73fe6-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="73fe6-113">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="73fe6-113">The service receives messages from the queue.</span></span> <span data-ttu-id="73fe6-114">Službu a klient proto nemusí běžet současně, aby bylo možné komunikovat pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="73fe6-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="73fe6-115">V některých případech klient odesílá sadu zpráv, které jsou vzájemně propojené ve skupině.</span><span class="sxs-lookup"><span data-stu-id="73fe6-115">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="73fe6-116">Pokud se zprávy musí zpracovávat společně nebo v zadaném pořadí, můžete k jejich seskupení použít frontu pro zpracování v rámci jedné přijímající aplikace.</span><span class="sxs-lookup"><span data-stu-id="73fe6-116">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="73fe6-117">To je důležité hlavně v případě, že je na skupině serverů několik přijímajících aplikací a je nutné zajistit, aby byla skupina zpráv zpracována stejnou přijímající aplikací.</span><span class="sxs-lookup"><span data-stu-id="73fe6-117">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="73fe6-118">Relace ve frontě jsou mechanizmus, který slouží k posílání a přijímání souvisejících sad zpráv, které musí zpracovat všechny najednou.</span><span class="sxs-lookup"><span data-stu-id="73fe6-118">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="73fe6-119">Relace ve frontě vyžadují transakci, která se projeví v tomto modelu.</span><span class="sxs-lookup"><span data-stu-id="73fe6-119">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="73fe6-120">V ukázce pošle klient několik zpráv do služby jako součást relace v rámci oboru jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="73fe6-120">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="73fe6-121">Kontrakt služby je `IOrderTaker`, který definuje jednosměrnou službu, která je vhodná pro použití s frontami.</span><span class="sxs-lookup"><span data-stu-id="73fe6-121">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="73fe6-122"><xref:System.ServiceModel.SessionMode> Použití v kontraktu uvedené v následujícím ukázkovém kódu indikuje, že zprávy jsou součástí relace.</span><span class="sxs-lookup"><span data-stu-id="73fe6-122">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface IOrderTaker  
{  
    [OperationContract(IsOneWay = true)]  
    void OpenPurchaseOrder(string customerId);  
  
    [OperationContract(IsOneWay = true)]  
    void AddProductLineItem(string productId, int quantity);  
  
    [OperationContract(IsOneWay = true)]  
    void EndPurchaseOrder();  
}  
```

 <span data-ttu-id="73fe6-123">Služba definuje operace služeb takovým způsobem, že první operace zařadí v transakci, ale neprovede automatické dokončení transakce.</span><span class="sxs-lookup"><span data-stu-id="73fe6-123">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="73fe6-124">Následující operace také zařadí do stejné transakce, ale neprovádí se automaticky.</span><span class="sxs-lookup"><span data-stu-id="73fe6-124">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="73fe6-125">Poslední operace v relaci automaticky dokončí transakci.</span><span class="sxs-lookup"><span data-stu-id="73fe6-125">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="73fe6-126">Proto se stejná transakce používá pro několik vyvolání operací v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="73fe6-126">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="73fe6-127">Pokud některá z operací vyvolá výjimku, transakce se vrátí zpět a relace se vrátí zpět do fronty.</span><span class="sxs-lookup"><span data-stu-id="73fe6-127">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="73fe6-128">Po úspěšném dokončení poslední operace se transakce potvrdí.</span><span class="sxs-lookup"><span data-stu-id="73fe6-128">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="73fe6-129">Služba používá `PerSession` <xref:System.ServiceModel.InstanceContextMode> jako pro příjem všech zpráv v relaci na stejné instanci služby.</span><span class="sxs-lookup"><span data-stu-id="73fe6-129">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class OrderTakerService : IOrderTaker  
{  
    PurchaseOrder po;  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                 TransactionAutoComplete = false)]  
    public void OpenPurchaseOrder(string customerId)  
    {  
        Console.WriteLine("Creating purchase order");  
        po = new PurchaseOrder(customerId);  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                  TransactionAutoComplete = false)]  
    public void AddProductLineItem(string productId, int quantity)  
    {  
        po.AddProductLineItem(productId, quantity);  
        Console.WriteLine("Product " + productId + " quantity " +   
                            quantity + " added to purchase order");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                  TransactionAutoComplete = true)]  
    public void EndPurchaseOrder()  
    {  
       Console.WriteLine("Purchase Order Completed");  
       Console.WriteLine();  
       Console.WriteLine(po.ToString());  
    }  
}  
```

 <span data-ttu-id="73fe6-130">Služba je hostována svým hostitelem.</span><span class="sxs-lookup"><span data-stu-id="73fe6-130">The service is self hosted.</span></span> <span data-ttu-id="73fe6-131">Při použití přenosu služby MSMQ musí být použitá fronta předem vytvořená.</span><span class="sxs-lookup"><span data-stu-id="73fe6-131">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="73fe6-132">To lze provést ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="73fe6-132">This can be done manually or through code.</span></span> <span data-ttu-id="73fe6-133">V této ukázce služba obsahuje <xref:System.Messaging> kód pro kontrolu existence fronty a v případě potřeby ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="73fe6-133">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="73fe6-134">Název fronty se načte z konfiguračního souboru pomocí <xref:System.Configuration.ConfigurationManager.AppSettings%2A> třídy.</span><span class="sxs-lookup"><span data-stu-id="73fe6-134">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderTakerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderTakerService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();   
    }  
}  
```

 <span data-ttu-id="73fe6-135">Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="73fe6-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="73fe6-136">Koncový bod pro službu je definován v oddílu System. ServiceModel konfiguračního souboru a určuje `netMsmqBinding` vazbu.</span><span class="sxs-lookup"><span data-stu-id="73fe6-136">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesSession" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesSession"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
      ...  
    </service>  
  </services>  
  ...  
<system.serviceModel>  
```  
  
 <span data-ttu-id="73fe6-137">Klient vytvoří obor transakce.</span><span class="sxs-lookup"><span data-stu-id="73fe6-137">The client creates a transaction scope.</span></span> <span data-ttu-id="73fe6-138">Všechny zprávy v relaci jsou odesílány do fronty v rámci oboru transakce, což způsobuje, že se bude považovat za atomickou jednotku, ve které všechny zprávy jsou úspěšné nebo neúspěšné.</span><span class="sxs-lookup"><span data-stu-id="73fe6-138">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="73fe6-139">Transakce je potvrzena voláním <xref:System.Transactions.TransactionScope.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="73fe6-139">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  

```csharp
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Create a client with given client endpoint configuration.  
    OrderTakerClient client = new OrderTakerClient("OrderTakerEndpoint");  
    // Open a purchase order.  
    client.OpenPurchaseOrder("somecustomer.com");  
    Console.WriteLine("Purchase Order created");  
  
    // Add product line items.  
    Console.WriteLine("Adding 10 quantities of blue widget");  
    client.AddProductLineItem("Blue Widget", 10);  
  
    Console.WriteLine("Adding 23 quantities of red widget");  
    client.AddProductLineItem("Red Widget", 23);  
  
    // Close the purchase order.  
    Console.WriteLine("Closing the purchase order");  
    client.EndPurchaseOrder();  
  
    //Closing the client gracefully closes the connection and cleans up resources.  
    client.Close();                  
  
    // Complete the transaction.  
    scope.Complete();  
}  
```

> [!NOTE]
> <span data-ttu-id="73fe6-140">Pro všechny zprávy v relaci lze použít pouze jednu transakci a všechny zprávy v relaci je nutné před potvrzením transakce odeslat.</span><span class="sxs-lookup"><span data-stu-id="73fe6-140">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="73fe6-141">Ukončení klienta ukončí relaci.</span><span class="sxs-lookup"><span data-stu-id="73fe6-141">Closing the client closes the session.</span></span> <span data-ttu-id="73fe6-142">Proto musí být klient před dokončením transakce uzavřen, aby odesílal všechny zprávy v relaci do fronty.</span><span class="sxs-lookup"><span data-stu-id="73fe6-142">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="73fe6-143">Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta.</span><span class="sxs-lookup"><span data-stu-id="73fe6-143">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="73fe6-144">Můžete vidět, že služba přijímá zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="73fe6-144">You can see the service receive messages from the client.</span></span> <span data-ttu-id="73fe6-145">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="73fe6-145">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="73fe6-146">Počítejte s tím, že protože se používá služba zařazování do fronty, klient a služba nemusí být spuštěny ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="73fe6-146">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="73fe6-147">Můžete spustit klienta, vypnout ho a pak spustit službu a nadále přijímat zprávy.</span><span class="sxs-lookup"><span data-stu-id="73fe6-147">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="73fe6-148">Na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="73fe6-148">On the client.</span></span>  
  
```  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="73fe6-149">Ve službě.</span><span class="sxs-lookup"><span data-stu-id="73fe6-149">On the service.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Creating purchase order  
Product Blue Widget quantity 10 added to purchase order  
Product Red Widget quantity 23 added to purchase order  
Purchase Order Completed  
  
Purchase Order: 7c86fef0-2306-4c51-80e6-bcabcc1a6e5e  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 10 of Blue Widget @unit price: $2985  
                Order LineItem: 23 of Red Widget @unit price: $156  
        Total cost of this order: $33438  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="73fe6-150">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="73fe6-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="73fe6-151">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73fe6-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="73fe6-152">Pokud chcete vytvořit C#edici, C++nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73fe6-152">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="73fe6-153">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73fe6-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="73fe6-154">Ve výchozím nastavení <xref:System.ServiceModel.NetMsmqBinding>je zapnuto zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="73fe6-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="73fe6-155">Existují dvě důležité vlastnosti pro zabezpečení přenosu ve službě MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` to ve výchozím nastavení je režim ověřování nastaven na `Windows` hodnotu a úroveň ochrany je nastavena na `Sign`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="73fe6-155">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="73fe6-156">Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény a musí být nainstalovaná možnost integrace služby Active Directory pro službu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="73fe6-156">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="73fe6-157">Pokud tuto ukázku spustíte na počítači, který nesplňuje tato kritéria, zobrazí se chyba.</span><span class="sxs-lookup"><span data-stu-id="73fe6-157">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="73fe6-158">Spuštění ukázky na počítači připojeném k pracovní skupině nebo bez integrace služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="73fe6-158">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="73fe6-159">Pokud počítač není součástí domény nebo nemáte nainstalovanou integraci služby Active Directory, vypněte zabezpečení přenosu nastavením režimu ověřování a úrovně ochrany tak `None` , jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="73fe6-159">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
                 behaviorConfiguration="OrderTakerServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress=  
             "http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint  
              address=  
            "net.msmq://localhost/private/ServiceModelSamplesSession"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
          <!-- The mex endpoint is exposed at-->      
          <!--http://localhost:8000/ServiceModelSamples/service/mex. -->  
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
            <behavior name="OrderTakerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2. <span data-ttu-id="73fe6-160">Před spuštěním ukázky se ujistěte, že jste změnili konfiguraci na serveru i v klientovi.</span><span class="sxs-lookup"><span data-stu-id="73fe6-160">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="73fe6-161">Nastavení režimu zabezpečení na `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>a `Message` zabezpečení na `None`.</span><span class="sxs-lookup"><span data-stu-id="73fe6-161">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
