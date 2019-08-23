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
# <a name="message-queuing-to-windows-communication-foundation"></a>Řízení front zpráv do WCF
Tato ukázka předvádí, jak může aplikace řízení front zpráv (MSMQ) odesílat zprávy MSMQ službě Windows Communication Foundation (WCF). Služba je samoobslužná Konzolová aplikace, která vám umožní sledovat službu přijímající zprávy zařazené do fronty.  
  
 Kontrakt služby je `IOrderProcessor`, který definuje jednosměrnou službu, která je vhodná pro použití s frontami. Zpráva služby MSMQ neobsahuje záhlaví akce, takže není možné automaticky mapovat různé zprávy MSMQ na provozní kontrakty. Proto může existovat pouze jedna kontrakt operace. Pokud chcete pro službu definovat více než jednu kontrakt operace, aplikace musí poskytnout informace o tom, které záhlaví ve zprávě služby MSMQ (například popisek nebo ID korelace) se dá použít k rozhodnutí, který kontrakt operace se má odeslat.
  
 Zpráva služby MSMQ neobsahuje informace o tom, která záhlaví jsou namapována na různé parametry kontraktu operace. Parametr je typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), který obsahuje podkladovou zprávu služby MSMQ. Typ "T" v <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>třídě (`MsmqMessage<T>`) představuje data serializovaná do těla zprávy služby MSMQ. V této ukázce `PurchaseOrder` je typ serializován do těla zprávy služby MSMQ.  
  
 Následující vzorový kód ukazuje kontrakt služby pro službu zpracování objednávek.  

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

 Služba je hostována svým hostitelem. Při použití služby MSMQ musí být použitá fronta vytvořená předem. To lze provést ručně nebo prostřednictvím kódu. V této ukázce služba kontroluje existenci fronty a v případě potřeby ji vytvoří. Název fronty se načte z konfiguračního souboru.

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

 Služba vytvoří a otevře <xref:System.ServiceModel.ServiceHost> `OrderProcessorService`pro, jak je znázorněno v následujícím ukázkovém kódu.

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

 Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázkové konfiguraci.

> [!NOTE]
> Název fronty pro místní počítač a oddělovače zpětného lomítka v cestě používá tečku (.). Adresa koncového bodu WCF Určuje schéma služby MSMQ. formatname a pro místní počítač používá localhost. Adresa fronty pro každý název formátu MSMQ pokyny pro adresování se řídí schématem MSMQ. FormatName.

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 Klientská aplikace je aplikace služby MSMQ, která používá <xref:System.Messaging.MessageQueue.Send%2A> metodu k odeslání trvalé a transakční zprávy do fronty, jak je znázorněno v následujícím ukázkovém kódu.

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

 Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta. Můžete vidět, že služba přijímá zprávy z klienta. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta. Počítejte s tím, že protože se používá služba zařazování do fronty, klient a služba nemusí být spuštěny ve stejnou dobu. Můžete třeba spustit klienta, vypnout ho a pak službu spustit a zároveň se jim budou zobrazovat zprávy.

### <a name="to-setup-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici. Pokud fronta není přítomna, služba ji vytvoří. Službu můžete nejdřív spustit, abyste mohli vytvořit frontu, nebo ji můžete vytvořit pomocí Správce fronty MSMQ. Pomocí těchto kroků vytvořte ve Windows 2008 frontu.

    1. Otevřete Správce serveru v aplikaci Visual Studio 2012.

    2. Rozbalte kartu **funkce** .

    3. Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **Nový**, **soukromá fronta**.

    4. Zaškrtněte políčko **transakční** .

    5. Jako `ServiceModelSamplesTransacted` název nové fronty zadejte.

3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci s jedním počítačem, postupujte podle pokynů v [části spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači

1. Zkopírujte programové soubory služby ze složky \service\bin\ ve složce specifické pro daný jazyk do počítače služby.

2. Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.

3. V souboru Client. exe. config změňte orderQueueName a zadejte název počítače služby místo ".".

4. Na počítači služby spusťte z příkazového řádku Service. exe.

5. V klientském počítači spusťte z příkazového řádku soubor Client. exe.

> [!IMPORTANT]
>  Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a>Viz také:

- [Fronty ve WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Řízení front zpráv](https://go.microsoft.com/fwlink/?LinkId=94968)
