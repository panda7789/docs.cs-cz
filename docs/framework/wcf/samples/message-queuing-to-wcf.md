---
title: Řízení front zpráv do WCF
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 16b9c9fa3c66ad86fe9502b14fc09ff8d543d58a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47396991"
---
# <a name="message-queuing-to-windows-communication-foundation"></a>Řízení front zpráv do WCF
Tato ukázka předvádí, jak aplikace služby Řízení front zpráv (MSMQ) zprávy MSMQ odeslat do služby Windows Communication Foundation (WCF). Služba je v místním prostředí konzolovou aplikaci pro vám umožní sledovat službu přijímání zpráv zařazených do fronty.  
  
 Kontrakt služby je `IOrderProcessor`, která definuje jednosměrné, který je vhodný pro použití s frontami služby. Zprávy MSMQ nemá hlavičku akce, takže není možné automaticky mapovat různé zprávy služby MSMQ pro operaci smlouvy. Proto může být pouze jeden kontrakt. Pokud chcete definovat více než jeden kontrakt služby, aplikace musí poskytovat informace ohledně toho, která záhlaví zprávy služby MSMQ (například popisku nebo ID korelace) umožňuje rozhodnout, kterou kontrakt k odeslání.
  
 Zprávy služby MSMQ neobsahuje informace ohledně toho, která hlavičky jsou namapovány na různé parametry kontrakt. Parametr je typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), která obsahuje základní zprávy služby MSMQ. Typ "T" v <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) třída reprezentuje data, která je serializován do textu zprávy MSMQ. V této ukázce `PurchaseOrder` je typ serializován do textu zprávy MSMQ.  
  
 Následující ukázkový kód ukazuje kontrakt služby služba zpracování objednávky.  

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

 Tato služba je vlastní hostované. Při použití služby MSMQ, fronty, používá se musí vytvořit předem. To můžete udělat ručně nebo prostřednictvím kódu. V této ukázce služba zkontroluje existenci fronty a v případě potřeby ji vytvoří. Název fronty načítají z konfiguračního souboru.  

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

 Služba vytvoří a otevře <xref:System.ServiceModel.ServiceHost> pro `OrderProcessorService`, jak je znázorněno v následujícím ukázkovém kódu.  

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

 Název fronty MSMQ je zadat v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázková konfigurace.  
  
> [!NOTE]
>  Název fronty používá tečku (.) pro místní počítače a zpětné lomítko oddělovače v cestě. Adresa koncového bodu WCF Určuje schéma msmq.formatname a používá localhost pro místní počítač. Adresa fronty pro každý název formátu MSMQ adresování pokyny následuje schéma msmq.formatname.  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 Klientská aplikace je aplikace služby MSMQ, která se používá <xref:System.Messaging.MessageQueue.Send%2A> metodu pro odeslání odolné a transakční zprávy do fronty, jak je znázorněno v následujícím ukázkovém kódu.  

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

 Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly služby a klienta. Můžete zobrazit přijetí zprávy služby z klienta. Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby. Mějte na paměti, protože služba Řízení front se používá, klient a služba nemusí být zprovoznit ve stejnou dobu. Například může spustit klienta, vypněte ho a potom spusťte službu a pak by stále přijímat zprávy.  
  
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
  
4.  Na počítači se službou spusťte z příkazového řádku Service.exe.  
  
5.  Na klientském počítači spusťte Client.exe z příkazového řádku.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a>Viz také  
 [Fronty ve WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Služba Řízení front zpráv](https://go.microsoft.com/fwlink/?LinkId=94968)
