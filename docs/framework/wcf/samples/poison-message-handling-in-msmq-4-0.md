---
title: Zacházení s nezpracovatelnými zprávami v MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 4555a6d322cbf9ca43aca0f93bc6eafe021fa569
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266521"
---
# <a name="poison-message-handling-in-msmq-40"></a>Zacházení s nezpracovatelnými zprávami v MSMQ 4.0
Tento příklad ukazuje, jak provádět zpracování ve službě nezpracovatelných zpráv. Tato ukázka je založena na [nepodporuje transakce vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) vzorku. Tento příklad používá `netMsmqBinding`. Služba je v místním prostředí konzolovou aplikaci pro vám umožní sledovat službu přijímání zpráv zařazených do fronty.

 V komunikaci ve frontě klient komunikuje se služby pomocí fronty. Přesněji řečeno klient odešle zprávy do fronty. Služba přijímá zprávy z fronty. Klienta a služby, proto není potřeba běžet současně na komunikaci pomocí fronty.

 Nezpracovatelná zpráva se zpráva, která opakovaně čte z fronty při čtení zprávy služby nelze zpracovat zprávu a proto ukončí transakce, pod kterým je pro čtení zprávy. V takových případech je zpráva opakovat znovu. To teoreticky přejít navždy Pokud dojde k nějakému problému s touto zprávou. Všimněte si, že to může dojít pouze při použití transakcí čtení z fronty a vyvolat operaci služby.

 Založené na verzi služby MSMQ, NetMsmqBinding podporuje omezenou zjišťování pro úplné zjišťování nezpracovatelných zpráv. Po zprávy byl zjištěn, protože je poškozen, pak může být zpracována několika způsoby. Znovu založené na verzi služby MSMQ, NetMsmqBinding podporuje omezenou zpracování na úplné zpracování nezpracovatelných zpráv.

 Tato ukázka ilustruje omezený počet poškozených zařízení k dispozici na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platformy a úplné počet poškozených zařízení k dispozici na [!INCLUDE[wv](../../../../includes/wv-md.md)]. V obou ukázky cílem je přesunout nezpracovatelná zpráva ven fronty do jiné fronty, který lze potom udržovat službou nezpracovatelných zpráv.

## <a name="msmq-v40-poison-handling-sample"></a>MSMQ 4.0 Poison zpracování vzorku
 V [!INCLUDE[wv](../../../../includes/wv-md.md)], služby MSMQ obsahuje poškozené dílčí fronty zařízení, které slouží k ukládání nezpracovatelných zpráv. V této ukázce osvědčený postup řešení problémů s nezpracovatelných zpráv pomocí [!INCLUDE[wv](../../../../includes/wv-md.md)].

 Zjišťování nezpracovatelných zpráv v [!INCLUDE[wv](../../../../includes/wv-md.md)] je poměrně složité. Existují 3 vlastností, které pomáhají s detekcí. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Je málokdy danou zprávu je znovu čtení z fronty a odeslaného do aplikace pro zpracování. Opětovné načtení zprávy z fronty při přejde zpět do fronty, protože zprávu nelze odeslat do aplikace nebo aplikace vrátí zpět transakce v operaci služby. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> je počet pokusů, které se zpráva bude přesunuta do fronty zkuste to znovu. Když <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> je dosaženo, zpráva bude přesunuta do fronty zkuste to znovu. Vlastnost <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> je časovou prodlevu, po jejímž uplynutí zpráva bude přesunuta z fronty opakování zpět do hlavní fronty. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Nastaven na hodnotu 0. Zpráva se pokusilo znovu. V případě, všechny pokusy o čtení zprávy, zprávu je označen jako poškozen.

 Jakmile zprávu je označen jako poškozen, zprávu je řešeno podle nastavení v <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> výčtu. Zdůrazňujeme možné hodnoty:

-   Odolnost (výchozí): pro selhání naslouchací proces a také hostitele služby.

-   Přetažení: Vyřadit zprávu.

-   Přesunout: Přesunout zprávu do dílčí fronty nezpracovatelných zpráv. Tato hodnota je dostupná jenom na [!INCLUDE[wv](../../../../includes/wv-md.md)].

-   Odmítnout: Pokud chcete odmítnout zprávu, odesílání zprávy odesílatel je onta nedoručených zpráv fronty. Tato hodnota je dostupná jenom na [!INCLUDE[wv](../../../../includes/wv-md.md)].

 Vzorek ukazuje použití `Move` dispozice pro nezpracovatelných zpráv. `Move` způsobí, že zpráva, kterou chcete přesunout do dílčí fronty poškozené.

 Kontrakt služby je `IOrderProcessor`, která definuje jednosměrné, který je vhodný pro použití s frontami služby.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Operace služby zobrazí zprávu s oznámením, že zpracování pořadí. Abychom si předvedli funkci nezpracovatelná zpráva byla `SubmitPurchaseOrder` operace služby dojde k výjimce při vracení transakce na náhodných vyvolání služby. To způsobí, že zpráva, kterou chcete vrátit zpět k frontě. Nakonec zprávy je označena jako poison. Nezpracovatelná zpráva přesunete nezpracovatelných dílčí fronta je nastavení konfigurace.

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

 Konfigurace služby obsahuje následující vlastnosti nezpracovatelných zpráv: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, a `receiveErrorHandling` jak je znázorněno v následující konfigurační soubor.

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

