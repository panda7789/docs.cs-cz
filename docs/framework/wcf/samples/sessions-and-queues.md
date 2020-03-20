---
title: Relace a fronty
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 8a342b185c7965e9ee0ff9941a09e00fc392ad4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144096"
---
# <a name="sessions-and-queues"></a><span data-ttu-id="0af30-102">Relace a fronty</span><span class="sxs-lookup"><span data-stu-id="0af30-102">Sessions and Queues</span></span>
<span data-ttu-id="0af30-103">Tato ukázka ukazuje, jak odesílat a přijímat sadu souvisejících zpráv ve frontové komunikaci prostřednictvím přenosu služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="0af30-103">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="0af30-104">Tato ukázka `netMsmqBinding` používá vazbu.</span><span class="sxs-lookup"><span data-stu-id="0af30-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="0af30-105">Služba je aplikace konzoly s vlastním hostitelem, která umožňuje sledovat službu přijímající zprávy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="0af30-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0af30-106">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="0af30-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0af30-107">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="0af30-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0af30-108">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="0af30-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0af30-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="0af30-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0af30-110">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0af30-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="0af30-111">Ve frontové komunikaci klient komunikuje se službou pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="0af30-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="0af30-112">Přesněji řečeno, klient odesílá zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="0af30-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="0af30-113">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="0af30-113">The service receives messages from the queue.</span></span> <span data-ttu-id="0af30-114">Služba a klient proto nemusí být spuštěny současně komunikovat pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="0af30-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="0af30-115">V některých případě klient odešle sadu zpráv, které spolu vzájemně souvisejí ve skupině.</span><span class="sxs-lookup"><span data-stu-id="0af30-115">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="0af30-116">Pokud zprávy musí být zpracovány společně nebo v zadaném pořadí, fronta může být použita k jejich seskupení, pro zpracování jednou přijímající aplikací.</span><span class="sxs-lookup"><span data-stu-id="0af30-116">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="0af30-117">To je obzvláště důležité v případě, že existuje několik přijímajících aplikací na skupině serverů a je nutné zajistit, aby skupina zpráv byla zpracována stejnou přijímající aplikací.</span><span class="sxs-lookup"><span data-stu-id="0af30-117">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="0af30-118">Relace ve frontě jsou mechanismus používaný k odesílání a přijímání související sady zpráv, které musí být zpracovány najednou.</span><span class="sxs-lookup"><span data-stu-id="0af30-118">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="0af30-119">Relace ve frontě vyžadují k zobrazení tohoto vzoru transakci.</span><span class="sxs-lookup"><span data-stu-id="0af30-119">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="0af30-120">V ukázce klient odešle několik zpráv do služby jako součást relace v rámci jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="0af30-120">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="0af30-121">Servisní smlouva `IOrderTaker`je , která definuje jednosměrnou službu, která je vhodná pro použití s frontami.</span><span class="sxs-lookup"><span data-stu-id="0af30-121">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="0af30-122">Použité <xref:System.ServiceModel.SessionMode> ve smlouvě uvedené v následujícím ukázkovém kódu označuje, že zprávy jsou součástí relace.</span><span class="sxs-lookup"><span data-stu-id="0af30-122">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  

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

 <span data-ttu-id="0af30-123">Služba definuje operace služby tak, že první operace zařadí do transakce, ale nedokončí automaticky transakci.</span><span class="sxs-lookup"><span data-stu-id="0af30-123">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="0af30-124">Následné operace také zařadit do stejné transakce, ale není automaticky dokončit.</span><span class="sxs-lookup"><span data-stu-id="0af30-124">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="0af30-125">Poslední operace v relaci automaticky dokončí transakci.</span><span class="sxs-lookup"><span data-stu-id="0af30-125">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="0af30-126">Stejná transakce se tedy používá pro několik vyvolání operace v servisní smlouvě.</span><span class="sxs-lookup"><span data-stu-id="0af30-126">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="0af30-127">Pokud některá z operací vyvolat výjimku, pak transakce vrátí zpět a relace je umístěn zpět do fronty.</span><span class="sxs-lookup"><span data-stu-id="0af30-127">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="0af30-128">Po úspěšném dokončení poslední operace je transakce potvrzena.</span><span class="sxs-lookup"><span data-stu-id="0af30-128">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="0af30-129">Služba používá `PerSession` jako <xref:System.ServiceModel.InstanceContextMode> přijímat všechny zprávy v relaci na stejné instanci služby.</span><span class="sxs-lookup"><span data-stu-id="0af30-129">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  

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

 <span data-ttu-id="0af30-130">Služba je hostována samostatně.</span><span class="sxs-lookup"><span data-stu-id="0af30-130">The service is self hosted.</span></span> <span data-ttu-id="0af30-131">Při použití přenosu služby MSMQ musí být použitá fronta vytvořena předem.</span><span class="sxs-lookup"><span data-stu-id="0af30-131">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="0af30-132">To lze provést ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="0af30-132">This can be done manually or through code.</span></span> <span data-ttu-id="0af30-133">V této ukázce služba obsahuje <xref:System.Messaging> kód pro kontrolu existence fronty a v případě potřeby ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="0af30-133">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="0af30-134">Název fronty se čte z konfiguračního souboru pomocí třídy. <xref:System.Configuration.ConfigurationManager.AppSettings%2A></span><span class="sxs-lookup"><span data-stu-id="0af30-134">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  

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

 <span data-ttu-id="0af30-135">Název fronty služby MSMQ je určen v části appSettings konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="0af30-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="0af30-136">Koncový bod pro službu je definován v části system.serviceModel konfiguračního souboru a určuje vazbu. `netMsmqBinding`</span><span class="sxs-lookup"><span data-stu-id="0af30-136">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
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
  
 <span data-ttu-id="0af30-137">Klient vytvoří obor transakce.</span><span class="sxs-lookup"><span data-stu-id="0af30-137">The client creates a transaction scope.</span></span> <span data-ttu-id="0af30-138">Všechny zprávy v relaci jsou odesílány do fronty v rámci oboru transakce, což způsobuje, že je považován za atomické jednotky, kde všechny zprávy úspěšné nebo neúspěšné.</span><span class="sxs-lookup"><span data-stu-id="0af30-138">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="0af30-139">Transakce je potvrzena <xref:System.Transactions.TransactionScope.Complete%2A>voláním .</span><span class="sxs-lookup"><span data-stu-id="0af30-139">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  

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
> <span data-ttu-id="0af30-140">Pro všechny zprávy v relaci můžete použít pouze jednu transakci a všechny zprávy v relaci musí být odeslány před potvrzením transakce.</span><span class="sxs-lookup"><span data-stu-id="0af30-140">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="0af30-141">Zavření klienta ukončí relaci.</span><span class="sxs-lookup"><span data-stu-id="0af30-141">Closing the client closes the session.</span></span> <span data-ttu-id="0af30-142">Proto musí být klient uzavřen před dokončením transakce odeslat všechny zprávy v relaci do fronty.</span><span class="sxs-lookup"><span data-stu-id="0af30-142">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="0af30-143">Při spuštění ukázky jsou aktivity klienta a služby zobrazeny v systému Windows služby i klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="0af30-143">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="0af30-144">Můžete vidět službu přijímat zprávy od klienta.</span><span class="sxs-lookup"><span data-stu-id="0af30-144">You can see the service receive messages from the client.</span></span> <span data-ttu-id="0af30-145">Stisknutím klávesy ENTER v každém okně konzoly vypněte službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="0af30-145">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="0af30-146">Všimněte si, že vzhledem k tomu, že je používána frontová služba, klient a služba nemusí být spuštěny současně.</span><span class="sxs-lookup"><span data-stu-id="0af30-146">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="0af30-147">Můžete spustit klienta, vypnout a potom spustit službu a stále přijímá jeho zprávy.</span><span class="sxs-lookup"><span data-stu-id="0af30-147">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="0af30-148">Na klienta.</span><span class="sxs-lookup"><span data-stu-id="0af30-148">On the client.</span></span>  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="0af30-149">Na bohoslužbě.</span><span class="sxs-lookup"><span data-stu-id="0af30-149">On the service.</span></span>  
  
