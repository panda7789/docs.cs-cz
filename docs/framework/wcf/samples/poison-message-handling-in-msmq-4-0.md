---
title: Zacházení s nezpracovatelnými zprávami v MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 0a9d4ec9657bacdbcb1273791dc7a593a9565c25
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094953"
---
# <a name="poison-message-handling-in-msmq-40"></a>Zacházení s nezpracovatelnými zprávami v MSMQ 4.0
Tato ukázka předvádí, jak ve službě provádět zpracování nezpracovatelných zpráv. Tato ukázka je založená na ukázce s [transakčními vazbami služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) . Tato ukázka používá `netMsmqBinding`. Služba je samoobslužná Konzolová aplikace, která vám umožní sledovat službu přijímající zprávy zařazené do fronty.

 V komunikaci ve frontě klient komunikuje se službou pomocí fronty. Klient přesněji odesílá zprávy do fronty. Služba přijímá zprávy z fronty. Službu a klient proto nemusí běžet současně, aby bylo možné komunikovat pomocí fronty.

 Nezpracovatelná zpráva je zpráva, která se opakovaně čte z fronty, když služba čte zprávu, nemůže zprávu zpracovat, a proto ukončí transakci, pod kterou je zpráva přečtena. V takových případech se zpráva znovu pokusí. To se může teoreticky opakovat, pokud dojde k potížím se zprávou. K tomu může dojít pouze v případě, že používáte transakce ke čtení z fronty a k vyvolání operace služby.

 V závislosti na verzi služby MSMQ podporuje NetMsmqBinding omezené zjišťování na úplnou detekci nezpracovatelných zpráv. Jakmile je zpráva zjištěna jako poškozená, může být zpracována několika způsoby. Na základě verze služby MSMQ podporuje NetMsmqBinding omezené zpracování na plné zpracování nezpracovatelných zpráv.

 Tato ukázka znázorňuje omezená poškození zařízení, která jsou k dispozici na platformě Windows Server 2003 a Windows XP a na zařízeních s úplnými poškozeními, které jsou k dispozici v systému V obou ukázkách je cílem přesunout nezpracovatelnou zprávu z fronty do jiné fronty. Tuto frontu pak může obsluhovat nezpracovatelná zpráva.

## <a name="msmq-v40-poison-handling-sample"></a>Ukázka zpracování poškození služby MSMQ v 4.0
 V systému Windows Vista nabízí služba MSMQ poškozené zařízení podfronty, které lze použít k ukládání nezpracovatelných zpráv. Tato ukázka předvádí osvědčené postupy při práci s nepoškozenými zprávami pomocí systému Windows Vista.

 Detekce nepoškozených zpráv v systému Windows Vista je sofistikovaná. Existují tři vlastnosti, které vám pomůžou s detekcí. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> je počet, kolikrát je daná zpráva znovu načtena z fronty a odeslána do aplikace ke zpracování. Zpráva je znovu načtena z fronty při návratu do fronty, protože zprávu nelze odeslat do aplikace nebo aplikace vrátí zpět transakci v rámci operace služby. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> je počet přesunutí zprávy do fronty opakovaných pokusů. Po dosažení <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> se zpráva přesune do fronty opakování. Vlastnost <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> je časová prodleva, po jejímž uplynutí je zpráva přesunuta z fronty opakování zpět do hlavní fronty. <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> se resetuje na 0. Zpráva se zopakuje. Pokud se všechny pokusy o čtení zprávy nezdařily, zpráva je označena jako poškozená.

 Jakmile je zpráva označena jako poškozená, zpráva se zabývá podle nastavení v <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> výčtu. Chcete-li znovu iterovat možné hodnoty:

- Chyba (výchozí): pro selhání naslouchacího procesu a také hostitele služby.

- Drop: k vyřazení zprávy.

- Move: pro přesunutí zprávy do podfronty nezpracovatelné zprávy. Tato hodnota je k dispozici pouze v systému Windows Vista.

