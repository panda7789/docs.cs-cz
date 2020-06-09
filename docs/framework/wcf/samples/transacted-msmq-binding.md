---
title: Zpracované vazby služby MSMQ
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: fa53099caba144f321698f180fe18f7614a1fa64
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596562"
---
# <a name="transacted-msmq-binding"></a><span data-ttu-id="397ab-102">Zpracované vazby služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="397ab-102">Transacted MSMQ Binding</span></span>

<span data-ttu-id="397ab-103">Tato ukázka předvádí, jak pomocí služby Řízení front zpráv (MSMQ) provádět komunikaci v transakční frontě.</span><span class="sxs-lookup"><span data-stu-id="397ab-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>

> [!NOTE]
> <span data-ttu-id="397ab-104">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="397ab-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="397ab-105">V komunikaci ve frontě klient komunikuje se službou pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="397ab-105">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="397ab-106">Klient přesněji odesílá zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="397ab-106">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="397ab-107">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="397ab-107">The service receives messages from the queue.</span></span> <span data-ttu-id="397ab-108">Služba a klient proto nemusí být spuštěná ve stejnou dobu, aby komunikovala s použitím fronty.</span><span class="sxs-lookup"><span data-stu-id="397ab-108">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="397ab-109">Pokud se pro posílání a přijímání zpráv používají transakce, jsou ve skutečnosti dvě samostatné transakce.</span><span class="sxs-lookup"><span data-stu-id="397ab-109">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="397ab-110">Když klient pošle zprávy v rámci oboru transakce, transakce je místní pro klienta a správce front klientů.</span><span class="sxs-lookup"><span data-stu-id="397ab-110">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="397ab-111">Když služba obdrží zprávy v rámci oboru transakce, transakce je místní pro službu a přijímacího správce fronty.</span><span class="sxs-lookup"><span data-stu-id="397ab-111">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="397ab-112">Je velmi důležité si uvědomit, že klient a služba nejsou zapojeny do stejné transakce; místo toho používají různé transakce při provádění jejich operací (jako je například posílání a přijímání) s frontou.</span><span class="sxs-lookup"><span data-stu-id="397ab-112">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>

<span data-ttu-id="397ab-113">V této ukázce klient pošle dávku zpráv službě v rámci rozsahu transakce.</span><span class="sxs-lookup"><span data-stu-id="397ab-113">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="397ab-114">Zprávy odeslané do fronty jsou poté přijímány službou v rámci oboru transakce definovaném službou.</span><span class="sxs-lookup"><span data-stu-id="397ab-114">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>

<span data-ttu-id="397ab-115">Kontrakt služby je `IOrderProcessor` , jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="397ab-115">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="397ab-116">Rozhraní definuje jednosměrnou službu, která je vhodná pro použití s frontami.</span><span class="sxs-lookup"><span data-stu-id="397ab-116">The interface defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

<span data-ttu-id="397ab-117">Chování služby definuje chování operace s `TransactionScopeRequired` nastavením na `true` .</span><span class="sxs-lookup"><span data-stu-id="397ab-117">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="397ab-118">Tím se zajistí, že stejný obor transakce, který se použije k načtení zprávy z fronty, je používán všemi správci prostředků, ke kterým přistupovala metoda.</span><span class="sxs-lookup"><span data-stu-id="397ab-118">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="397ab-119">Zaručuje také, že pokud metoda vyvolá výjimku, zpráva se vrátí do fronty.</span><span class="sxs-lookup"><span data-stu-id="397ab-119">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="397ab-120">Bez nastavení této operace vytvoří kanál zařazený do fronty transakci, která načte zprávu z fronty a potvrdí ji automaticky před odesláním tak, že pokud operace nebude úspěšná, zpráva se ztratí.</span><span class="sxs-lookup"><span data-stu-id="397ab-120">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="397ab-121">Nejběžnějším scénářem je, aby se operace služby zařadí do transakce, která se používá ke čtení zprávy z fronty, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="397ab-121">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>

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

<span data-ttu-id="397ab-122">Služba je hostována svým hostitelem.</span><span class="sxs-lookup"><span data-stu-id="397ab-122">The service is self hosted.</span></span> <span data-ttu-id="397ab-123">Při použití přenosu služby MSMQ musí být použitá fronta předem vytvořená.</span><span class="sxs-lookup"><span data-stu-id="397ab-123">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="397ab-124">To lze provést ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="397ab-124">This can be done manually or through code.</span></span> <span data-ttu-id="397ab-125">V této ukázce služba obsahuje kód pro kontrolu existence fronty a vytvoření fronty, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="397ab-125">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="397ab-126">Název fronty se načte z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="397ab-126">The queue name is read from the configuration file.</span></span> <span data-ttu-id="397ab-127">Základní adresa je používána [nástrojem Svcutil. exe](../servicemodel-metadata-utility-tool-svcutil-exe.md) pro vygenerování proxy serveru ke službě.</span><span class="sxs-lookup"><span data-stu-id="397ab-127">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>

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

<span data-ttu-id="397ab-128">Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="397ab-128">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="397ab-129">Název fronty používá tečku (.) pro místní počítač a oddělovače zpětného lomítka v cestě při vytváření fronty pomocí <xref:System.Messaging> .</span><span class="sxs-lookup"><span data-stu-id="397ab-129">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="397ab-130">Koncový bod služby Windows Communication Foundation (WCF) používá adresu fronty se schématem NET. MSMQ, používá localhost k označení místního počítače a používá lomítka v cestě.</span><span class="sxs-lookup"><span data-stu-id="397ab-130">The Windows Communication Foundation (WCF) endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>

