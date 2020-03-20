---
title: Zacházení s nezpracovatelnými zprávami v MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 4b662094923c85e825edcc9025a73f1a1b42cb9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144237"
---
# <a name="poison-message-handling-in-msmq-40"></a>Zacházení s nezpracovatelnými zprávami v MSMQ 4.0
Tato ukázka ukazuje, jak provádět zpracování poškozená zpráva ve službě. Tato ukázka je založena na [transacted MSMQ binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) vzorku. Tato ukázka `netMsmqBinding`používá . Služba je aplikace konzoly s vlastním hostitelem, která umožňuje sledovat službu přijímající zprávy ve frontě.

 Ve frontové komunikaci klient komunikuje se službou pomocí fronty. Přesněji řečeno, klient odesílá zprávy do fronty. Služba přijímá zprávy z fronty. Služba a klient proto nemusí být spuštěny současně komunikovat pomocí fronty.

 Poškozená zpráva je zpráva, která je opakovaně číst z fronty, když služba čtení zprávy nemůže zpracovat zprávu a proto ukončí transakci, pod kterou je zpráva číst. V takových případech je zpráva zopakována znovu. To může teoreticky pokračovat navždy, pokud je problém se zprávou. K tomu může dojít pouze v případě, že pomocí transakcí číst z fronty a vyvolat operaci služby.

 Na základě verze služby MSMQ podporuje netmsmqbinding omezenou detekci na úplnou detekci poškozená zpráva. Poté, co byla zpráva zjištěna jako poškozená, může být zpracována několika způsoby. Opět na základě verze služby MSMQ netmsmqbinding podporuje omezené zpracování na úplné zpracování poškozená zprávy.

 Tato ukázka ilustruje omezené jedovaté zařízení poskytované na platformě Windows Server 2003 a Windows XP a zařízení s úplným jevem, která jsou k dispozici v systému Windows Vista. V obou ukázkách je cílem přesunout poškozenou zprávu z fronty do jiné fronty. Tato fronta pak může být obsluhována službou poškozená zpráva.

## <a name="msmq-v40-poison-handling-sample"></a>Ukázka zpracování jedů vSMQ v4.0
 V systému Windows Vista poskytuje služba MSMQ jedovaté podfronty, které lze použít k ukládání jedovacích zpráv. Tato ukázka ukazuje osvědčené postupy zpracování jedovaté zprávy pomocí systému Windows Vista.

 Detekce poškozená zpráva v systému Windows Vista je sofistikovaná. Existují 3 vlastnosti, které pomáhají s detekcí. Je <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> počet, kolikrát je daná zpráva znovu přečtena z fronty a odeslána do aplikace ke zpracování. Zpráva je znovu číst z fronty při jeho vrácení zpět do fronty, protože zpráva nemůže být odeslána do aplikace nebo aplikace vrátí transakci v operaci služby. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>je počet přesunů zprávy do fronty opakování. Po <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> dosažení je zpráva přesunuta do fronty opakování. Vlastnost <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> je časová prodleva, po jejímž uplynutí je zpráva přesunuta z fronty opakování zpět do hlavní fronty. Je <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> nastaven na 0. Zpráva je zopakována. Pokud všechny pokusy o čtení zprávy se nezdařily, je zpráva označena jako poškozená.

 Jakmile je zpráva označena jako poškozená, zpráva je zpracována podle nastavení ve výčtu. <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> Chcete-li zopakovat možné hodnoty:

- Chyba (výchozí): Chyba naslouchací proces a také hostitele služby.

- Přetažení: Chcete-li zprávu přetáhnout.

- Přesunout: Chcete-li přesunout zprávu do podfronty poškozená zpráva. Tato hodnota je k dispozici pouze v systému Windows Vista.

- Odmítnout: Chcete-li zprávu odmítnout, odešlete zprávu zpět do fronty nedoručených zpráv odesílatele. Tato hodnota je k dispozici pouze v systému Windows Vista.

 Ukázka ukazuje použití `Move` dispozice pro zprávu poison. `Move`způsobí, že zpráva přesunout do podfronty poison.

 Servisní smlouva `IOrderProcessor`je , která definuje jednosměrnou službu, která je vhodná pro použití s frontami.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Operace služby zobrazí zprávu oznamující, že zpracovává objednávku. Chcete-li demonstrovat funkce `SubmitPurchaseOrder` poškozená zpráva, operace služby vyvolá výjimku vrátit zpět transakce na náhodné vyvolání služby. To způsobí, že zpráva, která má být umístěna zpět do fronty. Nakonec je zpráva označena jako jed. Konfigurace je nastavena na přesunutí poškozená zpráva poison podfronty.

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

 Konfigurace služby obsahuje následující vlastnosti `retryCycleDelay`poškozená `receiveErrorHandling` zpráva: `receiveRetryCount`, `maxRetryCycles`, a jak je znázorněno v následujícím konfiguračním souboru.

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

