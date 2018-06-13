---
title: Transakční dávkování
ms.date: 03/30/2017
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
ms.openlocfilehash: 7df65b8f3f149deac841010e392f3919b24506b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508875"
---
# <a name="transacted-batching"></a>Transakční dávkování
Tento příklad ukazuje, jak dávky zpracovaných čtení pomocí služby Řízení front zpráv (MSMQ). Zpracovaných Batching je funkce optimalizace výkonu pro zpracovaných čtení v komunikaci ve frontě.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 V komunikaci ve frontě klient komunikuje se služby pomocí fronty. Přesněji řečeno klient odešle zprávy do fronty. Služba přijímá zprávy z fronty. Služba a klient proto nemusíte používat současně na komunikaci pomocí fronty.  
  
 Tento příklad znázorňuje zpracovaných dávkování. Dávkové je chování, které umožňuje použití jedné transakci při čtení mnoho zpráv ve frontě a jejich zpracování.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty. Pokud fronta neexistuje, vytvoří služba jeden. Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ. Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.  
  
    1.  Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozbalte **funkce** kartě.  
  
    3.  Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.  
  
    4.  Zkontrolujte **transakcí** pole.  
  
    5.  Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.  
  
    > [!NOTE]
    >  V této ukázce klient odešle stovky zprávy jako část dávky. Je normální, pro aplikaci služby pro zpracování těchto chvíli trvat.  
  
3.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Ke spuštění ukázky na počítač připojen k pracovní skupině nebo bez integrace služby active directory  
  
1.  Ve výchozím nastavení se <xref:System.ServiceModel.NetMsmqBinding>, je povoleno zabezpečení přenosu. Existují dvě vlastnosti důležité pro zabezpečení přenosu služby MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` ve výchozím nastavení je režim ověřování nastaven na `Windows` a úroveň ochrany je nastavena na `Sign`. Pro služby MSMQ k ověřování a podepisování funkce musí být součástí domény a možnost integrace služby active directory pro službu MSMQ musí být nainstalován. Pokud tuto ukázku spustit na počítači, který nesplňuje tato kritéria obdržíte chybu.  
  
2.  Pokud počítač není součástí domény nebo nemá nainstalované integrační služby active directory, vypněte zabezpečení přenosu podle nastavení úrovně režim a ochrany ověřování na `None` jak je znázorněno v následující ukázka konfigurace:  
  
    ```xml  
    <system.serviceModel>  
      <behaviors>  
        <serviceBehaviors>  
          <behavior name="ThrottlingBehavior">  
            <serviceMetadata httpGetEnabled="true"/>  
            <serviceThrottling maxConcurrentCalls="5"/>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="BatchingBehavior">  
            <transactedBatching maxBatchSize="100"/>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <services>  
        <service   
            behaviorConfiguration="ThrottlingBehavior"   
            name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                    binding="netMsmqBinding"  
                    bindingConfiguration="Binding1"   
                    behaviorConfiguration="BatchingBehavior"   
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
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
  
    </system.serviceModel>  
    ```  
  
3.  Ujistěte se, změnit konfiguraci na serveru a klienta, před spuštěním ukázky.  
  
    > [!NOTE]
    >  Nastavení `security``mode` k `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, a `Message` zabezpečení `None`.  
  
4.  Pokud chcete spustit databáze ve vzdáleném počítači, změňte připojovací řetězec tak, aby odkazoval na počítač, na kterém je umístěna databáze.  
  
## <a name="requirements"></a>Požadavky  
 Chcete-li tuto ukázku spustit, musí být nainstalované služby MSMQ a je zapotřebí SQL nebo SQL Express.  
  
