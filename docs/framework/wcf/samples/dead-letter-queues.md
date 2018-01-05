---
title: "Fronty nedoručených zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09a41abc8bc9fc3469ba35d7c7cfbe85d05ca174
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="dead-letter-queues"></a>Fronty nedoručených zpráv
Tento příklad znázorňuje postup zpracování a zpracování zpráv, které selhaly doručení. Je založena na [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) ukázka. V tomto příkladu `netMsmqBinding` vazby. Služba je vlastním hostováním konzolové aplikace, které vám umožňují sledovat službu přijetí zprávy ve frontě.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
> [!NOTE]
>  Tento příklad znázorňuje každou frontu nedoručených zpráv aplikace, která je dostupná pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)]. Ukázku můžete upravit tak, aby použít výchozí systémové fronty služby MSMQ 3.0 na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 V komunikaci ve frontě klient komunikuje se služby pomocí fronty. Přesněji řečeno klient odešle zprávy do fronty. Služba přijímá zprávy z fronty. Služba a klient proto nemusíte používat současně na komunikaci pomocí fronty.  
  
 Vzhledem k tomu, že komunikace ve frontě zahrnuje množství dormanci; můžete přidružit hodnota time to live na zprávu zajistit, že zpráva není získat doručí aplikaci pokud je mimo po čase. Existují také případy, kdy aplikace musí být informováni zda zprávu se nepovedlo doručení. Ve všech těchto případech například když time-to-live na zprávu vypršela platnost nebo se nezdařilo, doručení, zpráva bude umístěna do fronty nedoručených zpráv. Odesílající aplikací můžete číst zprávy do fronty nedoručených zpráv a provést opravné akce, které odešlete zprávu a odstranění příčiny selhání doručení v rozsahu od žádná akce.  
  
 Frontu nedoručených zpráv v `NetMsmqBinding` vazba je vyjádřena v následujících vlastností:  
  
-   <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>Vlastnost express druh frontu nedoručených zpráv požadované klientem. Tento výčet má následující hodnoty:  
  
-   `None`: Klient vyžaduje žádná fronta nedoručených zpráv.  
  
-   `System`: Fronty nedoručených zpráv systému se používá k ukládání neaktivní zprávy. Fronty nedoručených zpráv systému sdílejí všechny aplikace spuštěné v počítači.  
  
-   `Custom`: Vlastní frontu nedoručených zpráv zadán pomocí <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> vlastnost se používá k ukládání neaktivní zprávy. Tato funkce je dostupná pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)]. To se používá, když aplikace musí používat vlastní frontu nedoručených zpráv místo sdílení s dalších aplikací běžících na stejném počítači.  
  
