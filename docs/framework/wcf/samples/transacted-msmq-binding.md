---
title: Zpracované vazby služby MSMQ
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: a3592195f853dd97bf8e4351526bf0fff9ce78fd
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715634"
---
# <a name="transacted-msmq-binding"></a>Zpracované vazby služby MSMQ

Tato ukázka předvádí, jak pomocí služby Řízení front zpráv (MSMQ) provádět komunikaci v transakční frontě.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

V komunikaci ve frontě klient komunikuje se službou pomocí fronty. Klient přesněji odesílá zprávy do fronty. Služba přijímá zprávy z fronty. Služba a klient proto nemusí být spuštěná ve stejnou dobu, aby komunikovala s použitím fronty.

Pokud se pro posílání a přijímání zpráv používají transakce, jsou ve skutečnosti dvě samostatné transakce. Když klient pošle zprávy v rámci oboru transakce, transakce je místní pro klienta a správce front klientů. Když služba obdrží zprávy v rámci oboru transakce, transakce je místní pro službu a přijímacího správce fronty. Je velmi důležité si uvědomit, že klient a služba nejsou zapojeny do stejné transakce; místo toho používají různé transakce při provádění jejich operací (jako je například posílání a přijímání) s frontou.

V této ukázce klient pošle dávku zpráv službě v rámci rozsahu transakce. Zprávy odeslané do fronty jsou poté přijímány službou v rámci oboru transakce definovaném službou.

Kontrakt služby je `IOrderProcessor`, jak je znázorněno v následujícím ukázkovém kódu. Rozhraní definuje jednosměrnou službu, která je vhodná pro použití s frontami.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

Chování služby definuje chování operace s `TransactionScopeRequired` nastavenou na `true`. Tím se zajistí, že stejný obor transakce, který se použije k načtení zprávy z fronty, je používán všemi správci prostředků, ke kterým přistupovala metoda. Zaručuje také, že pokud metoda vyvolá výjimku, zpráva se vrátí do fronty. Bez nastavení této operace vytvoří kanál zařazený do fronty transakci, která načte zprávu z fronty a potvrdí ji automaticky před odesláním tak, že pokud operace nebude úspěšná, zpráva se ztratí. Nejběžnějším scénářem je, aby se operace služby zařadí do transakce, která se používá ke čtení zprávy z fronty, jak je znázorněno v následujícím kódu.

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

Služba je hostována svým hostitelem. Při použití přenosu služby MSMQ musí být použitá fronta předem vytvořená. To lze provést ručně nebo prostřednictvím kódu. V této ukázce služba obsahuje kód pro kontrolu existence fronty a vytvoření fronty, pokud neexistuje. Název fronty se načte z konfiguračního souboru. Základní adresa je používána [nástrojem Svcutil. exe](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pro vygenerování proxy serveru ke službě.

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

Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázkové konfiguraci.

```xml
<appSettings>
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />
</appSettings>
```

> [!NOTE]
> Název fronty používá tečku (.) pro místní počítač a oddělovače zpětného lomítka v cestě při vytváření fronty pomocí <xref:System.Messaging>. Koncový bod služby Windows Communication Foundation (WCF) používá adresu fronty se schématem NET. MSMQ, používá localhost k označení místního počítače a používá lomítka v cestě.

Klient vytvoří obor transakce. Komunikace s frontou probíhá v rámci rozsahu transakce, což způsobuje, že se bude považovat za atomickou jednotku, do které jsou odesílány všechny zprávy do fronty, nebo žádná z zpráv není odeslána do fronty. Transakce je potvrzena voláním <xref:System.Transactions.TransactionScope.Complete%2A> v oboru transakce.

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

Chcete-li ověřit, zda transakce fungují, upravte klienta přidáním komentáře k oboru transakce, jak je znázorněno v následujícím ukázkovém kódu, znovu sestavte řešení a spusťte klienta.

```csharp
//scope.Complete();
```

Vzhledem k tomu, že transakce není dokončena, zprávy nejsou odesílány do fronty.

Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta. Můžete vidět, že služba přijímá zprávy z klienta. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta. Počítejte s tím, že protože se používá služba zařazování do fronty, klient a služba nemusí být spuštěny ve stejnou dobu. Můžete spustit klienta, vypnout ho a pak spustit službu a pořád zprávy obdrží.

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

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici. Pokud fronta není přítomna, služba ji vytvoří. Službu můžete nejdřív spustit, abyste mohli vytvořit frontu, nebo ji můžete vytvořit pomocí Správce fronty MSMQ. Pomocí těchto kroků vytvořte ve Windows 2008 frontu.

    1. Otevřete Správce serveru v aplikaci Visual Studio 2012.

    2. Rozbalte kartu **funkce** .

    3. Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **Nový**, **soukromá fronta**.

    4. Zaškrtněte políčko **transakční** .

    5. Jako název nové fronty zadejte `ServiceModelSamplesTransacted`.

3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

Ve výchozím nastavení je u <xref:System.ServiceModel.NetMsmqBinding>povolena možnost zabezpečení přenosu. Existují dvě důležité vlastnosti pro zabezpečení přenosu služby MSMQ <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>. Ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`. Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény a musí být nainstalovaná možnost integrace služby Active Directory pro službu MSMQ. Pokud tuto ukázku spustíte na počítači, který nesplňuje tato kritéria, dojde k chybě.

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Spuštění ukázky na počítači připojeném k pracovní skupině nebo bez integrace služby Active Directory

1. Pokud počítač není součástí domény nebo nemáte nainstalovanou integraci služby Active Directory, vypněte zabezpečení přenosu nastavením režimu ověřování a úrovně ochrany na `None`, jak je znázorněno v následujícím ukázkovém kódu konfigurace.

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

2. Před spuštěním ukázky se ujistěte, že jste změnili konfiguraci na serveru i v klientovi.

    > [!NOTE]
    > Nastavení `security mode` na `None` je ekvivalentem nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>a `Message` zabezpečení na `None`.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`
