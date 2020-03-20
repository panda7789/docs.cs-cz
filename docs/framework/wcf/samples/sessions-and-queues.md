---
title: Relace a fronty
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 8a342b185c7965e9ee0ff9941a09e00fc392ad4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144096"
---
# <a name="sessions-and-queues"></a>Relace a fronty
Tato ukázka ukazuje, jak odesílat a přijímat sadu souvisejících zpráv ve frontové komunikaci prostřednictvím přenosu služby Řízení front zpráv (MSMQ). Tato ukázka `netMsmqBinding` používá vazbu. Služba je aplikace konzoly s vlastním hostitelem, která umožňuje sledovat službu přijímající zprávy ve frontě.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 Ve frontové komunikaci klient komunikuje se službou pomocí fronty. Přesněji řečeno, klient odesílá zprávy do fronty. Služba přijímá zprávy z fronty. Služba a klient proto nemusí být spuštěny současně komunikovat pomocí fronty.  
  
 V některých případě klient odešle sadu zpráv, které spolu vzájemně souvisejí ve skupině. Pokud zprávy musí být zpracovány společně nebo v zadaném pořadí, fronta může být použita k jejich seskupení, pro zpracování jednou přijímající aplikací. To je obzvláště důležité v případě, že existuje několik přijímajících aplikací na skupině serverů a je nutné zajistit, aby skupina zpráv byla zpracována stejnou přijímající aplikací. Relace ve frontě jsou mechanismus používaný k odesílání a přijímání související sady zpráv, které musí být zpracovány najednou. Relace ve frontě vyžadují k zobrazení tohoto vzoru transakci.  
  
 V ukázce klient odešle několik zpráv do služby jako součást relace v rámci jedné transakce.  
  
 Servisní smlouva `IOrderTaker`je , která definuje jednosměrnou službu, která je vhodná pro použití s frontami. Použité <xref:System.ServiceModel.SessionMode> ve smlouvě uvedené v následujícím ukázkovém kódu označuje, že zprávy jsou součástí relace.  

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

 Služba definuje operace služby tak, že první operace zařadí do transakce, ale nedokončí automaticky transakci. Následné operace také zařadit do stejné transakce, ale není automaticky dokončit. Poslední operace v relaci automaticky dokončí transakci. Stejná transakce se tedy používá pro několik vyvolání operace v servisní smlouvě. Pokud některá z operací vyvolat výjimku, pak transakce vrátí zpět a relace je umístěn zpět do fronty. Po úspěšném dokončení poslední operace je transakce potvrzena. Služba používá `PerSession` jako <xref:System.ServiceModel.InstanceContextMode> přijímat všechny zprávy v relaci na stejné instanci služby.  

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

 Služba je hostována samostatně. Při použití přenosu služby MSMQ musí být použitá fronta vytvořena předem. To lze provést ručně nebo prostřednictvím kódu. V této ukázce služba obsahuje <xref:System.Messaging> kód pro kontrolu existence fronty a v případě potřeby ji vytvoří. Název fronty se čte z konfiguračního souboru pomocí třídy. <xref:System.Configuration.ConfigurationManager.AppSettings%2A>  

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

 Název fronty služby MSMQ je určen v části appSettings konfiguračního souboru. Koncový bod pro službu je definován v části system.serviceModel konfiguračního souboru a určuje vazbu. `netMsmqBinding`  
  
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
  
 Klient vytvoří obor transakce. Všechny zprávy v relaci jsou odesílány do fronty v rámci oboru transakce, což způsobuje, že je považován za atomické jednotky, kde všechny zprávy úspěšné nebo neúspěšné. Transakce je potvrzena <xref:System.Transactions.TransactionScope.Complete%2A>voláním .  

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
> Pro všechny zprávy v relaci můžete použít pouze jednu transakci a všechny zprávy v relaci musí být odeslány před potvrzením transakce. Zavření klienta ukončí relaci. Proto musí být klient uzavřen před dokončením transakce odeslat všechny zprávy v relaci do fronty.  
  
 Při spuštění ukázky jsou aktivity klienta a služby zobrazeny v systému Windows služby i klientské konzole. Můžete vidět službu přijímat zprávy od klienta. Stisknutím klávesy ENTER v každém okně konzoly vypněte službu a klienta. Všimněte si, že vzhledem k tomu, že je používána frontová služba, klient a služba nemusí být spuštěny současně. Můžete spustit klienta, vypnout a potom spustit službu a stále přijímá jeho zprávy.  
  
 Na klienta.  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 Na bohoslužbě.  
  
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
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c#, C++ nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Ve výchozím <xref:System.ServiceModel.NetMsmqBinding>nastavení je povoleno zabezpečení přenosu. Existují dvě relevantní vlastnosti zabezpečení přenosu služby <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` MSMQ a ve `Windows` výchozím nastavení je režim `Sign`ověřování nastaven na a úroveň ochrany je nastavena na hodnotu . Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény a musí být nainstalována možnost integrace služby Active Directory pro službu MSMQ. Pokud spustíte tuto ukázku v počítači, který nesplňuje tato kritéria, zobrazí se chyba.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Spuštění ukázky v počítači připojovat se k pracovní skupině nebo bez integrace služby Active Directory  
  
1. Pokud počítač není součástí domény nebo není nainstalována integrace služby Active Directory, vypněte zabezpečení `None` přenosu nastavením režimu ověřování a úrovně ochrany na úroveň uvedenou v následující ukázkové konfiguraci.  
  
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
  
2. Před spuštěním ukázky se ujistěte, že změníte konfiguraci na serveru i na klientovi.  
  
    > [!NOTE]
    > Nastavení režimu `None` zabezpečení na <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>nastavení `Message` je `None`ekvivalentní nastavení a zabezpečení .  
