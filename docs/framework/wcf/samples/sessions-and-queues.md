---
title: Relace a fronty
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 623077450157b0bf87b85a85309adc10511b32b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007874"
---
# <a name="sessions-and-queues"></a>Relace a fronty
Tento příklad ukazuje, jak odesílat a přijímat sadu související zprávy ve frontě komunikace prostřednictvím přenosu služby Řízení front zpráv (MSMQ). Tento příklad používá `netMsmqBinding` vazby. Služba je v místním prostředí konzolovou aplikaci pro vám umožní sledovat službu přijímání zpráv zařazených do fronty.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 V komunikaci ve frontě klient komunikuje se služby pomocí fronty. Přesněji řečeno klient odešle zprávy do fronty. Služba přijímá zprávy z fronty. Klienta a služby, proto není potřeba běžet současně na komunikaci pomocí fronty.  
  
 V některých případech klient odešle sadu zpráv, které se vztahují k sobě navzájem ve skupině. Pokud zprávy musí být zpracovány současně nebo v určeném pořadí, fronty je možné seskupit dohromady, pro účely zpracování jedné přijímající aplikace. To je zvlášť důležité, když jsou k dispozici několik přijímající aplikace pro skupinu serverů a je potřeba zajistit, že skupinu zpráv je zpracována stejným přijímající aplikace. Relace ve frontě jsou mechanismus používaný k odesílání a příjem související sadu zpráv, které musí zpracovat všechny najednou. Relace ve frontě vyžadují transakci vykazovat tohoto modelu.  
  
 Ve vzorku klient odešle počet zpráv ve službě jako součást relaci v rámci jedné transakce.  
  
 Kontrakt služby je `IOrderTaker`, která definuje jednosměrné, který je vhodný pro použití s frontami služby. <xref:System.ServiceModel.SessionMode> Používaných pro smlouvy uvedené v následující vzorový kód označuje, že zprávy jsou součástí relace.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface IOrderTaker  
{  
    [OperationContract(IsOneWay = true)]  
    void OpenPurchaseOrder(string customerId);  
  
    [OperationContract(IsOneWay = true)]  
    void AddProductLineItem(string productId, int quantity);  
  
    [OperationContract(IsOneWay = true)]  
    void EndPurchaseOrder();  
}  
```

 Služba definuje operace služby tak, že první operace využívá v rámci transakce, ale nebude automaticky dokončen transakce. Následné operace také zařadit do jedné transakce, ale nedokončí automaticky. Poslední operaci v relaci se automaticky dokončí transakce. Díky tomu se stejnou transakci se používá pro několik vyvolání operace v kontraktu služby. Pokud všechny operace, vyvolá výjimku, transakce se vrátí zpět a relace se znovu zařadí do fronty. Po úspěšném dokončení poslední operace transakce se potvrzeny. Služba používá `PerSession` jako <xref:System.ServiceModel.InstanceContextMode> přijímat všechny zprávy v relaci ve stejné instanci služby.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class OrderTakerService : IOrderTaker  
{  
    PurchaseOrder po;  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                 TransactionAutoComplete = false)]  
    public void OpenPurchaseOrder(string customerId)  
    {  
        Console.WriteLine("Creating purchase order");  
        po = new PurchaseOrder(customerId);  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                  TransactionAutoComplete = false)]  
    public void AddProductLineItem(string productId, int quantity)  
    {  
        po.AddProductLineItem(productId, quantity);  
        Console.WriteLine("Product " + productId + " quantity " +   
                            quantity + " added to purchase order");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                  TransactionAutoComplete = true)]  
    public void EndPurchaseOrder()  
    {  
       Console.WriteLine("Purchase Order Completed");  
       Console.WriteLine();  
       Console.WriteLine(po.ToString());  
    }  
}  
```

 Tato služba je vlastní hostované. Při použití přenosu služby MSMQ, fronty, používá se musí vytvořit předem. To můžete udělat ručně nebo prostřednictvím kódu. V této ukázce obsahuje službu <xref:System.Messaging> kódu k provedení kontroly existence fronty a vytvoří, pokud je to nutné. Název fronty je pro čtení v konfiguračním souboru pomocí <xref:System.Configuration.ConfigurationManager.AppSettings%2A> třídy.  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderTakerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderTakerService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();   
    }  
}  
```

 Název fronty MSMQ je zadán v oddílu appSettings konfiguračním souboru. Koncový bod služby je definován v oddíle system.serviceModel konfiguračního souboru a určuje, `netMsmqBinding` vazby.  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesSession" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesSession"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
      ...  
    </service>  
  </services>  
  ...  
<system.serviceModel>  
```  
  
 Klient vytvoří obor transakce. Všechny zprávy v relaci se odesílají do fronty v rámci oboru transakcí, vyvolá zacházet jako atomickou jednotku, kde všechny zprávy úspěch nebo neúspěch. Transakce se potvrdí při volání <xref:System.Transactions.TransactionScope.Complete%2A>.  

