---
title: Aktivace MSMQ
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: d83759f321abe7fa7e39202daadd4ceda82d8f23
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295676"
---
# <a name="msmq-activation"></a>Aktivace MSMQ
Tento příklad ukazuje, jak hostovat aplikace ve Windows WAS Process Activation Service (), které se načítají z fronty zpráv. Tento příklad používá `netMsmqBinding` a je založena na [obousměrné komunikace](../../../../docs/framework/wcf/samples/two-way-communication.md) vzorku. Služby v tomto případě je hostované webové aplikace a klient je v místním prostředí a vypíše do konzoly sledovat stav nákupní objednávky odeslané.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
> [!NOTE]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  \<InstallDrive>:\WF_WCF_Samples  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny WCF a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  \<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.  
  
 Windows WAS Process Activation Service (), nový mechanismus procesu aktivace pro [!INCLUDE[lserver](../../../../includes/lserver-md.md)], poskytuje služby IIS jako funkce, které byly dřív dostupné jenom pro aplikace založené na protokolu HTTP pro aplikace, které používají protokoly jiným protokolem než HTTP. Windows Communication Foundation (WCF) používá ke komunikaci žádosti o aktivaci, které jsou přijímány prostřednictvím protokolů jiným protokolem než HTTP nepodporuje WCF, jako je například TCP, pojmenované kanály a MSMQ rozhraní adaptér naslouchací proces. Funkce pro příjem požadavků prostřednictvím protokolů jiným protokolem než HTTP je hostitelem spravovaných služeb Windows používané SMSvcHost.exe.  
  
 Adaptér naslouchání Net.Msmq service (NetMsmqActivator) aktivuje ve frontě aplikací založených na zprávy ve frontě.  
  
 Klient odešle nákupních objednávek ke službě z v rámci oboru transakce. Služba přijímá objednávky v transakci a zpracovává je. Služba potom zavolá zpět klienta se stavem pořadí. Pro usnadnění obousměrná komunikace klienta a služby pomocí fronty zařadit nákupních objednávek a stav objednávky.  
  
 Kontrakt služby `IOrderProcessor` definuje operace jednosměrné služby, které využívají službu Řízení front. Operace služby používá koncový bod odpovědi k odesílání pořadí stavy do klienta. Adresa koncového bodu odpověď je identifikátor URI fronty používají k odesílání stav objednávky zpět do klienta. Pořadí zpracování aplikace implementuje tento kontrakt.  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 Kontrakt odpověď k odeslání stavu objednávky je určená klientem. Klient implementuje tento kontrakt stavu objednávky. Služba používá generovaného klienta této smlouvy k odeslání objednávky stavu zpět do klienta.  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 Operace služby odeslané nákupní objednávku zpracovává. <xref:System.ServiceModel.OperationBehaviorAttribute> Se použije pro operace služby k určení automatické zařazení v transakci, která se používá k přijetí zprávy z fronty a automatické dokončení transakce na dokončení operace služby. `Orders` Třídy zapouzdřuje funkce zpracování objednávky. V takovém případě nákupní objednávku přidá do slovníku. Operace služby uveden v transakci je k dispozici s operacemi `Orders` třídy.  
  
 Operace služby, kromě odeslané nákupní objednávky, odešle odpověď zpět do klienta o stavu objednávky.  
  
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
  
 Vytvoření vazby na použití klienta je zadán pomocí konfiguračního souboru.  
  
 Název fronty MSMQ je zadán v oddílu appSettings konfiguračním souboru. Koncový bod služby je definován v oddíle System.serviceModel konfiguračního souboru.  
  
> [!NOTE]
>  Adresa název a koncový bod fronty MSMQ používají mírně odlišná adresování konvence. Název fronty MSMQ používá tečku (.) pro místní počítače a zpětné lomítko oddělovače v cestě. Určuje adresu koncového bodu WCF net.msmq: schéma, používá "localhost" pro místní počítač a v jeho cesty používá lomítka. Chcete-li načítají z fronty, která je hostována na vzdáleném počítači, nahraďte "." a "localhost" pro název vzdáleného počítače.  
  
 .Svc soubor s názvem třídy se používá k hostování kódu služby ve WAS.  
  
 Samotný soubor Service.svc obsahuje direktivu vytvořit `OrderProcessorService`.  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 Soubor Service.svc také obsahuje direktivu sestavení k zajištění, že je načten uživatelský System.Transactions.dll.  
  
