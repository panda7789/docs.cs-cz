---
title: Nestálá komunikace ve frontě
ms.date: 03/30/2017
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
ms.openlocfilehash: 8ed10262d319664d404e6beb630593cb93748a7d
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715283"
---
# <a name="volatile-queued-communication"></a><span data-ttu-id="4036b-102">Nestálá komunikace ve frontě</span><span class="sxs-lookup"><span data-stu-id="4036b-102">Volatile Queued Communication</span></span>

<span data-ttu-id="4036b-103">Tato ukázka předvádí, jak provést nestálou komunikaci ve frontě prostřednictvím přenosu služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="4036b-103">This sample demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="4036b-104">Tato ukázka používá <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="4036b-104">This sample uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="4036b-105">Tato služba je v tomto případě samoobslužná Konzolová aplikace, která vám umožní sledovat službu přijímající zprávy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="4036b-105">The service in this case is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="4036b-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4036b-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="4036b-107">V komunikaci ve frontě klient komunikuje se službou pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="4036b-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="4036b-108">Klient přesněji odesílá zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="4036b-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="4036b-109">Služba přijímá zprávy z fronty.</span><span class="sxs-lookup"><span data-stu-id="4036b-109">The service receives messages from the queue.</span></span> <span data-ttu-id="4036b-110">Službu a klient proto nemusí běžet současně, aby bylo možné komunikovat pomocí fronty.</span><span class="sxs-lookup"><span data-stu-id="4036b-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="4036b-111">Když odešlete zprávu bez jakýchkoli ujištění, služba MSMQ bude k dispozici jenom k tomu, aby se tato zpráva dostala na rozdíl od přesně po ujištění, že služba MSMQ zajišťuje doručení zprávy, nebo pokud nemůže být doručena, a oznamuje, že zprávu nelze doručit.</span><span class="sxs-lookup"><span data-stu-id="4036b-111">When you send a message with no assurances, MSMQ only makes a best effort to deliver the message, unlike with Exactly Once assurances where MSMQ ensures that the message gets delivered or, if it cannot be delivered, lets you know that the message cannot be delivered.</span></span>

<span data-ttu-id="4036b-112">V některých scénářích můžete chtít poslat nestálou zprávu bez jakýchkoli zárukou v rámci fronty, pokud je včasné doručování důležitější než ztráty zpráv.</span><span class="sxs-lookup"><span data-stu-id="4036b-112">In certain scenarios, you may want to send a volatile message with no assurances over a queue, when timely delivery is more important than losing messages.</span></span> <span data-ttu-id="4036b-113">Nestálé zprávy neobsahují chyby Správce fronty.</span><span class="sxs-lookup"><span data-stu-id="4036b-113">Volatile messages do not survive queue manager crashes.</span></span> <span data-ttu-id="4036b-114">Proto pokud správce front dojde k chybě, netransakční fronta používaná k ukládání netransakčních zpráv se zachovají, ale zprávy samotné neobsahují, protože zprávy nejsou uloženy na disku.</span><span class="sxs-lookup"><span data-stu-id="4036b-114">Therefore if the queue manager crashes, the non-transactional queue used to store volatile messages survives but the messages themselves do not because the messages are not stored on the disk.</span></span>

> [!NOTE]
> <span data-ttu-id="4036b-115">Nemůžete posílat nestálé zprávy bez zárukou v rámci rozsahu transakce pomocí služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4036b-115">You cannot send volatile messages with no assurances within the scope of a transaction using MSMQ.</span></span> <span data-ttu-id="4036b-116">Je také nutné vytvořit netransakční frontu pro odesílání nestálých zpráv.</span><span class="sxs-lookup"><span data-stu-id="4036b-116">You also must create a non-transactional queue to send volatile messages.</span></span>

