---
title: Řízení front zpráv do WCF
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 74cac9789dc187b4940b67e94d726471f978a472
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930653"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="6d53c-102">Řízení front zpráv do WCF</span><span class="sxs-lookup"><span data-stu-id="6d53c-102">Message Queuing to Windows Communication Foundation</span></span>
<span data-ttu-id="6d53c-103">Tato ukázka předvádí, jak může aplikace řízení front zpráv (MSMQ) odesílat zprávy MSMQ službě Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6d53c-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="6d53c-104">Služba je samoobslužná Konzolová aplikace, která vám umožní sledovat službu přijímající zprávy zařazené do fronty.</span><span class="sxs-lookup"><span data-stu-id="6d53c-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
 <span data-ttu-id="6d53c-105">Kontrakt služby je `IOrderProcessor`, který definuje jednosměrnou službu, která je vhodná pro použití s frontami.</span><span class="sxs-lookup"><span data-stu-id="6d53c-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="6d53c-106">Zpráva služby MSMQ neobsahuje záhlaví akce, takže není možné automaticky mapovat různé zprávy MSMQ na provozní kontrakty.</span><span class="sxs-lookup"><span data-stu-id="6d53c-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="6d53c-107">Proto může existovat pouze jedna kontrakt operace.</span><span class="sxs-lookup"><span data-stu-id="6d53c-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="6d53c-108">Pokud chcete pro službu definovat více než jednu kontrakt operace, aplikace musí poskytnout informace o tom, které záhlaví ve zprávě služby MSMQ (například popisek nebo ID korelace) se dá použít k rozhodnutí, který kontrakt operace se má odeslat.</span><span class="sxs-lookup"><span data-stu-id="6d53c-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span>
  
 <span data-ttu-id="6d53c-109">Zpráva služby MSMQ neobsahuje informace o tom, která záhlaví jsou namapována na různé parametry kontraktu operace.</span><span class="sxs-lookup"><span data-stu-id="6d53c-109">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="6d53c-110">Parametr je typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), který obsahuje podkladovou zprávu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6d53c-110">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="6d53c-111">Typ "T" v <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>třídě (`MsmqMessage<T>`) představuje data serializovaná do těla zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6d53c-111">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="6d53c-112">V této ukázce `PurchaseOrder` je typ serializován do těla zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6d53c-112">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  
  
 <span data-ttu-id="6d53c-113">Následující vzorový kód ukazuje kontrakt služby pro službu zpracování objednávek.</span><span class="sxs-lookup"><span data-stu-id="6d53c-113">The following sample code shows the service contract of the order processing service.</span></span>  

```csharp
// Define a service contract.
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="6d53c-114">Služba je hostována svým hostitelem.</span><span class="sxs-lookup"><span data-stu-id="6d53c-114">The service is self hosted.</span></span> <span data-ttu-id="6d53c-115">Při použití služby MSMQ musí být použitá fronta vytvořená předem.</span><span class="sxs-lookup"><span data-stu-id="6d53c-115">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="6d53c-116">To lze provést ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="6d53c-116">This can be done manually or through code.</span></span> <span data-ttu-id="6d53c-117">V této ukázce služba kontroluje existenci fronty a v případě potřeby ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="6d53c-117">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="6d53c-118">Název fronty se načte z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="6d53c-118">The queue name is read from the configuration file.</span></span>

```csharp
public static void Main()
{
    // Get the MSMQ queue name from the application settings in
    // configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];
    // Create the MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName, true);
    …
}
```

 <span data-ttu-id="6d53c-119">Služba vytvoří a otevře <xref:System.ServiceModel.ServiceHost> `OrderProcessorService`pro, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="6d53c-119">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
    serviceHost.Open();
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
    serviceHost.Close();
}
```

 <span data-ttu-id="6d53c-120">Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="6d53c-120">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="6d53c-121">Název fronty pro místní počítač a oddělovače zpětného lomítka v cestě používá tečku (.).</span><span class="sxs-lookup"><span data-stu-id="6d53c-121">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="6d53c-122">Adresa koncového bodu WCF Určuje schéma služby MSMQ. formatname a pro místní počítač používá localhost.</span><span class="sxs-lookup"><span data-stu-id="6d53c-122">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="6d53c-123">Adresa fronty pro každý název formátu MSMQ pokyny pro adresování se řídí schématem MSMQ. FormatName.</span><span class="sxs-lookup"><span data-stu-id="6d53c-123">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="6d53c-124">Klientská aplikace je aplikace služby MSMQ, která používá <xref:System.Messaging.MessageQueue.Send%2A> metodu k odeslání trvalé a transakční zprávy do fronty, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="6d53c-124">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>

