---
title: Aktivace MSMQ
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 805ab78908b4d1146cce94cac5357bafbb35c832
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744786"
---
# <a name="msmq-activation"></a>Aktivace MSMQ

Tato ukázka předvádí, jak hostovat aplikace v aktivační službě procesů systému Windows (WAS), které se čtou z fronty zpráv. Tato ukázka používá `netMsmqBinding` a je založena na ukázce [obousměrné komunikace](../../../../docs/framework/wcf/samples/two-way-communication.md) . V tomto případě se jedná o aplikaci hostovanou v rámci webu a klient je v místním prostředí a výstupem do konzoly, aby bylo možné sledovat stav odeslaných nákupních objednávek.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

> [!NOTE]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> \<InstallDrive >: \ WF_WCF_Samples
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech ukázek WCF a [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Tato ukázka se nachází v následujícím adresáři.
>
> \<InstallDrive >: \Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.

Aktivační služba procesů systému Windows (WAS) nový mechanismus aktivace procesu pro Windows Server 2008 poskytuje funkce, které byly dříve dostupné jenom pro aplikace založené na protokolu HTTP, do aplikací, které používají protokoly jiného typu než HTTP. Windows Communication Foundation (WCF) používá rozhraní naslouchacího adaptéru k sdělování požadavků na aktivaci přijatých přes protokoly jiného typu než HTTP podporované službou WCF, jako je například TCP, pojmenované kanály a služba MSMQ. Funkce pro příjem požadavků přes protokoly jiné než HTTP je hostována spravovanými službami systému Windows, které jsou spuštěny v SMSvcHost. exe.

Služba NET. MSMQ Listener Adapter (NetMsmqActivator) aktivuje aplikace zařazené do fronty na základě zpráv ve frontě.

Klient odešle službě nákupní objednávky v rámci rozsahu transakce. Služba obdrží objednávky v transakci a zpracuje je. Služba pak zavolá zpět klienta se stavem pořadí. Aby se usnadnila obousměrná komunikace klienta a služby, používají fronty k zařazování nákupních objednávek a stavu objednávek.

`IOrderProcessor` kontraktu služby definuje jednosměrné operace služby, které fungují s řazením do fronty. Operace služby používá koncový bod odpovědi k odeslání stavů objednávky klientovi. Adresa koncového bodu odpovědi je identifikátor URI fronty, která byla použita k odeslání stavu objednávky zpět klientovi. Aplikace pro zpracování objednávek tuto smlouvu implementuje.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po,
                                           string reportOrderStatusTo);
}
```

Kontrakt odpovědi na odeslání stavu objednávky je určen klientem. Klient implementuje kontrakt stavu objednávky. Služba používá vygenerovaný klient této smlouvy k odeslání stavu objednávky zpět do klienta.

```csharp
[ServiceContract]
public interface IOrderStatus
{
    [OperationContract(IsOneWay = true)]
    void OrderStatus(string poNumber, string status);
}
```

Operace služby zpracuje odeslanou nákupní objednávku. <xref:System.ServiceModel.OperationBehaviorAttribute> se použije na operaci služby a určí se automatické zařazení v transakci, která se používá k přijetí zprávy z fronty, a automatickému dokončení transakce při dokončení operace služby. Třída `Orders` zapouzdřuje funkce zpracování objednávek. V tomto případě přidá nákupní objednávku do slovníku. Transakce, ve které je zapsána operace služby v nástroji, je k dispozici pro operace ve třídě `Orders`.

Operace služby kromě zpracování odeslané nákupní objednávky odpoví zpátky na klienta o stavu objednávky.

```csharp
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
        Console.WriteLine("Sending back order status information");
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));
        // please note that the same transaction that is used to dequeue purchase order is used
        // to send back order status
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.OrderStatus(po.PONumber, po.Status);
            scope.Complete();
        }
    }
}
```

Vazba klienta k použití je určena pomocí konfiguračního souboru.

Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru. Koncový bod služby je definován v oddílu System. serviceModel konfiguračního souboru.

> [!NOTE]
> Název fronty MSMQ a adresa koncového bodu používají mírně odlišnou konvenci adres. Název fronty MSMQ používá tečku (.) pro místní počítač a oddělovače zpětného lomítka v cestě. Adresa koncového bodu WCF Určuje možnost NET. MSMQ:, používá pro místní počítač "localhost" a v cestě používá lomítka. Chcete-li číst z fronty hostované na vzdáleném počítači, nahraďte "." a "localhost" názvem vzdáleného počítače.

Soubor. svc s názvem třídy slouží k hostování kódu služby v nástroji.

Samotný soubor Service. svc obsahuje direktivu pro vytvoření `OrderProcessorService`.

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>`

Soubor Service. svc obsahuje také direktivu sestavení, aby bylo zajištěno, že je načten System. Transactions. dll.

