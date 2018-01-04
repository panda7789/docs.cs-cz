---
title: "Řízení front zpráv do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a4b63dd620d071b875caa255f681bdd5fb867f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="message-queuing-to-windows-communication-foundation"></a>Řízení front zpráv do WCF
Tento příklad ukazuje, jak můžete k aplikaci služby Řízení front zpráv (MSMQ) odešle zprávu služby MSMQ pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby. Služba je vlastním hostováním konzolové aplikace, které vám umožňují sledovat službu přijetí zprávy ve frontě.  
  
 Kontrakt služby je `IOrderProcessor`, která definuje jednosměrné služby, který je vhodný pro použití s front. Zprávy MSMQ nemá hlavičku akce, takže není možné automaticky mapovat různé zprávy služby MSMQ kontrakty operaci. Proto může být pouze jeden kontrakt operaci. Pokud chcete definovat více než jeden kontrakt operace služby, aplikace musí poskytovat informace o tom, které záhlaví zprávy služby MSMQ (například popisek nebo correlationID) slouží k rozhodnout, které operace kontrakt k odeslání. Tento postup je znázorněn v [vlastní Demux](../../../../docs/framework/wcf/samples/custom-demux.md).  
  
 Zprávy služby MSMQ neobsahuje informace o tom, které hlavičky jsou namapované na různé parametry operace kontrakt. Parametr je typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), která obsahuje základní zprávy služby MSMQ. Typ "T" v <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) třída reprezentuje data, která je serializován do textu zprávy služby MSMQ. V této ukázce `PurchaseOrder` typ serializován do textu zprávy služby MSMQ.  
  
 Následující vzorový kód ukazuje kontrakt služby pořadí zpracování služby.  
  
```  
// Define a service contract.  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```  
  
 Služba je sám sebou hostované. Při použití služby MSMQ, používá fronty musí být vytvořeny předem. Tento krok můžete provést ručně nebo prostřednictvím kódu. V této ukázce služba zkontroluje existenci fronty a v případě potřeby ji vytvoří. Název fronty je číst z konfiguračního souboru.  
  
```  
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
  
```  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
{  
    serviceHost.Open();  
    Console.WriteLine("The service is ready.");  
    Console.WriteLine("Press <ENTER> to terminate service.");  
    Console.ReadLine();  
    serviceHost.Close();  
}  
```  
  
 Název fronty služby MSMQ je zadaný v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázka konfigurace.  
  
> [!NOTE]
>  Název fronty používá tečku (.) pro místní počítač a oddělovače zpětné lomítko, v jeho cesty. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Adresa koncového bodu určuje schématu msmq.formatname a používá localhost pro místní počítač. Adresu fronty pro každý název formátu MSMQ adresování pokyny následuje msmq.formatname schéma.  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 Klientská aplikace je aplikace služby MSMQ, která používá <xref:System.Messaging.MessageQueue.Send%2A> metoda odeslání odolné a transakční zprávy do fronty, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
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
  
 Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly služby a klienta. Uvidíte služby přijmout zprávy z klienta. Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby. Všimněte si, že vzhledem k tomu, že služby Řízení front se používá, klient a služba nemusí být spuštěná ve stejnou dobu. Například můžete spustit klienta, vypněte ho a potom spuštění služby a je stále by přijímat jeho zprávy.  
  
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
  
4.  Na počítači se službou spusťte z příkazového řádku Service.exe.  
  
5.  Na klientském počítači spusťte z příkazového řádku Client.exe.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a>Viz také  
 [Fronty ve WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Služba Řízení front zpráv](http://go.microsoft.com/fwlink/?LinkId=94968)
