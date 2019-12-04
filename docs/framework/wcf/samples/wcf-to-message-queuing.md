---
title: Z WCF do Řízení front zpráv
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: 1cbc1251a8e4eaaaf4b47357851dd681ae326f25
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715061"
---
# <a name="windows-communication-foundation-to-message-queuing"></a>Z WCF do Řízení front zpráv
Tato ukázka předvádí, jak může aplikace Windows Communication Foundation (WCF) odeslat zprávu do aplikace řízení front zpráv (MSMQ). Služba je samoobslužná Konzolová aplikace, která vám umožní sledovat službu přijímající zprávy zařazené do fronty. Službu a klienta nemusíte spouštět ve stejnou dobu.

 Služba přijímá zprávy z objednávek front a procesů. Služba vytvoří transakční frontu a nastaví zprávu s oznámením o přijetí zprávy, jak je znázorněno v následujícím ukázkovém kódu.

```csharp
static void Main(string[] args)
{
    if (!MessageQueue.Exists(
              ConfigurationManager.AppSettings["queueName"]))
       MessageQueue.Create(
           ConfigurationManager.AppSettings["queueName"], true);
        //Connect to the queue
        MessageQueue Queue = new
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);
    Queue.ReceiveCompleted +=
                 new ReceiveCompletedEventHandler(ProcessOrder);
    Queue.BeginReceive();
    Console.WriteLine("Order Service is running");
    Console.ReadLine();
}
```

 Při přijetí zprávy ve frontě je vyvolána obslužná rutina zprávy `ProcessOrder`.

```csharp
public static void ProcessOrder(Object source,
    ReceiveCompletedEventArgs asyncResult)
{
    try
    {
        // Connect to the queue.
        MessageQueue Queue = (MessageQueue)source;
        // End the asynchronous receive operation.
        System.Messaging.Message msg =
                     Queue.EndReceive(asyncResult.AsyncResult);
        msg.Formatter = new System.Messaging.XmlMessageFormatter(
                                new Type[] { typeof(PurchaseOrder) });
        PurchaseOrder po = (PurchaseOrder) msg.Body;
        Random statusIndexer = new Random();
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
        Console.WriteLine("Processing {0} ", po);
        Queue.BeginReceive();
    }
    catch (System.Exception ex)
    {
        Console.WriteLine(ex.Message);
    }

}
```

 Služba extrahuje `ProcessOrder` z těla zprávy služby MSMQ a zpracuje objednávku.

 Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázkové konfiguraci.

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

> [!NOTE]
> Název fronty pro místní počítač a oddělovače zpětného lomítka v cestě používá tečku (.).

 Klient vytvoří nákupní objednávku a odešle nákupní objednávku v rámci oboru transakce, jak je znázorněno v následujícím ukázkovém kódu.

```csharp
// Create the purchase order
PurchaseOrder po = new PurchaseOrder();
// Fill in the details
...

OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");

MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    client.SubmitPurchaseOrder(ordermsg);
    scope.Complete();
}
Console.WriteLine("Order has been submitted:{0}", po);

//Closing the client gracefully closes the connection and cleans up resources
client.Close();
```

 Klient pro odeslání zprávy služby MSMQ do fronty používá vlastního klienta. Vzhledem k tomu, že aplikace, která přijímá a zpracovává zprávu, je aplikace služby MSMQ a ne aplikace WCF, není mezi těmito dvěma aplikacemi žádný implicitní kontrakt služby. Proto nemůžeme vytvořit proxy pomocí nástroje Svcutil. exe v tomto scénáři.

 Vlastní klient je v podstatě stejný pro všechny aplikace WCF, které používají vazbu `MsmqIntegration` k posílání zpráv. Na rozdíl od jiných klientů nezahrnuje rozsah operací služby. Jedná se pouze o operaci Odeslat zprávu.

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor
{
    public OrderProcessorClient(){}

    public OrderProcessorClient(string configurationName)
        : base(configurationName)
    { }

    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SubmitPurchaseOrder(msg);
    }
}
```

 Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta. Můžete vidět, že služba přijímá zprávy z klienta. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta. Počítejte s tím, že protože se používá služba zařazování do fronty, klient a služba nemusí být spuštěny ve stejnou dobu. Můžete třeba spustit klienta, vypnout ho a pak službu spustit a zároveň se jim budou zobrazovat zprávy.

> [!NOTE]
> Tato ukázka vyžaduje instalaci služby Řízení front zpráv. Projděte si pokyny k instalaci ve [službě Řízení front zpráv](https://go.microsoft.com/fwlink/?LinkId=94968).  
  
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
  
3. V souboru Client. exe. config změňte adresu koncového bodu klienta tak, aby určovala název počítače služby místo ".".  
  
4. Na počítači služby spusťte z příkazového řádku Service. exe.  
  
5. V klientském počítači spusťte z příkazového řádku soubor Client. exe.  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Řízení front zpráv](https://go.microsoft.com/fwlink/?LinkId=94968)
