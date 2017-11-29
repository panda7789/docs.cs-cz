---
title: "Z WCF do Řízení front zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
caps.latest.revision: "32"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6800db4e5f8dc1a0d571be3eed556503b907e16e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="windows-communication-foundation-to-message-queuing"></a>Z WCF do Řízení front zpráv
Tento příklad ukazuje, jak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace můžete odeslat zprávu do aplikace služby Řízení front zpráv (MSMQ). Služba je vlastním hostováním konzolové aplikace, které vám umožňují sledovat službu přijetí zprávy ve frontě. Klienta a služby nemusíte používat ve stejnou dobu.  
  
 Služba přijímá zprávy z fronty a zpracovává objednávky. Služba vytvoří transakční fronty a nastaví obslužné rutiny zpráv přijata zpráva, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
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
  
 Při příjmu zprávy ve frontě obslužné rutiny zpráv `ProcessOrder` je volána.  
  
```  
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
  
 Extrahuje služby `ProcessOrder` ze služby MSMQ tělo zprávy a zpracuje pořadí.  
  
 Název fronty služby MSMQ je zadaný v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázka konfigurace.  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  Název fronty používá tečku (.) pro místní počítač a oddělovače zpětné lomítko, v jeho cesty.  
  
 Klient vytvoří nákupní objednávka a odešle nákupní objednávka v rámci oboru transakce, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
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
  
 Klient použije k odeslání zprávy služby MSMQ do fronty vlastní klienta v daném pořadí. Vzhledem k tomu, že je aplikace, který obdrží a zpracuje zprávy aplikací služby MSMQ a ne [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, neexistuje žádný kontrakt implicitní služby mezi těmito dvěma aplikacemi. Ano nemůžeme vytvořit proxy server pomocí nástroje Svcutil.exe v tomto scénáři.  
  
 Vlastní klienta je v podstatě stejný pro všechny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, které používají `MsmqIntegration` vazby k odesílání zpráv. Na rozdíl od ostatních klientů nebude obsahovat celou řadu operací služby. Je zpráva operaci odeslání jenom.  
  
```  
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
  
 Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly služby a klienta. Uvidíte služby přijmout zprávy z klienta. Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby. Všimněte si, že vzhledem k tomu, že služby Řízení front se používá, klient a služba nemusí být spuštěná ve stejnou dobu. Například můžete spustit klienta, vypněte ho a potom spuštění služby a je stále by přijímat jeho zprávy.  
  
> [!NOTE]
>  Tato ukázka vyžaduje instalaci služby Řízení front zpráv. Najdete v pokynech k instalaci v [služby Řízení front zpráv](http://go.microsoft.com/fwlink/?LinkId=94968).  
  
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
  
3.  V souboru Client.exe.config změnit adresa koncového bodu klienta k zadání názvu počítače služba místo ".".  
  
4.  Na počítači se službou spusťte z příkazového řádku Service.exe.  
  
5.  Na klientském počítači spusťte z příkazového řádku Client.exe.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a>Viz také  
 [Postupy: výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Služba Řízení front zpráv](http://go.microsoft.com/fwlink/?LinkId=94968)
