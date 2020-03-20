---
title: Fronty nedoručených zpráv
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: eab1c52f4d0b3d0f82cf561a9478ea8233598e1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144945"
---
# <a name="dead-letter-queues"></a>Fronty nedoručených zpráv
Tato ukázka ukazuje, jak zpracovat a zpracovat zprávy, které se nezdařilo doručení. Je založen na [transacted MSMQ binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) vzorku. Tato ukázka `netMsmqBinding` používá vazbu. Služba je aplikace konzoly s vlastním hostitelem, která umožňuje sledovat službu přijímající zprávy ve frontě.

> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.

> [!NOTE]
> Tato ukázka ukazuje každou frontu nedoručených zpráv aplikace, která je k dispozici pouze v systému Windows Vista. Ukázku lze upravit tak, aby používala výchozí systémové fronty pro službu MSMQ 3.0 v systémech Windows Server 2003 a Windows XP.

 Ve frontové komunikaci klient komunikuje se službou pomocí fronty. Přesněji řečeno, klient odesílá zprávy do fronty. Služba přijímá zprávy z fronty. Služba a klient proto nemusí být spuštěny současně komunikovat pomocí fronty.

 Vzhledem k tomu, že komunikace ve frontě může zahrnovat určité množství klid, můžete přidružit hodnotu time-to-live na zprávu, abyste zajistili, že zpráva nebude doručena do aplikace, pokud uplynula. Existují také případy, kdy aplikace musí být informováni, zda zpráva selhala doručení. Ve všech těchto případech, například při vypršení doby do provozu na zprávu nebo zprávy se nezdařilo doručení, je zpráva umístěna do fronty nedoručených zpráv. Odesílající aplikace pak můžete číst zprávy ve frontě nedoručených zpráv a přijmout nápravná opatření, která sahají od žádné akce k opravě důvodů pro neúspěšné doručení a opětovné odeslání zprávy.

 Fronta nedoručených `NetMsmqBinding` zpráv ve vazbě je vyjádřena v následujících vlastnostech:

- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>vlastnost vyjádřit druh fronty nedoručených zpráv vyžadované klientem. Tento výčet má následující hodnoty:

- `None`: Klient nevyžaduje žádnou frontu nedoručených zpráv.

- `System`: Fronta nedoručených zpráv systému se používá k ukládání nedoručených zpráv. Systémová fronta nedoručených zpráv je sdílena všemi aplikacemi spuštěnými v počítači.

- `Custom`: Vlastní fronta nedoručených <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> zpráv zadaná pomocí vlastnosti se používá k ukládání nedoručených zpráv. Tato funkce je k dispozici pouze v systému Windows Vista. Používá se v případě, že aplikace musí používat vlastní frontu nedoručených zpráv namísto sdílení s jinými aplikacemi spuštěnými ve stejném počítači.

- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>vlastnost vyjádřit konkrétní fronty použít jako fronty nedoručených zpráv. Tato možnost je k dispozici pouze v systému Windows Vista.

 V této ukázce klient odešle dávku zpráv do služby z rozsahu transakce a určuje libovolně nízkou hodnotu pro "time-to-live" pro tyto zprávy (asi 2 sekundy). Klient také určuje vlastní frontu nedoručených zpráv, která se má použít k zařazení zpráv, jejichž platnost vypršela.

 Klientská aplikace může číst zprávy ve frontě nedoručených zpráv a zkuste zprávu odeslat znovu nebo opravit chybu, která způsobila umístění původní zprávy do fronty nedoručených zpráv a odeslat zprávu. V ukázce se zobrazí chybová zpráva klienta.

 Servisní smlouva `IOrderProcessor`je , jak je znázorněno v následujícím ukázkovém kódu.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Kód služby v ukázce je [kód transacted msmq vazby](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).

 Komunikace se službou probíhá v rámci transakce. Služba čte zprávy z fronty, provádí operaci a potom zobrazí výsledky operace. Aplikace také vytvoří frontu nedoručených zpráv pro nedoručené zprávy.

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

 Konfigurace klienta určuje krátkou dobu trvání zprávy k dosažení služby. Pokud zprávu nelze přenést v rámci zadané doby trvání, vyprší platnost zprávy a je přesunuta do fronty nedoručených zpráv.

> [!NOTE]
> Je možné, aby klient doručit zprávu do fronty služeb v zadaném čase. Chcete-li zajistit, že se služba nedoručených dat zobrazí v akci, měli byste před spuštěním služby spustit klienta. Časový nebo poslední den zprávy a je doručena do služby nedoručených zpráv.

 Aplikace musí definovat, které fronty se mají použít jako frontu nedoručených zpráv. Pokud není zadána žádná fronta, výchozí transakční fronta nedoručených zpráv pro celý systém se používá k zařazení nedoručených zpráv do fronty. V tomto příkladu určuje klientská aplikace vlastní frontu nedoručených zpráv vlastní aplikace.

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

 Služba nedoručených zpráv čte zprávy z fronty nedoručených zpráv. Služba nedoručených zpráv implementuje smlouvu. `IOrderProcessor` Jeho realizace však není zpracování objednávek. Služba nedoručených zpráv je klientská služba a nemá možnost zpracovávat objednávky.

