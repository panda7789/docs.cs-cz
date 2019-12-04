---
title: Obousměrná komunikace
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 9cf8d3746cea5746bee186a8a68a515c8503cb85
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715903"
---
# <a name="two-way-communication"></a>Obousměrná komunikace
Tato ukázka předvádí, jak provést transakční obousměrnou komunikaci přes službu MSMQ ve frontě. V této ukázce se používá vazba `netMsmqBinding`. V tomto případě je tato služba samoobslužná Konzolová aplikace, která umožňuje sledovat službu přijímající zprávy ve frontě.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Tato ukázka je založená na [transakční vazbě služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
 V komunikaci ve frontě klient komunikuje se službou pomocí fronty. Klient odesílá zprávy do fronty a služba přijímá zprávy z fronty. Službu a klient proto nemusí běžet současně, aby bylo možné komunikovat pomocí fronty.  
  
 Tato ukázka předvádí obousměrnou komunikaci pomocí front. Klient odesílá nákupní objednávky do fronty z rozsahu transakce. Služba obdrží objednávky, zpracuje objednávku a pak zavolá zpět klienta se stavem pořadí z fronty v rámci rozsahu transakce. Aby se usnadnila obousměrná komunikace klienta a služby, používají fronty k zařazování nákupních objednávek a stavu objednávek.  
  
 Kontrakt služby `IOrderProcessor` definuje jednosměrné operace služby, které vyhovují používání služby Řízení front zpráv. Operace služby zahrnuje koncový bod odpovědi, který se použije k odeslání stavu objednávky na. Koncový bod odpovědi je identifikátor URI fronty, který odesílá stav objednávky zpátky klientovi. Aplikace pro zpracování objednávek tuto smlouvu implementuje.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}
```
  
 Klient zadá odpověď na odeslání stavu objednávky. Klient implementuje kontrakt stavu objednávky. Služba používá vygenerovaný proxy server této smlouvy k odeslání stavu objednávky zpět klientovi.  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 Operace služby zpracuje odeslanou nákupní objednávku. <xref:System.ServiceModel.OperationBehaviorAttribute> se použije na operaci služby a určí se automatické zařazení v transakci, která se používá k přijetí zprávy z fronty a automatickému dokončení transakcí při dokončení operace služby. Třída `Orders` zapouzdřuje funkce zpracování objednávek. V tomto případě přidá nákupní objednávku do slovníku. Transakce, ve které je zapsána operace služby v nástroji, je k dispozici pro operace ve třídě `Orders`.  
  
 Operace služby kromě zpracování odeslané nákupní objednávky odpoví zpátky na klienta ve stavu objednávky.  

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

 Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru. Koncový bod služby je definován v oddílu System. ServiceModel konfiguračního souboru.  
  
> [!NOTE]
> Název fronty MSMQ a adresa koncového bodu používají mírně odlišnou konvenci adres. Název fronty MSMQ používá tečku (.) pro místní počítač a oddělovače zpětného lomítka v cestě. Adresa koncového bodu služby Windows Communication Foundation (WCF) určuje položku NET. MSMQ: schéma, používá pro místní počítač localhost a v cestě používá lomítka. Chcete-li číst z fronty hostované na vzdáleném počítači, nahraďte název vzdáleného počítače "." a "localhost".  
  
 Služba je hostována svým hostitelem. Při použití přenosu služby MSMQ musí být použitá fronta předem vytvořená. To lze provést ručně nebo prostřednictvím kódu. V této ukázce služba kontroluje existenci fronty a v případě potřeby ji vytvoří. Název fronty se načte z konfiguračního souboru. Základní adresa je používána [nástrojem Svcutil. exe](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pro vygenerování proxy serveru ke službě.  

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

 Klient vytvoří transakci. Komunikace s frontou probíhá v rámci rozsahu transakce, což způsobuje, že se bude považovat za atomickou jednotku, ve které všechny zprávy budou úspěšné nebo neúspěšné.  

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

 Klientský kód implementuje kontrakt `IOrderStatus` pro příjem stavu objednávky ze služby. V tomto případě vytiskne stav objednávky.  

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

 Fronta stavů pořadí je vytvořena v metodě `Main`. Konfigurace klienta zahrnuje pořadí konfigurace stavové služby pro hostování služby stavu objednávky, jak je znázorněno v následující ukázkové konfiguraci.  
  
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
  
 Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta. Můžete vidět, že služba přijímá zprávy z klienta. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.  
  
 Služba zobrazí informace o objednávce nákupu a indikuje, že posílá zpět stav objednávky do fronty stavu objednávky.  
  
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
  
 Klient zobrazí informace o stavu objednávky odesílané službou.  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit názvy koncových bodů v konfiguraci klienta tak, aby odpovídaly kódu klienta.  
  
 Ve výchozím nastavení je u <xref:System.ServiceModel.NetMsmqBinding>povolena možnost zabezpečení přenosu. Existují dvě důležité vlastnosti zabezpečení přenosu ve službě MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`. Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény a musí být nainstalovaná možnost integrace služby Active Directory pro službu MSMQ. Pokud tuto ukázku spustíte na počítači, který nesplňuje tato kritéria, zobrazí se chyba.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Spuštění ukázky na počítači připojeném k pracovní skupině nebo bez integrace služby Active Directory  
  
1. Pokud počítač není součástí domény nebo nemáte nainstalovanou integraci služby Active Directory, vypněte zabezpečení přenosu nastavením režimu ověřování a úrovně ochrany na `None`, jak je znázorněno v následující ukázkové konfiguraci:  
  
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
  
2. Vypnutí zabezpečení pro konfiguraci klienta generuje následující:  
  
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
  
3. Služba pro tuto ukázku vytvoří vazbu v `OrderProcessorService`. Po vytvoření instance vazby přidejte řádek kódu, který nastaví režim zabezpečení na `None`.  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. Před spuštěním ukázky se ujistěte, že jste změnili konfiguraci na serveru i v klientovi.  
  
    > [!NOTE]
    > Nastavení `security mode` na `None` je ekvivalentem nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> nebo `Message` zabezpečení na `None`.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
