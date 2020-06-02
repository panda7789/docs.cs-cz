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
ms.openlocfilehash: 708ab9dc8df2ee3128036ffc71e9abc51a56e33b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287910"
---
# <a name="blockingcollection-overview"></a>BlockingCollection – přehled
<xref:System.Collections.Concurrent.BlockingCollection%601>je třída kolekce bezpečná pro přístup z více vláken, která poskytuje následující funkce:  
  
- Implementace vzoru producent-příjemce.  
  
- Souběžné přidávání a přebírání položek z více vláken.  
  
- Volitelná maximální kapacita  
  
- Operace vložení a odebrání, které blokují, když je kolekce prázdná nebo plná  
  
- Vložení a odebrání operací "Try", které neblokují nebo zablokují do zadaného časového období.  
  
- Zapouzdřuje libovolný typ kolekce, který implementuje<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>  
  
- Zrušení s tokeny zrušení  
  
- Dva druhy výčtu s `foreach` ( `For Each` v Visual Basic):  
  
    1. Výčet jen pro čtení.  
  
    2. Výčet, který odebere položky při vytváření výčtu.  
  
## <a name="bounding-and-blocking-support"></a>Podpora ohraničování a blokování  
 <xref:System.Collections.Concurrent.BlockingCollection%601>podporuje ohraničování a blokování. Ohraničování znamená, že můžete nastavit maximální kapacitu kolekce. Ohraničování je důležité v určitých situacích, protože umožňuje řídit maximální velikost kolekce v paměti a brání v tom, aby vyráběná vlákna byla přetažena příliš daleko před náročnými vlákny.  
  
 Více vláken nebo úkolů může do kolekce současně přidávat položky a pokud kolekce dosáhne zadané maximální kapacity, výrobní vlákna zablokuje, dokud nebude položka odebrána. Více příjemců může odebírat položky souběžně, a pokud je kolekce prázdná, budou spotřebovávat vlákna zablokovat, dokud producent nepřidá položku. Produkující vlákno může zavolat <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> , aby označovalo, že nebudou přidány žádné další položky. Příjemci monitorují <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> vlastnost, aby věděli, že je kolekce prázdná a nepřidaly se žádné další položky. Následující příklad ukazuje jednoduchou Blokujícícollection s ohraničenou kapacitou 100. Úkol výrobce přidá položky do kolekce, pokud je některá externí podmínka pravdivá a pak volá <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> . Úkol příjemce přijímá položky, dokud vlastnost nevrátí <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> hodnotu true.  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 Úplný příklad naleznete v tématu [How to: Add and přebírat Items from a BlockingCollection](how-to-add-and-take-items.md).  
  
## <a name="timed-blocking-operations"></a>Časované operace blokování  
 V případě časovaného blokování <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operací u ohraničených kolekcí se metoda pokusí přidat nebo převzít položku. Pokud je položka k dispozici, je umístěna do proměnné, která byla předána odkazem, a metoda vrátí hodnotu true. Pokud po zadaném časovém limitu není načtena žádná položka, vrátí metoda hodnotu false. Vlákno je pak zdarma, aby před dalším pokusem o přístup k této kolekci provede nějakou další užitečnou práci. Příklad časovaného blokování přístupu naleznete v druhém příkladu v tématu [Postupy: Přidání a převzetí položek jednotlivě z blokující kolekce](how-to-add-and-take-items.md).  
  
## <a name="cancelling-add-and-take-operations"></a>Rušení přidání a provedení operací  
 Operace přidání a provedení operací se obvykle provádějí ve smyčce. Smyčku můžete zrušit předáním do <xref:System.Threading.CancellationToken> <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metody nebo a následnou kontrolou hodnoty vlastnosti tokenu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> u každé iterace. Pokud je hodnota true, pak je až na to, abyste odpověděli na žádost o zrušení vyčištěním všech prostředků a ukončením smyčky. Následující příklad ukazuje přetížení <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> , které přijímá token zrušení a kód, který ho používá:  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 Příklad, jak přidat podporu zrušení, naleznete v druhém příkladu v tématu [Postupy: Přidání a převzetí položek jednotlivě z blokující kolekce](how-to-add-and-take-items.md).  
  
## <a name="specifying-the-collection-type"></a>Určení typu kolekce  
 Když vytvoříte <xref:System.Collections.Concurrent.BlockingCollection%601> , můžete zadat nejen ohraničenou kapacitu, ale také typ kolekce, která se má použít. Můžete například určit, že se má použít jako <xref:System.Collections.Concurrent.ConcurrentQueue%601> první (in-first out), nebo <xref:System.Collections.Concurrent.ConcurrentStack%601> pro chování Last in-first out (LIFO). Můžete použít libovolnou třídu kolekce, která implementuje <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> rozhraní. Výchozí typ kolekce pro <xref:System.Collections.Concurrent.BlockingCollection%601> je <xref:System.Collections.Concurrent.ConcurrentQueue%601> . Následující příklad kódu ukazuje, jak vytvořit řetězce s <xref:System.Collections.Concurrent.BlockingCollection%601> kapacitou 1000 a používá <xref:System.Collections.Concurrent.ConcurrentBag%601> :  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 Další informace najdete v tématu [Postup: Přidání ohraničování a blokování funkcí do kolekce](how-to-add-bounding-and-blocking.md).  
  
## <a name="ienumerable-support"></a>Podpora IEnumerable  
 <xref:System.Collections.Concurrent.BlockingCollection%601>poskytuje <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metodu, která umožňuje příjemcům použít `foreach` ( `For Each` v Visual Basic) k odebrání položek do doby, než je kolekce dokončena, což znamená, že je prázdná a nebudou přidány žádné další položky. Další informace naleznete v tématu [Postupy: použití příkazu foreach k odebrání položek v blokujícícollection](how-to-use-foreach-to-remove.md).  
  
## <a name="using-many-blockingcollections-as-one"></a>Použití mnoha BlockingCollections jako jednoho  
 Pro scénáře, ve kterých musí příjemce převzít položky z více kolekcí současně, můžete vytvořit pole <xref:System.Collections.Concurrent.BlockingCollection%601> a použít statické metody, jako například <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> , které budou přidány nebo přebírat ze všech kolekcí v poli. Pokud je jedna kolekce blokována, metoda se okamžitě pokusí o další, dokud nenajde tu, která může provést operaci. Další informace najdete v tématu [How to: use Arrays Blocking Collections in a Pipeline](how-to-use-arrays-of-blockingcollections.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekce a datové struktury](../index.md)
- [Kolekce bezpečné pro přístup z více vláken](index.md)