> [!NOTE]
> Fronta nedoručených zpráv je fronta klientů a je místní pro správce front klienta.

 Implementace služby nedoručených zpráv z kontroluje z důvodu, že zpráva selhala doručení a přijímá nápravná opatření. Důvod selhání zprávy je zachycen ve dvou <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> výčtů <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>a . Můžete načíst <xref:System.ServiceModel.Channels.MsmqMessageProperty> z <xref:System.ServiceModel.OperationContext> jak je znázorněno v následujícím ukázkovém kódu:

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

 Zprávy ve frontě nedoručených zpráv jsou zprávy adresované službě, která zprávu zpracovává. Proto při službě nedoručených zpráv čte zprávy z fronty, vrstva kanálu Windows Communication Foundation (WCF) najde neshodu v koncových bodech a neodešle zprávu. V takovém případě je zpráva určena službě zpracování objednávek, ale je přijata službou nedoručených zpráv. Chcete-li obdržet zprávu adresovanou jinému koncovému bodu, je v `ServiceBehavior`aplikaci zadán filtr adresy odpovídající libovolné adrese. To je nutné úspěšně zpracovat zprávy, které jsou čteny z fronty nedoručených zpráv.

 V této ukázce služba nedoručených zpráv znovu odešle zprávu, pokud důvodem selhání je, že časový čas zprávy. Ze všech ostatních důvodů zobrazuje selhání dodávky, jak je znázorněno v následujícím ukázkovém kódu:

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

 Následující ukázka ukazuje konfiguraci nedoručené zprávy:

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

 Při spuštění ukázky existují 3 spustitelné soubory ke spuštění, aby viděli, jak funguje fronta nedoručených zpráv pro každou aplikaci; klient, služba a služba nedoručených zpráv, která čte z fronty nedoručených zpráv pro každou aplikaci a znovu odešle zprávu službě. Všechny jsou konzolové aplikace s výstupem v konzolových oknech.

> [!NOTE]
> Vzhledem k tomu, že se používá fronty, klient a služba nemusí být současně spuštěni. Můžete spustit klienta, vypnout a potom spustit službu a stále přijímá jeho zprávy. Měli byste spustit službu a vypnout ji, aby bylo možné vytvořit frontu.

 Při spuštění klienta se zobrazí zpráva:

```console
Press <ENTER> to terminate client.
```

 Klient se pokusil odeslat zprávu, ale s krátkým časovým limitem, zpráva vypršela a je nyní zařazena do fronty nedoručených zpráv pro každou aplikaci.

 Potom spustíte službu nedoručených zpráv, která přečte zprávu a zobrazí kód chyby a znovu odešle zprávu zpět do služby.

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

 Služba se spustí a potom přečte zprávu s opakováním a zpracuje ji.

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

1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici. Pokud fronta není k dispozici, služba ji vytvoří. Nejprve můžete spustit službu a vytvořit frontu, nebo ji můžete vytvořit pomocí Správce front služby MSMQ. Vytvořenífronty v systému Windows 2008 postupujte takto.

    1. Otevřete Správce serveru v sadě Visual Studio 2012.

    2. Rozbalte kartu **Funkce.**

    3. Klepněte pravým tlačítkem myši na **položku Fronty soukromých zpráv**a vyberte příkaz **Nová**, **Soukromá fronta**.

    4. Zaškrtněte políčko **Transakční** transakce.

    5. Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.

3. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači změnit názvy fronty odpovídajícím způsobem, nahrazení localhost s úplný název počítače a postupujte podle pokynů v [spuštění windows communication foundation ukázky](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Spuštění ukázky v počítači připojovato k pracovní skupině

1. Pokud počítač není součástí domény, vypněte zabezpečení přenosu nastavením režimu `None` ověřování a úrovně ochrany na úroveň uvedenou v následující ukázkové konfiguraci:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Ujistěte se, že koncový bod je přidružen `bindingConfiguration` k vazbě nastavením atributu koncového bodu.

2. Ujistěte se, že změníte konfiguraci na DeadLetterService, server a klient před spuštěním ukázky.

    > [!NOTE]
    > Nastavení `security mode` `None` na je `MsmqAuthenticationMode`ekvivalentní `MsmqProtectionLevel` `Message` nastavení `None`a zabezpečení .

## <a name="comments"></a>Komentáře
 Ve výchozím `netMsmqBinding` nastavení s přenosem vazby je povoleno zabezpečení. Dvě `MsmqAuthenticationMode` vlastnosti `MsmqProtectionLevel`a společně určují typ zabezpečení přenosu. Ve výchozím nastavení je `Windows` režim ověřování nastaven na `Sign`hodnotu a úroveň ochrany je nastavena na hodnotu . Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény. Pokud spustíte tuto ukázku v počítači, který není součástí domény, zobrazí se následující chyba: "Interní certifikát fronty zpráv uživatele neexistuje".

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