```csharp
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Create a client with given client endpoint configuration.  
    OrderTakerClient client = new OrderTakerClient("OrderTakerEndpoint");  
    // Open a purchase order.  
    client.OpenPurchaseOrder("somecustomer.com");  
    Console.WriteLine("Purchase Order created");  
  
    // Add product line items.  
    Console.WriteLine("Adding 10 quantities of blue widget");  
    client.AddProductLineItem("Blue Widget", 10);  
  
    Console.WriteLine("Adding 23 quantities of red widget");  
    client.AddProductLineItem("Red Widget", 23);  
  
    // Close the purchase order.  
    Console.WriteLine("Closing the purchase order");  
    client.EndPurchaseOrder();  
  
    //Closing the client gracefully closes the connection and cleans up resources.  
    client.Close();                  
  
    // Complete the transaction.  
    scope.Complete();  
}  
```

> [!NOTE]
>  Pouze jedné transakce můžete použít pro všechny zprávy v relaci a všechny zprávy v relaci musí být odeslán před potvrzením transakce. Zavírá klienta ukončí relace. Klient proto musí být uzavřen předtím, než je transakce dokončena všechny zprávy v relaci odeslány do fronty.  
  
 Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly služby a klienta. Můžete zobrazit přijetí zprávy služby z klienta. Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby. Mějte na paměti, protože služba Řízení front se používá, klient a služba nemusí být zprovoznit ve stejnou dobu. Můžete spustit klienta, vypněte ho a spusťte službu a stále přijímá zprávy.  
  
 Na straně klienta.  
  
```  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 Ve službě.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Creating purchase order  
Product Blue Widget quantity 10 added to purchase order  
Product Red Widget quantity 23 added to purchase order  
Purchase Order Completed  
  
Purchase Order: 7c86fef0-2306-4c51-80e6-bcabcc1a6e5e  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 10 of Blue Widget @unit price: $2985  
                Order LineItem: 23 of Red Widget @unit price: $156  
        Total cost of this order: $33438  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C#, C++ nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Ve výchozím nastavení se <xref:System.ServiceModel.NetMsmqBinding>, je povoleno zabezpečení přenosu. Existují dvě vlastnosti důležité pro zabezpečení přenosu služby MSMQ konkrétně <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` výchozí režim ověřování nastaven na `Windows` a aby úroveň ochrany je nastavená na `Sign`. Pro službu MSMQ. k ověřování a podepisování funkce musí být součástí domény a možnost integrace služby active directory pro službu MSMQ musí být nainstalována. Pokud tuto ukázku spustit na počítači, který nevyhovuje těmto kritériím zobrazí chybová zpráva.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Ke spuštění ukázky na počítač připojen k pracovní skupině nebo bez integrace služby active directory  
  
1. Pokud počítač není součástí domény nebo nemá nainstalované integrace služby active directory, vypněte zabezpečení přenosu nastavením úroveň ověření režimu a ochrany na `None` jak je znázorněno v následující ukázková konfigurace.  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
                 behaviorConfiguration="OrderTakerServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress=  
             "http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint  
              address=  
            "net.msmq://localhost/private/ServiceModelSamplesSession"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
          <!-- The mex endpoint is exposed at-->      
          <!--http://localhost:8000/ServiceModelSamples/service/mex. -->  
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
            <behavior name="OrderTakerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2. Ujistěte se, že změníte konfiguraci na serveru a klienta, před spuštěním ukázky.  
  
    > [!NOTE]
    >  Nastavení režimu zabezpečení `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, a `Message` zabezpečení `None`.  
