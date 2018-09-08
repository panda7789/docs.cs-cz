---
title: Vlastní dělicí metody pro PLINQ a TPL
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, partitioners
ms.assetid: 96153688-9a01-47c4-8430-909cee9a2887
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b4e835d01ac0e1249a9a4c71a3a9db25082fec1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44214079"
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>Vlastní dělicí metody pro PLINQ a TPL
Pro paralelní zpracování operace na zdroji dat, jedním ze základních kroků je *oddílu* zdroje do několika oddílů, které může přistupovat souběžně více vláken. PLINQ a Task Parallel Library (TPL) poskytují výchozí rozdělovače, které pracují transparentně při psaní paralelního dotazu nebo <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky. Pro pokročilejší scénáře můžete zařadit vlastní dělicí metody.  
  
## <a name="kinds-of-partitioning"></a>Druhy dělení  
 Při vytváření oddílů zdroji dat mnoha způsoby. V nejúčinnější přístupy více vláken spolupracují s cílem procesu původní zdrojové sekvence, nikoli fyzické oddělení zdroje do více dílčích sekvencí. Pro pole a další indexovat zdroje <xref:System.Collections.IList> kolekce, kde délka je znám předem, *dělení rozsah* je nejjednodušší druh dělení. Každé vlákno přijímá jedinečný počáteční a koncové indexy, tak, aby jeho rozsah zdroje může zpracovat bez přepsání nebo přepsání z žádného vlákna. Pouze režie spojená s rozsah dělení je počáteční pracovní vytváření rozsahů; Po tomto není nutná žádná další synchronizace. Tak dlouho, dokud zatížení je rozděleno rovnoměrně, je proto poskytují dobrý výkon. Nevýhodou rozsah dělení je, že pokud se jedno vlákno brzy dokončí, nemůže pomoct ostatní vlákna dokončí svou práci.  
  
 Propojené seznamy nebo další kolekce, jejichž délka není znám, můžete použít *dělení bloků*. Při dělení bloků dat, každý vlákna nebo úlohy v paralelní smyčce nebo dotaz využívá některé zdrojové prvky v jednom bloku, zpracovává je a potom se vrátí zpět k načtení dalších prvků. Dělicí zajistí, že všechny prvky mají distribuovat a, že neexistují žádné duplicity. Blok může být libovolné velikosti. Například dělicí metodou, která je znázorněna v [postupy: implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md) vytvoří bloky dat, které obsahují pouze jeden element. Za předpokladu, bloky dat nejsou příliš velké, tento druh dělení je ze své podstaty Vyrovnávání zatížení protože přiřazení prvky na vláknech není předem určit. Dělicí ale účtovat režii synchronizace pokaždé, když vlákno je potřeba získat jiného bloku. Množství synchronizace vzniklé v těchto případech je nepřímo úměrná velikosti bloky dat.  
  
 Obecně platí rozsah dělení probíhá pouze rychleji, pokud čas spuštění delegáta je malé a střední, zdroj má velký počet prvků a celkovou práci každý oddíl je zhruba ekvivalentní. Vytváření oddílů datových dávek tedy obecně rychlejší ve většině případů. U zdrojů s malý počet elementů nebo delší dobu provádění pro delegáta pak výkon bloků dat a vytváření oddílů rozsah je o stejné.  
  
 Dělicí metody TPL také podporují dynamické počet oddílů. To znamená, že můžete například vytvořit oddíly v běhu, když <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky vytvoří nový úkol. Tato funkce umožňuje rozdělovač škálovat společně s smyčky, samotného. Dynamické dělicí metody jsou také ze své podstaty Vyrovnávání zatížení. Při vytváření vlastního rozdělovače, musí podporovat dynamické dělení, abyste se lze použít z <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky.  
  