<span data-ttu-id="397ab-131">Klient vytvoří obor transakce.</span><span class="sxs-lookup"><span data-stu-id="397ab-131">The client creates a transaction scope.</span></span> <span data-ttu-id="397ab-132">Komunikace s frontou probíhá v rámci rozsahu transakce, což způsobuje, že se bude považovat za atomickou jednotku, do které jsou odesílány všechny zprávy do fronty, nebo žádná z zpráv není odeslána do fronty.</span><span class="sxs-lookup"><span data-stu-id="397ab-132">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="397ab-133">Transakce je potvrzena voláním <xref:System.Transactions.TransactionScope.Complete%2A> v oboru transakce.</span><span class="sxs-lookup"><span data-stu-id="397ab-133">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>

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

<span data-ttu-id="397ab-134">Chcete-li ověřit, zda transakce fungují, upravte klienta přidáním komentáře k oboru transakce, jak je znázorněno v následujícím ukázkovém kódu, znovu sestavte řešení a spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="397ab-134">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>

```csharp
//scope.Complete();
```

<span data-ttu-id="397ab-135">Vzhledem k tomu, že transakce není dokončena, zprávy nejsou odesílány do fronty.</span><span class="sxs-lookup"><span data-stu-id="397ab-135">Because the transaction is not completed, the messages are not sent to the queue.</span></span>

<span data-ttu-id="397ab-136">Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta.</span><span class="sxs-lookup"><span data-stu-id="397ab-136">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="397ab-137">Můžete vidět, že služba přijímá zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="397ab-137">You can see the service receive messages from the client.</span></span> <span data-ttu-id="397ab-138">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="397ab-138">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="397ab-139">Počítejte s tím, že protože se používá služba zařazování do fronty, klient a služba nemusí být spuštěny ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="397ab-139">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="397ab-140">Můžete spustit klienta, vypnout ho a pak spustit službu a pořád zprávy obdrží.</span><span class="sxs-lookup"><span data-stu-id="397ab-140">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>

```console
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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="397ab-141">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="397ab-141">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="397ab-142">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="397ab-142">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="397ab-143">Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici.</span><span class="sxs-lookup"><span data-stu-id="397ab-143">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="397ab-144">Pokud fronta není přítomna, služba ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="397ab-144">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="397ab-145">Službu můžete nejdřív spustit, abyste mohli vytvořit frontu, nebo ji můžete vytvořit pomocí Správce fronty MSMQ.</span><span class="sxs-lookup"><span data-stu-id="397ab-145">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="397ab-146">Pomocí těchto kroků vytvořte ve Windows 2008 frontu.</span><span class="sxs-lookup"><span data-stu-id="397ab-146">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="397ab-147">Otevřete Správce serveru v aplikaci Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="397ab-147">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="397ab-148">Rozbalte kartu **funkce** .</span><span class="sxs-lookup"><span data-stu-id="397ab-148">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="397ab-149">Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **Nový**, **soukromá fronta**.</span><span class="sxs-lookup"><span data-stu-id="397ab-149">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="397ab-150">Zaškrtněte políčko **transakční** .</span><span class="sxs-lookup"><span data-stu-id="397ab-150">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="397ab-151">`ServiceModelSamplesTransacted`Jako název nové fronty zadejte.</span><span class="sxs-lookup"><span data-stu-id="397ab-151">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="397ab-152">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="397ab-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="397ab-153">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="397ab-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="397ab-154">Ve výchozím nastavení <xref:System.ServiceModel.NetMsmqBinding> je zapnuto zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="397ab-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="397ab-155">Existují dvě důležité vlastnosti pro zabezpečení přenosu ve službě MSMQ <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> .</span><span class="sxs-lookup"><span data-stu-id="397ab-155">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="397ab-156">Ve výchozím nastavení je režim ověřování nastaven na hodnotu `Windows` a úroveň ochrany je nastavena na hodnotu `Sign` .</span><span class="sxs-lookup"><span data-stu-id="397ab-156">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="397ab-157">Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény a musí být nainstalovaná možnost integrace služby Active Directory pro službu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="397ab-157">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="397ab-158">Pokud tuto ukázku spustíte na počítači, který nesplňuje tato kritéria, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="397ab-158">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="397ab-159">Spuštění ukázky na počítači připojeném k pracovní skupině nebo bez integrace služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="397ab-159">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>

1. <span data-ttu-id="397ab-160">Pokud počítač není součástí domény nebo nemáte nainstalovanou integraci služby Active Directory, vypněte zabezpečení přenosu nastavením režimu ověřování a úrovně ochrany tak, `None` jak je znázorněno v následujícím ukázkovém kódu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="397ab-160">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>

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
          <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
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

2. <span data-ttu-id="397ab-161">Před spuštěním ukázky se ujistěte, že jste změnili konfiguraci na serveru i v klientovi.</span><span class="sxs-lookup"><span data-stu-id="397ab-161">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="397ab-162">Nastavení `security mode` na `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> , <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> a `Message` zabezpečení na `None` .</span><span class="sxs-lookup"><span data-stu-id="397ab-162">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="397ab-163">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="397ab-163">The samples may already be installed on your computer.</span></span> <span data-ttu-id="397ab-164">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="397ab-164">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="397ab-165">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="397ab-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="397ab-166">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="397ab-166">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`
