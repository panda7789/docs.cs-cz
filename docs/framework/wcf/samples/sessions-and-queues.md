---
title: Relace a fronty
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 719212d908b9d5b5207dd5b4e7701ef903de31a0
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715070"
---
# <a name="sessions-and-queues"></a>Relace a fronty
Tato ukázka předvádí, jak odeslat a přijmout sadu souvisejících zpráv v komunikaci ve frontě prostřednictvím přenosu služby Řízení front zpráv (MSMQ). V této ukázce se používá vazba `netMsmqBinding`. Služba je samoobslužná Konzolová aplikace, která vám umožní sledovat službu přijímající zprávy zařazené do fronty.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 V komunikaci ve frontě klient komunikuje se službou pomocí fronty. Klient přesněji odesílá zprávy do fronty. Služba přijímá zprávy z fronty. Službu a klient proto nemusí běžet současně, aby bylo možné komunikovat pomocí fronty.  
  
 V některých případech klient odesílá sadu zpráv, které jsou vzájemně propojené ve skupině. Pokud se zprávy musí zpracovávat společně nebo v zadaném pořadí, můžete k jejich seskupení použít frontu pro zpracování v rámci jedné přijímající aplikace. To je důležité hlavně v případě, že je na skupině serverů několik přijímajících aplikací a je nutné zajistit, aby byla skupina zpráv zpracována stejnou přijímající aplikací. Relace ve frontě jsou mechanizmus, který slouží k posílání a přijímání souvisejících sad zpráv, které musí zpracovat všechny najednou. Relace ve frontě vyžadují transakci, která se projeví v tomto modelu.  
  
 V ukázce pošle klient několik zpráv do služby jako součást relace v rámci oboru jedné transakce.  
  
 Kontrakt služby je `IOrderTaker`, který definuje jednosměrnou službu, která je vhodná pro použití s frontami. <xref:System.ServiceModel.SessionMode> použitá v kontraktu uvedené v následujícím ukázkovém kódu označují, že zprávy jsou součástí relace.  

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

 Služba definuje operace služeb takovým způsobem, že první operace zařadí v transakci, ale neprovede automatické dokončení transakce. Následující operace také zařadí do stejné transakce, ale neprovádí se automaticky. Poslední operace v relaci automaticky dokončí transakci. Proto se stejná transakce používá pro několik vyvolání operací v kontraktu služby. Pokud některá z operací vyvolá výjimku, transakce se vrátí zpět a relace se vrátí zpět do fronty. Po úspěšném dokončení poslední operace se transakce potvrdí. Služba používá `PerSession` jako <xref:System.ServiceModel.InstanceContextMode> pro příjem všech zpráv v relaci ve stejné instanci služby.  

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

 Služba je hostována svým hostitelem. Při použití přenosu služby MSMQ musí být použitá fronta předem vytvořená. To lze provést ručně nebo prostřednictvím kódu. V této ukázce služba obsahuje kód <xref:System.Messaging> pro kontrolu existence fronty a v případě potřeby ji vytvoří. Název fronty se načte z konfiguračního souboru pomocí třídy <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.  

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

 Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru. Koncový bod pro službu je definován v oddílu System. serviceModel konfiguračního souboru a určuje `netMsmqBinding` vazby.  
  
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
  
 Klient vytvoří obor transakce. Všechny zprávy v relaci jsou odesílány do fronty v rámci oboru transakce, což způsobuje, že se bude považovat za atomickou jednotku, ve které všechny zprávy jsou úspěšné nebo neúspěšné. Transakce je potvrzena voláním <xref:System.Transactions.TransactionScope.Complete%2A>.  

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
> Pro všechny zprávy v relaci lze použít pouze jednu transakci a všechny zprávy v relaci je nutné před potvrzením transakce odeslat. Ukončení klienta ukončí relaci. Proto musí být klient před dokončením transakce uzavřen, aby odesílal všechny zprávy v relaci do fronty.  
  
 Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta. Můžete vidět, že služba přijímá zprávy z klienta. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta. Počítejte s tím, že protože se používá služba zařazování do fronty, klient a služba nemusí být spuštěny ve stejnou dobu. Můžete spustit klienta, vypnout ho a pak spustit službu a nadále přijímat zprávy.  
  
 Na straně klienta.  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 Ve službě.  
  
```console  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C#edici, C++nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Ve výchozím nastavení je u <xref:System.ServiceModel.NetMsmqBinding>povolena možnost zabezpečení přenosu. Existují dvě důležité vlastnosti zabezpečení přenosu ve službě MSMQ, konkrétně <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`. Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény a musí být nainstalovaná možnost integrace služby Active Directory pro službu MSMQ. Pokud tuto ukázku spustíte na počítači, který nesplňuje tato kritéria, zobrazí se chyba.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Spuštění ukázky na počítači připojeném k pracovní skupině nebo bez integrace služby Active Directory  
  
1. Pokud počítač není součástí domény nebo nemáte nainstalovanou integraci služby Active Directory, vypněte zabezpečení přenosu nastavením režimu ověřování a úrovně ochrany na `None`, jak je znázorněno v následující ukázkové konfiguraci.  
  
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
  
2. Před spuštěním ukázky se ujistěte, že jste změnili konfiguraci na serveru i v klientovi.  
  
    > [!NOTE]
    > Nastavení režimu zabezpečení na `None` je ekvivalentem nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>a `Message` zabezpečení na `None`.  
