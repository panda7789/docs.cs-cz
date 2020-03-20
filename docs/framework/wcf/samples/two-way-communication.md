---
title: Obousměrná komunikace
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 56f789fe185cb2885c215e9512e82ae2fbb64a36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143756"
---
# <a name="two-way-communication"></a>Obousměrná komunikace
Tato ukázka ukazuje, jak provádět transakční obousměrnou komunikaci ve frontě přes službu MSMQ. Tato ukázka `netMsmqBinding` používá vazbu. V tomto případě je služba aplikace konzoly s vlastním hostitelem, která umožňuje sledovat službu přijímající zprávy ve frontě.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Tato ukázka je založena na [transacted MSMQ vazby](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
 Ve frontové komunikaci klient komunikuje se službou pomocí fronty. Klient odesílá zprávy do fronty a služba přijímá zprávy z fronty. Služba a klient proto nemusí být spuštěny současně komunikovat pomocí fronty.  
  
 Tato ukázka ukazuje obousměrnou komunikaci pomocí front. Klient odešle nákupní objednávky do fronty z rozsahu transakce. Služba přijímá objednávky, zpracovává objednávku a pak zavolá zpět klientovi se stavem objednávky z fronty v rámci transakce. Pro usnadnění obousměrné komunikace klient i služba používají fronty k zařazení nákupních objednávek do fronty a stavu objednávky.  
  
 Servisní smlouva `IOrderProcessor` definuje jednosměrné operace služeb, které vyhovují použití fronty. Operace služby zahrnuje koncový bod odpovědi, který se má použít k odeslání stavů objednávek. Koncový bod odpovědi je identifikátor URI fronty pro odeslání stavu objednávky zpět klientovi. Aplikace zpracování objednávky implementuje tuto smlouvu.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string
                                  reportOrderStatusTo);  
}
```
  
 Kontrakt odpovědi na odeslání stavu objednávky je určen klientem. Klient implementuje kontrakt stavu objednávky. Služba používá generovaný proxy serveru této smlouvy k odeslání stavu objednávky zpět klientovi.  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 Operace služby zpracovává odeslanou nákupní objednávku. Použije <xref:System.ServiceModel.OperationBehaviorAttribute> se na operaci služby k určení automatického zařazení do transakce, která se používá k přijetí zprávy z fronty a automatického dokončení transakcí po dokončení operace služby. Třída `Orders` zapouzdřuje funkce zpracování objednávek. V tomto případě přidá nákupní objednávku do slovníku. Transakce, která operace služby zapsána v je `Orders` k dispozici operace ve třídě.  
  
 Operace servisu kromě zpracování odeslané nákupní objednávky odpovídá klientovi zpět na stav objednávky.  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
{  
    Orders.Add(po);  
    Console.WriteLine("Processing {0} ", po);  
    Console.WriteLine("Sending back order status information");  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding("ClientCallbackBinding");  
    OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
  
    // Please note that the same transaction that is used to dequeue the purchase order is used  
    // to send back order status.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        client.OrderStatus(po.PONumber, po.Status);  
        scope.Complete();  
    }  
    //Close the client.  
    client.Close();  
}  
```

 Název fronty služby MSMQ je určen v části appSettings konfiguračního souboru. Koncový bod služby je definován v části System.ServiceModel konfiguračního souboru.  
  
