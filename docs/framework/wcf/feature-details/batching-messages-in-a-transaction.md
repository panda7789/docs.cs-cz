---
title: "Dávkování zpráv v transakci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0587624dd3b9bc12c6e421343ad2cdc1da6b970f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="batching-messages-in-a-transaction"></a>Dávkování zpráv v transakci
Zkontrolujte správnost a spolehlivé doručování zpráv ve frontě aplikací pomocí transakce. Transakce, ale jsou náročná operace a může výrazně snížit propustnost zpráv. Jeden způsob, jak zlepšit propustnost zpráva má mít aplikaci, čtení a zpracování více zpráv v rámci jedné transakce. Je nejvhodnější poměr mezi výkonem a obnovení: jak zvyšuje počet zpráv v dávce, takže nemá množství práce obnovení, který vyžaduje, pokud jsou transakce vrácena zpět. Je důležité si uvědomit rozdíl mezi dávkování zpráv v transakci a relace. A *relace* je seskupení související zprávy, které jsou zpracovávány jednu aplikaci a potvrzené jako na jednu jednotku. Relace se běžně používají, pokud skupina související zprávy musí být zpracován jako společně. Příkladem je nákupní webový server s online. *Dávky* se používají ke zpracování více, které nejsou v relaci zprávy způsobem, že zpráva zvyšuje propustnost. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]relace, viz [seskupování zpráv zařazených do fronty v relaci](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md). Také zpracovává jednu aplikaci a potvrzené jako na jednu jednotku zpráv v dávce, ale může být žádný vztah mezi zprávy v dávce. Dávkování zpráv v transakci je optimalizace, která se nezmění, jak je aplikace spuštěná.  
  
## <a name="entering-batching-mode"></a>Zadání dávkování režimu  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior> Ovládací prvky chování koncový bod dávkování. Přidání toto chování koncový bod pro koncový bod služby informuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] do dávky zpráv v transakci. Ne všechny zprávy vyžadují transakci, takže pouze zprávy, které vyžadují transakce jsou umístěny v dávce a označené jako pouze zprávy z operace `TransactionScopeRequired`  =  `true` a `TransactionAutoComplete`  =  `true` jsou za pro dávku. Pokud jsou všechny operace v kontrakt služby označené `TransactionScopeRequired`  =  `false` a `TransactionAutoComplete`  =  `false`, pak dávkování režimu se nikdy zadá.  
  
## <a name="committing-a-transaction"></a>Potvrzení transakce.  
 Dávkové transakce je potvrzená podle těchto kritérií:  
  
-   `MaxBatchSize`. Vlastnost <xref:System.ServiceModel.Description.TransactedBatchingBehavior> chování. Tato vlastnost určuje maximální počet zpráv, které jsou umístěny v dávce. Při dosažení tohoto počtu se zavazuje dávky. Toto je hodnota není striktní omezení, je možné potvrdit dávku před příjmem tento počet zpráv.  
  
-   `Transaction Timeout`. Po uplynutí časového limitu transakce 80 procent, dávky je potvrzená a se vytvoří novou dávku. To znamená, že pokud 20 procent nebo méně čas zadaný pro transakci pro dokončení zůstává, dávky je potvrzená.  
  
-   `TransactionScopeRequired`. Při zpracování dávku zpráv, pokud [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vybere ten, který má `TransactionScopeRequired`  =  `false`, se potvrdí dávky a znovu otevře novou dávku na přijetí první zprávy s `TransactionScopeRequired`  =  `true` a `TransactionAutoComplete` = `true`.  
  
-   Pokud neexistují žádné další zprávy ve frontě, pak je aktuální dávku potvrdit, i když `MaxBatchSize` nebyl dosažen nebo nebyla 80 procent transakce časový limit uplynul.  
  
## <a name="leaving-batching-mode"></a>Opouštění dávkování režimu  
 Zrušení způsobí, že zprávu v dávce, dojde k následující kroky:  
  
1.  Celý batch zpráv vrácena zpět.  
  
2.  Zprávy se čtou jednu po druhé, dokud dvakrát maximální velikost dávky překračuje počet čtení zpráv.  
  
3.  V dávkovém režimu je zadat znovu.  
  
## <a name="choosing-the-batch-size"></a>Výběr velikost dávky  
 Velikost dávky je aplikace závislá. Základě zkušeností metodou je nejlepší způsob, jak přicházejí na velikost optimální dávky pro aplikaci. Je důležité si pamatovat při výběru velikost dávky zvolte velikost podle modelu skutečné nasazení vaší aplikace. Například Pokud nasazujete aplikaci, pokud budete potřebovat systému SQL server na vzdáleném počítači a transakce, která zahrnuje fronty a serverem SQL server, pak velikost dávky je nejlépe určen spuštěním této přesnou konfiguraci.  
  
## <a name="concurrency-and-batching"></a>Souběžnost a dávkování  
 Pokud chcete zvýšit propustnost, může mít velký počet dávek běžet souběžně. Nastavením `ConcurrencyMode.Multiple` v `ServiceBehaviorAttribute`, povolíte souběžných dávkování.  
  
 *Služba omezení* je chování služby, který slouží k určení, kolik maximální počet souběžných volání můžete provést ve službě. Při použití s dávkování, to interpretována, jak lze spustit mnoho souběžných dávky. Pokud bude služba omezení není nastavena, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] výchozí maximální souběžných volání na 16. Proto pokud dávkování chování bylo přidáno ve výchozím nastavení, nesmí být delší než 16 dávky můžou být aktivní ve stejnou dobu. Je nejvhodnější pro optimalizaci omezení služby a dávkování na základě vaší kapacity. Například pokud má 100 zprávy fronty a dávky 20 se požaduje, s maximální souběžných volání nastaven na hodnotu 16 není užitečné proto, že v závislosti na propustnost, může být 16 transakce aktivní, podobně jako nemusí dávkování zapnutý. Proto při optimalizaci výkonu, není mít souběžných dávkování nebo mít souběžných dávkování s velikostí omezení správné služby.  
  
## <a name="batching-and-multiple-endpoints"></a>Dávkování a několik koncových bodů  
 Koncový bod se skládá z adresy a kontraktu. Může mít několik koncových bodů, které sdílejí stejnou vazbu. Je možné pro dva koncové body naslouchání identifikátor URI (Uniform Resource) nebo adresu fronty a sdílet stejnou vazbu. Pokud jsou dva koncové body čtení ze stejné fronty a zpracovaných dávkování chování se přidá do obou koncových bodů, ke konfliktu v dávce, které by mohly nastat velikosti definované. To se vyřeší implementací dávkování pomocí velikost dávky minimální zadaný v rozmezí dvou zpracovaných dávkování chování. V tomto scénáři Pokud jeden z koncových bodů neurčuje, dávkové, pak oba koncové body nepoužívejte dávkování.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