```svc  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 Klient vytvoří obor transakce. Komunikace se službou se provádí v rámci oboru transakcí, vyvolá zacházet jako atomickou jednotku, kde všechny zprávy úspěch nebo neúspěch. Transakce se potvrdí při volání `Complete` v oboru transakce.  
  
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
  
 Klientský kód implementuje `IOrderStatus` smlouvy získat ze služby stavu objednávky. V takovém případě se vytiskne stavu objednávky.  
  
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
  
 Je vytvářena fronta stav objednávky v `Main` metody. Konfigurace klienta zahrnuje konfiguraci služby stavu objednávky pro hostování služby stavu objednávky, jak je znázorněno v následující ukázková konfigurace.  
  
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
  
 Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly klienta i serveru. Můžete vidět server pro příjem zpráv z klienta. Stisknutím klávesy ENTER v okně konzoly se každý vypnout server i klient.  
  
 Klient se zobrazí informace o stavu objednávky odeslané serverem:  
  
```console  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že [!INCLUDE[iisver](../../../../includes/iisver-md.md)] je nainstalovaná, jak je vyžadováno pro aktivaci WAS.  
  
2. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md). Kromě toho je třeba nainstalovat jiným protokolem než HTTP aktivačních komponent WCF:  
  
    1.  Z **Start** nabídce zvolte **ovládací panely**.  
  
    2.  Vyberte **programy a funkce**.  
  
    3.  Klikněte na tlačítko **zapnout nebo vypnout funkce Windows**.  
  
    4.  V části **Souhrn funkcí**, klikněte na tlačítko **přidat funkce**.  
  
    5.  Rozbalte **rozhraní Microsoft .NET Framework 3.0** uzlu a kontrolu **Aktivace jiným protokolem než HTTP Windows Communication Foundation** funkce.  
  
3. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Spustíte klienta spuštěním client.exe z příkazového okna. Tím se vytvoří frontu a odešle zprávu do něj. Nechte klienty k zobrazení výsledku čtení zprávy služby  
  
5. Aktivační služba MSMQ je ve výchozím nastavení spouští jako síťová služba. Proto musí mít fronty, který se používá k aktivaci aplikace přijímat a náhled oprávnění pro síťovou službu. Jde přidat pomocí konzoly MMC služby Řízení front zpráv:  
  
    1.  Z **Start** nabídky, klikněte na tlačítko **spustit**, zadejte `Compmgmt.msc` a stiskněte klávesu ENTER.  
  
    2.  V části **služeb a aplikací**, rozbalte **služby Řízení front zpráv**.  
  
    3.  Klikněte na tlačítko **soukromé fronty**.  
  
    4.  Klikněte pravým tlačítkem na fronty (servicemodelsamples/Service.svc) a zvolte **vlastnosti**.  
  
    5.  Na **zabezpečení** klikněte na tlačítko **přidat** a poskytnout náhled a přijímat oprávnění pro síťovou službu.  
  
6. Konfigurace Windows WAS Process Activation Service () pro podporu aktivace služby MSMQ.  
  
     Pro zjednodušení následující kroky jsou implementovány v dávkovém souboru volá AddMsmqSiteBinding.cmd nachází v adresáři ukázkové.  
  
    1.  Kvůli podpoře aktivace net.msmq, musíte ji nejdřív svázat výchozí webový server net.msmq protokolu. To lze provést pomocí appcmd.exe, která se instaluje s [!INCLUDE[iisver](../../../../includes/iisver-md.md)] sada nástrojů pro správu. Z příkazového řádku se zvýšenými oprávněními (správce) spusťte následující příkaz.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je jeden řádek textu.  
  
         Tento příkaz přidá vazbu webu net.msmq výchozí webový server.  
  
    2.  Přestože všechny aplikace v rámci lokality sdílejí společné net.msmq vazby, každá aplikace můžete povolit podporu net.msmq jednotlivě. Pokud chcete povolit net.msmq /servicemodelsamples aplikace, spusťte následující příkaz z příkazového řádku se zvýšenými oprávněními.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je jeden řádek textu.  
  
         Tento příkaz umožňuje aplikaci /servicemodelsamples přistupovat pomocí `http://localhost/servicemodelsamples` a `net.msmq://localhost/servicemodelsamples`.
  
