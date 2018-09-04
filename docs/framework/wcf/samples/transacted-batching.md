---
title: Transakční dávkování
ms.date: 03/30/2017
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
ms.openlocfilehash: abada9aaf5fac8f05599467f385e708e1898832f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558505"
---
# <a name="transacted-batching"></a>Transakční dávkování
Tento příklad ukazuje, jak dávkové transakce čtení pomocí služby Řízení front zpráv (MSMQ). Transakční dávkování je funkce optimalizace výkonu pro transakční operace čtení v komunikaci ve frontě.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 V komunikaci ve frontě klient komunikuje se služby pomocí fronty. Přesněji řečeno klient odešle zprávy do fronty. Služba přijímá zprávy z fronty. Klienta a služby, proto není potřeba běžet současně na komunikaci pomocí fronty.  
  
 V této ukázce provedené dávkování. Provedené dávkování je chování, které umožňuje použití jedné transakce při čtení počet zpráv ve frontě a jejich zpracování.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pokud je služba spuštěna první, zkontroluje se tak, aby byl do fronty k dispozici. Pokud fronta neexistuje, služba ho vytvoří. Můžete spustit služba nejdřív vytvořte frontu nebo můžete vytvořit prostřednictvím Správce fronty MSMQ. Postupujte podle těchto kroků můžete vytvořit frontu Windows 2008.  
  
    1.  Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozbalte **funkce** kartu.  
  
    3.  Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **nový**, **soukromou frontu**.  
  
    4.  Zkontrolujte, **transakční** pole.  
  
    5.  Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.  
  
    > [!NOTE]
    >  V této ukázce klient odešle stovky zprávy jako součást služby batch. Je běžné pro aplikaci služby pro zpracování těchto nějakou dobu trvat.  
  
3.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Ke spuštění ukázky na počítač připojen k pracovní skupině nebo bez integrace služby active directory  
  
1.  Ve výchozím nastavení se <xref:System.ServiceModel.NetMsmqBinding>, je povoleno zabezpečení přenosu. Existují dvě vlastnosti důležité pro zabezpečení přenosu služby MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` výchozí režim ověřování nastaven na `Windows` a aby úroveň ochrany je nastavená na `Sign`. Pro službu MSMQ. k ověřování a podepisování funkce musí být součástí domény a možnost integrace služby active directory pro službu MSMQ musí být nainstalována. Pokud tuto ukázku spustit na počítači, který nevyhovuje těmto kritériím zobrazí chybová zpráva.  
  
2.  Pokud počítač není součástí domény nebo nemá nainstalované integrace služby active directory, vypněte zabezpečení přenosu nastavením úroveň ověření režimu a ochrany na `None` jak je znázorněno v následující ukázková konfigurace:  
  
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
  
3.  Ujistěte se, že změníte konfiguraci na serveru a klienta, před spuštěním ukázky.  
  
    > [!NOTE]
    >  Nastavení `security``mode` k `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, a `Message` zabezpečení `None`.  
  
4.  Ke spuštění databáze ve vzdáleném počítači, změňte připojovací řetězec tak, aby odkazoval na počítač, na kterém je umístěna databáze.  
  
