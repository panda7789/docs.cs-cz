---
title: Fronty nedoručených zpráv
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: 70007289e457588e94128a573ced4b28e238acf4
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710878"
---
# <a name="dead-letter-queues"></a>Fronty nedoručených zpráv
Tato ukázka předvádí, jak zpracovávat a zpracovávat zprávy, které selhaly při doručování. Vychází ze vzorových [vazeb v transakční službě MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) . V této ukázce se používá vazba `netMsmqBinding`. Služba je samoobslužná Konzolová aplikace, která vám umožní sledovat službu přijímající zprávy zařazené do fronty.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

> [!NOTE]
> Tato ukázka demonstruje každou frontu nedoručených zpráv aplikace, která je k dispozici pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)]. Ukázku můžete upravit tak, aby používala výchozí systémové fronty pro službu MSMQ 3,0 na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].

 V komunikaci ve frontě klient komunikuje se službou pomocí fronty. Klient přesněji odesílá zprávy do fronty. Služba přijímá zprávy z fronty. Službu a klient proto nemusí běžet současně, aby bylo možné komunikovat pomocí fronty.

 Vzhledem k tomu, že komunikace zařazená do fronty může zahrnovat určité množství dormancy, možná budete chtít ke zprávě přidružit hodnotu TTL (Time to Live), aby se zajistilo, že se zpráva nebude doručena do aplikace, pokud zmizela po čase. Existují také případy, kdy musí být aplikace informována o tom, zda se nezdařila doručení zprávy. Ve všech těchto případech, například když vypršel časový limit u zprávy nebo když zpráva selhala při doručování, je zpráva vložena do fronty nedoručených zpráv. Odesílající aplikace potom může číst zprávy ve frontě nedoručených zpráv a provádět nápravné akce, které se nezdařily z důvodu opravy důvodů neúspěšného doručení a opětovného odeslání zprávy.

 Fronta nedoručených zpráv ve vazbě `NetMsmqBinding` je vyjádřená v následujících vlastnostech:

- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> vlastnost, která vyjadřuje druh fronty nedoručených zpráv, kterou klient vyžaduje. Tento výčet má následující hodnoty:

- `None`: klient nepožaduje žádnou frontu nedoručených zpráv.

- `System`: fronta nedoručených zpráv systému se používá k ukládání nedoručených zpráv. Fronta nedoručených zpráv systému je sdílena všemi aplikacemi spuštěnými v počítači.

- `Custom`: k ukládání nedoručených zpráv se používá vlastní fronta nedoručených zpráv, která je určená pomocí vlastnosti <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>. Tato funkce je k dispozici pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)]. Tato část se používá, když aplikace musí používat vlastní frontu nedoručených zpráv místo jejího sdílení s jinými aplikacemi spuštěnými ve stejném počítači.

- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> vlastnost pro vyjádření konkrétní fronty, která se má použít jako fronta nedoručených zpráv. Tato dostupnost je k dispozici pouze v [!INCLUDE[wv](../../../../includes/wv-md.md)].

 V této ukázce klient pošle dávku zpráv službě v rámci rozsahu transakce a určí libovolně nízkou hodnotu "Time to Live" pro tyto zprávy (přibližně 2 sekundy). Klient také určuje vlastní frontu nedoručených zpráv, která má být použita k zařazování zpráv, jejichž platnost vypršela.

 Klientská aplikace může číst zprávy ve frontě nedoručených zpráv a buď znovu odeslat zprávu, nebo opravit chybu, která způsobila, že původní zpráva bude umístěna do fronty nedoručených zpráv, a odeslat zprávu. V ukázce klient zobrazuje chybovou zprávu.

 Kontrakt služby je `IOrderProcessor`, jak je znázorněno v následujícím ukázkovém kódu.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Kód služby v ukázce je výsledkem [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).

 Komunikace se službou se uskutečňuje v rámci rozsahu transakce. Služba přečte zprávy z fronty, provede operaci a potom zobrazí výsledky operace. Aplikace také vytvoří frontu nedoručených zpráv pro zprávy s nedoručenými zprávami.

```csharp
//The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.

//Client implementation code.
class Client
{
    static void Main()
    {
        // Get MSMQ queue name from app settings in configuration
        string deadLetterQueueName = ConfigurationManager.AppSettings["deadLetterQueueName"];

        // Create the transacted MSMQ queue for storing dead message if necessary.
        if (!MessageQueue.Exists(deadLetterQueueName))
            MessageQueue.Create(deadLetterQueueName, true);

        // Create a proxy with given client endpoint configuration
        OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");

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
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            // Make a queued call to submit the purchase order
            client.SubmitPurchaseOrder(po);
            // Complete the transaction.
            scope.Complete();
        }

        client.Close();

        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate client.");
        Console.ReadLine();
    }
}
```

 Konfigurace klienta Určuje krátkou dobu trvání zprávy pro dosažení služby. Pokud zprávu nelze přenést do zadané doby trvání, vyprší platnost zprávy a bude přesunuta do fronty nedoručených zpráv.

