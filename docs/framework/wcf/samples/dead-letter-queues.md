---
title: Fronty nedoručených zpráv
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: 379b6901e835a6820d194edda1d7727df789bfd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051959"
---
# <a name="dead-letter-queues"></a>Fronty nedoručených zpráv
Tento příklad ukazuje, jak pro zpracování a zpracování zpráv, které selhaly doručování. Je založen na [nepodporuje transakce vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) vzorku. Tento příklad používá `netMsmqBinding` vazby. Služba je v místním prostředí konzolovou aplikaci pro vám umožní sledovat službu přijímání zpráv zařazených do fronty.

> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.

> [!NOTE]
>  V této ukázce každou frontu nedoručených zpráv aplikace, která je dostupná pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)]. Ukázku můžete upravit tak, aby používat fronty výchozí systémové služby MSMQ 3.0 na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].

 V komunikaci ve frontě klient komunikuje se služby pomocí fronty. Přesněji řečeno klient odešle zprávy do fronty. Služba přijímá zprávy z fronty. Klienta a služby, proto není potřeba běžet současně na komunikaci pomocí fronty.

 Protože množství dormanci; může zahrnovat komunikaci ve frontě, můžete chtít přiřadit hodnotu time-to-live u zprávy k zajištění, že zprávu získat nedoručilo aplikaci pokud zmizí po čase. Existují také případy, kde aplikace musí být informováni, zda zprávy se nezdařilo doručování. Ve všech těchto případech, jako když time-to-live ve zprávě vypršela nebo se nezdařilo, doručení, zprávy je umístit do fronty nedoručených zpráv. Odesílací aplikace můžete načítat zprávy ve frontě nedoručených zpráv a provést opravné akce, které k opravě příčiny selhání doručení a odeslání zprávy v rozsahu od žádná akce.

 Fronty nedoručených zpráv v `NetMsmqBinding` vazby je vyjádřen v následující vlastnosti:

- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> Vlastnost express typ fronty nedoručených zpráv klientů. Tento výčet má následující hodnoty:

- `None`: Žádné fronty nedoručených zpráv nevyžadovala klienta.

- `System`: Fronty nedoručených zpráv systému se používá k ukládání nedoručené zprávy. Fronty nedoručených zpráv systému sdílí všechny aplikace spuštěné v počítači.

- `Custom`: Vlastní frontu nedoručených zadat pomocí <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> vlastnost se používá k ukládání nedoručené zprávy. Tato funkce je dostupná pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)]. To se používá při aplikace musíte použít svoji vlastní frontu nedoručených zpráv místo sdílení s ostatními aplikacemi spuštěnými ve stejném počítači.

- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> Vlastnost express konkrétní fronty pro použití jako fronty nedoručených zpráv. Tato možnost je dostupná jenom v [!INCLUDE[wv](../../../../includes/wv-md.md)].

 V této ukázce klient odešle dávku zpráv do služby z v rámci oboru transakce a určuje libovolně nízkou hodnotu "time-to-live" pro tyto zprávy (přibližně 2 sekundy). Klient také určuje vlastní frontu nedoručených zpráv používat k zařazení do fronty zpráv, jejichž platnost vypršela.

 Klientská aplikace může číst zprávy ve frontě nedoručených zpráv a buď opakovat odeslání zprávy nebo opravte tuto chybu, která způsobila původní zprávu umístit do fronty nedoručených zpráv a odeslat zprávu. V ukázce klient se zobrazí chybová zpráva.

 Kontrakt služby je `IOrderProcessor`, jak je znázorněno v následujícím ukázkovém kódu.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Služba kódu v ukázce je [nepodporuje transakce vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).

 Komunikace se službou se provádí v rámci oboru transakce. Služba čte zprávy z fronty, provede operaci a poté zobrazí výsledky operace. Aplikace také vytvoří frontu nedoručených zpráv nedoručených zpráv.

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

 Konfigurace klienta určuje krátkou dobu pro zprávu ke zpřístupnění služby. Pokud zpráva nelze přenášet v rámci zadaná doba, zpráva vypršení platnosti a je přesunuta do fronty nedoručených zpráv.

> [!NOTE]
>  Je možné pro klienta doručení zprávy do fronty služby v zadaném čase. K zajištění, že se zobrazí služba dead-letter v akci, měli byste spustit před spuštěním služby klienta. Zpráva vyprší časový limit a doručit službě onta nedoručených zpráv.

 Aplikace musí definovat které fronty pro použití jako fronty nedoručených zpráv. Pokud není zadána žádná fronta, se používá výchozí systémová transakční fronty nedoručených zpráv do fronty nedoručené zprávy. V tomto příkladě určuje klientské aplikace svoji vlastní frontu nedoručených zpráv aplikace.

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

 Nedoručených zpráv služby čte zprávy z fronty nedoručených zpráv. Služba implementuje nedoručených zpráv `IOrderProcessor` kontraktu. Jeho implementace ale není na zpracovávat objednávky. Služba nedoručených zpráv je služba klienta a nemá žádné zařízení ke zpracování objednávek.