## <a name="processing-messages-from-the-poison-message-queue"></a>Zpracování zpráv z fronty poškozená zpráva
 Služba poškozená zpráva čte zprávy z fronty konečných poškozená zpráva a zpracuje je.

 Zprávy ve frontě poškozená zpráva jsou zprávy, které jsou určeny pro službu, která zpracovává zprávu, které se mohou lišit od koncového bodu služby poškozená zpráva. Proto při službě poškozená zpráva čte zprávy z fronty, vrstva kanálu WCF najde neshodu v koncových bodech a neodešle zprávu. V takovém případě je zpráva určena službě zpracování objednávek, ale je přijímána službou poškozená zpráva. Chcete-li i nadále přijímat zprávy i v případě, že zpráva `ServiceBehavior` je určena k jinému koncovému bodu, musíme přidat do filtru adresy, kde je kritérium shody tak, aby odpovídaly všechny koncového bodu služby zpráva je určena. To je nutné úspěšně zpracovat zprávy, které čtete z fronty poškozená zpráva.

 Samotná implementace služby poškozená zpráva je velmi podobná implementaci služby. Implementuje smlouvu a zpracovává objednávky. Příklad kódu je následující.

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

 Na rozdíl od služby zpracování objednávek, která čte zprávy z fronty objednávek, služba poškozená zpráva čte zprávy z podfronty poison. Fronty je podfronty hlavní fronty, je s názvem "poison" a je automaticky generována služba MSMQ. Chcete-li k němu získat přístup, zadejte název hlavní fronty následovaný ";" a název podfronty, v tomto případě "poison", jak je znázorněno na následující ukázce konfigurace.

> [!NOTE]
> V ukázce pro službu MSMQ v3.0 není název fronty poison dílčí frontou, spíše frontou, do které jsme zprávu přesunuli.

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

 Při spuštění ukázky jsou v oknech konzoly zobrazeny aktivity služby klienta, služby a služby poškozená zpráva. Můžete vidět službu přijímat zprávy od klienta. Chcete-li služby vypnout stisknutím klávesy ENTER v každém okně konzoly.

 Služba se spustí, zpracování objednávek a náhodně začne ukončit zpracování. Pokud zpráva označuje, že objednávku zpracoval, můžete klienta znovu spustit a odeslat další zprávu, dokud se nezobrazí, že služba skutečně ukončila zprávu. Na základě nakonfigurované nastavení jepoškozen, zpráva se pokusí jednou pro zpracování před přesunutím do konečné fronty jed.

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

 Spusťte službu poškozená zpráva číst poškozenou zprávu z fronty poškozen. V tomto příkladu služba poškozená zpráva přečte zprávu a zpracuje ji. Můžete vidět, že nákupní objednávka, která byla ukončena a otrávena, je přečtena službou poškozená zpráva.

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

1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici. Pokud fronta není k dispozici, služba ji vytvoří. Nejprve můžete spustit službu a vytvořit frontu, nebo ji můžete vytvořit pomocí Správce front služby MSMQ. Vytvořenífronty v systému Windows 2008 postupujte takto.

    1. Otevřete Správce serveru v sadě Visual Studio 2012.

    2. Rozbalte kartu **Funkce.**

    3. Klepněte pravým tlačítkem myši na **položku Fronty soukromých zpráv**a vyberte příkaz **Nová**, **Soukromá fronta**.

    4. Zaškrtněte políčko **Transakční** transakce.

    5. Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.

3. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, změňte názvy front tak, aby odrážely skutečný název hostitele namísto localhost a postupujte podle pokynů v [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

 Ve výchozím `netMsmqBinding` nastavení s přenosem vazby je povoleno zabezpečení. Dvě `MsmqAuthenticationMode` vlastnosti `MsmqProtectionLevel`a společně určují typ zabezpečení přenosu. Ve výchozím nastavení je režim `Windows` ověřování nastaven na `Sign`hodnotu a úroveň ochrany je nastavena na hodnotu . Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény. Pokud spustíte tuto ukázku v počítači, který není součástí domény, zobrazí se následující chyba: "Interní certifikát fronty zpráv uživatele neexistuje".

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Spuštění ukázky v počítači připojovato k pracovní skupině

1. Pokud počítač není součástí domény, vypněte zabezpečení přenosu nastavením režimu `None` ověřování a úrovně ochrany na úroveň uvedenou v následující ukázkové konfiguraci:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Ujistěte se, že koncový bod je přidružen k vazbě nastavením atributu vazby koncového boduConfiguration.

2. Ujistěte se, že změníte konfiguraci na PoisonMessageServer, server a klient před spuštěním ukázky.

    > [!NOTE]
    > Nastavení `security mode` `None` na je `MsmqAuthenticationMode`ekvivalentní `MsmqProtectionLevel`nastavení `Message` a `None`zabezpečení .  
  
3. Aby Meta Data Exchange fungovala, zaregistrujeme adresu URL s vazbou http. To vyžaduje, aby služba spuštěna v okně příkazu se zvýšenými oprávněními. V opačném případě se dostanete `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`výjimku, například: .  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