`<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>`

Klient vytvoří obor transakce. Komunikace se službou probíhá v rámci rozsahu transakce, což způsobuje, že by byla považována za atomickou jednotku, ve které všechny zprávy jsou úspěšné nebo neúspěšné. Transakce je potvrzena voláním `Complete` v oboru transakce.

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))
{
    // Open the ServiceHostBase to create listeners and start listening
    // for order status messages.
    serviceHost.Open();

    // Create a proxy with given client endpoint configuration
    OrderProcessorClient client = new OrderProcessorClient();

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
    using (TransactionScope scope = new
        TransactionScope(TransactionScopeOption.Required))
    {
        // Make a queued call to submit the purchase order
        client.SubmitPurchaseOrder(po,
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");
        // Complete the transaction.
        scope.Complete();
    }

    //Closing the client gracefully closes the connection and cleans up
    //resources
    client.Close();

    Console.WriteLine();
    Console.WriteLine("Press <ENTER> to terminate client.");
    Console.ReadLine();

    // Close the ServiceHostBase to shutdown the service.
    serviceHost.Close();
    }
```

Klientský kód implementuje kontrakt `IOrderStatus` pro příjem stavu objednávky ze služby. V tomto případě vytiskne stav objednávky.

```csharp
[ServiceBehavior]
public class OrderStatusService : IOrderStatus
{
    [OperationBehavior(TransactionAutoComplete = true,
                        TransactionScopeRequired = true)]
    public void OrderStatus(string poNumber, string status)
    {
        Console.WriteLine("Status of order {0}:{1} ",
                                         poNumber , status);
    }
}
```

Fronta stavů pořadí je vytvořena v metodě `Main`. Konfigurace klienta zahrnuje pořadí konfigurace stavové služby pro hostování služby stavu objednávky, jak je znázorněno v následující ukázkové konfiguraci.

```xml
<appSettings>
    <!-- use appSetting to configure MSMQ queue name -->
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />
  </appSettings>

<system.serviceModel>

    <services>
      <service
         name="Microsoft.ServiceModel.Samples.OrderStatusService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
    </client>

  </system.serviceModel>
```

Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzole serveru i klienta. Můžete vidět, že server obdrží zprávy od klienta. Pro vypnutí serveru a klienta stiskněte klávesu ENTER v každém okně konzoly.

Klient zobrazí informace o stavu objednávky odeslané serverem:

```console
Press <ENTER> to terminate client.
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že je nainstalovaná služba IIS 7,0, jak je potřeba pro aktivaci.

2. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md). Kromě toho musíte nainstalovat komponenty WCF, které nejsou součástí aktivace přes protokol HTTP:

    1. V nabídce **Start** klikněte na položku **Ovládací panely**.

    2. Vyberte **programy a funkce**.

    3. Klikněte na **zapnout nebo vypnout funkce systému Windows**.

    4. V části **Souhrn funkcí**klikněte na **Přidat funkce**.

    5. Rozbalte uzel **Microsoft .NET Framework 3,0** a podívejte se na funkci **Windows Communication Foundation aktivace jiným protokolem než http** .

3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Spusťte klienta spuštěním příkazu Client. exe z příkazového okna. Tím se vytvoří fronta a pošle se do ní zpráva. Ponechte spuštěného klienta, aby se zobrazil výsledek služby, která čte zprávu.

5. Aktivační služba MSMQ je ve výchozím nastavení spuštěna jako síťová služba. Proto fronta, která se používá k aktivaci aplikace, musí mít oprávnění Receive a prohlížet pro síťovou službu. Dá se přidat pomocí konzoly MMC služby Řízení front zpráv:

    1. V nabídce **Start** klikněte na tlačítko **Spustit**a zadejte příkaz `Compmgmt.msc` a stiskněte klávesu ENTER.

    2. V části **služby a aplikace**rozbalte položku **Řízení front zpráv**.

    3. Klikněte na **soukromé fronty**.

    4. Klikněte pravým tlačítkem na frontu (ServiceModelSamples/service. svc) a vyberte **vlastnosti**.

    5. Na kartě **zabezpečení** klikněte na **Přidat** a poskytněte síťové službě oprávnění k prohlížení a příjmu.

