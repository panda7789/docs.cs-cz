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
ms.openlocfilehash: fb01d29c723962e28d8ec4afc984cb4d6c48f9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711321"
---
# <a name="blockingcollection-overview"></a>BlockingCollection – přehled
<xref:System.Collections.Concurrent.BlockingCollection%601>je třída kolekce bezpečná pro přístup z více vláken, která poskytuje následující funkce:  
  
- Implementace vzoru výrobce a spotřebitele.  
  
- Souběžné přidávání a přijímání položek z více vláken.  
  
- Volitelná maximální kapacita.  
  
- Operace vkládání a odebrání, které blokují, když je kolekce prázdná nebo plná.  
  
- Vložení a odebrání "zkuste" operace, které neblokují nebo které blokují až do zadaného časového období.  
  
- Zapouzdřuje libovolný typ kolekce, který implementuje<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>  
  
- Zrušení s tokeny zrušení.  
  
- Dva druhy výčtu `foreach` `For Each` s ( v jazyce Visual Basic):  
  
    1. Výčet jen pro čtení.  
  
    2. Výčet, který odebere položky, jak jsou uvedeny.  
  
## <a name="bounding-and-blocking-support"></a>Podpora ohraničování a blokování  
 <xref:System.Collections.Concurrent.BlockingCollection%601>podporuje ohraničování a blokování. Ohraničující znamená, že můžete nastavit maximální kapacitu kolekce. Ohraničování je důležité v určitých scénářích, protože umožňuje řídit maximální velikost kolekce v paměti a zabraňuje vytváření podprocesů z přesunutí příliš daleko před náročné podprocesů.  
  
 Více podprocesů nebo úkolů můžete přidat položky do kolekce souběžně a pokud kolekce dosáhne své zadané maximální kapacitu, bude produkovat podprocesů blokovat, dokud je odebrána položka. Více spotřebitelů můžete odebrat položky současně a pokud kolekce stane prázdný, náročné podprocesy bude blokovat, dokud výrobce přidá položku. Produkující vlákno může <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> volat označující, že nebudou přidány žádné další položky. Spotřebitelé sledovat <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> vlastnost vědět, kdy je prázdná kolekce a žádné další položky budou přidány. Následující příklad ukazuje jednoduchý BlockingCollection s ohraničenou kapacitou 100. Úloha výrobce přidá položky do kolekce tak dlouho, dokud <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>některé externí podmínku je true a potom volání . Úloha příjemce trvá <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> položky, dokud je vlastnost true.  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 Úplný příklad najdete v [tématu Jak: Přidat a přijmout položky jednotlivě z BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="timed-blocking-operations"></a>Časované blokovací operace  
 V časované <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> blokování a operace na ohraničené kolekce, metoda se pokusí přidat nebo přijmout položku. Pokud je položka k dispozici, je umístěna do proměnné, která byla předána odkazem a metoda vrátí hodnotu true. Pokud žádná položka je načten po zadaném časovém období, metoda vrátí false. Vlákno je pak zdarma provést některé další užitečné práce před pokusem znovu získat přístup ke kolekci. Příklad časovanéblokování přístupu naleznete v druhém příkladu v [How to: Přidat a vzít položky jednotlivě z BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="cancelling-add-and-take-operations"></a>Zrušení operací přidání a převzetí  
 Přidat a přijmout operace jsou obvykle prováděny ve smyčce. Můžete zrušit smyčku předáním <xref:System.Threading.CancellationToken> <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> do <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metody nebo a potom zkontrolujte hodnotu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnosti tokenu v každé iteraci. Pokud je hodnota true, pak je na vás reagovat na požadavek na zrušení vyčištěním všech prostředků a ukončení smyčky. Následující příklad ukazuje <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> přetížení, které trvá zrušení tokena a kód, který jej používá:  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 Příklad, jak přidat podporu zrušení, naleznete v druhém příkladu v [How to: Add and Take Items Jednotlivě z BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="specifying-the-collection-type"></a>Určení typu kolekce  
 Při vytváření <xref:System.Collections.Concurrent.BlockingCollection%601>můžete zadat nejen ohraničenou kapacitu, ale také typ kolekce, která se má použít. Můžete například zadat <xref:System.Collections.Concurrent.ConcurrentQueue%601> chování pro první in-first out (FIFO) nebo <xref:System.Collections.Concurrent.ConcurrentStack%601> pro chování poslední in-first out (LIFO). Můžete použít libovolnou třídu <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> kolekce, která implementuje rozhraní. Výchozí typ kolekce <xref:System.Collections.Concurrent.BlockingCollection%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601>pro je . Následující příklad kódu ukazuje, <xref:System.Collections.Concurrent.BlockingCollection%601> jak vytvořit řetězce, které má kapacitu 1000 a používá <xref:System.Collections.Concurrent.ConcurrentBag%601>:  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 Další informace naleznete v [tématu How to: Add Bounding and Blocking Functionality to a Collection](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md).  
  
## <a name="ienumerable-support"></a>Podpora iEnumerable  
 <xref:System.Collections.Concurrent.BlockingCollection%601>poskytuje <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metodu, která `foreach` umožňuje`For Each` spotřebitelům použít (v jazyce Visual Basic) odebrat položky, dokud není dokončena kolekce, což znamená, že je prázdný a žádné další položky budou přidány. Další informace naleznete v [tématu How to: Use ForEach to Remove Items in a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).  
  
## <a name="using-many-blockingcollections-as-one"></a>Použití mnoho BlockingCollections jako jeden  
 Pro scénáře, ve kterých spotřebitel potřebuje přijmout položky z více <xref:System.Collections.Concurrent.BlockingCollection%601> kolekcí současně, můžete <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> vytvořit pole a použít statické metody, jako je například a které budou přidávat nebo trvat z některé z kolekcí v poli. Pokud jedna kolekce je blokování, metoda okamžitě pokusí jiný, dokud nenajde ten, který může provést operaci. Další informace naleznete v [tématu How to: Use Arrays of Blocking Collections in a Pipeline](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekce a datové struktury](../../../../docs/standard/collections/index.md)
- [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
