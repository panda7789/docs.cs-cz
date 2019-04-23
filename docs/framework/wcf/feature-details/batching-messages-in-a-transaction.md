---
title: Dávkování zpráv v transakci
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: 2d820087973e689514a0a19a7adc912f49e9d0a2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310522"
---
# <a name="batching-messages-in-a-transaction"></a>Dávkování zpráv v transakci
Ve frontě aplikací používání transakcí k zajištění správnosti a spolehlivé doručování zpráv. Transakce, ale jsou nákladný provoz a může výrazně snížit propustnost zpráv. Jedním způsobem, jak zlepšit propustnost zpráv je, aby aplikaci číst a zpracovávat více zpráv v rámci jedné transakce. Nutný kompromis je mezi výkonem a možností obnovení: jak se zvyšuje počet zpráv v dávce, postupy zločinců se množství práce obnovení, který vyžaduje, pokud jsou transakce vrácena zpět. Je důležité si uvědomit rozdíl mezi dávkování zpráv v transakci a relací. A *relace* je seskupení související zprávy, které jsou zpracovány jednu aplikaci a potvrzena jako jeden celek. Relace se běžně používají, pokud skupina související zprávy musí být zpracovány současně. Příkladem je online nakupování webové stránky. *Dávky* se používají ke zpracování více, nesouvisející zprávy tak, že zpráva zvýšení propustnosti. Další informace o relacích najdete v tématu [seskupování zpráv zařazených do fronty v relaci](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md). Také zpracování jedné aplikace a potvrzena jako jednu jednotku zpráv v dávce, ale může být žádný vztah mezi zpráv v dávce. Dávkování zpráv v transakci je optimalizace, která se nemění, jak je aplikace spuštěná.  
  
## <a name="entering-batching-mode"></a>Zadat režim dávkování byl  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior> Dávkování řídí chování koncového bodu. Přidání tohoto chování koncového bodu na koncový bod služby říká Windows Communication Foundation (WCF) do služby batch zpráv v transakci. Ne všechny zprávy vyžadují transakci, takže pouze zprávy, které vyžadují transakce jsou umístěny v dávce, a pouze zprávy odeslané z operace označené `TransactionScopeRequired`  =  `true` a `TransactionAutoComplete`  =  `true` jsou zahrnutých do dávky. Pokud všechny operace v kontraktu služby jsou označeny `TransactionScopeRequired`  =  `false` a `TransactionAutoComplete`  =  `false`, pak režim dávkování byl se nezadal.  
  
## <a name="committing-a-transaction"></a>Potvrzení transakce  
 Dávkové transakce se potvrzeny založené na těchto faktorech:  
  
-   `MaxBatchSize`. Vlastnost <xref:System.ServiceModel.Description.TransactedBatchingBehavior> chování. Tato vlastnost určuje maximální počet zpráv, které se umístí do dávky. Při dosažení tohoto počtu se zavazuje služby batch. Toto je hodnota není striktní limitu, je možné potvrdit dávku před přijetím tento počet zpráv.  
  
-   `Transaction Timeout`. Po uplynutí 80 procent společností z žebříčku časový limit transakce, usiluje o dávky a vytvoří novou dávku. To znamená, že pokud 20 procent nebo méně času pro k dokončení transakce zůstává, služby batch je potvrzená.  
  
-   `TransactionScopeRequired`. Při zpracování dávky zprávy, pokud WCF nenajde ten, který má `TransactionScopeRequired`  =  `false`, potvrzení změn služby batch a znovu neotevře novou dávku na příjem první zprávy s `TransactionScopeRequired`  =  `true` a `TransactionAutoComplete`  = `true`.  
  
-   Pokud neexistují žádné další zprávy ve frontě, je aktuální dávku potvrzené, i v případě `MaxBatchSize` nebyl dosažen nebo nebyl 80 procent společností z žebříčku transakce časový limit vypršel.  
  
## <a name="leaving-batching-mode"></a>Opustit režim dávkování byl  
 Pokud zpráva v dávce způsobí, že transakce pro přerušení, dojde k následujícím krokům:  
  
1. Celý dávku zpráv se vrátí zpět.  
  
2. Zprávy jsou jeden po druhém, dokud počet zpráv, přečtěte si, které překročí dvakrát maximální velikost dávky pro čtení.  
  
3. Režim dávky je zadat znovu.  
  
## <a name="choosing-the-batch-size"></a>Vyberete velikost dávky  
 Velikost dávky je aplikace závislá. Metoda empirical je nejlepší způsob, jak dorazí na velikost optimální služby batch pro aplikaci. Je důležité pamatovat při volbě velikosti dávky zvolte velikost podle vaší aplikace skutečný nasazení modelu. Například při nasazování aplikací, pokud je třeba SQL server na vzdáleném počítači a transakce, která zahrnuje fronty a SQL server, pak velikost dávky je nejlepší určí spuštěním této přesnou konfiguraci.  
  
## <a name="concurrency-and-batching"></a>Souběžnost a dávkové zpracování  
 Pokud chcete zvýšit propustnost, můžete mít také mnoho dávky běžet souběžně. Nastavením `ConcurrencyMode.Multiple` v `ServiceBehaviorAttribute`, můžete povolit souběžné dávkování.  
  
 *Služba omezování* je chování služby, který se používá k označení, nelze realizovat maximální počet souběžných volání služby. Při použití s dávkové zpracování, je interpretován jako způsob, jakým lze spustit mnoho souběžných dávky. Pokud omezení služby není nastavená, WCF výchozí maximální souběžných volání na 16. Proto pokud ve výchozím nastavení byly přidány do dávek chování, maximálně 16 dávek může být aktivní ve stejnou dobu. Je nejvhodnější k vyladění omezení služby a dávkové zpracování na základě vaší kapacity. Například pokud fronta má 100 zpráv a je požadován dávku 20, s maximální souběžných volání nastaven na hodnotu 16 není užitečné proto, že v závislosti na propustnost, může být 16 transakce aktivní, podobně jako nemít dávkování zapnuté. Proto při optimalizaci výkonu, buď nemáte k dispozici souběžných dávkování nebo mít souběžných dávkování omezení velikosti správné služby.  
  
## <a name="batching-and-multiple-endpoints"></a>Dávkové zpracování a několik koncových bodů  
 Koncový bod se skládá z adresy a kontrakt. Může existovat více koncových bodů, které sdílejí stejnou vazbu. Je možné pro dva koncové body sdílet stejnou vazbu a naslouchání identifikátor URI (Uniform Resource), nebo adresa fronty. Pokud jsou dva koncové body čtení ze stejné fronty a transakční dávkování chování je přidána do oba koncové body, konfliktu ve službě batch, které by mohly nastat velikosti. Je to vyřešit implementací dávkování použitím velikosti minimální dávky určena v rozsahu mezi dvěma provedené dávkování chování. V tomto scénáři Pokud jeden z koncových bodů není určen provedené dávkování, pak oba koncové body nepoužívejte dávkování.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit `TransactedBatchingBehavior` v konfiguračním souboru.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 Následující příklad ukazuje, jak určit <xref:System.ServiceModel.Description.TransactedBatchingBehavior> v kódu.  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
     ServiceEndpoint sep = ServiceHost.AddServiceEndpoint(typeof(IOrderProcessor), new NetMsmqBinding(), "net.msmq://localhost/private/ServiceModelSamplesTransacted");
     sep.Behaviors.Add(new TransactedBatchingBehavior(100));
     
     // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();
  
    // The service can now be accessed.
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.WriteLine();
    Console.ReadLine();
  
    // Close the ServiceHostB to shut down the service.
    serviceHost.Close();
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