### <a name="configuring-load-balancing-partitioners-for-plinq"></a>Konfigurace rozložení zátěže dělicí metody pro PLINQ  
 Některá přetížení <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metody umožňují vytvořit dělicí metody pro pole nebo <xref:System.Collections.IList> zdroje a určit, zda by měl pokusit o vyrovnávat zatížení mezi vlákna. Když dělicí je konfigurován pro vyrovnávání zatížení, dělení bloků dat se používá, a jsou prvky předávána do jednotlivých oddílů v menších dávkách jsou požadované. Tento přístup pomáhá zajistit, že všechny oddíly mají prvky ke zpracování celé smyčka until nebo dokončení dotazu. Další přetížení je možné poskytovat žádné služby Vyrovnávání zatížení dělení <xref:System.Collections.IEnumerable> zdroje.  
  
 Obecně platí Vyrovnávání zatížení vyžaduje oddíly pro žádosti o prvky poměrně často dělicí. Naopak dělicí metodou, která nepodporuje statické dělení můžete přiřadit elementy každý rozdělovač najednou pomocí rozsah nebo blok dělení. To vyžaduje, aby menší nároky na než Vyrovnávání zatížení, ale může trvat delší dobu spuštění, pokud jedno vlákno končí mnohem více práce než ostatní. Ve výchozím nastavení je předána IList nebo pole, PLINQ vždy používá rozsah dělení bez vyrovnávání zatížení. Chcete-li povolit Vyrovnávání zatížení pro PLINQ, použijte `Partitioner.Create` způsob, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
 [!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]  
  
 Nejlepší způsob, jak zjistit, jestli použít zatížení vyrovnávání v jakékoli situaci je můžete experimentovat a změřit, jak dlouho trvá, než operace dokončete podle reprezentativní zatížením a konfigurací počítače. Například statické dělení může poskytnout výrazné zrychlení v počítači více jader, který má pouze několik jader, ale může způsobit zpomalení na počítačích, které mají relativně mnoha jádrech.  
  
 V následující tabulce jsou uvedeny dostupné přetížení <xref:System.Collections.Concurrent.Partitioner.Create%2A> metody. Tato dělicí metody nejsou omezeny na použití pouze pomocí jazyka PLINQ nebo <xref:System.Threading.Tasks.Task>. Můžete také používají se všechny vlastní paralelní konstrukce.  
  
|přetížení|Použití vyrovnávání zatížení|  
|--------------|-------------------------|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Vždy|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Když je zadaný logický argument jako true|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Když je zadaný logický argument jako true|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|Nikdy|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|Nikdy|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|Nikdy|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|Nikdy|  
  
### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Konfigurace statický rozsah dělicí metody pro paralelní ForEach  
 V <xref:System.Threading.Tasks.Parallel.For%2A> smyčky, tělo smyčky je k dispozici na metodu jako delegát. Náklady na vyvolání tohoto delegáta je stejné jako volání virtuální metody. V některých případech může být dostatečně malá, že náklady na volání delegáta při každé iteraci smyčky stane významné tělo paralelní smyčky. V takových případech můžete použít jednu z <xref:System.Collections.Concurrent.Partitioner.Create%2A> přetížení k vytvoření <xref:System.Collections.Generic.IEnumerable%601> rozsah oddílů přes zdrojové elementy. Pak můžete předat tuto kolekci rozsahy <xref:System.Threading.Tasks.Parallel.ForEach%2A> metoda, jehož subjekt se skládá z běžný `for` smyčky. Výhodou tohoto přístupu je, že náklady na volání delegáta vzniknou pouze jednou na rozsah, nikoli po jeden element. Následující příklad ukazuje základní vzor.  
  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Každé vlákno ve smyčce obdrží vlastní <xref:System.Tuple%602> , která obsahuje počáteční a koncové hodnoty indexu v zadaném rozsahu dílčí. Vnitřní `for` smyčky používá `fromInclusive` a `toExclusive` hodnoty pole ve smyčce nebo <xref:System.Collections.IList> přímo.  
  
 Jeden z <xref:System.Collections.Concurrent.Partitioner.Create%2A> přetížení umožňuje zadat velikost oddíly a počet oddílů. Toto přetížení lze použít ve scénářích, kde je tak malý, dokonce i jediný virtuální metodu volání na prvek má znatelnému dopadu na výkon, práce na prvek.  
  
## <a name="custom-partitioners"></a>Vlastní dělicí metody  
 V některých případech může být vhodné nebo dokonce musí implementovat vlastní dělicí metody. Například může mít vlastní třídu kolekce, která můžete dělit efektivnější než výchozí rozdělovače můžete na základě vašich znalostí interní struktury třídy. Nebo můžete chtít vytvořit rozsah oddíly na základě vašich znalostí o jak dlouho bude trvat prvky procesu na různých místech ve zdrojové kolekci různých velikostí.  
  
 Chcete-li vytvořit základní vlastního rozdělovače, odvoďte třídu z <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> a přepsat virtuální metody, jak je popsáno v následující tabulce.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Tato metoda se volá jednou pomocí hlavního vlákna a vrátí IList(IEnumerator(TSource)). Každý pracovní podproces smyčky nebo dotazu můžete volat `GetEnumerator` v seznamu můžete načíst <xref:System.Collections.Generic.IEnumerator%601> prostřednictvím samostatného oddílu.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Vrátí `true` Pokud implementujete <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, v opačném případě `false`.|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|Pokud <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> je `true`, tuto metodu lze volat volitelně místo <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Pokud musí být výsledky řazení nebo vyžadujete indexovaný přístup do prvků, pak jsou odvozeny z <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> a přepsat její virtuální metody, jak je popsáno v následující tabulce.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Tato metoda se volá jednou pomocí hlavního vlákna a vrátí `IList(IEnumerator(TSource))`. Každý pracovní podproces smyčky nebo dotazu můžete volat `GetEnumerator` v seznamu můžete načíst <xref:System.Collections.Generic.IEnumerator%601> prostřednictvím samostatného oddílu.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Vrátí `true` Pokud implementujete <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>; jinak hodnota false.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|Obvykle to jen volá <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|Pokud <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> je `true`, tuto metodu lze volat volitelně místo <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Následující tabulka obsahuje další podrobnosti o tři druhy implementace dělicí metody vyrovnávání zatížení <xref:System.Collections.Concurrent.OrderablePartitioner%601> třídy.  
  