> [!NOTE]
> Je možné, že klient doručí zprávu do fronty služby v určeném čase. Abyste měli jistotu, že se služba nedoručených zpráv zobrazuje v akci, měli byste před spuštěním služby spustit klienta. Vyprší časový limit zprávy a doručuje se do služby nedoručených zpráv.

 Aplikace musí definovat, kterou frontu použít jako svou frontu nedoručených zpráv. Není-li zadána žádná fronta, je pro zařazení nedoručených zpráv použita výchozí fronta nedoručených transakčních zpráv v rámci systému. V tomto příkladu klientská aplikace určí svoji vlastní frontu nedoručených zpráv aplikace.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- use appSetting to configure MSMQ Dead Letter queue name -->
    <add key="deadLetterQueueName" value=".\private$\ServiceModelSamplesOrdersAppDLQ"/>
  </appSettings>

  <system.serviceModel>
    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                binding="netMsmqBinding"
                bindingConfiguration="PerAppDLQBinding"
                contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="PerAppDLQBinding"
                 deadLetterQueue="Custom"
                 customDeadLetterQueue="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                 timeToLive="00:00:02"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>

</configuration>
```

 Nedoručená služba zpráv čte zprávy z fronty nedoručených zpráv. Nedoručená služba zpráv implementuje kontrakt `IOrderProcessor`. Jeho implementace ale nezpracovává objednávky. Nedoručená služba zpráv je klientská služba a nemá k dispozici zařízení pro zpracování objednávek.

> [!NOTE]
> Fronta nedoručených zpráv je klientská fronta a je místní pro správce front klienta.

 Nedoručená implementace služby zpráv s nedoručenými zprávami kontroluje důvod neúspěšného doručení zprávy a provádí nápravná opatření. Důvod selhání zprávy je zachycen ve dvou výčtech, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> a <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>. <xref:System.ServiceModel.Channels.MsmqMessageProperty> můžete načíst z <xref:System.ServiceModel.OperationContext>, jak je znázorněno v následujícím ukázkovém kódu:

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succeed ", po);
    MsmqMessageProperty mqProp =
                  OperationContext.Current.IncomingMessageProperties[
                  MsmqMessageProperty.Name] as MsmqMessageProperty;
    Console.WriteLine("Message Delivery Status: {0} ",
                                                mqProp.DeliveryStatus);
    Console.WriteLine("Message Delivery Failure: {0}",
                                               mqProp.DeliveryFailure);
    Console.WriteLine();
    …
}
```

 Zprávy ve frontě nedoručených zpráv jsou zprávy, které jsou adresovány službě, která zpracovává zprávu. Proto když služba zpráv nedoručených zpráv přečte zprávy z fronty, vrstva kanálu Windows Communication Foundation (WCF) nalezne neshodu v koncových bodech a neodešle zprávu. V tomto případě je zpráva adresována službě zpracování objednávky, ale je přijímána službou nedoručených zpráv. Chcete-li získat zprávu adresovanou jinému koncovému bodu, je ve `ServiceBehavior`uveden Filtr adres, který bude odpovídat libovolné adrese. Tato operace je nutná k úspěšnému zpracování zpráv, které jsou čteny z fronty nedoručených zpráv.

 V této ukázce služba zasílání zpráv s nedoručenými zprávami znovu odešle zprávu, pokud příčinou chyby je, že došlo k vypršení časového limitu zprávy. Pro všechny ostatní důvody se zobrazí chyba doručení, jak je znázorněno v následujícím ukázkovém kódu:

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Single, AddressFilterMode=AddressFilterMode.Any)]
public class PurchaseOrderDLQService : IOrderProcessor
{
    OrderProcessorClient orderProcessorService;
    public PurchaseOrderDLQService()
    {
        orderProcessorService = new OrderProcessorClient("OrderProcessorEndpoint");
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Submitting purchase order did not succeed ", po);
        MsmqMessageProperty mqProp = OperationContext.Current.IncomingMessageProperties[MsmqMessageProperty.Name] as MsmqMessageProperty;

        Console.WriteLine("Message Delivery Status: {0} ", mqProp.DeliveryStatus);
        Console.WriteLine("Message Delivery Failure: {0}", mqProp.DeliveryFailure);
        Console.WriteLine();

        // resend the message if timed out
        if (mqProp.DeliveryFailure == DeliveryFailure.ReachQueueTimeout ||
            mqProp.DeliveryFailure == DeliveryFailure.ReceiveTimeout)
        {
            // re-send
            Console.WriteLine("Purchase order Time To Live expired");
            Console.WriteLine("Trying to resend the message");

            // reuse the same transaction used to read the message from dlq to enqueue the message to app. queue
            orderProcessorService.SubmitPurchaseOrder(po);
            Console.WriteLine("Purchase order resent");
        }
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Create a ServiceHost for the PurchaseOrderDLQService type.
        using (ServiceHost serviceHost = new ServiceHost(typeof(PurchaseOrderDLQService)))
        {
            // Open the ServiceHostBase to create listeners and start listening for messages.
            serviceHost.Open();

            // The service can now be accessed.
            Console.WriteLine("The dead letter service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.WriteLine();
            Console.ReadLine();
        }
    }
}
```

 Následující příklad ukazuje konfiguraci pro zprávu s nedoručenými zprávami:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.PurchaseOrderDLQService">
        <!-- Define NetMsmqEndpoint in this case, DLQ end point to read messages-->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                  binding="netMsmqBinding"
                  bindingConfiguration="DefaultBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                 address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                 binding="netMsmqBinding"
                 bindingConfiguration="SystemDLQBinding"
                 contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="DefaultBinding" />
        <binding name="SystemDLQBinding"
                 deadLetterQueue="System"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

 Při spuštění ukázky jsou k dispozici tři spustitelné soubory, abyste viděli, jak fronta nedoručených zpráv funguje pro každou aplikaci. klient, služba a služba nedoručených zpráv, která čte z fronty nedoručených zpráv pro každou aplikaci a odesílá zprávu službě. Všechny jsou konzolové aplikace s výstupem v oknech konzoly.

> [!NOTE]
> Protože se služba Řízení front používá, není nutné, aby klient a služba běžely ve stejnou dobu. Můžete spustit klienta, vypnout ho a pak spustit službu a nadále přijímat zprávy. Službu je třeba spustit a vypnout, aby bylo možné vytvořit frontu.

 Při spuštění klienta se zobrazí zpráva klienta:

```console
Press <ENTER> to terminate client.
```

 Klient se pokusil zprávu poslat, ale má krátký časový limit, zpráva vypršela a je nyní zařazena do fronty nedoručených zpráv pro každou aplikaci.

 Poté spustíte službu nedoručených zpráv, která přečte zprávu, zobrazí kód chyby a znovu odešle zprávu zpět do služby.

```console
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 Služba se spustí a pak přečte zprávu o opakovaném odeslání a zpracuje ji.

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 97897eff-f926-4057-a32b-af8fb11b9bf9
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici. Pokud fronta není přítomna, služba ji vytvoří. Službu můžete nejdřív spustit, abyste mohli vytvořit frontu, nebo ji můžete vytvořit pomocí Správce fronty MSMQ. Pomocí těchto kroků vytvořte ve Windows 2008 frontu.