```csharp
//Connect to the queue.
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);

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

// Submit the purchase order.
Message msg = new Message();
msg.Body = po;
//Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{

    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
    // Complete the transaction.
    scope.Complete();

}
Console.WriteLine("Placed the order:{0}", po);
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 <span data-ttu-id="6d53c-125">Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta.</span><span class="sxs-lookup"><span data-stu-id="6d53c-125">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="6d53c-126">Můžete vidět, že služba přijímá zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="6d53c-126">You can see the service receive messages from the client.</span></span> <span data-ttu-id="6d53c-127">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="6d53c-127">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="6d53c-128">Počítejte s tím, že protože se používá služba zařazování do fronty, klient a služba nemusí být spuštěny ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="6d53c-128">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="6d53c-129">Můžete třeba spustit klienta, vypnout ho a pak službu spustit a zároveň se jim budou zobrazovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="6d53c-129">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="6d53c-130">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="6d53c-130">To setup, build, and run the sample</span></span>

1. <span data-ttu-id="6d53c-131">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6d53c-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6d53c-132">Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6d53c-132">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="6d53c-133">Pokud fronta není přítomna, služba ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="6d53c-133">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="6d53c-134">Službu můžete nejdřív spustit, abyste mohli vytvořit frontu, nebo ji můžete vytvořit pomocí Správce fronty MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6d53c-134">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="6d53c-135">Pomocí těchto kroků vytvořte ve Windows 2008 frontu.</span><span class="sxs-lookup"><span data-stu-id="6d53c-135">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="6d53c-136">Otevřete Správce serveru v aplikaci Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="6d53c-136">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="6d53c-137">Rozbalte kartu **funkce** .</span><span class="sxs-lookup"><span data-stu-id="6d53c-137">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="6d53c-138">Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **Nový**, **soukromá fronta**.</span><span class="sxs-lookup"><span data-stu-id="6d53c-138">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="6d53c-139">Zaškrtněte políčko **transakční** .</span><span class="sxs-lookup"><span data-stu-id="6d53c-139">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="6d53c-140">Jako `ServiceModelSamplesTransacted` název nové fronty zadejte.</span><span class="sxs-lookup"><span data-stu-id="6d53c-140">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="6d53c-141">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6d53c-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="6d53c-142">Chcete-li spustit ukázku v konfiguraci s jedním počítačem, postupujte podle pokynů v [části spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6d53c-142">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="6d53c-143">Spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="6d53c-143">To run the sample across computers</span></span>

1. <span data-ttu-id="6d53c-144">Zkopírujte programové soubory služby ze složky \service\bin\ ve složce specifické pro daný jazyk do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="6d53c-144">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="6d53c-145">Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="6d53c-145">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="6d53c-146">V souboru Client. exe. config změňte orderQueueName a zadejte název počítače služby místo ".".</span><span class="sxs-lookup"><span data-stu-id="6d53c-146">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="6d53c-147">Na počítači služby spusťte z příkazového řádku Service. exe.</span><span class="sxs-lookup"><span data-stu-id="6d53c-147">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="6d53c-148">V klientském počítači spusťte z příkazového řádku soubor Client. exe.</span><span class="sxs-lookup"><span data-stu-id="6d53c-148">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="6d53c-149">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="6d53c-149">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6d53c-150">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="6d53c-150">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6d53c-151">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="6d53c-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6d53c-152">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6d53c-152">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a><span data-ttu-id="6d53c-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d53c-153">See also</span></span>

- [<span data-ttu-id="6d53c-154">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="6d53c-154">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="6d53c-155">Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="6d53c-155">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="6d53c-156">Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="6d53c-156">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
