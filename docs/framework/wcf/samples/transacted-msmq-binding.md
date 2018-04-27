---
title: Zpracované vazby služby MSMQ
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
caps.latest.revision: 50
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e0529aa940c02ee79e25034e57f89d4b476861b8
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="transacted-msmq-binding"></a>Zpracované vazby služby MSMQ
Tento příklad ukazuje, jak provést zpracovaných komunikace ve frontě pomocí služby Řízení front zpráv (MSMQ).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 V komunikaci ve frontě klient komunikuje se služby pomocí fronty. Přesněji řečeno klient odešle zprávy do fronty. Služba přijímá zprávy z fronty. Službu a klienta, proto nemusíte používat současně na komunikaci pomocí fronty.  
  
 Pokud transakce se používají k odesílání a přijímání zpráv, jsou ve skutečnosti dvě samostatné transakce. Když klient odešle zprávy v rámci oboru transakce, transakce je místní pro klienta a fronty správce klienta. Když služba přijímá zprávy v rámci oboru transakce, transakce je místní služby a využívá správce fronty. Je důležité si pamatovat, klient a služba nejsou součástí stejné transakci; různé transakce místo toho používají při provádění operací (například odesílat a přijímat) s fronty.  
  
 V této ukázce klient odešle dávku zpráv do služby z v rámci oboru transakce. Služba v rámci oboru transakce definované ve službě jsou pak přijímá zprávy odeslané do fronty.  
  
 Kontrakt služby je `IOrderProcessor`, jak je znázorněno v následujícím ukázkovém kódu. Rozhraní definuje jednosměrné služby, který je vhodný pro použití s front.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 Chování služby definuje chování operaci s `TransactionScopeRequired` nastavena na `true`. To zajistí, že je žádné správci prostředků přístup metodu použít stejný obor transakce, který se používá k načtení zprávy z fronty. Také zaručuje, že pokud metoda vyvolá výjimku, bude vráceno do fronty. Bez nastavení toto chování operace, zařazených do fronty kanál vytvoří transakci čtení zprávy ve frontě a provede ji automaticky před odesláním tak, že pokud se operace nezdaří, dojde ke ztrátě zprávy. Nejběžnější scénáře je pro operace služby zařazení v transakci, která slouží k načtení zprávy z fronty, jak je ukázáno v následujícím kódu.  

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

 Služba je sám sebou hostované. Pokud používáte přenos MSMQ, používá fronty musí být vytvořeny předem. Tento krok můžete provést ručně nebo prostřednictvím kódu. V této ukázce služby obsahuje kód kontrolovat existenci fronty a vytvořit frontu, pokud neexistuje. Název fronty je číst z konfiguračního souboru. Základní adresa se používá [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování proxy ke službě.  

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

 Název fronty služby MSMQ je zadaný v oddílu appSettings konfiguračního souboru, jak je znázorněno v následující ukázka konfigurace.  
  
```xml  
<appSettings>  
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />  
</appSettings>  
```  
  
> [!NOTE]
>  Název fronty používá tečku (.) pro místní počítač a oddělovačů zpětné lomítko, v cestě, při vytváření fronty pomocí <xref:System.Messaging>. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Koncový bod používá adresu fronty s schéma net.msmq, používá "localhost" k označení místního počítače, a používá předávání lomítka v jeho cesty.  
  
 Klient vytvoří oboru transakce. Komunikace s fronty probíhá v rámci oboru transakce, příčinou je považován za atomické jednotky, kde jsou všechny zprávy odeslané do fronty nebo žádné zprávy jsou odesílány do fronty. Transakce se potvrdí voláním <xref:System.Transactions.TransactionScope.Complete%2A> v oboru transakce.  

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

 Pokud chcete ověřit, že transakce funguje, měnit klienta, a jak je znázorněno v následujícím ukázkovém kódu komentářů oboru transakce, znovu sestavte řešení a spuštění klienta.  

```csharp
//scope.Complete();  
```

 Protože transakce není dokončena, nejsou zprávy odeslané do fronty.  
  
 Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly služby a klienta. Uvidíte služby přijmout zprávy z klienta. Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby. Všimněte si, že vzhledem k tomu, že služby Řízení front se používá, klient a služba nemusí být spuštěná ve stejnou dobu. Spuštění klienta, vypněte ho a potom spuštění služby a stále obdrží zprávy.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty. Pokud fronta neexistuje, vytvoří služba jeden. Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ. Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.  
  
    1.  Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozbalte **funkce** kartě.  
  
    3.  Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.  
  
    4.  Zkontrolujte **transakcí** pole.  
  
    5.  Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.  
  
3.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Ve výchozím nastavení se <xref:System.ServiceModel.NetMsmqBinding>, je povoleno zabezpečení přenosu. Existují dvě vlastnosti důležité pro zabezpečení přenosu služby MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>. Ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`. Pro služby MSMQ k ověřování a podepisování funkce musí být součástí domény a možnost integrace služby Active Directory pro službu MSMQ musí být nainstalován. Pokud tuto ukázku spustit na počítači, který nesplňuje tato kritéria, obdržíte chybu.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Ke spuštění ukázky na počítač připojen k pracovní skupině nebo bez integrace služby Active Directory  
  
1.  Pokud počítač není součástí domény nebo nemá nainstalované integrační služby Active Directory, vypněte zabezpečení přenosu podle nastavení úrovně režim a ochrany ověřování na `None` jak je znázorněno v následujícím ukázkovém kódu konfigurace.  
  
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
  
2.  Ujistěte se, změnit konfiguraci na serveru a klienta, před spuštěním ukázky.  
  
    > [!NOTE]
    >  Nastavení `security``mode` k `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, a `Message` zabezpečení `None`.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`  
  
## <a name="see-also"></a>Viz také
