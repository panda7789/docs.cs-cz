---
title: Aktivace MSMQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b4112be5980bee171d0b6b79f0126919f1d0865d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="msmq-activation"></a>Aktivace MSMQ
Tento příklad ukazuje, jak pro hostování aplikací v procesu aktivace služby WAS (Windows), které se načítají z fronty zpráv. Této ukázce se používá `netMsmqBinding` a je založena na [obousměrné komunikace](../../../../docs/framework/wcf/samples/two-way-communication.md) ukázka. Služba je v tomto případě hostované webové aplikace a klient se hostuje sama a výstupy ke konzole sledovat stav nákupních objednávek odeslána.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
> [!NOTE]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  \<InstallDrive >: \WF_WCF_Samples  
>   
>  Pokud tento adresář neexistuje, přejděte na [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] HYPERLINK "http://go.microsoft.com/fwlink/?LinkId=150780" \t "_blank" a [!INCLUDE[wf](../../../../includes/wf-md.md)] ukázky pro [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] ke stažení všechny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  \<InstallDrive >: \Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.  
  
 Proces aktivace služby WAS (Windows), nový mechanismus aktivace procesů pro [!INCLUDE[lserver](../../../../includes/lserver-md.md)], poskytuje službě IIS jako funkce, které byly dřív dostupné jenom pro aplikace založené na protokolu HTTP pro aplikace, které pomocí jiných protokolů než HTTP. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]používá ke komunikaci žádosti o aktivaci, které jsou přijaty prostřednictvím protokolů než HTTP nepodporuje rozhraní adaptér naslouchání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], jako jsou například TCP, pojmenované kanály a služby MSMQ. Funkce pro přijímání požadavků pomocí jiných protokolů než HTTP je hostován spravované služby systému Windows, které jsou spuštěny v SMSvcHost.exe.  
  
 Adaptér naslouchání Net.Msmq služby (NetMsmqActivator) aktivuje zařazených do fronty aplikací založených na zprávy ve frontě.  
  
 Klient odešle nákupních objednávek ke službě z v rámci oboru transakce. Služba přijímá objednávky v transakci a zpracovává je. Služba zpět pak zavolá klienta se stav pořadí. Pro usnadnění obousměrné komunikace klienta a služby používat fronty zařazování nákupních objednávek a stav pořadí.  
  
 Kontrakt služby `IOrderProcessor` definuje operace jednosměrné služby, které pracují s služby Řízení front. Operace služby používá k odesílání pořadí stavy klientovi odpovědi koncového bodu. Adresa koncového bodu odpovědi je identifikátor URI fronty používají k odesílání pořadí stavu zpět do klienta. Pořadí zpracování aplikace implementuje tuto smlouvu.  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 Kontrakt odpověď k odeslání pořadí stav je zadat klientem. Klient implementuje stav kontrakt pořadí. Služba používá k odeslání pořadí stavu zpět do klienta generovaného klienta této smlouvy.  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 Operace služby zpracovává odeslaná nákupní objednávka. <xref:System.ServiceModel.OperationBehaviorAttribute> Se použije pro operaci služby k určení automatických zařazení v transakci, která se používá k přijetí zprávy z fronty a automatického dokončování transakce na dokončení operace služby. `Orders` Třída zapouzdří funkce pořadí zpracování. V takovém případě přidá nákupní objednávka do slovníku. Je k dispozici pro operace v transakci, která v uvedené operaci služby `Orders` třídy.  
  
 Operace služby, kromě zpracování odeslaného nákupní objednávka, odpověď zpět do klienta o stavu pořadí.  
  
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
```  
  
 Klient pro vytvoření vazby na použití je zadán pomocí konfiguračního souboru.  
  
 Název fronty služby MSMQ je zadán v oddílu appSettings konfiguračního souboru. Koncový bod pro službu je definovaný v oddílu System.serviceModel konfiguračního souboru.  
  
> [!NOTE]
>  Adresu název a koncový bod služby MSMQ fronty pomocí mírně odlišné adresování konvence. Název fronty služby MSMQ používá tečku (.) pro místní počítač a oddělovače zpětné lomítko, v jeho cesty. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Adresa koncového bodu určuje net.msmq: schéma, používá "localhost" pro místní počítač a v jeho cesty používá lomítka. Čtení z fronty, která je hostována na vzdáleném počítači, nahraďte "." a "localhost" pro název vzdáleného počítače.  
  
 .Svc soubor s názvem třídy se používá k hostování kódu služby ve WAS.  
  
 Samotný soubor Service.svc obsahuje direktivu vytvořit `OrderProcessorService`.  
  
```xml  
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 Soubor Service.svc také obsahuje direktivu sestavení zajistit, že je načteno System.Transactions.dll.  
  