7. Pokud jste neudělali dříve, ujistěte se, že je povolená aktivace služby MSMQ. Z **Start** nabídky, klikněte na tlačítko **spustit**a typ `Services.msc`. V seznamu služeb pro vyhledejte **adaptér naslouchání Net.Msmq**. Klikněte pravým tlačítkem a vyberte **vlastnosti**. Nastavte **typ spouštění** k **automatické**, klikněte na tlačítko **použít** a klikněte na tlačítko **Start** tlačítko. Tento krok je třeba provést pouze jednou před první využití služby adaptér naslouchání Net.Msmq.  
  
8. Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Kromě toho změňte kód na straně klienta, který odešle nákupní pořadí tak, aby odrážely název počítače v identifikátoru URI fronty, při odesílání nákupní objednávky. Pomocí následujícího kódu:  
  
    ```csharp  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. Odeberte net.msmq vazby webu, kterou jste přidali pro tuto ukázku.  
  
     Pro zjednodušení následující kroky jsou implementovány v dávkovém souboru volá RemoveMsmqSiteBinding.cmd nachází v adresáři ukázkové:  
  
    1.  Odeberte net.msmq ze seznamu povolených protokolů spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je jeden řádek textu.  
  
    2.  Odeberte vazbu webu net.msmq spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je jeden řádek textu.  
  
    > [!WARNING]
    >  Spuštění dávkový soubor se resetuje DefaultAppPool pro spuštění pomocí rozhraní .NET Framework verze 2.0.  
  
 Ve výchozím nastavení se `netMsmqBinding` vazby přenosu, zabezpečení je povolená. Dvě vlastnosti `MsmqAuthenticationMode` a `MsmqProtectionLevel`, společně určují typ zabezpečení přenosu. Ve výchozím nastavení je režim ověřování nastaven na `Windows` a aby úroveň ochrany je nastavená na `Sign`. Pro službu MSMQ. k ověřování a podepisování funkce musí být součástí domény. Pokud tuto ukázku spustit na počítači, který není součástí domény, je přijata následující chyba: "Certifikátu interní front uživatele neexistuje".  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Ke spuštění ukázky na počítač připojen k pracovní skupině  
  
1. Pokud počítač není součástí domény, vypněte tak, že nastavíte úroveň ověření režimu a ochrany na hodnotu none, jak je znázorněno v následující ukázkové konfiguraci zabezpečení přenosu.  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2. Před spuštěním ukázky, změňte konfiguraci na serveru a klienta.  
  
    > [!NOTE]
    >  Nastavení `security mode` k `None` je ekvivalentní nastavení `MsmqAuthenticationMode`, `MsmqProtectionLevel` a `Message` zabezpečení `None`.  
  
3. Chcete-li aktivovat počítač připojen k pracovní skupině, musí být spuštěna aktivace služby a pracovní proces s konkrétního uživatelského účtu (musí být stejná pro obě) a fronty musí mít seznamy ACL pro konkrétní uživatelský účet.  
  
     Chcete-li změnit identitu, která poběží pracovní proces v části:  
  
    1.  Run Inetmgr.exe.  
  
    2.  V části **fondy aplikací**, klikněte pravým tlačítkem myši **fondu aplikací** (obvykle **DefaultAppPool**) a zvolte **nastavit výchozí nastavení fondu aplikací...** .  
  
    3.  Změňte vlastnosti Identity pro použití konkrétního uživatelského účtu.  
  
     Chcete-li změnit identita, pod kterým běží služba Aktivace:  
  
    1.  Run Services.msc.  
  
    2.  Klikněte pravým tlačítkem myši **Net.MsmqListener adaptér**a zvolte **vlastnosti**.  
  
4. Změna účtu v **přihlášení** kartu.  
  
5. V pracovní skupině se musí taky spustit služba používá token pro neomezený. Chcete-li to provést, spusťte následující v příkazovém okně:  
  
    ```console  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