-   <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>Vlastnost express konkrétní fronty, které chcete použít jako frontu nedoručených zpráv. Toto je k dispozici pouze v [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 V této ukázce klient odešle dávku zpráv do služby z rozsahu transakce a určuje nahodile nízkou hodnotu "time-to-live" pro tyto zprávy (přibližně 2 sekundy). Klient také určuje vlastní frontu nedoručených zpráv používat k zařazování zprávy, jejichž platnost vypršela.  
  
 Klientská aplikace můžou číst zprávy do fronty nedoručených zpráv a buď opakování odesílání zprávy nebo opravte chybu, která způsobila, že na původní zprávu o umístit do fronty nedoručených zpráv a odeslat zprávu. V ukázce klient se zobrazí chybová zpráva.  
  
 Kontrakt služby je `IOrderProcessor`, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 Služba kód v ukázce je u [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
 Komunikace se službou probíhá v rámci oboru transakce. Tato služba čte zprávy z fronty, provede operaci a potom zobrazí výsledky operace. Aplikace také vytvoří frontu nedoručených zpráv nedoručených zpráv.  
  
```  
//The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        // Get MSMQ queue name from app settings in configuration  
        string deadLetterQueueName = ConfigurationManager.AppSettings["deadLetterQueueName"];  
  
        // Create the transacted MSMQ queue for storing dead message if necessary.  
        if (!MessageQueue.Exists(deadLetterQueueName))  
            MessageQueue.Create(deadLetterQueueName, true);  
  
        // Create a proxy with given client endpoint configuration  
        OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
        // Create the purchase order  
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
  
        //Create a transaction scope.  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            // Make a queued call to submit the purchase order  
            client.SubmitPurchaseOrder(po);  
            // Complete the transaction.  
            scope.Complete();  
        }  
  
        client.Close();  
  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```  
  
 Konfigurace klienta určuje krátká doba trvání pro zprávy cílové službě. Pokud zpráva nemůže přenášených v rámci zadaná doba trvání, zprávy vyprší a je přesunuta do fronty nedoručených zpráv.  
  
> [!NOTE]
>  Je možné pro klienta pro doručení zprávy do fronty služby v rámci zadané doby. Zajistit, že vidíte službu nedoručených zpráv v akci, byste měli spustit před spuštěním služby klienta. Zpráva vyprší časový limit a doručí se do služby nedoručených zpráv.  
  
 Aplikace musí definovat fronty, které chcete použít jako jeho frontu nedoručených zpráv. Pokud je zadána žádná fronta, výchozí systémové transakční fronty nedoručených zpráv se používá k neaktivní zprávy ve frontě. V tomto příkladu klientská aplikace určuje vlastní frontu nedoručených zpráv aplikace.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- use appSetting to configure MSMQ Dead Letter queue name -->  
    <add key="deadLetterQueueName" value=".\private$\ServiceModelSamplesOrdersAppDLQ"/>  
  </appSettings>  
  
  <system.serviceModel>  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"   
                binding="netMsmqBinding"   
                bindingConfiguration="PerAppDLQBinding"   
                contract="IOrderProcessor" />  
    </client>  
  
    <bindings>  
      <netMsmqBinding>  
        <binding name="PerAppDLQBinding"  
                 deadLetterQueue="Custom"  
                 customDeadLetterQueue="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"   
                 timeToLive="00:00:02"/>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Služba nedoručených zpráv přečte zprávy z fronty nedoručených zpráv. Implementuje služby nedoručených zpráv `IOrderProcessor` kontrakt. Jeho implementace ale není na proces objednávky. Služba nedoručených zpráv je služba klienta a nemá zařízení při zpracování objednávky.  
  
> [!NOTE]
>  Frontu nedoručených zpráv je fronty klienta a místní účet správce klienta fronty.  
  
 Implementace služby nedoručených zpráv kontroluje z důvodu, že se že zprávu nepodařilo doručení a trvá opravná opatření. Důvod selhání zpráv zachytí ve dvou výčty <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> a <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>. Můžete získat <xref:System.ServiceModel.Channels.MsmqMessageProperty> z <xref:System.ServiceModel.OperationContext> jak je znázorněno v následujícím ukázkovém kódu:  
  
```  
public void SubmitPurchaseOrder(PurchaseOrder po)  
{  
    Console.WriteLine("Submitting purchase order did not succed ", po);  
    MsmqMessageProperty mqProp =   
                  OperationContext.Current.IncomingMessageProperties[  
                  MsmqMessageProperty.Name] as MsmqMessageProperty;  
    Console.WriteLine("Message Delivery Status: {0} ",   
                                                mqProp.DeliveryStatus);  
    Console.WriteLine("Message Delivery Failure: {0}",   
                                               mqProp.DeliveryFailure);  
    Console.WriteLine();  
    ….  
}  
```  
  
 Zprávy do fronty nedoručených zpráv jsou zprávy adresované do služby, která je zpracování zprávy. Proto když služba nedoručených zpráv čte zprávy z fronty [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vrstvy kanálu najde neshody v koncových bodů a není odeslat zprávu. V takovém případě zprávy je řešit pořadí zpracování služby, ale je přijatých službou nedoručených zpráv. Pro příjem zprávy, která je určena k jinému koncovému bodu, filtr adres tak, aby odpovídaly libovolná adresa je uveden v `ServiceBehavior`. To je nutné úspěšně zpracovat zprávy, které se načítají z fronty nedoručených zpráv.  
  
 V této ukázce služba nedoručených zpráv znovu odešle zprávu Pokud z důvodu selhání je, že zpráva Vypršel časový limit. Z jiných důvodů zobrazí chyba doručení, jak je znázorněno v následujícím ukázkovém kódu:  
  
```  
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Single, AddressFilterMode=AddressFilterMode.Any)]  
public class PurchaseOrderDLQService : IOrderProcessor  
{  
    OrderProcessorClient orderProcessorService;  
    public PurchaseOrderDLQService()  
    {  
        orderProcessorService = new OrderProcessorClient("OrderProcessorEndpoint");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Console.WriteLine("Submitting purchase order did not succeed ", po);  
        MsmqMessageProperty mqProp = OperationContext.Current.IncomingMessageProperties[MsmqMessageProperty.Name] as MsmqMessageProperty;  
  
        Console.WriteLine("Message Delivery Status: {0} ", mqProp.DeliveryStatus);  
        Console.WriteLine("Message Delivery Failure: {0}", mqProp.DeliveryFailure);  
        Console.WriteLine();  
  
        // resend the message if timed out  
        if (mqProp.DeliveryFailure == DeliveryFailure.ReachQueueTimeout ||  
            mqProp.DeliveryFailure == DeliveryFailure.ReceiveTimeout)  
        {  
            // re-send  
            Console.WriteLine("Purchase order Time To Live expired");  
            Console.WriteLine("Trying to resend the message");  
  
            // reuse the same transaction used to read the message from dlq to enqueue the message to app. queue  
            orderProcessorService.SubmitPurchaseOrder(po);  
            Console.WriteLine("Purchase order resent");  
        }  
    }  
  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the PurchaseOrderDLQService type.  
        using (ServiceHost serviceHost = new ServiceHost(typeof(PurchaseOrderDLQService)))  
        {  
            // Open the ServiceHostBase to create listeners and start listening for messages.  
            serviceHost.Open();  
  
            // The service can now be accessed.  
            Console.WriteLine("The dead letter service is ready.");  
            Console.WriteLine("Press <ENTER> to terminate service.");  
            Console.WriteLine();  
            Console.ReadLine();  
        }  
    }  
}   
```  
  
 Následující příklad ukazuje konfiguraci nedoručených zpráv:  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.PurchaseOrderDLQService">  
        <!-- Define NetMsmqEndpoint in this case, DLQ end point to read messages-->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"  
                  binding="netMsmqBinding"  
                  bindingConfiguration="DefaultBinding"   
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                 address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"   
                 binding="netMsmqBinding"   
                 bindingConfiguration="SystemDLQBinding"   
                 contract="IOrderProcessor" />  
    </client>  
  
    <bindings>  
      <netMsmqBinding>  
        <binding name="DefaultBinding" />  
        <binding name="SystemDLQBinding"  
                 deadLetterQueue="System"/>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
 V běžícím ukázku, jsou 3 spustitelných souborů a zkontrolujte, jak funguje frontu nedoručených zpráv pro každou aplikaci; klienta, služby a služby nedoručených zpráv, který čte z fronty nedoručených zpráv pro každou aplikaci a znovu odešle zprávu do služby. Všechny jsou konzolové aplikace s výstupem v oknech konzoly.  
  
> [!NOTE]
>  Protože služba Řízení front se používá, klient a služba nemusí být spuštěná ve stejnou dobu. Spuštění klienta, vypněte ho a potom spuštění služby a stále přijímá jeho zprávy. Doporučujeme spustit službu a vypnout, aby bylo možné vytvořit frontu.  
  
 Při spuštění klienta, klient se zobrazí zpráva:  
  
```  
Press <ENTER> to terminate client.  
```  
  
 Klient se pokusil o odeslání zprávy, ale s krátkou vypršení časového limitu, zpráva vypršela a je nyní zařazeny do fronty nedoručených zpráv pro každou aplikaci.  
  
 Pak spusťte službu nedoručených zpráv, která čte zprávy a zobrazí kód chyby a znovu odešle zprávu zpět ke službě.  
  
```  
The dead letter service is ready.  
Press <ENTER> to terminate service.  
  
Submitting purchase order did not succeed  
Message Delivery Status: InDoubt  
Message Delivery Failure: ReachQueueTimeout  
  
Purchase order Time To Live expired  
Trying to resend the message  
Purchase order resent  
```  
  
 Služba spustí a pak přečte zprávu opětovného odeslání a procesy.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 97897eff-f926-4057-a32b-af8fb11b9bf9  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
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
  
4.  Ke spuštění ukázky ve frontě změnit konfiguraci jednoho nebo více počítače názvy správně, nahraďte localhost úplný název počítače a postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Ke spuštění ukázky na počítače připojeného k pracovní skupině  
  
1.  Pokud počítač není součástí domény, vypněte zabezpečení přenosu podle nastavení úrovně režim a ochrany ověřování na `None` jak je znázorněno v následující ukázka konfigurace:  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding name="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
     Ujistěte se, koncový bod je přidružen vazbu pomocí nastavení pro koncový bod `bindingConfiguration` atribut.  
  
2.  Ujistěte se, že změníte konfiguraci DeadLetterService, serveru a klienta, před spuštěním ukázky.  
  
    > [!NOTE]
    >  Nastavení `security mode` k `None` je ekvivalentní nastavení `MsmqAuthenticationMode`, `MsmqProtectionLevel` a `Message` zabezpečení `None`.  
  
## <a name="comments"></a>Komentáře  
 Ve výchozím nastavení se `netMsmqBinding` vazby přenos, zabezpečení je povoleno. Dvě vlastnosti `MsmqAuthenticationMode` a `MsmqProtectionLevel`, společně určují typ zabezpečení přenosu. Ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`. Pro MSMQ k ověřování a podepisování funkce musí být součástí domény. Pokud tuto ukázku spustit na počítači, který není součástí domény, můžete dojít k následující chybě: "Uživatele interní zpráv služby Řízení front certifikát neexistuje".  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
  
## <a name="see-also"></a>Viz také