> [!NOTE]
>  Fronty nedoručených zpráv je fronta klienta a je lokální vzhledem k frontě správce klienta.

 Implementace služby nedoručených zpráv zkontroluje z důvodu, že zprávy se nezdařilo, doručování a přijímá nápravné opatření. Důvod selhání zprávy jsou zachyceny dvě výčty <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> a <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>. Můžete načíst <xref:System.ServiceModel.Channels.MsmqMessageProperty> z <xref:System.ServiceModel.OperationContext> jak je znázorněno v následujícím ukázkovém kódu:

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succed ", po);
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

 Jsou zprávy ve frontě nedoručených zpráv, které se tak vyřeší, službě, která zpracovává zprávu. Proto když služba nedoručených zpráv čte zprávy z fronty, vrstvy kanálu Windows Communication Foundation (WCF) vyhledá Neshoda v koncových bodů a není odeslání zprávy. V tomto případě zprávy je určeno služba zpracování objednávky, ale je přijatých službou nedoručených zpráv. Pokud chcete přijímat zprávy, která je určena k jinému koncovému bodu, filtr adres tak, aby odpovídaly libovolnou adresu zadaný v `ServiceBehavior`. To se vyžaduje úspěšně zpracovávat zprávy, které se načítají z fronty nedoručených zpráv.

 V této ukázce nedoručených zpráv služby znovu odešle zprávu Pokud důvod chyby je, že zpráva vypršení časového limitu. Z jiných důvodů zobrazí doručování selhání, jak je znázorněno v následujícím ukázkovém kódu:

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

 Následující příklad znázorňuje konfiguraci pro nedoručených zpráv:

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

 Ve vzorku spuštěném, existují 3 spustitelné soubory a jak funguje fronty nedoručených zpráv pro každou aplikaci, se spustí Klient, služba a služba onta nedoručených zpráv, která čte z fronty nedoručených zpráv pro každou aplikaci a znovu odešle zprávy do služby. Všechny jsou konzolové aplikace s výstupem v oknech konzoly.

> [!NOTE]
>  Protože služba Řízení front se používá, klient a služba nemusí být zprovoznit ve stejnou dobu. Můžete spustit klienta, vypněte ho a spusťte službu a stále přijímá zprávy. By měl spustit službu a vypnete ji, takže lze vytvořit frontu.

 Při spuštění klienta, klient se zobrazí zpráva:

```
Press <ENTER> to terminate client.
```

 Klient se pokusil o odeslání zprávy, ale s časovým limitem krátké zprávy vypršela platnost a je nyní zařazeny do fronty nedoručených zpráv pro každou aplikaci.

 Potom spusťte službu onta nedoručených zpráv, která přečte zprávu a zobrazí kód chyby a znovu odešle zprávy zpět do služby.

```
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 Služba spustí přečte opětovného odeslání zprávy a zpracovává je.

```
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

### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku

1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud je služba spuštěna první, zkontroluje se tak, aby byl do fronty k dispozici. Pokud fronta neexistuje, služba ho vytvoří. Můžete spustit služba nejdřív vytvořte frontu nebo můžete vytvořit prostřednictvím Správce fronty MSMQ. Postupujte podle těchto kroků můžete vytvořit frontu Windows 2008.

    1. Otevřete správce serveru v sadě Visual Studio 2012.

    2. Rozbalte **funkce** kartu.

    3. Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **nový**, **soukromou frontu**.

    4. Zkontrolujte, **transakční** pole.

    5. Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.

3. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Ke spuštění ukázky ve frontě změnit konfiguraci jednoho nebo víc počítače názvy správně, nahradíte localhost úplný název počítače a postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Ke spuštění ukázky na počítač připojen k pracovní skupině

1. Pokud počítač není součástí domény, vypněte zabezpečení přenosu nastavením úroveň ověření režimu a ochrany na `None` jak je znázorněno v následující ukázková konfigurace:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Ujistěte se koncový bod je přidružen vazby nastavením koncového `bindingConfiguration` atribut.

2. Ujistěte se, že změníte konfiguraci DeadLetterService, server a klienta, před spuštěním ukázky.

    > [!NOTE]
    >  Nastavení `security mode` k `None` je ekvivalentní nastavení `MsmqAuthenticationMode`, `MsmqProtectionLevel` a `Message` zabezpečení `None`.

## <a name="comments"></a>Komentáře
 Ve výchozím nastavení se `netMsmqBinding` vazby přenosu, zabezpečení je povolená. Dvě vlastnosti `MsmqAuthenticationMode` a `MsmqProtectionLevel`, společně určují typ zabezpečení přenosu. Ve výchozím nastavení je režim ověřování nastaven na `Windows` a aby úroveň ochrany je nastavená na `Sign`. Pro službu MSMQ. k ověřování a podepisování funkce musí být součástí domény. Pokud tuto ukázku spustit na počítači, který není součástí domény, zobrazí se následující chybová zpráva: "Certifikátu interní front uživatele neexistuje".

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
