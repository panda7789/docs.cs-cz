---
title: Vlastní demux
ms.date: 03/30/2017
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
ms.openlocfilehash: 1542743a6e1658bad162d7ee9ca73e6b9b0444e2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43803418"
---
# <a name="custom-demux"></a>Vlastní demux
Tato ukázka předvádí, jak záhlaví zpráv MSMQ lze mapovat na jinou službu operations tak, aby služba Windows Communication Foundation (WCF), které používají <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nejsou možné použít jedna operace služby, jak je ukázáno v [ Zprávy služby Řízení front zpráv do služby Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) a [Windows Communication Foundation do služby Řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) ukázky.  
  
 Služby v této ukázce je v místním prostředí konzoly aplikace, která vám umožní sledovat, že služba, která bude přijímat zprávy zařazené do fronty.  
  
 Kontrakt služby je `IOrderProcessor`a definuje jednosměrné, který je vhodný pro použití s frontami služby.  

```csharp
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

 Zprávy MSMQ nemá hlavičku akce. Není možné automaticky mapovat různé zprávy služby MSMQ pro operaci smlouvy. Proto může být pouze jeden kontrakt. K překonání tohoto omezení, služba implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> metodu <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> rozhraní. <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> Metoda povoluje službu k mapování Zadaná hlavička zprávy pro konkrétní službu operaci. V této ukázce je popisek hlavičky namapované k operacím služby. `Name` Parametr kontrakt Určuje, kterou služba operaci musí být odeslána pro danou zprávu popisek. Například pokud hlavička popisek zprávy obsahuje "SubmitPurchaseOrder", "SubmitPurchaseOrder" service je operace vyvolávána.  

```csharp
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```

 Musí implementovat službu <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> metodu <xref:System.ServiceModel.Description.IContractBehavior> rozhraní, jak je znázorněno v následujícím ukázkovém kódu. To platí pro vlastní `OperationSelector` na modul runtime služby rozhraní framework odeslání.  

```csharp
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```

 Zpráva musí projít přes dispečera <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> před získáním třída OperationSelector. Ve výchozím nastavení je zpráva odmítnuta, pokud jeho akce nebyl nalezen v jakékoli kontraktů implementovaných službou. Aby tato kontrola Implementujeme <xref:System.ServiceModel.Description.IEndpointBehavior> s názvem `MatchAllFilterBehavior`, umožňuje jakákoliv zpráva o předávání `ContractFilter` použitím <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> následujícím způsobem.  

```csharp
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```
  
 Při doručení zprávy do službou operace příslušnou službu je odeslána, pomocí informací uvedených v hlavičce popisek. Text zprávy je deserializovat do `PurchaseOrder` objektu, jak je znázorněno v následujícím ukázkovém kódu.  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```

 Tato služba je v místním prostředí. Při použití služby MSMQ, fronty, který se používá, je nutné vytvořit předem. To můžete udělat ručně nebo prostřednictvím kódu. V této ukázce služby obsahuje kód pro provedení kontroly existence fronty a ji vytvoří, pokud fronta neexistuje. Název fronty načítají z konfiguračního souboru.  

```csharp
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

 Název fronty MSMQ je zadán v oddílu appSettings konfiguračním souboru.  
  
> [!NOTE]
>  Název fronty používá tečku (.) pro místní počítače a zpětné lomítko oddělovače v cestě. Adresa koncového bodu WCF Určuje schéma msmq.formatname a používá localhost pro místní počítač. Schéma následuje adresa správně formátovaná fronty podle názvu formátu MSMQ adresování pokyny.  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  Tato ukázka vyžaduje instalaci [služby Řízení front zpráv](https://go.microsoft.com/fwlink/?LinkId=95143).  
  
 Spusťte službu a klienta.  
  
 Následující výstup je zobrazena na straně klienta.  
  
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
  
 Ve službě musí zobrazit následující výstup.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pokud je služba spuštěna první, zkontroluje se tak, aby byl do fronty k dispozici. Pokud fronta neexistuje, služba ho vytvoří. Můžete spustit služba nejdřív vytvořte frontu nebo můžete vytvořit prostřednictvím Správce fronty MSMQ. Postupujte podle těchto kroků můžete vytvořit frontu Windows 2008.  
  
    1.  Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozbalte **funkce** kartu.  
  
    3.  Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **nový**, **soukromou frontu**.  
  
    4.  Zkontrolujte, **transakční** pole.  
  
    5.  Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.  
  
3.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a>Viz také  
 [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Služba Řízení front zpráv](https://go.microsoft.com/fwlink/?LinkId=95143)
