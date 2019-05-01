---
title: Relace a fronty
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 623077450157b0bf87b85a85309adc10511b32b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007874"
---
# <a name="sessions-and-queues"></a><span data-ttu-id="e9be9-102">Relace a fronty</span><span class="sxs-lookup"><span data-stu-id="e9be9-102">Sessions and Queues</span></span>
<span data-ttu-id="e9be9-103">Tento příklad ukazuje, jak odesílat a přijímat sadu související zprávy ve frontě komunikace prostřednictvím přenosu služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="e9be9-103">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="e9be9-104">Tento příklad používá `netMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="e9be9-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="e9be9-105">Služba je v místním prostředí konzolovou aplikaci pro vám umožní sledovat službu přijímání zpráv zařazených do fronty.</span><span class="sxs-lookup"><span data-stu-id="e9be9-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9be9-106">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e9be9-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e9be9-107">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="e9be9-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e9be9-108">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e9be9-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e9be9-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e9be9-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e9be9-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e9be9-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="e9be9-111">V komunikaci ve frontě klient komunikuje se služby pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="e9be9-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="e9be9-112">Přesněji řečeno klient odešle zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="e9be9-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="e9be9-113">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="e9be9-113">The service receives messages from the queue.</span></span> <span data-ttu-id="e9be9-114">Klienta a služby, proto není potřeba běžet současně na komunikaci pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="e9be9-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="e9be9-115">V některých případech klient odešle sadu zpráv, které se vztahují k sobě navzájem ve skupině.</span><span class="sxs-lookup"><span data-stu-id="e9be9-115">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="e9be9-116">Pokud zprávy musí být zpracovány současně nebo v určeném pořadí, fronty je možné seskupit dohromady, pro účely zpracování jedné přijímající aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9be9-116">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="e9be9-117">To je zvlášť důležité, když jsou k dispozici několik přijímající aplikace pro skupinu serverů a je potřeba zajistit, že skupinu zpráv je zpracována stejným přijímající aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9be9-117">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="e9be9-118">Relace ve frontě jsou mechanismus používaný k odesílání a příjem související sadu zpráv, které musí zpracovat všechny najednou.</span><span class="sxs-lookup"><span data-stu-id="e9be9-118">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="e9be9-119">Relace ve frontě vyžadují transakci vykazovat tohoto modelu.</span><span class="sxs-lookup"><span data-stu-id="e9be9-119">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="e9be9-120">Ve vzorku klient odešle počet zpráv ve službě jako součást relaci v rámci jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="e9be9-120">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="e9be9-121">Kontrakt služby je `IOrderTaker`, která definuje jednosměrné, který je vhodný pro použití s frontami služby.</span><span class="sxs-lookup"><span data-stu-id="e9be9-121">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="e9be9-122"><xref:System.ServiceModel.SessionMode> Používaných pro smlouvy uvedené v následující vzorový kód označuje, že zprávy jsou součástí relace.</span><span class="sxs-lookup"><span data-stu-id="e9be9-122">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  

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

 <span data-ttu-id="e9be9-123">Služba definuje operace služby tak, že první operace využívá v rámci transakce, ale nebude automaticky dokončen transakce.</span><span class="sxs-lookup"><span data-stu-id="e9be9-123">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="e9be9-124">Následné operace také zařadit do jedné transakce, ale nedokončí automaticky.</span><span class="sxs-lookup"><span data-stu-id="e9be9-124">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="e9be9-125">Poslední operaci v relaci se automaticky dokončí transakce.</span><span class="sxs-lookup"><span data-stu-id="e9be9-125">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="e9be9-126">Díky tomu se stejnou transakci se používá pro několik vyvolání operace v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="e9be9-126">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="e9be9-127">Pokud všechny operace, vyvolá výjimku, transakce se vrátí zpět a relace se znovu zařadí do fronty.</span><span class="sxs-lookup"><span data-stu-id="e9be9-127">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="e9be9-128">Po úspěšném dokončení poslední operace transakce se potvrzeny.</span><span class="sxs-lookup"><span data-stu-id="e9be9-128">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="e9be9-129">Služba používá `PerSession` jako <xref:System.ServiceModel.InstanceContextMode> přijímat všechny zprávy v relaci ve stejné instanci služby.</span><span class="sxs-lookup"><span data-stu-id="e9be9-129">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  

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

 <span data-ttu-id="e9be9-130">Tato služba je vlastní hostované.</span><span class="sxs-lookup"><span data-stu-id="e9be9-130">The service is self hosted.</span></span> <span data-ttu-id="e9be9-131">Při použití přenosu služby MSMQ, fronty, používá se musí vytvořit předem.</span><span class="sxs-lookup"><span data-stu-id="e9be9-131">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="e9be9-132">To můžete udělat ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="e9be9-132">This can be done manually or through code.</span></span> <span data-ttu-id="e9be9-133">V této ukázce obsahuje službu <xref:System.Messaging> kódu k provedení kontroly existence fronty a vytvoří, pokud je to nutné.</span><span class="sxs-lookup"><span data-stu-id="e9be9-133">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="e9be9-134">Název fronty je pro čtení v konfiguračním souboru pomocí <xref:System.Configuration.ConfigurationManager.AppSettings%2A> třídy.</span><span class="sxs-lookup"><span data-stu-id="e9be9-134">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  

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

 <span data-ttu-id="e9be9-135">Název fronty MSMQ je zadán v oddílu appSettings konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="e9be9-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="e9be9-136">Koncový bod služby je definován v oddíle system.serviceModel konfiguračního souboru a určuje, `netMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="e9be9-136">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
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
  
 <span data-ttu-id="e9be9-137">Klient vytvoří obor transakce.</span><span class="sxs-lookup"><span data-stu-id="e9be9-137">The client creates a transaction scope.</span></span> <span data-ttu-id="e9be9-138">Všechny zprávy v relaci se odesílají do fronty v rámci oboru transakcí, vyvolá zacházet jako atomickou jednotku, kde všechny zprávy úspěch nebo neúspěch.</span><span class="sxs-lookup"><span data-stu-id="e9be9-138">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="e9be9-139">Transakce se potvrdí při volání <xref:System.Transactions.TransactionScope.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="e9be9-139">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  

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
>  <span data-ttu-id="e9be9-140">Pouze jedné transakce můžete použít pro všechny zprávy v relaci a všechny zprávy v relaci musí být odeslán před potvrzením transakce.</span><span class="sxs-lookup"><span data-stu-id="e9be9-140">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="e9be9-141">Zavírá klienta ukončí relace.</span><span class="sxs-lookup"><span data-stu-id="e9be9-141">Closing the client closes the session.</span></span> <span data-ttu-id="e9be9-142">Klient proto musí být uzavřen předtím, než je transakce dokončena všechny zprávy v relaci odeslány do fronty.</span><span class="sxs-lookup"><span data-stu-id="e9be9-142">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="e9be9-143">Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="e9be9-143">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="e9be9-144">Můžete zobrazit přijetí zprávy služby z klienta.</span><span class="sxs-lookup"><span data-stu-id="e9be9-144">You can see the service receive messages from the client.</span></span> <span data-ttu-id="e9be9-145">Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="e9be9-145">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="e9be9-146">Mějte na paměti, protože služba Řízení front se používá, klient a služba nemusí být zprovoznit ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="e9be9-146">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="e9be9-147">Můžete spustit klienta, vypněte ho a spusťte službu a stále přijímá zprávy.</span><span class="sxs-lookup"><span data-stu-id="e9be9-147">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="e9be9-148">Na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="e9be9-148">On the client.</span></span>  
  
