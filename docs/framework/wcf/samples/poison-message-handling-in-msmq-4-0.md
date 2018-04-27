---
title: Zacházení s nezpracovatelnými zprávami v MSMQ 4.0
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6f2361ed862986d2490968ae422b9b1313eedea3
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="poison-message-handling-in-msmq-40"></a>Zacházení s nezpracovatelnými zprávami v MSMQ 4.0
Tento příklad znázorňuje postup zpracování ve službě poškozených zpráv. Tato ukázka je založena na [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) ukázka. V tomto příkladu `netMsmqBinding`. Služba je vlastním hostováním konzolové aplikace, které vám umožňují sledovat službu přijetí zprávy ve frontě.  
  
 V komunikaci ve frontě klient komunikuje se služby pomocí fronty. Přesněji řečeno klient odešle zprávy do fronty. Služba přijímá zprávy z fronty. Služba a klient proto nemusíte používat současně na komunikaci pomocí fronty.  
  
 Nezpracovatelná zpráva je zpráva, která je opakovaně pro čtení z fronty při čtení zprávy služby nelze zpracovat zprávu a proto ukončí transakce, pod kterým je zpráva pro čtení. V takových případech je zpráva opakovat znovu. To může teoreticky, přejděte na navždy Pokud došlo k potížím se zprávou. Všimněte si, že to může dojít pouze při použití transakce čtení z fronty a volat operace služby.  
  
 Na základě verze služby MSMQ, – NetMsmqBinding podporuje omezenou zjišťování pro úplné zjišťování poškozených zpráv. Po zpráva byla zjištěna jako poškozen, pak může ošetřit několika způsoby. Znovu podle verze služby MSMQ, – NetMsmqBinding podporuje omezenou zpracování úplné zpracování poškozených zpráv.  
  
 Tato ukázka znázorňuje omezené poškozených zařízení, které jsou na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platformy a úplné poškozených zařízení, které jsou na [!INCLUDE[wv](../../../../includes/wv-md.md)]. V obou ukázky cílem je přesunout nezpracovatelná zpráva fronty do jiné fronty, která pak můžete obsloužení služba poškozených zpráv.  
  