## <a name="requirements"></a>Požadavky  
 Tuto ukázku spustit, musí být služba MSMQ nainstalovaná a je potřeba SQL nebo systém SQL Express.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vzorek ukazuje chování dávkového zpracování. Provedené dávkování je funkce optimalizace výkonu součástí služby MSMQ zařazených do fronty přenosu.  
  
 Pokud transakce se používají k odesílání a příjem zpráv, které nejsou ve skutečnosti 2 oddělte transakce. Když klient odešle zprávy v rámci oboru transakce, transakce je místní pro klienta a klient správce fronty. Když služba přijímá zprávy v rámci oboru transakce, transakce je místní pro službu a využívá správce fronty. Je velmi dobré si uvědomit, že klient a služba nenachází v rámci jedné transakce; Místo toho stále používá jinou transakcí při provádění operací (například odesílání a příjem) s frontou.  
  
 V ukázce používáme k provádění více operací služby jedné transakce. To slouží pouze jako funkce optimalizace výkonu a nemá vliv na sémantiku aplikace. Vzorek je založen na [nepodporuje transakce vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
## <a name="comments"></a>Komentáře  
 V této ukázce klient odešle dávku zpráv ke službě z v rámci oboru transakce. Chcete-li zobrazit optimalizace výkonu, pošleme velkého počtu zpráv; v takovém případě až 2500 zpráv.  
  
 Služby v rámci oboru transakce definovány službou pak přijme zprávy odeslané do fronty. Bez dávkování, výsledkem 2500 transakce pro každé vyvolání operace služby. To má vliv na výkon systému. Vzhledem k tomu, že dvě správce prostředků se využívá řada – fronta MSMQ a `Orders` databáze-každou transakci DTC je takový transakce. Jsme optimalizovat pomocí mnohem menším počtu transakcí tím, že zajišťuje, který dávku zpráv a vyvolání operace služby dojít v rámci jedné transakce.  
  
 Můžeme použít funkci dávkování podle:  
  
-   Určení chování dávkového zpracování v konfiguraci.  
  
-   Určení velikosti dávky z hlediska počtu zpráv ke čtení pomocí jedné transakce.  
  
-   Zadání maximální počet souběžných dávek, pro spuštění.  
  
 V tomto příkladu vám ukážeme, zvýšení výkonu snížením počtu transakcí tím, že zajišťuje, že v rámci jedné transakce před potvrzením transakce jsou vyvolány 100 operací služby.  
  
 Definuje chování služby na chování operace s `TransactionScopeRequired` nastavena na `true`. Tím se zajistí, že všechny správce prostředků přistupovat pomocí metody používají stejný obor transakcí, která se používá k načtení zprávy z fronty. V tomto příkladu používáme základní databáze k ukládání informací o pořadí nákupní obsažené ve zprávě. Obor transakce také zaručuje, že pokud metoda vyvolá výjimku, se vrátí zprávu do fronty. Bez nastavení tohoto chování operace kanálu ve frontě vytvoří transakce čtení zprávy z fronty a potvrdí ji automaticky, předtím, než je odeslána, takže pokud se operace nezdaří, dojde ke ztrátě zprávy. Nejběžnější scénář je pro operace služby k zařazení v transakci, která slouží k načtení zprávy z fronty, jak je ukázáno v následujícím kódu.  
  
 Všimněte si, že `ReleaseServiceInstanceOnTransactionComplete` je nastavena na `false`. Toto je důležité požadavek pro dávkové zpracování. Vlastnost `ReleaseServiceInstanceOnTransactionComplete` na `ServiceBehaviorAttribute` indikuje, co dělat s instancí služby, po dokončení transakce. Ve výchozím nastavení instance služby je uvolněn po dokončení transakce. Základní aspekt pro dávkové zpracování je použití jedné transakce pro čtení a odesílání počet zpráv ve frontě. Proto uvolňování instance služby končí dokončení transakce předčasně negace velmi použití dávkování. Pokud je tato vlastnost nastavená na `true` a chování dávkového zpracování je přidán do koncového bodu, vyvolá výjimku, dávkování chování ověřování.  

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

 `Orders` Třída zapouzdří zpracování objednávky. V ukázce databáze se aktualizuje informace o objednávce.  

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

 Dávkování chování a jeho konfigurace jsou uvedeny v konfiguraci aplikace služby.  
  
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
>  Velikost dávky se o nápovědu k systému. Například pokud chcete zadat velikost dávky 20, pak 20 zpráv četla a pomocí jedné transakce a pak je transakce potvrzena. Ale existují případy, kde může transakci potvrdit dávku předtím, než je dosaženo velikost dávky.  
>   
>  Spojené s každou transakci je časový limit, který se spustí tikání po vytvoření transakce. Když vyprší platnost tento časový limit transakce byla přerušena. Je možné pro tento časový limit vyprší ještě předtím, než je dosaženo velikost dávky. Aby se zabránilo znovu dávku práce z důvodu přerušení, `TransactedBatchingBehavior` kontroluje, jak dlouho zůstane v transakci. Pokud se využilo 80 % limitu transakcí, je transakce potvrzeny.  
>   
>  Pokud nejsou žádné další zprávy ve frontě a místo abyste čekali, plnění velikost dávky <xref:System.ServiceModel.Description.TransactedBatchingBehavior> potvrzení transakce.  
>   
>  Volba velikosti dávky je závislá na aplikaci. Pokud velikost dávky je příliš malá, nelze získat požadovaný výkon. Na druhé straně Pokud velikost dávky je příliš velká, může zhoršit výkon. Například transakce může již live a podržte zámky ve vaší databázi nebo transakce může stát dead uzamčen, které by mohly způsobit batch k získání vrátit zpět a vrátit ke svému práce.  
  
 Klient vytvoří obor transakce. Komunikace s frontou probíhá v rámci oboru transakcí, vyvolá zacházet jako atomickou jednotku, kde jsou všechny zprávy odeslané do fronty nebo jsou žádné zprávy odeslané do fronty. Transakce se potvrdí při volání <xref:System.Transactions.TransactionScope.Complete%2A> v oboru transakce.  

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

 Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly služby a klienta. Můžete zobrazit přijetí zprávy služby z klienta. Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby. Mějte na paměti, protože služba Řízení front se používá, klient a služba nemusí být zprovoznit ve stejnou dobu. Můžete spustit klienta, vypněte ho a spusťte službu a stále přijímá zprávy. Postupné výstup můžete prohlédnout, jak číst v dávce a zpracování zpráv.  
  
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
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a>Viz také
