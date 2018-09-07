---
title: Zpracované vazby služby MSMQ
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: 381304bcef40245bac882a4fe4ae18a6998665cf
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085089"
---
# <a name="transacted-msmq-binding"></a>Zpracované vazby služby MSMQ
Tento příklad znázorňuje způsob provedení transakčního komunikaci ve frontě pomocí služby Řízení front zpráv (MSMQ).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 V komunikaci ve frontě klient komunikuje se služby pomocí fronty. Přesněji řečeno klient odešle zprávy do fronty. Služba přijímá zprávy z fronty. Služby a klienta, proto není potřeba běžet současně na komunikaci pomocí fronty.  
  
 Když transakce se používají k odesílání a příjem zpráv, se ve skutečnosti dvě samostatné transakce. Když klient odešle zprávy v rámci oboru transakce, transakce je místní pro klienta a klient správce fronty. Když služba přijímá zprávy v rámci oboru transakce, transakce je místní pro službu a využívá správce fronty. Je velmi dobré si uvědomit, že klient a služba nenachází v rámci jedné transakce; Místo toho které využívají jiné transakce při provádění operací (například odesílání a příjem) s frontou.  
  
 V této ukázce klient odešle dávku zpráv ke službě z v rámci oboru transakce. Služby v rámci oboru transakce definovány službou pak přijme zprávy odeslané do fronty.  
  
 Kontrakt služby je `IOrderProcessor`, jak je znázorněno v následujícím ukázkovém kódu. Rozhraní definuje jednosměrné, který je vhodný pro použití s frontami služby.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 Definuje chování služby na chování operace s `TransactionScopeRequired` nastavena na `true`. Tím se zajistí, že všechny správce prostředků přistupovat pomocí metody používají stejný obor transakcí, která se používá k načtení zprávy z fronty. Také zaručuje, že pokud metoda vyvolá výjimku, se vrátí zprávu do fronty. Bez nastavení tohoto chování operace kanálu ve frontě vytvoří transakce čtení zprávy z fronty a potvrdí ji automaticky před odesláním tak, že pokud se operace nezdaří, dojde ke ztrátě zprávy. Nejběžnější scénář je pro operace služby k zařazení v transakci, která slouží k načtení zprávy z fronty, jak je ukázáno v následujícím kódu.  

```csharp
 // This service class that implements the service contract.  
 // This added code writes output to the console window.  
 public class OrderProcessorService : IOrderProcessor  
 {  
     [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
     public void SubmitPurchaseOrder(PurchaseOrder po)  
     {  
         Orders.Add(po);  
         Console.WriteLine("Processing {0} ", po);  
     }  
  …  
}  
```

 Tato služba je vlastní hostované. Při použití přenosu služby MSMQ, fronty, používá se musí vytvořit předem. To můžete udělat ručně nebo prostřednictvím kódu. V této ukázce služby obsahuje kód pro provedení kontroly existence fronty a vytvořit frontu, pokud neexistuje. Název fronty načítají z konfiguračního souboru. Základní adresa je používána [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generovat proxy ke službě.  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get the MSMQ queue name from appSettings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderProcessorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shut down the service.  
        serviceHost.Close();  
    }  
}  
```

 Název fronty MSMQ je zadat v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázková konfigurace.  
  
```xml  
<appSettings>  
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />  
</appSettings>  
```  
  
> [!NOTE]
>  Název fronty používá tečku (.) pro místní počítače a zpětné lomítko oddělovače v cestě při vytvoření fronty pomocí <xref:System.Messaging>. Koncový bod služby Windows Communication Foundation (WCF) používá adresa fronty s schéma net.msmq, používá "localhost" k označení místním počítači a používá lomítek v cestě.  
  
 Klient vytvoří obor transakce. Komunikace s frontou probíhá v rámci oboru transakcí, vyvolá zacházet jako atomickou jednotku, kde jsou všechny zprávy odeslané do fronty nebo jsou žádné zprávy odeslané do fronty. Transakce se potvrdí při volání <xref:System.Transactions.TransactionScope.Complete%2A> v oboru transakce.  

```csharp
// Create a client.  
OrderProcessorClient client = new OrderProcessorClient();  
  
// Create the purchase order.  
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
  
// Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Make a queued call to submit the purchase order.  
    client.SubmitPurchaseOrder(po);  
    // Complete the transaction.  
    scope.Complete();  
}  
  
// Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```

 Pokud chcete ověřit, že transakce fungují, upravte klienta tak, že komentování obor transakcí, jak je znázorněno v následujícím ukázkovém kódu, znovu sestavte řešení a spusťte klienta.  

```csharp
//scope.Complete();  
```

 Protože transakce není dokončena, nejsou odesílány zprávy do fronty.  
  
 Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly služby a klienta. Můžete zobrazit přijetí zprávy služby z klienta. Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby. Mějte na paměti, protože služba Řízení front se používá, klient a služba nemusí být zprovoznit ve stejnou dobu. Můžete spustit klienta, vypněte ho a spusťte službu a stále přijímá zprávy.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 7b31ce51-ae7c-4def-9b8b-617e4288eafd  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
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
  
 Ve výchozím nastavení se <xref:System.ServiceModel.NetMsmqBinding>, je povoleno zabezpečení přenosu. Existují dvě vlastnosti důležité pro zabezpečení přenosu služby MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>. Ve výchozím nastavení, režim ověřování nastaven na `Windows` a aby úroveň ochrany je nastavená na `Sign`. Pro službu MSMQ. k ověřování a podepisování funkce musí být součástí domény a možnost integrace služby Active Directory pro službu MSMQ musí být nainstalována. Pokud tuto ukázku spustit na počítači, který tato kritéria nesplňuje, zobrazí se chybová zpráva.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Ke spuštění ukázky na počítač připojen k pracovní skupině nebo bez integrace služby Active Directory  
  
1.  Pokud počítač není součástí domény nebo nemá nainstalované integrace služby Active Directory, vypněte zabezpečení přenosu nastavením úroveň ověření režimu a ochrany na `None` jak je znázorněno v následujícím ukázkovém kódu konfigurace.  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderProcessorService"  
                 behaviorConfiguration="OrderProcessorServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint. -->  
          <endpoint  
              address="net.msmq://localhost/private/ServiceModelSamplesTransacted"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <!-- The mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex. -->  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="OrderProcessorServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  Ujistěte se, že změníte konfiguraci na serveru a klienta, před spuštěním ukázky.  
  
    > [!NOTE]
    >  Nastavení `security``mode` k `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, a `Message` zabezpečení `None`.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`  
  
## <a name="see-also"></a>Viz také
