---
title: "BlockingCollection – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: BlockingCollection, overview
ms.assetid: 987ea3d7-0ad5-4238-8b64-331ce4eb3f0b
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5e2235c1a5bbe4a39cf029059290268faa5be154
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="blockingcollection-overview"></a>BlockingCollection – přehled
<xref:System.Collections.Concurrent.BlockingCollection%601>je třída kolekce, která poskytuje následující funkce:  
  
-   Implementace vzoru producent – příjemce.  
  
-   Souběžné přidávání a odebírání položek z více vláken.  
  
-   Volitelné maximální kapacity.  
  
-   Operace vložení a odstranění tohoto bloku, pokud je kolekce prázdná, nebo úplné.  
  
-   Vložení a odebrání operací try, které nejsou blokovány nebo které jsou blokovány po zadaném časovém období.  
  
-   Zapouzdřuje jakýkoli typ kolekce, který implementuje<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>  
  
-   Zrušení s zrušení tokenů.  
  
-   Dva druhy výčet s `foreach` (`For Each` v jazyce Visual Basic):  
  
    1.  Výčet jen pro čtení.  
  
    2.  Výčet, který odebere položky, jako jsou ve výčtu.  
  
## <a name="bounding-and-blocking-support"></a>Podpora ohraničování a blokování  
 <xref:System.Collections.Concurrent.BlockingCollection%601>podporuje funkcí ohraničování a blokování. Ohraničujícího znamená můžete nastavit maximální kapacita kolekce. Ohraničujícího je důležité v některých scénářích, protože umožňuje řídit maximální velikost kolekce v paměti a vytváření vláken zabrání přesunutí příliš daleko před náročné vláken.  
  
 Více vláken nebo úkolů položky můžete přidat do kolekce souběžně, a pokud kolekce dosáhne zadané maximální kapacity, vytváření vláken se zablokuje, dokud se odebrání položky. Více příjemců může souběžně odebrat položky, a pokud kolekce prázdná, dokud producent přidá položku bude blokovat náročné vláken. Produkující vlákno může volat <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> k označení, že nebudou přidány žádné další položky. Příjemci knihovny monitorování <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> vlastnost vědět, kdy kolekce je prázdná a přidá se žádné další položky. Následující příklad ukazuje jednoduchý BlockingCollection s ohraničenou kapacitou 100. Úlohu producent přidá položky do kolekce, dokud nějaká externí podmínka platí a pak zavolá <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>. Přijímající úloha přijímá položky až <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> vlastnost na hodnotu true.  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 Úplný příklad najdete v tématu [postupy: Přidání a odebírání jednotlivých položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="timed-blocking-operations"></a>Vypršel časový limit operace blokování  
 V vypršel časový limit blokování <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operace na ohraničené kolekce, metoda pokusí přidat nebo odebrat položku. Pokud je k dispozici položka je umístěna do proměnné, která byla předána odkazem a metoda vrací hodnotu true. Metoda vrátí hodnotu false, pokud žádná položka, převzato po zadaný časový limit. Vlákno se pak můžete provést některé další užitečné práce před dalším pokusem o přístup ke kolekci. Příklad vypršel blokování přístupu, najdete v druhém příkladu v [postupy: Přidání a odebírání jednotlivých položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="cancelling-add-and-take-operations"></a>Zrušení operací přidání a odebrání  
 Přidejte a proveďte obvykle operací ve smyčce. Můžete zrušit smyčku předávání <xref:System.Threading.CancellationToken> k <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> nebo <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metoda a potom kontrolou hodnoty tokenu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost při každém opakování. Pokud je hodnota true, je na vás odpovědět požadavek na zrušení vyčistit všechny prostředky, a ukončení smyčky. Následující příklad ukazuje přetížení <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> který přijme token zrušení, a kód, který se používá:  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 Příklad toho, jak přidat podporu zrušení, najdete v druhém příkladu v [postupy: Přidání a odebírání jednotlivých položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="specifying-the-collection-type"></a>Určení typu kolekce  
 Při vytváření <xref:System.Collections.Concurrent.BlockingCollection%601>, můžete zadat jenom ohraničenou kapacitu, ale také typ kolekce pro použití. Například můžete zadat <xref:System.Collections.Concurrent.ConcurrentQueue%601> pro první v first out (FIFO) chování nebo <xref:System.Collections.Concurrent.ConcurrentStack%601> poslední chování v první out (LIFO). Můžete použít jakékoli třídy kolekce, který implementuje <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> rozhraní. Výchozí typ kolekce pro <xref:System.Collections.Concurrent.BlockingCollection%601> je <xref:System.Collections.Concurrent.ConcurrentQueue%601>. Následující příklad kódu ukazuje, jak vytvořit <xref:System.Collections.Concurrent.BlockingCollection%601> řetězců, které má kapacitu 1000 a používá <xref:System.Collections.Concurrent.ConcurrentBag%601>:  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 Další informace najdete v tématu [postupy: přidání funkcí ohraničování a blokování funkce kolekce](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md).  
  
## <a name="ienumerable-support"></a>Podpora rozhraní IEnumerable  
 <xref:System.Collections.Concurrent.BlockingCollection%601>poskytuje <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metoda, která umožní příjemcům používat `foreach` (`For Each` v [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) odebrat položky, dokud se nedokončí kolekce, což znamená, že je prázdná a přidá se žádné další položky. Další informace najdete v tématu [postupy: použití příkazu ForEach k odebrání položek v kolekci BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).  
  
## <a name="using-many-blockingcollections-as-one"></a>Použití mnoha BlockingCollection jako jeden  
 Pro scénáře, ve kterých příjemce musí vzít položky z více kolekcí současně, můžete vytvořit pole <xref:System.Collections.Concurrent.BlockingCollection%601> a používání statických metod, jako <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> , budou přidávat nebo odebírat z jakéhokoli z kolekce v pole. Pokud jedna kolekce blokuje, metoda okamžitě zkusí jinou dokud nenajde ten, který může provést operaci. Další informace najdete v tématu [postupy: použití pole blokujících kolekcí v kanálu](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Kolekce a datové struktury](../../../../docs/standard/collections/index.md)  
 [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