- Odmítnout: Pokud chcete zprávu zamítnout, odešlete zprávu zpátky do fronty nedoručených zpráv odesilatele. Tato hodnota je k dispozici pouze v systému Windows Vista.

 Ukázka ukazuje použití dispoziční `Move` pro nezpracovatelnou zprávu. `Move` způsobí, že se zpráva přesune do podfronty nepoškozeného.

 Kontrakt služby je `IOrderProcessor`, který definuje jednosměrnou službu, která je vhodná pro použití s frontami.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Operace služby zobrazí zprávu informující o tom, že zpracovává objednávku. Aby bylo možné předvést funkci nezpracovatelné zprávy, vyvolá operace `SubmitPurchaseOrder` služby výjimku, která vrátí transakci při náhodném volání služby. Tím dojde k vrácení zprávy do fronty. Nakonec je zpráva označena jako nepoškozená. Konfigurace je nastavená tak, aby se nezpracovatelná zpráva přesunula do podfronty nepoškozeného.

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

 Konfigurace služby zahrnuje následující vlastnosti nezpracovatelné zprávy: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`a `receiveErrorHandling`, jak je znázorněno v následujícím konfiguračním souboru.

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
 Služba nepoškozených zpráv čte zprávy z konečné fronty zpráv o nepoškozených zprávách a zpracovává je.

 Zprávy ve frontě nepoškozených zpráv jsou zprávy, které jsou adresovány službě, která zpracovává zprávu, což se může lišit od koncového bodu služby zprávy o nepoškozeném provozu. Proto když služba nepoškozených zpráv přečte zprávy z fronty, vrstva kanálu WCF nalezne neshodu v koncových bodech a neodešle zprávu. V tomto případě je zpráva adresována službě zpracování objednávky, ale je přijímána službou nezpracovatelných zpráv. Chcete-li nadále přijímat zprávy i v případě, že je zpráva adresována jinému koncovému bodu, je nutné přidat `ServiceBehavior` pro filtrování adres, kde kritérium shody odpovídá jakémukoli koncovému bodu služby, na který je zpráva adresována. Tato operace je nutná k úspěšnému zpracování zpráv přečtených z fronty nezpracovatelných zpráv.

 Samotná implementace služby nepoškozených zpráv je velmi podobná implementaci služby. Implementuje kontrakt a zpracuje objednávky. Příklad kódu je následující.

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

 Na rozdíl od služby zpracování objednávek, která čte zprávy z fronty objednávek, služba nepoškozených zpráv přečte zprávy z podfronty pro poškození. Fronta poškození je podfrontou hlavní fronty, má název "jed" a generuje se automaticky pomocí služby MSMQ. Pokud k němu chcete získat přístup, zadejte název hlavní fronty následovaný znakem ";" a dílčí frontou, v tomto případě – "jed", jak je znázorněno v následující ukázkové konfiguraci.

> [!NOTE]
> V ukázce pro službu MSMQ v 3.0 není název fronty nefungují jako Podfronta, nikoli do fronty, do které jste zprávu přesunuli.

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

 Když spustíte ukázku, aktivity služby klienta, služby a nepoškozená zpráva se zobrazí v oknech konzoly. Můžete vidět, že služba přijímá zprávy z klienta. V každém okně konzoly stiskněte klávesu ENTER a ukončete služby.

 Služba se spustí, pořadí zpracování a náhodně se spustí pro ukončení zpracování. Pokud zpráva indikuje, že zpracovala objednávku, můžete spustit klienta znovu a odeslat další zprávu, dokud se nezobrazí zpráva, že služba skutečně ukončila zprávu. V závislosti na nakonfigurovaných nastaveních poškození se zpráva před přesunem do konečné fronty nezpracovatele vyzkouší pro zpracování.

```console
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

 Spusťte službu nezpracovatelných zpráv pro čtení poškozené zprávy z fronty poškození. V tomto příkladu služba nepoškozených zpráv přečte zprávu a zpracuje ji. Je možné, že se v případě nezpracovatele přečte objednávka, která byla ukončena a poškozená.

```console
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

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici. Pokud fronta není přítomna, služba ji vytvoří. Službu můžete nejdřív spustit, abyste mohli vytvořit frontu, nebo ji můžete vytvořit pomocí Správce fronty MSMQ. Pomocí těchto kroků vytvořte ve Windows 2008 frontu.

    1. Otevřete Správce serveru v aplikaci Visual Studio 2012.

    2. Rozbalte kartu **funkce** .

    3. Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **Nový**, **soukromá fronta**.

    4. Zaškrtněte políčko **transakční** .

    5. Jako název nové fronty zadejte `ServiceModelSamplesTransacted`.

3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, změňte názvy front tak, aby odrážely skutečný název hostitele namísto názvu localhost, a postupujte podle pokynů v [části spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

 Ve výchozím nastavení se u `netMsmqBinding` vazby vazeb povoluje zabezpečení. Dvě vlastnosti, `MsmqAuthenticationMode` a `MsmqProtectionLevel`, společně určují typ zabezpečení přenosu. Ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`. Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény. Pokud tuto ukázku spustíte na počítači, který není součástí domény, zobrazí se následující chyba: "vnitřní certifikát služby Řízení front zpráv" neexistuje.

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Spuštění ukázky na počítači připojeném k pracovní skupině

1. Pokud počítač není součástí domény, vypněte zabezpečení přenosu nastavením režimu ověřování a úrovně ochrany tak, aby `None`, jak je znázorněno v následující ukázkové konfiguraci:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Nastavením atributu bindingConfiguration koncového bodu zajistěte, aby byl koncový bod přidružen k vazbě.

2. Před spuštěním ukázky se ujistěte, že jste změnili konfiguraci na PoisonMessageServer, serveru a klientovi.

    > [!NOTE]
    > Nastavení `security mode` na `None` je ekvivalentem nastavení `MsmqAuthenticationMode`, `MsmqProtectionLevel`a `Message` zabezpečení na `None`.  
  
3. Aby výměna metadat mohla fungovat, zaregistrujeme adresu URL s vazbou http. To vyžaduje, aby se služba spouštěla v okně příkazového řádku se zvýšenými oprávněními. V opačném případě získáte výjimku, například: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