    1. Otevřete Správce serveru v aplikaci Visual Studio 2012.

    2. Rozbalte kartu **funkce** .

    3. Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **Nový**, **soukromá fronta**.

    4. Zaškrtněte políčko **transakční** .

    5. Jako název nové fronty zadejte `ServiceModelSamplesTransacted`.

3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Chcete-li ukázku spustit v jednom nebo několika počítačích ve frontě změny konfigurace, nahraďte localhost úplným názvem počítače a postupujte podle pokynů v [části spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Spuštění ukázky na počítači připojeném k pracovní skupině

1. Pokud počítač není součástí domény, vypněte zabezpečení přenosu nastavením režimu ověřování a úrovně ochrany tak, aby `None`, jak je znázorněno v následující ukázkové konfiguraci:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Nastavením atributu `bindingConfiguration` koncového bodu zajistěte, aby byl koncový bod přidružen k vazbě.

2. Před spuštěním ukázky se ujistěte, že jste změnili konfiguraci na DeadLetterService, serveru a klientovi.

    > [!NOTE]
    > Nastavení `security mode` na `None` je ekvivalentem nastavení `MsmqAuthenticationMode`, `MsmqProtectionLevel` a `Message` zabezpečení na `None`.

## <a name="comments"></a>Komentáře
 Ve výchozím nastavení se u `netMsmqBinding` vazby vazeb povoluje zabezpečení. Dvě vlastnosti, `MsmqAuthenticationMode` a `MsmqProtectionLevel`, společně určují typ zabezpečení přenosu. Ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`. Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény. Pokud tuto ukázku spustíte na počítači, který není součástí domény, zobrazí se následující chyba: "vnitřní certifikát služby Řízení front zpráv" neexistuje.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
