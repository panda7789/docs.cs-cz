---
title: BlockingCollection – přehled
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BlockingCollection, overview
ms.assetid: 987ea3d7-0ad5-4238-8b64-331ce4eb3f0b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 257435516b38d0e4389b7feceba68371bcc8f90e
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2018
ms.locfileid: "46711143"
---
# <a name="blockingcollection-overview"></a>BlockingCollection – přehled
<xref:System.Collections.Concurrent.BlockingCollection%601> je třídy kolekce bezpečné pro vlákna, která poskytuje následující funkce:  
  
-   Implementace vzoru producent – příjemce.  
  
-   Souběžné přidávání a odebírání položek z více vláken.  
  
-   Volitelné maximální kapacity.  
  
-   Operace vložení a odstranění, které blokovat, pokud kolekce je prázdná nebo úplná.  
  
-   Vkládání a odstranění "akci" operace, které neblokují nebo které jsou blokovány až po zadaném časovém období.  
  
-   Zapouzdřuje jakýkoli typ kolekce, která implementuje <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>  
  
-   Zrušení s tokeny zrušení.  
  
-   Dva druhy výčet s `foreach` (`For Each` v jazyce Visual Basic):  
  
    1.  Výčet jen pro čtení.  
  
    2.  Výčet, který odebere položky, jako jsou ve výčtu.  
  
## <a name="bounding-and-blocking-support"></a>Podpora ohraničování a blokování  
 <xref:System.Collections.Concurrent.BlockingCollection%601> podporuje funkcí ohraničování a blokování. Ohraničující znamená, že můžete nastavit maximální kapacitu kolekce. Ohraničující je důležité v některých scénářích, protože umožňuje řídit maximální velikost kolekce v paměti a vytváření vláken zabraňuje přesunutí příliš daleko náskok před používání vláken.  
  
 Více vláken nebo úloh můžete přidat položky do kolekce souběžně, a pokud kolekce dosáhne zadané maximální kapacity, vytváření vláken bude blokovat, dokud je položka odebrána. Více příjemců odebrání položek současně, a pokud kolekce prázdná, používání vláken bude blokovat, dokud producent přidá položku. Vytváření vlákno může volat <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> k označení, že nebudou přidány žádné další položky. Monitorování spotřebitelů <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> vlastnost vědět, pokud kolekce je prázdná a budou přidány žádné další položky. Následující příklad ukazuje jednoduchý BlockingCollection s ohraničenou kapacitu 100. Výrobce úkol přidá položky do kolekce tak dlouho, dokud některé externí podmínka je PRAVDA a pak zavolá <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>. Příjemce úkolu trvá až do položky <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> vlastnost má hodnotu true.  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 Kompletní příklad naleznete v tématu [postupy: Přidání a jednotlivě trvat položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="timed-blocking-operations"></a>Vypršel časový limit operace blokování  
 V vypršel časový limit blokování <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operace na ohraničené kolekce, metoda se pokusí přidat nebo odebrat položky. Pokud je k dispozici položka přejde do proměnné, která byla předána odkazem a metoda vrátí hodnotu true. Metoda vrátí hodnotu false, pokud žádná položka nenačtete po zadaný časový limit. Vlákno je potom můžete provést některé další užitečné práce než to zkusíte znovu získat přístup ke kolekci. Příklad vypršel časový limit blokování přístupu, najdete ve druhém příkladu v [postupy: Přidání a jednotlivě trvat položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="cancelling-add-and-take-operations"></a>Rušení operací přidání a odebrání  
 Přidat a provést operace se obvykle provádí ve smyčce. Zrušíte smyčku předáním <xref:System.Threading.CancellationToken> k <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> nebo <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metodu a poté kontrolu hodnoty tokenu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost při každé iteraci. Pokud je hodnota true, je jenom na vás tak, požadavek na zrušení čištění jakýchkoli prostředků a ukončení smyčky. Následující příklad ukazuje přetížení <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> , který přijme token zrušení, a kód, který se používá:  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 Příklad toho, jak přidat podporu zrušení, najdete ve druhém příkladu v [postupy: Přidání a jednotlivě trvat položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="specifying-the-collection-type"></a>Zadání typu kolekce  
 Když vytvoříte <xref:System.Collections.Concurrent.BlockingCollection%601>, můžete zadat pouze omezená kapacitou, ale také typ kolekce pro použití. Například můžete zadat <xref:System.Collections.Concurrent.ConcurrentQueue%601> pro první v prvním out (FIFO) chování, nebo <xref:System.Collections.Concurrent.ConcurrentStack%601> pro poslední chování v first-out (LIFO). Můžete použít jakékoli třídy kolekce, která implementuje <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> rozhraní. Výchozí typ kolekce pro <xref:System.Collections.Concurrent.BlockingCollection%601> je <xref:System.Collections.Concurrent.ConcurrentQueue%601>. Následující příklad kódu ukazuje, jak vytvořit <xref:System.Collections.Concurrent.BlockingCollection%601> řetězců, které má kapacitu 1000 a používá <xref:System.Collections.Concurrent.ConcurrentBag%601>:  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 Další informace najdete v tématu [postupy: přidání funkcí ohraničování a blokování funkce kolekce](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md).  
  
## <a name="ienumerable-support"></a>Podpora IEnumerable  
 <xref:System.Collections.Concurrent.BlockingCollection%601> poskytuje <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metodu, která umožňuje uživatelům používat `foreach` (`For Each` v jazyce Visual Basic) k odebrání položek, dokud se nedokončí kolekce, což znamená, že je prázdný a nebudou přidány žádné další položky. Další informace najdete v tématu [postupy: použití příkazu ForEach k odebrání položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).  
  
## <a name="using-many-blockingcollections-as-one"></a>Použití mnoha BlockingCollection jako jeden  
 Pro scénáře, ve kterých je potřeba příjemce současně provést položky z několika kolekcí, můžete vytvářet pole <xref:System.Collections.Concurrent.BlockingCollection%601> a používají statické metody, jako <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> , který bude přidávat nebo odebírat z některého z kolekce v pole. Pokud je blokování jednu kolekci, metodu okamžitě pokusí jiného dokud nenajde ten, který můžete provádět operace. Další informace najdete v tématu [postupy: použití polí blokující kolekce v kanálu](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [Kolekce a datové struktury](../../../../docs/standard/collections/index.md)  
- [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