```  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="e9be9-149">Ve službě.</span><span class="sxs-lookup"><span data-stu-id="e9be9-149">On the service.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e9be9-150">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="e9be9-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e9be9-151">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e9be9-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e9be9-152">K sestavení edice řešení C#, C++ nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e9be9-152">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e9be9-153">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e9be9-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="e9be9-154">Ve výchozím nastavení se <xref:System.ServiceModel.NetMsmqBinding>, je povoleno zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="e9be9-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="e9be9-155">Existují dvě vlastnosti důležité pro zabezpečení přenosu služby MSMQ konkrétně <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` výchozí režim ověřování nastaven na `Windows` a aby úroveň ochrany je nastavená na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="e9be9-155">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="e9be9-156">Pro službu MSMQ. k ověřování a podepisování funkce musí být součástí domény a možnost integrace služby active directory pro službu MSMQ musí být nainstalována.</span><span class="sxs-lookup"><span data-stu-id="e9be9-156">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="e9be9-157">Pokud tuto ukázku spustit na počítači, který nevyhovuje těmto kritériím zobrazí chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="e9be9-157">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="e9be9-158">Ke spuštění ukázky na počítač připojen k pracovní skupině nebo bez integrace služby active directory</span><span class="sxs-lookup"><span data-stu-id="e9be9-158">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="e9be9-159">Pokud počítač není součástí domény nebo nemá nainstalované integrace služby active directory, vypněte zabezpečení přenosu nastavením úroveň ověření režimu a ochrany na `None` jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e9be9-159">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
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
  
2. <span data-ttu-id="e9be9-160">Ujistěte se, že změníte konfiguraci na serveru a klienta, před spuštěním ukázky.</span><span class="sxs-lookup"><span data-stu-id="e9be9-160">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e9be9-161">Nastavení režimu zabezpečení `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, a `Message` zabezpečení `None`.</span><span class="sxs-lookup"><span data-stu-id="e9be9-161">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