> [!NOTE]
> Název fronty a adresa koncového bodu msmq používají mírně odlišné konvence adresování. Název fronty msmq používá tečku (.) pro místní počítač a oddělovače zpětného lomítka v jeho cestě. Adresa koncového bodu WCF (Windows Communication Foundation) určuje schéma net.msmq:, používá "localhost" pro místní počítač a používá lomítka v cestě. Chcete-li číst z fronty, která je hostována ve vzdáleném počítači, nahraďte "." a "localhost" na název vzdáleného počítače.  
  
 Služba je hostována samostatně. Při použití přenosu služby MSMQ musí být použitá fronta vytvořena předem. To lze provést ručně nebo prostřednictvím kódu. V této ukázce služba zkontroluje existenci fronty a v případě potřeby ji vytvoří. Název fronty se čte z konfiguračního souboru. Základní adresa se používá [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generovat proxy služby.  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from appSettings in configuration.  
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
    }  
}  
```

 Klient vytvoří transakci. Komunikace s frontou probíhá v rámci transakce, což způsobuje, že je považována za atomovou jednotku, kde všechny zprávy úspěšné nebo neúspěšné.  

```csharp
// Create a ServiceHost for the OrderStatus service type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
  
    // Open the ServiceHostBase to create listeners and start listening for order status messages.  
    serviceHost.Open();  
  
    // Create the purchase order.  
    ...  
  
    // Create a client with given client endpoint configuration.  
    OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        string hostName = Dns.GetHostName();  
  
        // Make a queued call to submit the purchase order.  
        client.SubmitPurchaseOrder(po, "net.msmq://" + hostName + "/private/ServiceModelSamplesTwo-way/OrderStatus");  
  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Close down the client.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHost to shutdown the service.  
    serviceHost.Close();  
}  
```

 Kód klienta implementuje smlouvu `IOrderStatus` pro příjem stavu objednávky ze služby. V tomto případě vytiskne stav objednávky.  

```csharp
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ", poNumber ,
                                                           status);  
    }  
}  
```

 V metodě je vytvořena `Main` fronta stavu objednávky. Konfigurace klienta zahrnuje konfiguraci služby stavu objednávky pro hostování služby stavu objednávky, jak je znázorněno v následující vzorové konfiguraci.  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
</appSettings>  
  
<system.serviceModel>  
  
  <services>  
    <service
       name="Microsoft.ServiceModel.Samples.OrderStatusService">  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
    </service>  
  </services>  
  
  <client>  
    <!-- Define NetMsmqEndpoint -->  
    <endpoint name="OrderProcessorEndpoint"  
              address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
              binding="netMsmqBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
  </client>  
  
</system.serviceModel>  
```  
  
 Při spuštění ukázky jsou aktivity klienta a služby zobrazeny v systému Windows služby i klientské konzole. Můžete vidět službu přijímat zprávy od klienta. Stisknutím klávesy ENTER v každém okně konzoly vypněte službu a klienta.  
  
 Služba zobrazí informace o nákupní objednávce a označuje, že odesílá zpět stav objednávky do fronty stavu objednávky.  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 124a1f69-3699-4b16-9bcc-43147a8756fc  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Sending back order status information  
```  
  
 Klient zobrazí informace o stavu objednávky odeslané službou.  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Pokud používáte Svcutil.exe k obnovení konfigurace pro tuto ukázku, nezapomeňte upravit názvy koncových bodů v konfiguraci klienta tak, aby odpovídaly kódu klienta.  
  
 Ve výchozím <xref:System.ServiceModel.NetMsmqBinding>nastavení je povoleno zabezpečení přenosu. Existují dvě relevantní vlastnosti zabezpečení přenosu <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> služby MSMQ a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` `Windows` ve výchozím nastavení je `Sign`režim ověřování nastaven na a úroveň ochrany je nastavena na hodnotu . Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény a musí být nainstalována možnost integrace služby Active Directory pro službu MSMQ. Pokud spustíte tuto ukázku v počítači, který nesplňuje tato kritéria, zobrazí se chyba.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Spuštění ukázky v počítači připojovat se k pracovní skupině nebo bez integrace služby Active Directory  
  
1. Pokud počítač není součástí domény nebo není nainstalována integrace služby Active Directory, vypněte zabezpečení `None` přenosu nastavením režimu ověřování a úrovně ochrany na úroveň uvedenou v následující ukázkové konfiguraci:  
  
    ```xml  
    <configuration>  
  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderProcessor" />  
      </appSettings>  
  
      <system.serviceModel>  
        <services>  
          <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding"
                      contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
2. Vypnutí zabezpečení konfigurace klienta generuje následující:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
      </appSettings>  
  
      <system.serviceModel>  
  
        <services>  
          <service
             name="Microsoft.ServiceModel.Samples.OrderStatusService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding" contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
          </service>  
        </services>  
  
        <client>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint name="OrderProcessorEndpoint"  
                    address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
                    binding="netMsmqBinding"
                    bindingConfiguration="TransactedBinding"  
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        </client>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
3. Služba pro tuto ukázku vytvoří `OrderProcessorService`vazbu v . Přidejte řádek kódu po vytvoření instance vazby pro nastavení `None`režimu zabezpečení na .  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. Před spuštěním ukázky se ujistěte, že změníte konfiguraci na serveru i na klientovi.  
  
    > [!NOTE]
    > Nastavení `security mode` `None` na je <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>ekvivalentní <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `Message` nastavení `None`nebo zabezpečení .  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