|Metoda/vlastnost|IList / pole bez vyrovnávání zatížení|IList nebo pole s vyrovnáváním zatížení|IEnumerable|  
|----------------------|-------------------------------------------|----------------------------------------|-----------------|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Používá rozsah dělení|Používá blok dělení optimalizovaná pro seznamy pro partitionCount zadaný|Používá blok dělení vytvořením statického počtu oddílů.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|Nepodporované vyvolá výjimka|Používá blok dělení optimalizované pro seznamy a dynamických oddílů|Používá blok dělení tak, že vytvoříte dynamické počet oddílů.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|Vrátí `true`|Vrátí `true`|Vrátí `true`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|Vrátí `true`|Vrátí `false`|Vrátí `false`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|Vrátí `true`|Vrátí `true`|Vrátí `true`|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Vrátí `false`|Vrátí `true`|Vrátí `true`|  
  
### <a name="dynamic-partitions"></a>Dynamických oddílů  
 Pokud máte v úmyslu dělicí metody pro použití v <xref:System.Threading.Tasks.Parallel.ForEach%2A> metodu, musí být schopni vracet dynamické počet oddílů. To znamená, že dělicí můžete zadat enumerátor pro nového oddílu na vyžádání kdykoli během provádění smyčky. V podstatě pokaždé, když smyčky přidá nový paralelních úkolů, požadavků nový oddíl pro tuto úlohu. Pokud potřebujete data, která mají být uspořádatelná, pak jsou odvozeny z <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> tak, aby každá položka v každém oddílu je přiřazen jedinečný index.  
  
 Další informace a příklad najdete v tématu [postupy: implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
### <a name="contract-for-partitioners"></a>Kontrakt pro dělicí metody  
 Při implementaci vlastního rozdělovače, postupujte podle následujících pokynů k zajištění správné interakci s PLINQ a <xref:System.Threading.Tasks.Parallel.ForEach%2A> v TPL:  
  
-   Pokud <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> je volána s argumentem nula nebo pro `partitionsCount`, throw <xref:System.ArgumentOutOfRangeException>. I když PLINQ a TPL se nikdy předat `partitionCount` rovná 0, přesto doporučujeme, aby je pomáhalo chránit před možnost.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> a <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> by měla vždy vrátit `partitionsCount` počet oddílů. Pokud dělicí vyčerpá data a nelze vytvořit libovolný počet oddílů, jak si vyžádal, metoda by měla vrátit prázdný výčet pro každý zbývající oddílů. V opačném případě se vyvolá PLINQ a TPL <xref:System.InvalidOperationException>.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>, <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, a <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> nikdy by měla vrátit `null` (`Nothing` v jazyce Visual Basic). V takovém případě PLINQ / TPL vyvolá výjimku <xref:System.InvalidOperationException>.  
  
-   Metody, které vracejí oddíly by měla vždy vrátit oddíly, které můžete plně a jednoznačně zobrazit výčet zdroj dat. Měla by existovat žádné duplicity ve zdroji dat nebo přeskočené položky není-li konkrétně vyžadováno záměrné dělicí. Pokud se toto pravidlo nedodrží, může zamíchal pořadí výstupu.  
  
-   Následující metody getter logická musí vždy přesně vrátit následující hodnoty tak, aby není zamíchal pořadí výstupu:  
  
    -   `KeysOrderedInEachPartition`: Každý oddíl vrátí elementy rostoucími klíče indexy.  
  
    -   `KeysOrderedAcrossPartitions`: Pro všechny oddíly, které jsou vráceny klíče indexy v oddílu *můžu* jsou vyšší než klíče indexy v oddílu *můžu*-1.  
  
    -   `KeysNormalized`: Všechny klíče indexy monotónně roste bez mezer, od nuly.  
  
-   Všechny indexy musí být jedinečný. Možná duplicitní indexy. Pokud se toto pravidlo nedodrží, může zamíchal pořadí výstupu.  
  
-   Všechny indexy musí být nezáporná. Pokud se toto pravidlo nedodrží, PLINQ a TPL může vyvolat výjimky.  
  
## <a name="see-also"></a>Viz také:

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
- [Postupy: Implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)  
- [Postupy: Implementace rozdělovače pro statické dělení](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