## <a name="processing-messages-from-the-poison-message-queue"></a>Zpracování zpráv z fronty nezpracovatelných zpráv
 Nezpracovatelná zpráva byla Služba čte zprávy z fronty konečné nezpracovatelných zpráv a zpracovává je.

 Zprávy ve frontě nezpracovatelných zpráv jsou zprávy, které se tak vyřeší, službě, která zpracovává zprávu, která může být odlišné od koncového bodu služby nezpracovatelných zpráv. Proto když nezpracovatelná zpráva byla služba načte zprávy z fronty, vrstvy kanálu WCF vyhledá Neshoda v koncových bodů a není odeslání zprávy. V tomto případě zprávy je určeno služba zpracování objednávky, ale je přijímáno službou nezpracovatelná zpráva byla. Chcete-li pokračovat i v případě, že zprávy je určena k jinému koncovému bodu, zobrazí se zpráva, musí přidáme `ServiceBehavior` na filtr adresy, kde kritérium přiřazování je tak, aby odpovídaly libovolný koncový bod služby je určeno zprávy. To se vyžaduje úspěšně zpracovávat zprávy, které načítají z fronty nezpracovatelných zpráv.

 Implementace služby nezpracovatelných zpráv, samotného je velmi podobný implementaci služby. Implementuje tento kontrakt a zpracovávat objednávky. Příklad kódu vypadá takto.

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

 Na rozdíl od služby, která čte zprávy z fronty pořadí zpracování objednávek služba nezpracovatelných zpráv čte zprávy typu z nezpracovatelných dílčí fronty. Počet poškozených fronty je dílčí fronta hlavní fronty, má název "poison" a je automaticky generovaný službou MSMQ. Chcete-li získat přístup, zadejte název hlavní frontou, za nímž následuje ";" a dílčí název fronty, v tomto případě – "nezpracovatelných", jak je znázorněno v následující ukázková konfigurace.

> [!NOTE]
>  V ukázce pro službu MSMQ verze 3.0 název fronty nezpracovatelných není dílčí fronty, místo toho fronty, který jsme přesunuli zpráva, kterou chcete.

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

 Při spuštění ukázky klienta, služby a činnosti nezpracovatelná zpráva se zobrazí v oknech konzoly. Můžete zobrazit přijetí zprávy služby z klienta. Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí služby.

 Spuštění spuštěný, zpracování objednávky a spustí náhodně k ukončení zpracování služby. Pokud zpráva označuje, že nezpracuje pořadí, můžete spustit klienta znovu odeslat další zprávu, dokud neuvidíte, že služba byl ukončen ve skutečnosti zprávu. Podle nakonfigurovaného nastavení nezpracovatelná zpráva zkusí se jednou pro zpracování před přesunutím do konečné nezpracovatelných fronty.

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

 Spusťte službu nezpracovatelná zpráva byla poškozená po zprávu z fronty nezpracovatelných číst. V tomto příkladu služba nezpracovatelných zpráv přečte zprávu a zpracovává je. Je možné, že uvidíte, že služba nezpracovatelných zpráv přečte nákupní objednávka, který byl ukončen a poškozen.

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

#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku

1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Pokud je služba spuštěna první, zkontroluje se tak, aby byl do fronty k dispozici. Pokud fronta neexistuje, služba ho vytvoří. Můžete spustit služba nejdřív vytvořte frontu nebo můžete vytvořit prostřednictvím Správce fronty MSMQ. Postupujte podle těchto kroků můžete vytvořit frontu Windows 2008.

    1.  Otevřete správce serveru v sadě Visual Studio 2012.

    2.  Rozbalte **funkce** kartu.

    3.  Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **nový**, **soukromou frontu**.

    4.  Zkontrolujte, **transakční** pole.

    5.  Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.

3.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4.  Spusťte ukázku v konfiguraci s jedním nebo více počítač, změňte názvy front, aby odrážel skutečný název hostitele, místo localhost a postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

 Ve výchozím nastavení se `netMsmqBinding` vazby přenosu, zabezpečení je povolená. Dvě vlastnosti `MsmqAuthenticationMode` a `MsmqProtectionLevel`, společně určují typ zabezpečení přenosu. Ve výchozím nastavení, režim ověřování nastaven na `Windows` a aby úroveň ochrany je nastavená na `Sign`. Pro službu MSMQ. k ověřování a podepisování funkce musí být součástí domény. Pokud tuto ukázku spustit na počítači, který není součástí domény, se zobrazí následující chybová zpráva: "Uživatele interní zprávy služby Řízení front certifikát neexistuje".

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Ke spuštění ukázky na počítač připojen k pracovní skupině

1.  Pokud počítač není součástí domény, vypněte zabezpečení přenosu nastavením úroveň ověření režimu a ochrany na `None` jak je znázorněno v následující ukázková konfigurace:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Zkontrolujte, že koncový bod je přidružen vazbu tak, že nastavíte atribut bindingConfiguration koncového bodu.

2.  Ujistěte se, že změníte konfiguraci PoisonMessageServer, server a klienta, před spuštěním ukázky.

    > [!NOTE]
    >  Nastavení `security mode` k `None` je ekvivalentní nastavení `MsmqAuthenticationMode`, `MsmqProtectionLevel`, a `Message` zabezpečení `None`.  
  
3.  Aby Meta výměna dat pro práci můžeme zaregistrovat adresu URL s vazbou http. To vyžaduje, že služba běžet v okně se zvýšenými oprávněními příkaz. Jinak dojde k výjimce, jako: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`