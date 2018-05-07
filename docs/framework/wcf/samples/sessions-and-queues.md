---
title: Relace a fronty
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: ee360f7a95529142437764a74c9f6261221af8b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="sessions-and-queues"></a>Relace a fronty
Tento příklad ukazuje, jak odesílat a přijímat sadu související zprávy ve frontě komunikace přes přenosu služby Řízení front zpráv (MSMQ). V tomto příkladu `netMsmqBinding` vazby. Služba je vlastním hostováním konzolové aplikace, které vám umožňují sledovat službu přijetí zprávy ve frontě.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 V komunikaci ve frontě klient komunikuje se služby pomocí fronty. Přesněji řečeno klient odešle zprávy do fronty. Služba přijímá zprávy z fronty. Služba a klient proto nemusíte používat současně na komunikaci pomocí fronty.  
  
 V některých případech klient odešle sadu zpráv, které se vztahují k sobě navzájem ve skupině. Když zprávy musí být zpracovány současně nebo v uvedeném pořadí, fronty lze seskupovat je společně pro zpracování v jednom přijímající aplikace. To je důležité zvláště tehdy, když existuje několik přijímající aplikací na skupinu serverů a je nutné zajistit, že má stejné přijímající aplikace zpracovává zprávy skupinu. Mechanismus používaný k odesílání a příjmu související sadu zpráv, které musí všechny najednou zpracovat jsou ve frontě relace. Ve frontě relací vyžadují transakci vykazovat tohoto vzoru.  
  
 V ukázce klient odešle počet zpráv ve službě v rámci relace v rámci oboru jedné transakci.  
  
 Kontrakt služby je `IOrderTaker`, která definuje jednosměrné služby, který je vhodný pro použití s front. <xref:System.ServiceModel.SessionMode> Použít v kontraktu vidět v následujícím ukázkovém kódu označuje, že zprávy jsou součástí relace.  

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

 Služba definuje operací služby tak, že první operace využívá v transakci, ale není automaticky dokončit transakce. Další operacích také zařazení ve stejné transakci ale neprovádějte automaticky. Poslední operaci v relaci automaticky dokončení transakce. Proto se používá stejné transakci pro několik volání operace v kontrakt služby. Pokud všechny operace, způsobí výjimku, transakce se vrátí zpět a relace je vrátit zpět do fronty. Po úspěšném poslední operace že je transakce potvrzena. Služba používá `PerSession` jako <xref:System.ServiceModel.InstanceContextMode> přijmout všechny zprávy v relaci ve stejné instanci služby.  

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

 Služba je sám sebou hostované. Pokud používáte přenos MSMQ, používá fronty musí být vytvořeny předem. Tento krok můžete provést ručně nebo prostřednictvím kódu. V této ukázce služba obsahuje <xref:System.Messaging> kód zkontrolujte existenci fronty a vytvoří, pokud je to nutné. Název fronty je pro čtení ze souboru konfigurace pomocí <xref:System.Configuration.ConfigurationManager.AppSettings%2A> třídy.  

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

 Název fronty služby MSMQ je zadán v oddílu appSettings konfiguračního souboru. Koncový bod pro službu je definováno v sekci system.serviceModel konfiguračního souboru a určuje `netMsmqBinding` vazby.  
  
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
  
 Klient vytvoří oboru transakce. Všechny zprávy v relaci jsou odesílány do fronty v oboru transakce, příčinou je považován za atomické jednotky, kde všechny zprávy úspěch nebo neúspěch. Transakce se potvrdí voláním <xref:System.Transactions.TransactionScope.Complete%2A>.  

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
>  Pouze jedné transakci můžete použít pro všechny zprávy v relaci a všechny zprávy v relaci musí být odeslány před potvrzením transakce. Zavření klienta ukončí relace. Klient proto musí být ukončeno před dokončením transakce odesílat všechny zprávy do fronty v relaci.  
  
 Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly služby a klienta. Uvidíte služby přijmout zprávy z klienta. Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby. Všimněte si, že vzhledem k tomu, že služby Řízení front se používá, klient a služba nemusí být spuštěná ve stejnou dobu. Spuštění klienta, vypněte ho a potom spuštění služby a stále přijímá jeho zprávy.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C#, C++ nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Ve výchozím nastavení se <xref:System.ServiceModel.NetMsmqBinding>, je povoleno zabezpečení přenosu. Existují dvě vlastnosti důležité pro zabezpečení služby MSMQ přenosu konkrétně, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`. Pro služby MSMQ k ověřování a podepisování funkce musí být součástí domény a možnost integrace služby active directory pro službu MSMQ musí být nainstalován. Pokud tuto ukázku spustit na počítači, který nesplňuje tato kritéria obdržíte chybu.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Ke spuštění ukázky na počítač připojen k pracovní skupině nebo bez integrace služby active directory  
  
1.  Pokud počítač není součástí domény nebo nemá nainstalované integrační služby active directory, vypněte zabezpečení přenosu podle nastavení úrovně režim a ochrany ověřování na `None` jak je znázorněno v následující ukázka konfigurace.  
  
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
  
2.  Ujistěte se, změnit konfiguraci na serveru a klienta, před spuštěním ukázky.  
  
    > [!NOTE]
    >  Nastavení režimu zabezpečení k `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, a `Message` zabezpečení `None`.  
  
## <a name="see-also"></a>Viz také
