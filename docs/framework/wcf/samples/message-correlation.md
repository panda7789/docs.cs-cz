---
title: Korelace zprávy
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: e4cd5dfd6f03370a408dc6f8fb39c983db3d43df
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "44756883"
---
# <a name="message-correlation"></a>Korelace zprávy
Tato ukázka předvádí, jak služby Řízení front zpráv (MSMQ) aplikace může odesílat zprávy MSMQ do služby Windows Communication Foundation (WCF) a korelace zpráv mezi aplikacemi odesílatele a příjemce v případě požadavku nebo odpovědi. Tato ukázka používá vazbu msmqIntegrationBinding. Služba není v tomto případě v místním prostředí konzolovou aplikaci, aby bylo možné sledovat, že služba, která bude přijímat zprávy zařazené do fronty. TIS.  
  
 Služba zpracovává zprávu přijatou od odesílatele a odešle odpověď zpět do odesílatele. Odesílatel koreluje odpovědí, žádost, u které původně odeslán přijaty. `MessageID` a `CorrelationID` vlastnosti zprávy jsou používány ke korelaci zprávy požadavků a odpovědí.  
  
 `IOrderProcessor` Operace jednosměrné služby, který je vhodný pro použití se službou Řízení front definuje kontrakt služby. Zprávy MSMQ nemá hlavičku akce, takže není možné automaticky mapovat různé zprávy služby MSMQ pro operaci smlouvy. Proto může existovat pouze jeden kontrakt operace v tomto případě. Pokud chcete definovat další operace smluv týkajících se služby, aplikace musíte zadat informace jako záhlaví, které v služby MSMQ zprávy (třeba popisek, nebo ID korelace) umožňuje rozhodnout, kterou kontrakt k odeslání. To je patrné [vlastní Demux](../../../../docs/framework/wcf/samples/custom-demux.md).  
  
 Zprávy služby MSMQ také neobsahuje informace ohledně toho, která hlavičky jsou namapovány na různé parametry kontrakt. Proto může existovat jenom jeden parametr v kontrakt. Parametr je typu <!--zz <xref:System.ServiceModel.MSMQIntegration.MsmqMessage%601>`MsmqMessage<T>`--> , `System.ServiceModel.MSMQIntegration.MsmqMessage` obsahující základní zprávy služby MSMQ. Typ "T" v `MsmqMessage<T>` třída reprezentuje data, která je serializován do textu zprávy MSMQ. V této ukázce `PurchaseOrder` je typ serializován do textu zprávy MSMQ.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```

 Operace služby nákupní objednávku zpracovává a zobrazí se obsah nákupní objednávky a jeho stav v okně konzoly služby. <xref:System.ServiceModel.OperationBehaviorAttribute> Nakonfiguruje operaci zařazení v transakci s frontou a označit dokončení transakce po návratu operaci. `PurchaseOrder` Obsahuje podrobnosti objednávky, které musí být zpracovány služby.  

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

 Služba používá vlastní klienta `OrderResponseClient` do fronty odesílat zprávy služby MSMQ. Protože se aplikace, který přijímá a zpracovává zprávy služby MSMQ aplikace a aplikace WCF, neexistuje žádný implicitní smlouvu mezi těmito dvěma aplikacemi. Takže nemůžeme vytvořit proxy server pomocí nástroje Svcutil.exe v tomto scénáři.  
  
 Vlastní proxy server je v podstatě stejný pro všechny aplikace WCF, které používají `msmqIntegrationBinding` vazby pro odesílání zpráv. Na rozdíl od jiných proxy neobsahoval celou řadu operací služby. Odeslat zprávu tato operace je pouze.  

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

 Tato služba je vlastní hostované. Při použití transport integrace MSMQ fronty používají se musí vytvořit předem. To můžete udělat ručně nebo prostřednictvím kódu. V této ukázce obsahuje službu <xref:System.Messaging> kód pro provedení kontroly existence fronty a v případě potřeby ji vytvořit. Název fronty načítají z konfiguračního souboru.  

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
  
 Fronta MSMQ, ke které se odesílají požadavky pořadí je definováno v sekci appSettings konfiguračního souboru. Koncové body klienta a služby jsou definovány v sekci system.serviceModel konfiguračního souboru. Jak určit `msmqIntegrationbinding` vazby.  
  
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
  
 Klientská aplikace používá <xref:System.Messaging> odeslat odolné a transakční zprávu do fronty. Tělo zprávy obsahuje nákupní objednávky.  

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

 Fronta MSMQ, ze kterého jsou přijaty odpovědi pořadí je zadán v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázková konfigurace.  
  
> [!NOTE]
>  Název fronty používá tečku (.) pro místní počítače a zpětné lomítko oddělovače v cestě. Adresa koncového bodu WCF Určuje schéma msmq.formatname a používá "localhost" v místním počítači. Název formátu správně vytvořená následuje msmq.formatname v identifikátoru URI podle pokynů služby MSMQ.  
  
```xml  
<appSettings>  
    <add key=" orderResponseQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 Uloží klientské aplikace `messageID` zprávy s požadavkem pořadí, který odešle do služby a čeká na odpověď ze služby. Po přijetí odpovědi ve frontě klienta, koreluje ji s zpráv pořadí je odeslat pomocí `correlationID` vlastnosti zprávy, která obsahuje `messageID` pořadí, zprávy, které klient původně odeslána do služby.  

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

 Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly služby a klienta. Zobrazí se služby přijmout zprávy z klienta a odešle odpověď zpět klientovi. Klient se zobrazí odpověď ze služby. Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.  
  
> [!NOTE]
>  Tato ukázka vyžaduje instalaci sady řízení front zpráv (MSMQ). MSMQ instalační pokyny naleznete v části Viz také.  
  
### <a name="to-setup-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pokud je služba spuštěna první, zkontroluje se tak, aby byl do fronty k dispozici. Pokud fronta neexistuje, služba ho vytvoří. Můžete spustit služba nejdřív vytvořte frontu nebo můžete vytvořit prostřednictvím Správce fronty MSMQ. Postupujte podle těchto kroků můžete vytvořit frontu Windows 2008.  
  
    1.  Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozbalte **funkce** kartu.  
  
    3.  Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **nový**, **soukromou frontu**.  
  
    4.  Zkontrolujte, **transakční** pole.  
  
    5.  Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.  
  
3.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spusťte ukázku v jednom počítači konfiguraci, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky v počítačích  
  
1.  Zkopírujte soubory programu služby ze složky \service\bin\ v rámci složky specifické pro jazyk, k počítači služby.  
  
2.  Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientského počítače.  
  
3.  V souboru Client.exe.config změnit orderQueueName k zadání názvu počítače služba namísto ".".  
  
4.  V souboru Service.exe.config, změňte adresu koncového bodu klienta k určení názvu klientského počítače namísto ".".  
  
5.  Na počítači se službou spusťte z příkazového řádku Service.exe.  
  
6.  Na klientském počítači spusťte Client.exe z příkazového řádku.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a>Viz také  
 [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Služba Řízení front zpráv](https://go.microsoft.com/fwlink/?LinkId=94968)
