---
title: Dávkování zpráv v transakci
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: be9661525c960ae558d21b05781007b81b8a3f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185441"
---
# <a name="batching-messages-in-a-transaction"></a>Dávkování zpráv v transakci
Aplikace ve frontě používají transakce k zajištění správnosti a spolehlivého doručování zpráv. Transakce jsou však nákladné operace a může výrazně snížit propustnost zpráv. Jedním ze způsobů, jak zlepšit propustnost zpráv, je, aby aplikace četla a zpracovávala více zpráv v rámci jedné transakce. Kompromis je mezi výkonem a obnovení: jako počet zpráv v dávce zvyšuje, tak se množství práce obnovení, které vyžadují, pokud jsou transakce vráceny zpět. Je důležité si uvědomit rozdíl mezi dávkově zprávy v transakci a relace. *Relace* je seskupení souvisejících zpráv, které jsou zpracovány jednou aplikací a potvrzeny jako jedna jednotka. Relace se obvykle používají, když skupina souvisejících zpráv musí být zpracována společně. Příkladem je web pro online nakupování. *Listy* se používají ke zpracování více nesouvisejících zpráv způsobem, který zvyšuje propustnost zpráv. Další informace o relacích naleznete [v tématu Seskupování zpráv ve frontě v relaci](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md). Zprávy v dávce jsou také zpracovány jednou aplikací a potvrzeny jako jedna jednotka, ale může existovat žádný vztah mezi zprávami v dávce. Dávkování zpráv v transakci je optimalizace, která nemění způsob, jakým aplikace běží.  
  
## <a name="entering-batching-mode"></a>Zadání dávkovacího režimu  
 Chování <xref:System.ServiceModel.Description.TransactedBatchingBehavior> koncového bodu řídí dávkování. Přidání tohoto chování koncového bodu do koncového bodu služby říká Windows Communication Foundation (WCF) dávkové zprávy v transakci. Ne všechny zprávy vyžadují transakci, takže pouze zprávy, které vyžadují transakci jsou umístěny `TransactionScopeRequired`  =  `true` `TransactionAutoComplete`  =  v dávce a pouze zprávy odeslané z operací označených a `true` jsou považovány za dávky. Pokud jsou všechny operace na `TransactionScopeRequired`  =  `false` servisní `TransactionAutoComplete`  =  `false`smlouvě označeny a , režim dávkování není nikdy zadán.  
  
## <a name="committing-a-transaction"></a>Potvrzení transakce  
 Dávková transakce je potvrzena na základě následujících:  
  
- `MaxBatchSize`. Vlastnost <xref:System.ServiceModel.Description.TransactedBatchingBehavior> chování. Tato vlastnost určuje maximální počet zpráv, které jsou umístěny do dávky. Po dosažení tohoto čísla je dávka potvrzena. Tato hodnota není přísnýlimit, je možné potvrdit dávku před přijetím tohoto počtu zpráv.  
  
- `Transaction Timeout`. Po uplynutí 80 procent časového limitu transakce je dávka potvrzena a je vytvořena nová dávka. To znamená, že pokud 20 procent nebo méně času přiděleného pro transakci k dokončení zůstane, dávka je potvrzena.  
  
- `TransactionScopeRequired`. Při zpracování dávky zpráv, pokud WCF `TransactionScopeRequired`  =  `false`najde ten, který má , potvrdí dávku a `TransactionScopeRequired`  =  `true` znovu `TransactionAutoComplete`  = otevře novou dávku při přijetí první zprávy s a `true`.  
  
- Pokud ve frontě neexistují žádné další zprávy, je aktuální `MaxBatchSize` dávka potvrzena, i když nebylo dosaženo nebo neuplynulo 80 procent časového limitu transakce.  
  
## <a name="leaving-batching-mode"></a>Opuštění režimu dávkování  
 Pokud zpráva v dávce způsobí přerušení transakce, dojde k následujícím krokům:  
  
1. Celá dávka zpráv je vrácena zpět.  
  
2. Zprávy jsou čteny jeden po druhém, dokud počet přečtených zpráv překročí dvojnásobek maximální velikosti dávky.  
  
3. Dávkový režim je znovu zadán.  
  
## <a name="choosing-the-batch-size"></a>Výběr velikosti dávky  
 Velikost dávky je závislá na aplikaci. Empirická metoda je nejlepší způsob, jak dosáhnout optimální velikosti dávky pro aplikaci. Je důležité mít na paměti při výběru velikosti dávky zvolit velikost podle skutečného modelu nasazení vaší aplikace. Například při nasazování aplikace, pokud potřebujete sql server na vzdáleném počítači a transakce, která zahrnuje fronty a SQL server, pak velikost dávky je nejlépe určit spuštěním této přesné konfigurace.  
  
## <a name="concurrency-and-batching"></a>Souběžnost a dávkování  
 Chcete-li zvýšit propustnost, můžete také mít mnoho dávek spustit současně. Nastavením `ConcurrencyMode.Multiple` `ServiceBehaviorAttribute`v , můžete povolit souběžné dávkování.  
  
 *Omezení služby* je chování služby, které se používá k označení, kolik maximální souběžná volání lze provést ve službě. Při použití s dávkování, to je interpretovánjako kolik souběžných dávek lze spustit. Pokud omezení služby není nastavena, WCF výchozí maximální souběžná volání 16. Proto pokud dávkování chování byly přidány ve výchozím nastavení, maximálně 16 dávek může být aktivní ve stejnou dobu. Nejlepší je vyladit omezení služby a dávkování na základě vaší kapacity. Například pokud fronta má 100 zpráv a dávka 20 je žádoucí, s maximální souběžná volání nastavena na 16 není užitečné, protože v závislosti na propustnost 16 transakcí může být aktivní, podobně jako s dávkování zapnuta. Proto při jemné množení pro výkon, buď nemají souběžné dávkování nebo mají souběžné dávkování se správnou velikostí omezení služby.  
  
## <a name="batching-and-multiple-endpoints"></a>Dávkování a více koncových bodů  
 Koncový bod se skládá z adresy a smlouvy. Může existovat více koncových bodů, které sdílejí stejnou vazbu. Je možné pro dva koncové body sdílet stejnou vazbu a poslouchat identifikátor jednotného prostředku (URI) nebo adresu fronty. Pokud dva koncové body jsou čtení ze stejné fronty a transakční dávkování chování je přidán do obou koncových bodů, může dojít ke konfliktu v velikosti dávky zadané. To je vyřešeno implementací dávkování pomocí minimální velikosti dávky zadané mezi dvěma transakčními chováními dávkování. V tomto scénáři pokud jeden z koncových bodů neurčuje transakční dávkování, pak by oba koncové body nepoužívaly dávkování.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak `TransactedBatchingBehavior` zadat v konfiguračním souboru.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 Následující příklad ukazuje, jak <xref:System.ServiceModel.Description.TransactedBatchingBehavior> zadat v kódu.  
  
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
  
## <a name="see-also"></a>Viz také

- [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Fronty ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