## <a name="msmq-v40-poison-handling-sample"></a>MSMQ v4.0 Poison zpracování vzorku  
 V [!INCLUDE[wv](../../../../includes/wv-md.md)], budovy poškozených dílčí fronty, který slouží k uložení poškozených zpráv poskytuje služby MSMQ. Tento příklad znázorňuje osvědčený postup, který se zabývá poškozených zpráv pomocí [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 Detekce nezpracovatelná zpráva v [!INCLUDE[wv](../../../../includes/wv-md.md)] je poměrně složité. Existují 3 vlastností, které pomáhají s detekce. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Je počet časech danou zprávu znovu čtení z fronty a odeslat do aplikace pro zpracování. Znovu načtení zprávy z fronty při jeho je vrátit zpět do fronty protože zprávu nelze odeslat do aplikace nebo aplikaci vrátí zpět transakci v operaci služby. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> je počet, kolikrát zpráva bude přesunuta do fronty opakování. Když <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> je dosaženo, zpráva bude přesunuta do fronty opakování. Vlastnost <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> je prodlevu, po jejímž uplynutí zpráva bude přesunuta z fronty opakování zpět do hlavní fronty. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Nastaven na hodnotu 0. Zpráva se pokus o znovu. Pokud mají všechny pokusy o tuto zprávu přečíst, zprávy jsou označeny jako poškozen.  
  
 Jakmile zprávy je označena jako poškozen, zpráva se zabývá podle nastavení v <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> výčtu. Chcete-li znovu opakují možné hodnoty:  
  
-   Selhání (výchozí): na poruch naslouchací proces a taky hostitele služby.  
  
-   Přetažení: Chcete-li vyřadit zprávu.  
  
-   Přesunutí: Přesunout zprávu do fronty dílčí poškozená zpráva. Tato hodnota je k dispozici pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
-   Odmítnutí: Tak, aby zamítal zprávy, poslal zpět do odesílatele je nedoručených zpráv fronty. Tato hodnota je k dispozici pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 Ukázka ukazuje, jak pomocí `Move` dispozice pro poškozená zpráva. `Move` způsobí, že zpráva, kterou chcete přesunout do poškozených dílčí fronty.  
  
 Kontrakt služby je `IOrderProcessor`, která definuje jednosměrné služby, který je vhodný pro použití s front.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 Operace služby zobrazí zprávu s oznámením, že pořadí zpracování. K předvedení funkci nezpracovatelná zpráva `SubmitPurchaseOrder` operace služby vyvolá výjimku pro vrácení transakce u náhodných volání služby. To způsobí, že zpráva, která má být vrátit zpět ve frontě. Nakonec zprávy je označena jako poison. Konfigurace je nastavena na poškozených zprávu přesunout do poškozených dílčí fronty.  

```csharp
// Service class that implements the service contract.  
// Added code to write output to the console window.  
public class OrderProcessorService : IOrderProcessor  
{  
    static Random r = new Random(137);  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
  
        int randomNumber = r.Next(10);  
  
        if (randomNumber % 2 == 0)  
        {  
            Orders.Add(po);  
            Console.WriteLine("Processing {0} ", po);  
        }  
        else  
        {  
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);  
            Console.WriteLine();  
            throw new Exception("Cannot process purchase order: " + po.PONumber);  
        }  
    }  
  
    public static void OnServiceFaulted(object sender, EventArgs e)   
    {  
        Console.WriteLine("Service Faulted");  
    }  
  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Get MSMQ queue name from app settings in configuration.  
        string queueName = ConfigurationManager.AppSettings["queueName"];  
  
        // Create the transacted MSMQ queue if necessary.  
        if (!System.Messaging.MessageQueue.Exists(queueName))  
            System.Messaging.MessageQueue.Create(queueName, true);  
  
        // Get the base address that is used to listen for WS-MetaDataExchange requests.  
        // This is useful to generate a proxy for the client.  
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];  
  
        // Create a ServiceHost for the OrderProcessorService type.  
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));  
  
        // Hook on to the service host faulted events.  
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);  
  
        // Open the ServiceHostBase to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        if(serviceHost.State != CommunicationState.Faulted) {  
            serviceHost.Close();  
        }  
  
    }  
}  
```

 Konfigurace služby obsahuje následující vlastnosti nezpracovatelná zpráva: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, a `receiveErrorHandling` jak je znázorněno v následujícím souboru konfigurace.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />  
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>  
  </appSettings>  
  <system.serviceModel>  
    <services>  
      <service   
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"  
                  binding="netMsmqBinding"  
                  bindingConfiguration="PoisonBinding"   
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  
    <bindings>  
      <netMsmqBinding>  
        <binding name="PoisonBinding"   
                 receiveRetryCount="0"  
                 maxRetryCycles="1"  
                 retryCycleDelay="00:00:05"                        
                 receiveErrorHandling="Move">  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="processing-messages-from-the-poison-message-queue"></a>Zpracování zpráv z fronty poškozených zpráv  
 Služba poškozených zpráv čte zprávy z fronty konečné poškozených zpráv a zpracovává je.  
  
 Zprávy ve frontě nezpracovatelná zpráva jsou zprávy adresované do služby, která zpracovává zprávu, která může lišit od koncový bod služby nezpracovatelná zpráva. Proto při službu nezpracovatelná zpráva čte zprávy z fronty [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vrstvy kanálu najde neshody v koncových bodů a není odeslat zprávu. V takovém případě zprávy je řešit pořadí zpracování služby, ale je přijímání službou poškozená zpráva. Pokud chcete pokračovat i v případě, že zpráva je určena k jinému koncovému bodu, zobrazí se zpráva, musí přidáme `ServiceBehavior` filtru adresy, kde je kritérium přiřazování tak, aby odpovídaly žádný koncový bod služby je určeno zprávy. To je nutné úspěšně zpracovat zprávy, které můžete číst zprávy z fronty poškozená zpráva.  
  
 Implementace služby nezpracovatelná zpráva, samotné je velmi podobné implementace služby. Implementuje kontrakt a zpracovává objednávky. Tady je příklad kódu.  

```csharp
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
  
    public static void OnServiceFaulted(object sender, EventArgs e)   
    {  
        Console.WriteLine("Service Faulted...exiting app");  
        Environment.Exit(1);  
    }  
  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
  
        // Create a ServiceHost for the OrderProcessorService type.  
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));  
  
        // Hook on to the service host faulted events.  
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);  
  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The poison message service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHostBase to shutdown the service.  
        if(serviceHost.State != CommunicationState.Faulted)  
        {  
            serviceHost.Close();  
        }  
    }  
```

 Na rozdíl od pořadí služby, který čte zprávy z fronty pořadí zpracování služba poškozených zpráv čte zprávy typu z poškozených dílčí fronty. Poškozených fronty je dílčí fronta hlavní fronty, má název "poison" a je automaticky generovaný službou MSMQ. K přístupu, zadejte název fronty, za nímž následuje ";" a dílčí název fronty, v takovém případě-"poškozených", jak je znázorněno v následující ukázka konfigurace.  
  
> [!NOTE]
>  V ukázce pro MSMQ v3.0 název poškozených fronty není dílčí fronta, místo fronta, kterou jsme přesunout zprávu, která se.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"  
                  binding="netMsmqBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >  
        </endpoint>  
      </service>  
    </services>  
  
  </system.serviceModel>  
</configuration>  
```  
  
 Při spuštění vzorového klienta, služby a služby aktivity nezpracovatelná zpráva se zobrazí v konzole windows. Uvidíte služby přijmout zprávy z klienta. Stisknutím klávesy ENTER v každé okna konzoly vypnutí služby.  
  
 Služba spustí spuštěna, zpracování objednávky a náhodně spustí ukončit zpracování. Pokud zpráva indikuje, že zpracovala pořadí, můžete spustit klienta znovu odeslat další zprávu, až se, že služba byl ukončen ve skutečnosti zprávu. Podle nakonfigurovaného nastavení poškozených, zpráva se pokus o jednou pro zpracování před přesunutím do konečné poškozených fronty.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89  
```  
  
 Spuštění služby nezpracovatelná zpráva poškozená po zprávu přečíst z poškozených fronty. V tomto příkladu službu nezpracovatelná zpráva přečte zprávu a procesy. By mohli zobrazit, že je služba nezpracovatelná zpráva pro čtení nákupní objednávka, která byla ukončena a poškozen.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty. Pokud fronta neexistuje, vytvoří služba jeden. Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ. Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.  
  
    1.  Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozbalte **funkce** kartě.  
  
    3.  Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.  
  
    4.  Zkontrolujte **transakcí** pole.  
  
    5.  Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.  
  
3.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Chcete-li v konfiguraci s jednou nebo mezi počítači spustit ukázku, změňte názvy fronty, aby odrážel skutečný název hostitele místo localhost a postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Ve výchozím nastavení se `netMsmqBinding` vazby přenos, zabezpečení je povoleno. Dvě vlastnosti `MsmqAuthenticationMode` a `MsmqProtectionLevel`, společně určují typ zabezpečení přenosu. Ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`. Pro MSMQ k ověřování a podepisování funkce musí být součástí domény. Pokud tuto ukázku spustit na počítači, který není součástí domény, můžete dojít k následující chybě: "Uživatele interní zpráv služby Řízení front certifikát neexistuje".  
  
#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Ke spuštění ukázky na počítače připojeného k pracovní skupině  
  
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
  
     Zajistěte, aby že koncový bod je přidružen vazby nastavením atributu bindingConfiguration pro koncový bod.  
  
2.  Ujistěte se, že změníte konfiguraci PoisonMessageServer, serveru a klienta, před spuštěním ukázky.  
  
    > [!NOTE]
    >  Nastavení `security mode` k `None` je ekvivalentní nastavení `MsmqAuthenticationMode`, `MsmqProtectionLevel`, a `Message` zabezpečení `None`.  
  
3.  Aby výměny dat Meta pracovat jsme zaregistrovat adresu URL s vazbou http. To vyžaduje, aby služba spuštěna v okně zvýšenými oprávněními příkaz. Jinak dojde k výjimce, jako: neošetřená výjimka: System.ServiceModel.AddressAccessDeniedException: HTTP nebylo možné zaregistrovat URL http://+:8000/ServiceModelSamples/service/. Váš proces nemá přístupová práva na tento obor názvů (viz http://go.microsoft.com/fwlink/?LinkId=70353 podrobnosti). ---> System.Net.HttpListenerException: přístup byl odepřen.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`  
  
## <a name="see-also"></a>Viz také