<span data-ttu-id="4036b-117">Kontrakt služby v této ukázce je `IStockTicker`, který definuje jednosměrné služby, které jsou nejvhodnější pro použití s řazením do fronty.</span><span class="sxs-lookup"><span data-stu-id="4036b-117">The service contract in this sample is `IStockTicker` that defines one-way services that are best suited for use with queuing.</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void StockTick(string symbol, float price);
}
```

<span data-ttu-id="4036b-118">Operace služby zobrazuje burzovní symbol a cenu, jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="4036b-118">The service operation displays the stock ticker symbol and price, as shown in the following sample code:</span></span>

```csharp
public class StockTickerService : IStockTicker
{
    public void StockTick(string symbol, float price)
    {
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);
     }
     …
}
```

<span data-ttu-id="4036b-119">Služba je hostována svým hostitelem.</span><span class="sxs-lookup"><span data-stu-id="4036b-119">The service is self hosted.</span></span> <span data-ttu-id="4036b-120">Při použití přenosu služby MSMQ musí být použitá fronta předem vytvořená.</span><span class="sxs-lookup"><span data-stu-id="4036b-120">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="4036b-121">To lze provést ručně nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="4036b-121">This can be done manually or through code.</span></span> <span data-ttu-id="4036b-122">V této ukázce služba obsahuje kód pro kontrolu existence fronty a v případě potřeby ji vytvoří.</span><span class="sxs-lookup"><span data-stu-id="4036b-122">In this sample, the service contains code to check for the existence of the queue and create it if required.</span></span> <span data-ttu-id="4036b-123">Název fronty se načte z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="4036b-123">The queue name is read from the configuration file.</span></span> <span data-ttu-id="4036b-124">Základní adresa je používána [nástrojem Svcutil. exe](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pro vygenerování proxy serveru pro službu.</span><span class="sxs-lookup"><span data-stu-id="4036b-124">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy for the service.</span></span>

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get MSMQ queue name from app settings in configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];

    // Create the transacted MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName);

    // Create a ServiceHost for the StockTickerService type.
    using (ServiceHost serviceHost = new ServiceHost(typeof(StockTickerService)))
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

<span data-ttu-id="4036b-125">Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="4036b-125">The MSMQ queue name is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="4036b-126">Koncový bod pro službu je definován v oddílu System. serviceModel konfiguračního souboru a určuje `netMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="4036b-126">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>

> [!NOTE]
> <span data-ttu-id="4036b-127">Název fronty používá tečku (.) pro místní počítač a oddělovače zpětného lomítka v cestě při vytváření fronty pomocí <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="4036b-127">The queue name uses a dot (.) for the local machine and backslash separators in its path when creating a queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="4036b-128">Adresa koncového bodu služby Windows Communication Foundation (WCF) určuje položku NET. MSMQ: schéma, pro místní počítač a lomítka v cestě používá localhost.</span><span class="sxs-lookup"><span data-stu-id="4036b-128">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine and forward slashes in its path.</span></span>

<span data-ttu-id="4036b-129">V konfiguraci jsou uvedeny také záruky a odolnost proti nestálosti zpráv.</span><span class="sxs-lookup"><span data-stu-id="4036b-129">The assurances and durability or volatility of messages are also specified in the configuration.</span></span>

```xml
<appSettings>
  <!-- use appSetting to configure MSMQ queue name -->
  <add key="queueName" value=".\private$\ServiceModelSamplesVolatile" />
</appSettings>

<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.StockTickerService"
             behaviorConfiguration="CalculatorServiceBehavior">
    ...
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                binding="netMsmqBinding"
                bindingConfiguration="volatileBinding"
                contract="Microsoft.ServiceModel.Samples.IStockTicker" />
    ...
    </service>
  </services>

  <bindings>
    <netMsmqBinding>
      <binding name="volatileBinding"
             durable="false"
           exactlyOnce="false"/>
    </netMsmqBinding>
  </bindings>
  ...
</system.serviceModel>
```

<span data-ttu-id="4036b-130">Vzhledem k tomu, že ukázka odesílá zprávy ve frontě pomocí netransakční fronty, nelze odeslat transakční zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="4036b-130">Because the sample sends queued messages by using a non-transactional queue, transacted messages cannot be sent to the queue.</span></span>

