---
title: "Vlastní demux"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
caps.latest.revision: "41"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d4a460adfb8076f5d2c0fe273511e6de80be4ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="custom-demux"></a>Vlastní demux
Tento příklad ukazuje, jak hlavičky zpráv MSMQ lze mapovat na jinou službu operations tak, aby [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby využívající <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nejsou omezeny na použití jedné operace služby, jak je předvedeno v [služba Řízení front zpráv Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) a [Windows Communication Foundation do řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) ukázky.  
  
 Služba v této ukázce je vlastním hostováním konzolové aplikace, které vám umožňují sledovat, že služby, která přijímá zprávy zařazené do fronty.  
  
 Kontrakt služby je `IOrderProcessor`a definuje jednosměrné služby, který je vhodný pro použití s front.  
  
```  
[ServiceContract]  
[KnownType(typeof(PurchaseOrder))]  
[KnownType(typeof(String))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Name = "SubmitPurchaseOrder")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
  
    [OperationContract(IsOneWay = true, Name = "CancelPurchaseOrder")]  
    void CancelPurchaseOrder(MsmqMessage<string> ponumber);  
}  
```  
  
 Zprávy MSMQ nemá hlavičku akce. Není možné automaticky mapovat různé zprávy služby MSMQ kontrakty operaci. Proto může být pouze jeden kontrakt operaci. K překonání tohoto omezení služby implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> metodu <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> rozhraní. <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> Metoda umožňuje službu, kterou chcete mapovat danou hlavičku zprávy pro konkrétní službu operaci. V této ukázce je záhlaví popisek zprávy je namapovaný k operacím služby. `Name` Parametr operaci kontrakt Určuje, které operace služby musí být odesílány pro danou zprávou štítek. Například pokud hlavička popisek zprávy obsahuje "SubmitPurchaseOrder", je volána operace služby "SubmitPurchaseOrder".  
  
```  
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```  
  
 Služba musí implementovat <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> metodu <xref:System.ServiceModel.Description.IContractBehavior> rozhraní, jak je znázorněno v následujícím ukázkovém kódu. To platí vlastní `OperationSelector` modulu runtime service framework odesílání.  
  
```  
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```  
  
 Zpráva musí projít dispečera <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> před získáním k třída OperationSelector. Ve výchozím nastavení je odmítnuta zprávu, pokud jeho akce nebyl nalezen na jakékoli smlouvy implementované službu. Abyste se vyhnuli tuto kontrolu, můžeme implementovat <xref:System.ServiceModel.Description.IEndpointBehavior> s názvem `MatchAllFilterBehavior`, což umožňuje jakékoli zprávy předávat `ContractFilter` použitím <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> následujícím způsobem.  
  
```  
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```  
  
 Zpráva odeslaná službou, je odeslána operaci příslušnou službu pomocí informací uvedených v hlavičce popisek. Tělo zprávy je deserializovat do `PurchaseOrder` objektu, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```  
  
 Služba se hostuje sama. Při použití služby MSMQ, fronty, který se používá, musí být vytvořeny předem. Tento krok můžete provést ručně nebo prostřednictvím kódu. V této ukázce služba obsahuje kód, zkontrolujte existenci fronty a ji vytvoří, pokud fronta neexistuje. Název fronty je číst z konfiguračního souboru.  
  
```  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration  
    string queueName = ConfigurationManager.AppSettings["orderQueueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {                 
        ServiceEndpoint endpoint = serviceHost.Description.Endpoints[0];  
        endpoint.Behaviors.Add(new MatchAllFilterBehavior());  
  
        //Open the ServiceHost to create listeners and start listening for messages.  
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
  
 Název fronty služby MSMQ je zadán v oddílu appSettings konfiguračního souboru.  
  
> [!NOTE]
>  Název fronty používá tečku (.) pro místní počítač a oddělovače zpětné lomítko, v jeho cesty. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Adresa koncového bodu určuje schématu msmq.formatname a používá localhost pro místní počítač. Následující schéma je adresa správně formátovaný fronty podle názvu formátu MSMQ adresování pokyny.  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  Tato ukázka vyžaduje instalaci [služby Řízení front zpráv](http://go.microsoft.com/fwlink/?LinkId=95143).  
  
 Spusťte službu a spustit klienta.  
  
 Tento výstup je vidět na straně klienta.  
  
```  
Placed the order:Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
Canceled the Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
Press <ENTER> to terminate client.  
```  
  
 Tento výstup musí zobrazit na službu.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
Processing Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Shipped  
Purchase Order 28fc457a-1a56-4fe0-9dde-156965c21ed6 is canceled  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty. Pokud fronta neexistuje, vytvoří služba jeden. Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ. Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.  
  
    1.  Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozbalte **funkce** kartě.  
  
    3.  Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.  
  
    4.  Zkontrolujte **transakcí** pole.  
  
    5.  Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.  
  
3.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a>Viz také  
 [Fronty ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Služba Řízení front zpráv](http://go.microsoft.com/fwlink/?LinkId=95143)