## <a name="demonstrates"></a>Demonstruje  
 Ukázka ukazuje chování dávkového zpracování. Dávkové je funkce optimalizace výkonu součástí služby MSMQ zařazených do fronty přenosu.  
  
 Pokud transakce se používají k odesílání a přijímání zpráv, které jsou ve skutečnosti 2 oddělte transakce. Když klient odešle zprávy v rámci oboru transakce, transakce je místní pro klienta a fronty správce klienta. Když služba přijímá zprávy v rámci oboru transakce, transakce je místní služby a využívá správce fronty. Je důležité si pamatovat, klient a služba nejsou součástí stejné transakci; různé transakce místo používají při provádění operací (například odesílat a přijímat) s fronty.  
  
 V ukázce používáme pro provádění více operací služby jedné transakci. To se používají pouze jako funkce optimalizace výkonu a nemá negativní vliv na sémantiku aplikace. Ukázka je založena na [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
## <a name="comments"></a>Komentáře  
 V této ukázce klient odešle dávku zpráv do služby z v rámci oboru transakce. Chcete-li zobrazit optimalizace výkonu, odešleme velkého počtu zpráv; v takovém případě až 2 500 zprávy.  
  
 Služba v rámci oboru transakce definované ve službě jsou pak přijímá zprávy odeslané do fronty. Bez dávkování, výsledkem 2 500 transakce pro každé vyvolání operace služby. Má to dopad na výkon systému. Protože se účastní - dvěma správci prostředků frontu MSMQ a `Orders` databáze-každé takové transakce je transakcí koordinátoru DTC. Jsme optimalizovat pomocí mnohem menší počet transakcí zajištěním toho docílit dávku zpráv a volání operace služby v rámci jedné transakce.  
  
 Můžeme použít funkci dávkování podle:  
  
-   Určení chování dávkového zpracování v konfiguraci.  
  
-   Zadání velikost dávky z hlediska počet zpráv ke čtení pomocí jedné transakce.  
  
-   Zadání maximální počet souběžných balíků ke spuštění.  
  
 V tomto příkladu ukážeme zvýšení výkonu snížením počtu transakcí tím, že zajistí, že v rámci jedné transakce před potvrzením transakce jsou vyvolány 100 operací služby.  
  
 Chování služby definuje chování operaci s `TransactionScopeRequired` nastavena na `true`. To zajistí, že je žádné správci prostředků přístup metodu použít stejný obor transakce, který se používá k načtení zprávy z fronty. V tomto příkladu používáme databáze basic uložit informace o nákupu pořadí obsažené ve zprávě. Oboru transakce také zaručuje, že pokud metoda vyvolá výjimku, bude vráceno do fronty. Bez nastavení toto chování operace, zařazených do fronty kanál, který vytvoří transakci čtení zprávy ve frontě a potvrdí automaticky předtím, než je odeslán, takže pokud se operace nezdaří, dojde ke ztrátě zprávy. Nejběžnější scénáře je pro operace služby zařazení v transakci, která slouží k načtení zprávy z fronty, jak je ukázáno v následujícím kódu.  
  
 Všimněte si, že `ReleaseServiceInstanceOnTransactionComplete` je nastaven na `false`. Toto je důležité požadavek pro dávkové zpracování. Vlastnost `ReleaseServiceInstanceOnTransactionComplete` na `ServiceBehaviorAttribute` označuje, co dělat s instancí služby po dokončení transakce. Ve výchozím nastavení je instance služby vydala po dokončení transakce. Základní aspekt pro dávkování je použití jedné transakci pro čtení a odeslání mnoho zpráv ve frontě. Proto uvolnění instance služby skončilo dokončení transakce předčasně negace velmi použití dávkování. Pokud je tato vlastnost nastavena na `true` a chování dávkového zpracování se přidá do koncového bodu, dávkování chování vyvolá výjimku.  

```csharp
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(ReleaseServiceInstanceOnTransactionComplete=false,   
TransactionIsolationLevel=  
System.Transactions.IsolationLevel.Serializable, ConcurrencyMode=ConcurrencyMode.Multiple)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                       TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
    …  
}  
```

 `Orders` Třída zapouzdří zpracování pořadí. V ukázce databáze se aktualizuje informace o objednávce.  

```csharp
// Order Processing Logic  
public class Orders  
{  
    public static void Add(PurchaseOrder po)  
    {  
        // Insert purchase order.  
        SqlCommand insertPurchaseOrderCommand =   
        new SqlCommand(  
        "insert into PurchaseOrders(poNumber, customerId)   
                               values(@poNumber, @customerId)");  
        insertPurchaseOrderCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        insertPurchaseOrderCommand.Parameters.Add("@customerId",   
                                         SqlDbType.VarChar, 50);  
  
        // Insert product line item.  
        SqlCommand insertProductLineItemCommand =   
             new SqlCommand("insert into ProductLineItems(productId,   
                    unitCost, quantity, poNumber) values(@productId,   
                    @unitCost, @quantity, @poNumber)");  
        insertProductLineItemCommand.Parameters.Add("@productId",   
                                           SqlDbType.VarChar, 50);  
        insertProductLineItemCommand.Parameters.Add("@unitCost",   
                                                  SqlDbType.Float);  
        insertProductLineItemCommand.Parameters.Add("@quantity",   
                                                     SqlDbType.Int);  
        insertProductLineItemCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        int rowsAffected = 0;  
        using (TransactionScope scope =   
              new TransactionScope(TransactionScopeOption.Required))  
        {  
             using (SqlConnection conn = new   
                 SqlConnection(  
                 ConfigurationManager.AppSettings["connectionString"]))  
             {  
                 conn.Open();  
  
                // Insert into purchase order table.  
               insertPurchaseOrderCommand.Connection = conn;  
               insertPurchaseOrderCommand.Parameters["@poNumber"].Value   
                                                       = po.PONumber;  
             insertPurchaseOrderCommand.Parameters["@customerId"].Value   
                                                    =po.CustomerId;  
             insertPurchaseOrderCommand.ExecuteNonQuery();  
  
            // Insert into product line item table.  
            insertProductLineItemCommand.Connection = conn;  
            foreach (PurchaseOrderLineItem orderLineItem in   
                                        po.orderLineItems) {  
            insertProductLineItemCommand.Parameters["@poNumber"].Value   
                                                          =po.PONumber;  
            insertProductLineItemCommand.Parameters["@productId"].Value   
                                             = orderLineItem.ProductId;  
            insertProductLineItemCommand.Parameters["@unitCost"].Value   
                                             = orderLineItem.UnitCost;  
            insertProductLineItemCommand.Parameters["@quantity"].Value   
                                             = orderLineItem.Quantity;  
            rowsAffected +=   
            insertProductLineItemCommand.ExecuteNonQuery();  
            }  
            scope.Complete();  
        }  
     }  
     Console.WriteLine(  
     "Updated database with {0} product line items  for purchase order   
                                     {1} ", rowsAffected, po.PONumber);  
    }  
}  
```

 Dávkování chování a jeho konfigurace jsou určené v konfiguraci aplikace služby.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName"   
     value=".\private$\ServiceModelSamplesTransactedBatching" />  
    <add key="baseAddress"   
     value=  
     "http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
    <add key="connectionString" value="Data Source=.\SQLEXPRESS;AttachDbFilename=|DataDirectory|orders.mdf;Integrated Security=True;User Instance=True;" />  
  </appSettings>  
  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ThrottlingBehavior">  
          <serviceThrottling maxConcurrentCalls="5"/>  
        </behavior>  
      </serviceBehaviors>  
  
      <endpointBehaviors>  
        <behavior name="BatchingBehavior">  
          <transactedBatching maxBatchSize="100"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service   
          behaviorConfiguration="ThrottlingBehavior"   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address=  
"net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                  binding="netMsmqBinding"  
                  behaviorConfiguration="BatchingBehavior"   
                  contract=  
                    "Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  Velikost dávky je nápovědu k systému. Například pokud zadáte velikost dávky 20, pak 20 zpráv by se přečíst a odeslat pomocí jedné transakce a pak je transakce potvrzena. Ale existují případy, kdy může transakce potvrdit dávku před dosažením velikost dávky.  
>   
>  Přidružený ke každé transakci je vypršení časového limitu, která se spouští tikání po vytvoření transakce. Transakce byla přerušena, když vyprší platnost tento časový limit. Je možné pro tento časový limit vyprší, ještě před dosažením velikosti dávky. Aby se zabránilo znovu práce dávky z důvodu přerušení, `TransactedBatchingBehavior` kontroluje, jak dlouho je ponechán v transakci. Pokud 80 % časový limit transakcí slouží, je transakce potvrzena.  
>   
>  Pokud neexistují žádné další zprávy ve frontě a nemusí se čekat splnění velikost dávky <xref:System.ServiceModel.Description.TransactedBatchingBehavior> potvrdí transakce.  
>   
>  Vybraná velikost dávky je závisí na vaší aplikace. Pokud velikost dávky je příliš malá, nelze získat požadovaný výkon. Na druhé straně Pokud velikost dávky je příliš velký, může zhoršit výkon. Například může vaší transakce a za provozu již a podržením zámky ve vaší databázi nebo vaší transakce a může přestat mrtvých uzamčené, které by mohly způsobit dávky k získání vrácena zpět a vrátit práce.  
  
 Klient vytvoří oboru transakce. Komunikace s fronty probíhá v rámci oboru transakce, příčinou je považován za atomické jednotky, kde jsou všechny zprávy odeslané do fronty nebo žádné zprávy jsou odesílány do fronty. Transakce se potvrdí voláním <xref:System.Transactions.TransactionScope.Complete%2A> v oboru transakce.  

```csharp
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        Random randomGen = new Random();  
        for (int i = 0; i < 2500; i++)  
        {  
            // Create a client with given client endpoint configuration.  
            OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
            // Create the purchase order.  
            PurchaseOrder po = new PurchaseOrder();  
            po.CustomerId = "somecustomer" + i + ".com";  
            po.PONumber = Guid.NewGuid().ToString();  
  
            PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
            lineItem1.ProductId = "Blue Widget";  
            lineItem1.Quantity = randomGen.Next(1, 100);  
            lineItem1.UnitCost = (float)randomGen.NextDouble() * 10;  
  
            PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
            lineItem2.ProductId = "Red Widget";  
            lineItem2.Quantity = 890;  
            lineItem2.UnitCost = 45.89F;  
  
            po.orderLineItems = new PurchaseOrderLineItem[2];  
            po.orderLineItems[0] = lineItem1;  
            po.orderLineItems[1] = lineItem2;  
  
            //Create a transaction scope.  
            using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
            {  
                // Make a queued call to submit the purchase order.  
                client.SubmitPurchaseOrder(po);  
                // Complete the transaction.  
                scope.Complete();  
            }  
  
            client.Close();  
        }  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```

 Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly služby a klienta. Uvidíte služby přijmout zprávy z klienta. Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby. Všimněte si, že vzhledem k tomu, že služby Řízení front se používá, klient a služba nemusí být spuštěná ve stejnou dobu. Spuštění klienta, vypněte ho a potom spuštění služby a stále přijímá jeho zprávy. Uvidíte postupného výstup jako přečtená v dávce a zpracování zpráv.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Updated database with 2 product line items for purchase order 493ac832-d216-4e94-b2a5-d7f492fb5e39  
Processing Purchase Order: 8b567f5b-0661-4662-aae2-6cef1bd6d278  
        Customer: somecustomer849.com  
        OrderDetails  
               Order LineItem: 80 of Blue Widget @unit price: $9.751623  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41622.23  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 41130b95-4ea8-40a9-91c3-2e129117fcb8  
Processing Purchase Order: 5ce2699d-9a31-4cc2-a8c5-64cda614b3c7  
        Customer: somecustomer850.com  
        OrderDetails  
               Order LineItem: 89 of Blue Widget @unit price: $6.369128  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41408.95  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 8b567f5b-0661-4662-aae2-6cef1bd6d278  
Processing Purchase Order: ea94486b-7c86-4309-a42d-2f06c00656cd  
        Customer: somecustomer851.com  
        OrderDetails  
             Order LineItem: 47 of Blue Widget @unit price: $0.9391424  
             Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $40886.24  
        Order status: Pending  
```  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a>Viz také