```csharp
// Create a client.
Random r = new Random(137);

StockTickerClient client = new StockTickerClient();

float price = 43.23F;
for (int i = 0; i < 10; i++)
{
    float increment = 0.01f * (r.Next(10));
    client.StockTick("zzz" + i, price + increment);
}

//Closing the client gracefully cleans up resources.
client.Close();
```

<span data-ttu-id="4036b-131">Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta.</span><span class="sxs-lookup"><span data-stu-id="4036b-131">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="4036b-132">Můžete vidět, že služba přijímá zprávy z klienta.</span><span class="sxs-lookup"><span data-stu-id="4036b-132">You can see the service receive messages from the client.</span></span> <span data-ttu-id="4036b-133">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="4036b-133">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="4036b-134">Počítejte s tím, že protože se používá služba zařazování do fronty, klient a služba nemusí být spuštěny ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="4036b-134">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="4036b-135">Můžete spustit klienta, vypnout ho a pak spustit službu a nadále přijímat zprávy.</span><span class="sxs-lookup"><span data-stu-id="4036b-135">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Stock Tick zzz0:43.25
Stock Tick zzz1:43.23
Stock Tick zzz2:43.28
Stock Tick zzz3:43.3
Stock Tick zzz4:43.23
Stock Tick zzz5:43.25
Stock Tick zzz6:43.25
Stock Tick zzz7:43.24
Stock Tick zzz8:43.32
Stock Tick zzz9:43.3
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4036b-136">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4036b-136">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="4036b-137">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4036b-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="4036b-138">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4036b-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="4036b-139">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4036b-139">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

<span data-ttu-id="4036b-140">Ve výchozím nastavení je u <xref:System.ServiceModel.NetMsmqBinding>povolena možnost zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="4036b-140">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="4036b-141">Existují dvě vlastnosti pro zabezpečení přenosu ve službě MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="4036b-141">There are two pertinent properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="4036b-142">Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény a musí být nainstalovaná možnost integrace služby Active Directory pro službu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4036b-142">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="4036b-143">Pokud tuto ukázku spustíte na počítači, který nesplňuje tato kritéria, zobrazí se chyba.</span><span class="sxs-lookup"><span data-stu-id="4036b-143">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="4036b-144">Spuštění ukázky na počítači připojeném k pracovní skupině nebo bez integrace služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="4036b-144">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>

1. <span data-ttu-id="4036b-145">Pokud počítač není součástí domény nebo nemáte nainstalovanou integraci služby Active Directory, vypněte zabezpečení přenosu nastavením režimu ověřování a úrovně ochrany tak, aby `None`, jak je znázorněno v následujícím ukázkovém kódu konfigurace:</span><span class="sxs-lookup"><span data-stu-id="4036b-145">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code:</span></span>

    ```xml
    <system.serviceModel>
        <services>
          <service name="Microsoft.ServiceModel.Samples.StockTickerService"
                   behaviorConfiguration="StockTickerServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>

            <!-- Define NetMsmqEndpoint -->
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                      binding="netMsmqBinding"
                      bindingConfiguration="volatileBinding"
                      contract="Microsoft.ServiceModel.Samples.IStockTicker" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />

          </service>
        </services>

        <bindings>
          <netMsmqBinding>
            <binding name="volatileBinding"
                  durable="false"
                  exactlyOnce="false">
              <security mode="None" />
            </binding>
          </netMsmqBinding>
        </bindings>

        <behaviors>
          <serviceBehaviors>
            <behavior name="StockTickerServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. <span data-ttu-id="4036b-146">Před spuštěním ukázky se ujistěte, že jste změnili konfiguraci na serveru i v klientovi.</span><span class="sxs-lookup"><span data-stu-id="4036b-146">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4036b-147">Nastavení `security mode` na `None` je ekvivalentem nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>a `Message` zabezpečení na `None`.</span><span class="sxs-lookup"><span data-stu-id="4036b-147">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4036b-148">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="4036b-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4036b-149">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="4036b-149">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="4036b-150">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="4036b-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4036b-151">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4036b-151">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`