6. Nakonfigurujte aktivační službu procesů systému Windows (WAS), aby podporovala aktivaci služby MSMQ.

    V rámci pohodlí jsou v dávkovém souboru s názvem AddMsmqSiteBinding. cmd, který je umístěn v ukázkovém adresáři, implementovány následující kroky.

    1. Aby bylo možné podporovat aktivaci NET. MSMQ, výchozí web musí být nejprve svázán s protokolem NET. MSMQ. To lze provést pomocí nástroje Appcmd. exe, který je nainstalován se sadou nástrojů pro správu služby IIS 7,0. Na příkazovém řádku se zvýšenými oprávněními (správce) spusťte následující příkaz.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > Tento příkaz je jedním řádkem textu.

        Tento příkaz přidá na výchozí web vazbu lokality NET. MSMQ.

    2. I když všechny aplikace v rámci lokality sdílejí společnou vazbu NET. MSMQ, každá aplikace může povolit podporu NET. msmq samostatně. Pokud chcete pro aplikaci/ServiceModelSamples povolit NET. MSMQ, spusťte z příkazového řádku se zvýšenými oprávněními následující příkaz.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq
        ```

        > [!NOTE]
        > Tento příkaz je jedním řádkem textu.

        Tento příkaz umožňuje, aby aplikace/ServiceModelSamples byla dostupná pomocí `http://localhost/servicemodelsamples` a `net.msmq://localhost/servicemodelsamples`.

7. Pokud jste tak dosud neučinili, ujistěte se, že je povolená aktivační služba MSMQ. V nabídce **Start** klikněte na **spustit**a zadejte `Services.msc`. Vyhledejte v seznamu služeb **adaptér naslouchání NET. MSMQ**. Klikněte pravým tlačítkem a vyberte **Vlastnosti**. Nastavte **Typ spouštění** na **automaticky**, klikněte na **použít** a klikněte na tlačítko **Spustit** . Tento krok je potřeba provést jenom jednou před prvním použitím služby NET. MSMQ Listener Adapter.

8. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Navíc můžete změnit kód v klientovi, který odešle nákupní objednávku tak, aby odrážel název počítače v identifikátoru URI fronty při odeslání nákupní objednávky. Použijte následující kód:

    ```csharp
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");
    ```

9. Odeberte vazbu na lokalitu NET. MSMQ, kterou jste přidali pro tuto ukázku.

    Pro usnadnění jsou v dávkovém souboru s názvem RemoveMsmqSiteBinding. cmd, který se nachází v ukázkovém adresáři, implementované následující kroky:

    1. Ze seznamu povolených protokolů odeberte NET. MSMQ spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > Tento příkaz je jedním řádkem textu.

    2. Odeberte vazbu lokality NET. MSMQ spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > Tento příkaz je jedním řádkem textu.

    > [!WARNING]
    > Spuštěním dávkového souboru resetujete službu DefaultAppPool tak, aby běžela pomocí .NET Framework verze 2,0.

Ve výchozím nastavení se u `netMsmqBinding` vazby vazeb povoluje zabezpečení. Dvě vlastnosti, `MsmqAuthenticationMode` a `MsmqProtectionLevel`, společně určují typ zabezpečení přenosu. Ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`. Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény. Pokud tuto ukázku spustíte na počítači, který není součástí domény, obdrží se následující chyba: "vnitřní certifikát služby Řízení front zpráv" neexistuje.

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Spuštění ukázky na počítači připojeném k pracovní skupině

1. Pokud počítač není součástí domény, vypněte zabezpečení přenosu nastavením režimu ověřování a úrovně ochrany na žádné, jak je znázorněno v následující ukázkové konfiguraci.

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding configurationName="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

2. Před spuštěním ukázky změňte konfiguraci na serveru i v klientovi.

    > [!NOTE]
    > Nastavení `security mode` na `None` je ekvivalentem nastavení `MsmqAuthenticationMode`, `MsmqProtectionLevel` a `Message` zabezpečení na `None`.

3. Chcete-li povolit aktivaci na počítači připojeném k pracovní skupině, musí být aktivační služba i pracovní proces spuštěny s konkrétním uživatelským účtem (musí být u obou) spuštěné a fronta musí mít pro konkrétní uživatelský účet seznamy ACL.

     Chcete-li změnit identitu, pod kterou běží pracovní proces:

    1. Spusťte příkaz inetmgr. exe.

    2. V části **fondy aplikací**klikněte pravým tlačítkem na **AppPool** (obvykle **DefaultAppPool**) a vyberte **nastavit výchozí nastavení fondu aplikací..** .

    3. Změňte vlastnosti identity tak, aby používaly konkrétní uživatelský účet.

     Chcete-li změnit identitu, pod kterou se aktivační služba spouští:

    1. Run Services.msc.

    2. Klikněte pravým tlačítkem na **adaptér NET. MsmqListener**a vyberte **vlastnosti**.

4. Změňte účet na kartě **přihlášení** .

5. V pracovní skupině musí služba také běžet pomocí neomezeného tokenu. Uděláte to tak, že v příkazovém okně spustíte následující příkaz:

    ```console
    sc sidtype netmsmqactivator unrestricted
    ```

## <a name="see-also"></a>Viz také

- [Hostování technologie AppFabric a ukázky trvalosti](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
