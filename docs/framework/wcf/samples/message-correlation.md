---
title: Korelace zprávy
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: 0f5124b8172a7a4d553d19e08309affb48e7468c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714868"
---
# <a name="message-correlation"></a>Korelace zprávy
Tato ukázka předvádí, jak může aplikace služby Řízení front zpráv (MSMQ) odesílat zprávy MSMQ službě Windows Communication Foundation (WCF) a jak se dají mezi aplikacemi odesílatele a přijímače sladit zprávy ve scénáři požadavků a odpovědí. V této ukázce se používá vazba msmqIntegrationBinding. Tato služba je v tomto případě samoobslužná Konzolová aplikace, která umožňuje sledovat službu, která přijímá zprávy ve frontě. tis.  
  
 Služba zpracuje zprávu přijatou od odesílatele a pošle zprávu odpovědi zpět odesilateli. Odesilatel koreluje odpověď, kterou obdržel, na žádost, kterou odeslal původně. Vlastnosti `MessageID` a `CorrelationID` zprávy slouží ke korelaci požadavků a zpráv odpovědí.  
  
 Kontrakt služby `IOrderProcessor` definuje jednosměrnou operaci služby, která je vhodná pro použití při zařazování do fronty. Zpráva služby MSMQ neobsahuje záhlaví akce, takže není možné automaticky mapovat různé zprávy MSMQ na provozní kontrakty. V tomto případě může v tomto případě existovat pouze jedna kontrakt operace. Chcete-li ve službě definovat více kontraktů operací, aplikace musí poskytnout informace o tom, které záhlaví ve zprávě služby MSMQ (například popisek nebo ID korelace) lze použít k rozhodnutí, který kontrakt operace se má odeslat. 
  
 Zpráva služby MSMQ neobsahuje také informace o tom, která záhlaví jsou namapována na různé parametry kontraktu operace. Proto může být v kontraktu operace pouze jeden parametr. Parametr je typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, který obsahuje podkladovou zprávu služby MSMQ. Typ "T" ve třídě `MsmqMessage<T>` představuje data serializovaná do těla zprávy služby MSMQ. V této ukázce je typ `PurchaseOrder` serializován do těla zprávy služby MSMQ.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 Operace služby zpracuje objednávku nákupu a zobrazí obsah nákupní objednávky a její stav v okně konzoly služby. <xref:System.ServiceModel.OperationBehaviorAttribute> nakonfiguruje operaci k zařazení do transakce s frontou a k označení transakce dokončené, když operace vrátí. `PurchaseOrder` obsahuje podrobnosti objednávky, které musí služba zpracovat.