```xml  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 Klient vytvoří oboru transakce. Komunikace se službou probíhá v rámci oboru transakce, příčinou je považován za atomické jednotky, kde všechny zprávy úspěch nebo neúspěch. Transakce se potvrdí voláním `Complete` v oboru transakce.  
  
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
  
 Implementuje kód klienta `IOrderStatus` smlouvy přijímat pořadí stav ze služby. V takovém případě vytiskne na stav pořadí.  
  
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
  
 Je vytvářena fronta stavu pořadí v `Main` metoda. Konfigurace klienta zahrnuje konfiguraci služby stavu pořadí k hostování služby stavu pořadí, jak je znázorněno v následující ukázka konfigurace.  
  
```csharp  
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
  
 Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly klienta i serveru. Můžete zobrazit server přijímat zprávy z klienta. Stisknutím klávesy ENTER v každé okno konzoly a ukončí se serverem a klientem.  
  
 Klient se zobrazí informace o stavu pořadí odeslaných serverem:  
  
```Output  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že [!INCLUDE[iisver](../../../../includes/iisver-md.md)] je nainstalovaná, jako je povinný aktivace WAS.  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md). Kromě toho je nutné nainstalovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Aktivace jiným protokolem než HTTP součásti:  
  
    1.  Z **spustit** nabídce zvolte **ovládací panely**.  
  
    2.  Vyberte **programy a funkce**.  
  
    3.  Klikněte na tlačítko **zapnout nebo vypnout funkce systému Windows**.  
  
    4.  V části **Souhrn funkcí**, klikněte na tlačítko **přidat funkce**.  
  
    5.  Rozbalte **rozhraní Microsoft .NET Framework 3.0** uzlu a kontroly **Aktivace jiným protokolem než HTTP Windows Communication Foundation** funkce.  
  
3.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spusťte klienta spuštěním client.exe z příkazového okna. Tím se vytvoří frontu a odešle zprávu do ní. Nechte klienty v provozu zobrazíte výsledek službu čtení zprávy  
  
5.  Aktivace služby MSMQ spouští jako síťová služba ve výchozím nastavení. Proto musí mít fronty, který se používá k aktivaci aplikace přijímat a prohlížet oprávnění pro síťovou službu. To lze přidat pomocí konzoly MMC služby Řízení front zpráv:  
  
    1.  Z **spustit** nabídky, klikněte na tlačítko **spustit**, pak zadejte `Compmgmt.msc` a stiskněte klávesu ENTER.  
  
    2.  V části **služeb a aplikací**, rozbalte položku **služby Řízení front zpráv**.  
  
    3.  Klikněte na tlačítko **soukromé fronty**.  
  
    4.  Klikněte pravým tlačítkem na fronty (servicemodelsamples/Service.svc) a zvolte **vlastnosti**.  
  
    5.  Na **zabezpečení** , klikněte na **přidat** a poskytují funkce Náhled a obdrží oprávnění k síťové službě.  
  
6.  Konfigurace proces aktivace služby WAS (Windows) pro podporu aktivace MSMQ.  
  
     Pro potřeby následující kroky jsou implementované v dávkovém souboru názvem AddMsmqSiteBinding.cmd umístěný v adresáři ukázka.  
  
    1.  Kvůli podpoře aktivace net.msmq, musí být nejprve vázána výchozí web na protokol net.msmq. To lze provést pomocí appcmd.exe, která se instaluje s [!INCLUDE[iisver](../../../../includes/iisver-md.md)] sada nástrojů pro správu. Z příkazového řádku s oprávněními zvýšenými na úroveň (správce) spusťte následující příkaz.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je na jednom řádku textu.  
  
         Tento příkaz přidá net.msmq vazba webu default Web site.  
  
    2.  Přestože všechny aplikace v rámci lokality sdílejí společné net.msmq vazbu, každá aplikace můžete povolit podporu net.msmq jednotlivě. Pokud chcete povolit net.msmq /servicemodelsamples aplikace, spusťte následující příkaz z příkazového řádku se zvýšenými oprávněními.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je na jednom řádku textu.  
  
         Tento příkaz umožňuje získat přístup pomocí http://localhost/servicemodelsamples a net.msmq://localhost/servicemodelsamples /servicemodelsamples aplikaci.  
  
7.  Pokud jste tak dosud neučinili dříve, ujistěte se, že je povolena služba Aktivace služby MSMQ. Z **spustit** nabídky, klikněte na tlačítko **spustit**a typ `Services.msc`. V seznamu služeb pro Hledat **adaptér naslouchání Net.Msmq**. Klikněte pravým tlačítkem a vyberte **vlastnosti**. Nastavte **typ spuštění** k **automatické**, klikněte na tlačítko **použít** a klikněte na tlačítko **spustit** tlačítko. Tento krok je třeba provést pouze jednou před první využití služby Net.Msmq adaptér naslouchání.  
  
8.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Kromě toho změňte kód v klientovi, který odešle nákupní objednávka podle názvu počítače v identifikátoru URI fronty při odesílání nákupní objednávka. Použijte následující kód:  
  
    ```  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. Odeberte net.msmq vazby webu, který jste přidali Tato ukázka.  
  
     Pro potřeby následující kroky jsou implementované v dávkovém souboru názvem RemoveMsmqSiteBinding.cmd umístěný v adresáři ukázka:  
  
    1.  Odeberte net.msmq ze seznamu povolených protokolů spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je na jednom řádku textu.  
  
    2.  Odeberte vazbu webu net.msmq spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je na jednom řádku textu.  
  
    > [!WARNING]
    >  Spuštění dávkového souboru obnoví DefaultAppPool běžely pomocí rozhraní .NET Framework verze 2.0.  
  
 Ve výchozím nastavení se `netMsmqBinding` vazby přenos, zabezpečení je povoleno. Dvě vlastnosti `MsmqAuthenticationMode` a `MsmqProtectionLevel`, společně určují typ zabezpečení přenosu. Ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`. Pro MSMQ k ověřování a podepisování funkce musí být součástí domény. Pokud tuto ukázku spustit na počítači, který není součástí domény, je přijatých k následující chybě: "Uživatele interní zpráv služby Řízení front certifikát neexistuje".  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Ke spuštění ukázky na počítače připojeného k pracovní skupině  
  
1.  Pokud počítač není součástí domény, vypněte podle nastavení úrovně ověřování režimu a ochrany na hodnotu none, jak je znázorněno v následující ukázka konfigurace zabezpečení přenosu.  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2.  Změňte konfiguraci na serveru a klienta, před spuštěním ukázky.  
  
    > [!NOTE]
    >  Nastavení `security mode` k `None` je ekvivalentní nastavení `MsmqAuthenticationMode`, `MsmqProtectionLevel` a `Message` zabezpečení `None`.  
  
3.  Povolit aktivace v počítače připojeného k pracovní skupině, je potřeba spustit službu Aktivace a pracovní proces s konkrétní uživatelský účet (musí být stejné pro obě) a fronty musí mít seznamy řízení přístupu pro konkrétní uživatelský účet.  
  
     Změna identity kompatibilní se pracovní proces:  
  
    1.  Spusťte Inetmgr.exe.  
  
    2.  V části **fondy aplikací**, klikněte pravým tlačítkem myši **AppPool** (obvykle **DefaultAppPool**) a zvolte **nastavit výchozí nastavení fondu aplikací...** .  
  
    3.  Změňte vlastnosti Identity pro použití účtu pro konkrétního uživatele.  
  
     Změna identity kompatibilní se službu Aktivace:  
  
    1.  Spusťte modul Services.msc.  
  
    2.  Klikněte pravým tlačítkem myši **Net.MsmqListener adaptér**a zvolte **vlastnosti**.  
  
4.  Změňte účet v **přihlášení** kartě.  
  
5.  V pracovní skupině se musí taky spustit služba pomocí neomezený tokenu. K tomu, spusťte následující příkazy v příkazovém okně:  
  
    ```  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