```console  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0af30-150">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="0af30-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0af30-151">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0af30-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0af30-152">Chcete-li vytvořit c#, C++ nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0af30-152">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0af30-153">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0af30-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="0af30-154">Ve výchozím <xref:System.ServiceModel.NetMsmqBinding>nastavení je povoleno zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="0af30-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="0af30-155">Existují dvě relevantní vlastnosti zabezpečení přenosu služby <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` MSMQ a ve `Windows` výchozím nastavení je režim `Sign`ověřování nastaven na a úroveň ochrany je nastavena na hodnotu .</span><span class="sxs-lookup"><span data-stu-id="0af30-155">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="0af30-156">Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény a musí být nainstalována možnost integrace služby Active Directory pro službu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="0af30-156">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="0af30-157">Pokud spustíte tuto ukázku v počítači, který nesplňuje tato kritéria, zobrazí se chyba.</span><span class="sxs-lookup"><span data-stu-id="0af30-157">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="0af30-158">Spuštění ukázky v počítači připojovat se k pracovní skupině nebo bez integrace služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="0af30-158">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="0af30-159">Pokud počítač není součástí domény nebo není nainstalována integrace služby Active Directory, vypněte zabezpečení `None` přenosu nastavením režimu ověřování a úrovně ochrany na úroveň uvedenou v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="0af30-159">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
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
  
2. <span data-ttu-id="0af30-160">Před spuštěním ukázky se ujistěte, že změníte konfiguraci na serveru i na klientovi.</span><span class="sxs-lookup"><span data-stu-id="0af30-160">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0af30-161">Nastavení režimu `None` zabezpečení na <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>nastavení `Message` je `None`ekvivalentní nastavení a zabezpečení .</span><span class="sxs-lookup"><span data-stu-id="0af30-161">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