```csharp
// Service class that implements the service contract.
public class OrderProcessorService : IOrderProcessor
{
   [OperationBehavior(TransactionScopeRequired = true,
          TransactionAutoComplete = true)]
   public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> ordermsg)
   {
       PurchaseOrder po = (PurchaseOrder)ordermsg.Body;
       Random statusIndexer = new Random();
       po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
       Console.WriteLine("Processing {0} ", po);
       //Send a response to the client that the order has been received
         and is pending fullfillment.
       SendResponse(ordermsg);
    }

    private void SendResponse(MsmqMessage<PurchaseOrder> ordermsg)
    {
        OrderResponseClient client = new OrderResponseClient("OrderResponseEndpoint");

        //Set the correlation ID such that the client can correlate the response to the order.
        MsmqMessage<PurchaseOrder> orderResponsemsg = new MsmqMessage<PurchaseOrder>(ordermsg.Body);
        orderResponsemsg.CorrelationId = ordermsg.Id;
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.SendOrderResponse(orderResponsemsg);
            scope.Complete();
        }

        client.Close();
    }
}
```

 Služba používá vlastní `OrderResponseClient` klienta k odeslání zprávy služby MSMQ do fronty. Vzhledem k tomu, že aplikace, která přijímá a zpracovává zprávu, je aplikace služby MSMQ a ne aplikace WCF, není mezi těmito dvěma aplikacemi žádný implicitní kontrakt služby. Proto nemůžeme vytvořit proxy pomocí nástroje Svcutil. exe v tomto scénáři.

 Vlastní proxy server je v podstatě stejný pro všechny aplikace WCF, které používají vazbu `msmqIntegrationBinding` k posílání zpráv. Na rozdíl od jiných proxy serverů nezahrnuje rozsah operací služby. Jedná se pouze o operaci Odeslat zprávu.

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderResponse
{

    [System.ServiceModel.OperationContractAttribute(IsOneWay = true, Action = "*")]
    void SendOrderResponse(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderResponseClient : System.ServiceModel.ClientBase<IOrderResponse>, IOrderResponse
{

    public OrderResponseClient()
    { }

    public OrderResponseClient(string configurationName)
        : base(configurationName)
    { }

    public OrderResponseClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SendOrderResponse(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SendOrderResponse(msg);
    }
}
```

 Služba je hostována svým hostitelem. Při použití přenosu integrace služby MSMQ musí být použitá fronta předem vytvořena. To lze provést ručně nebo prostřednictvím kódu. V této ukázce služba obsahuje kód <xref:System.Messaging> pro kontrolu existence fronty a v případě potřeby ji vytvoří. Název fronty se načte z konfiguračního souboru.

```csharp
public static void Main()
{
       // Get the MSMQ queue name from application settings in configuration.
      string queueName =
                ConfigurationManager.AppSettings["orderQueueName"];
      // Create the transacted MSMQ queue if necessary.
      if (!MessageQueue.Exists(queueName))
                MessageQueue.Create(queueName, true);
     // Create a ServiceHost for the OrderProcessorService type.
     using (ServiceHost serviceHost = new
                   ServiceHost(typeof(OrderProcessorService)))
     {
            serviceHost.Open();
            // The service can now be accessed.
            Console.WriteLine("The service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.ReadLine();
            // Close the ServiceHost to shutdown the service.
            serviceHost.Close();
      }
}
```

 Fronta MSMQ, na kterou jsou odesílány požadavky objednávky, je zadána v oddílu appSettings konfiguračního souboru. Koncové body klienta a služby jsou definovány v oddílu System. serviceModel konfiguračního souboru. Určete `msmqIntegrationbinding` vazby.

```xml
<appSettings>
  <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>

<system.serviceModel>
  <client>
    <endpoint    name="OrderResponseEndpoint"
              address="msmq.formatname:DIRECT=OS:.\private$\OrderResponse"
              binding="msmqIntegrationBinding"
              bindingConfiguration="OrderProcessorBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderResponse">
    </endpoint>
  </client>

  <services>
    <service
      name="Microsoft.ServiceModel.Samples.OrderProcessorService">
      <endpoint address="msmq.formatname:DIRECT=OS:.\private$\Orders"
                            binding="msmqIntegrationBinding"
                bindingConfiguration="OrderProcessorBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor">
      </endpoint>
    </service>
  </services>

  <bindings>
    <msmqIntegrationBinding>
      <binding name="OrderProcessorBinding" >
        <security mode="None" />
      </binding>
    </msmqIntegrationBinding>
  </bindings>

</system.serviceModel>
```

 Klientská aplikace používá <xref:System.Messaging> k odeslání trvalé a transakční zprávy do fronty. Tělo zprávy obsahuje nákupní objednávku.

```csharp
static void PlaceOrder()
{
    //Connect to the queue
    MessageQueue orderQueue =
            new MessageQueue(
                    ConfigurationManager.AppSettings["orderQueueName"])
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

    Message msg = new Message();
    msg.UseDeadLetterQueue = true;
    msg.Body = po;

    //Create a transaction scope.
    using (TransactionScope scope = new
     TransactionScope(TransactionScopeOption.Required))
    {
        // Submit the purchase order.
        orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
        // Complete the transaction.
        scope.Complete();
    }
    //Save the messageID for order response correlation.
    orderMessageID = msg.Id;
    Console.WriteLine("Placed the order, waiting for response...");
}
```

 Fronta MSMQ, ze které jsou přijímány odpovědi objednávek, je zadána v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázkové konfiguraci.

> [!NOTE]
> Název fronty pro místní počítač a oddělovače zpětného lomítka v cestě používá tečku (.). Adresa koncového bodu WCF Určuje schéma služby MSMQ. formatname a pro místní počítač používá localhost. Název formátu správně vytvořeného v závislosti na pokynech služby MSMQ dodržuje formát MSMQ. FormatName v identifikátoru URI.

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 Klientská aplikace uloží `messageID` zprávy žádosti o objednávku, kterou pošle službě, a počká na odpověď od služby. Jakmile odpověď dorazí do fronty, bude ji klient korelovat se zprávou objednávky, kterou odeslal, pomocí vlastnosti `correlationID` zprávy, která obsahuje `messageID` zprávy objednávky, kterou klient původně odeslal službě.

```csharp
static void DisplayOrderStatus()
{
    MessageQueue orderResponseQueue = new
     MessageQueue(ConfigurationManager.AppSettings
                  ["orderResponseQueueName"]);
    //Create a transaction scope.
    bool responseReceived = false;
    orderResponseQueue.MessageReadPropertyFilter.CorrelationId = true;
    while (!responseReceived)
    {
       Message responseMsg;
       using (TransactionScope scope2 = new
         TransactionScope(TransactionScopeOption.Required))
       {
          //Receive the Order Response message.
          responseMsg =
              orderResponseQueue.Receive
                   (MessageQueueTransactionType.Automatic);
          scope2.Complete();
     }
     responseMsg.Formatter = new
     System.Messaging.XmlMessageFormatter(new Type[] {
         typeof(PurchaseOrder) });
     PurchaseOrder responsepo = (PurchaseOrder)responseMsg.Body;
    //Check if the response is for the order placed.
    if (orderMessageID == responseMsg.CorrelationId)
    {
       responseReceived = true;
       Console.WriteLine("Status of current Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
    else
    {
       Console.WriteLine("Status of previous Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
  }
}
```

 Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta. Můžete vidět, že služba přijímá zprávy z klienta a odesílá odpověď zpátky klientovi. Klient zobrazuje odpověď přijatou od služby. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.

> [!NOTE]
> Tato ukázka vyžaduje instalaci služby Řízení front zpráv (MSMQ). Pokyny k instalaci služby MSMQ najdete v části Viz také.

### <a name="to-setup-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici. Pokud fronta není přítomna, služba ji vytvoří. Službu můžete nejdřív spustit, abyste mohli vytvořit frontu, nebo ji můžete vytvořit pomocí Správce fronty MSMQ. Pomocí těchto kroků vytvořte ve Windows 2008 frontu.

    1. Otevřete Správce serveru v aplikaci Visual Studio 2012.

    2. Rozbalte kartu **funkce** .

    3. Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **Nový**, **soukromá fronta**.

    4. Zaškrtněte políčko **transakční** .

    5. Jako název nové fronty zadejte `ServiceModelSamplesTransacted`.

3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci s jedním počítačem, postupujte podle pokynů v [části spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači

1. Zkopírujte programové soubory služby ze složky \service\bin\ ve složce specifické pro daný jazyk do počítače služby.

2. Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.

3. V souboru Client. exe. config změňte orderQueueName a zadejte název počítače služby místo ".".

4. V souboru Service. exe. config změňte adresu koncového bodu klienta tak, aby určovala název klientského počítače místo ".".

5. Na počítači služby spusťte z příkazového řádku Service. exe.

6. V klientském počítači spusťte z příkazového řádku soubor Client. exe.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a>Viz také:

- [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Řízení front zpráv](https://go.microsoft.com/fwlink/?LinkId=94968)
