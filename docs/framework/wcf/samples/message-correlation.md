---
title: "Korelace zprávy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 54b7b7d9ba247f329fbf3c9040c641e3194d3bfb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="message-correlation"></a>Korelace zprávy
Tento příklad ukazuje, jak můžete k aplikaci služby Řízení front zpráv (MSMQ) odešle zprávu služby MSMQ pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby a korelace zpráv mezi aplikacemi odesílatele a příjemce v případě požadavků a odpovědí. Tato ukázka používá – msmqIntegrationBinding vazby. Služba je v tomto případě vlastním hostováním konzolovou aplikaci, abyste mohli pozorovat, že služby, která přijímá zprávy zařazené do fronty. K  
  
 Služba zpracovává zprávu přijatou z odesílatele a odešle zprávu odpovědi zpátky do odesílatele. Odesílatel korelaci obdrženého na žádost, ke které původně odeslán odpovědi. `MessageID` a `CorrelationID` vlastnosti zprávy, které se používají ke korelaci zprávy požadavku a odpovědi.  
  
 `IOrderProcessor` Operace jednosměrné služby, který je vhodný pro použití se službou Řízení front definuje kontrakt služby. Zprávy MSMQ nemá hlavičku akce, takže není možné automaticky mapovat různé zprávy služby MSMQ kontrakty operaci. Proto může existovat pouze jedna smlouva operace v tomto případě. Pokud chcete definovat další operace měnící v rámci služby, aplikace musí poskytovat informace, které záhlaví v služby MSMQ zprávy (například štítek, nebo correlationID) slouží k rozhodnout, které operace kontrakt k odeslání. Tento postup je znázorněn v [vlastní Demux](../../../../docs/framework/wcf/samples/custom-demux.md).  
  
 Zprávy služby MSMQ také neobsahuje informace o tom, které hlavičky jsou namapované na různé parametry operace kontrakt. Proto může existovat jenom jeden parametr v operaci kontraktu. Parametr je typu <!--zz <xref:System.ServiceModel.MSMQIntegration.MsmqMessage%601>`MsmqMessage<T>`--> , `System.ServiceModel.MSMQIntegration.MsmqMessage` obsahující základní zprávy služby MSMQ. Typ "T" v `MsmqMessage<T>` třída reprezentuje data, která je serializován do textu zprávy služby MSMQ. V této ukázce `PurchaseOrder` typ serializován do textu zprávy služby MSMQ.  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```  
  
 Operace služby zpracovává nákupní objednávka a obsah nákupní objednávka a jeho stav se zobrazí v okně konzoly služby. <xref:System.ServiceModel.OperationBehaviorAttribute> Nakonfiguruje operaci zařazení v transakci s fronty a označit dokončení transakce po návratu operaci. `PurchaseOrder` Obsahuje podrobnosti o pořadí, které musí být služba.  
  
```  
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
  
 Služba používá vlastní klienta `OrderResponseClient` k odeslání zprávy služby MSMQ do fronty. Vzhledem k tomu, že je aplikace, který obdrží a zpracuje zprávy aplikací služby MSMQ a ne [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, neexistuje žádný kontrakt implicitní služby mezi těmito dvěma aplikacemi. Proto nemůžeme vytvořit proxy server pomocí nástroje Svcutil.exe v tomto scénáři.  
  
 Vlastní proxy server je v podstatě stejný pro všechny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, které používají `msmqIntegrationBinding` vazby k odesílání zpráv. Na rozdíl od jiných proxy nebude obsahovat celou řadu operací služby. Je zpráva operaci odeslání jenom.  
  
```  
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
  
 Služba je sám sebou hostované. Pokud používáte transport integrace MSMQ, používá fronty musí být vytvořeny předem. Tento krok můžete provést ručně nebo prostřednictvím kódu. V této ukázce služba obsahuje <xref:System.Messaging> kódu zkontrolujte existenci fronty a vytvořte ji v případě potřeby. Název fronty je číst z konfiguračního souboru.  
  
```  
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
  
 Frontu MSMQ, ke které se odesílají žádosti pořadí je zadána v oddílu appSettings konfiguračního souboru. Koncové body klienta a služby jsou definovány v sekci system.serviceModel konfiguračního souboru. Zadejte oba `msmqIntegrationbinding` vazby.  
  
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
  
 Klientská aplikace používá <xref:System.Messaging> k odeslání odolné a transakční zprávy do fronty. Tělo zprávy obsahuje nákupní objednávka.  
  
```  
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
  
 Frontu MSMQ, ve kterém jsou přijaty odpovědi pořadí je zadána v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázka konfigurace.  
  
> [!NOTE]
>  Název fronty používá tečku (.) pro místní počítač a oddělovače zpětné lomítko, v jeho cesty. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Adresa koncového bodu určuje schématu msmq.formatname a používá "localhost" pro místní počítač. Název formátu správně vytvořená následuje msmq.formatname v identifikátoru URI podle pokynů služby MSMQ.  
  
```xml  
<appSettings>  
    <add key=" orderResponseQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 Uloží aplikace klienta `messageID` pořadí zprávě požadavku, která ji odešle do služby a čeká na odpověď ze služby. Po odpověď dorazí ve frontě, klient ji koreluje s pořadí zpráva se odešle pomocí `correlationID` vlastnosti zprávy, která obsahuje `messageID` objednávky zprávou, která klient odešle do služby původně.  
  
```  
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
  
 Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly služby a klienta. Zobrazí se službu přijmout zprávy z klienta a odešle odpověď zpět klientovi. Klient se zobrazí odpověď přijal od služby. Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.  
  
> [!NOTE]
>  Tato ukázka vyžaduje instalaci služby Řízení front zpráv (MSMQ). Najdete v pokynech k instalaci služby MSMQ v části Viz také.  
  
### <a name="to-setup-build-and-run-the-sample"></a>Instalační program, sestavení a spuštění vzorku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty. Pokud fronta neexistuje, vytvoří služba jeden. Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ. Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.  
  
    1.  Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozbalte **funkce** kartě.  
  
    3.  Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.  
  
    4.  Zkontrolujte **transakcí** pole.  
  
    5.  Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.  
  
3.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci jednoho počítače, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Zkopírujte soubory programu služby ve složce \service\bin\ ve složce pro specifický jazyk k počítači služby.  
  
2.  Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.  
  
3.  V souboru Client.exe.config změnit orderQueueName k zadání názvu počítače služba místo ".".  
  
4.  V souboru Service.exe.config změnit adresa koncového bodu klienta k zadání názvu počítače klienta místo ".".  
  
5.  Na počítači se službou spusťte z příkazového řádku Service.exe.  
  
6.  Na klientském počítači spusťte z příkazového řádku Client.exe.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a>Viz také  
 [Fronty ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Služba Řízení front zpráv](http://go.microsoft.com/fwlink/?LinkId=94968)
