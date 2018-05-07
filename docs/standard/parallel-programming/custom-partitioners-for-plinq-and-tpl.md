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
ms.openlocfilehash: 0868ce76f82ed0575154744d9ab02814a0bd990a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>Vlastní dělicí metody pro PLINQ a TPL
Učinit paralelní operace pro zdroj dat, jedním z nezbytné kroky je *oddílu* zdroje do více oddílů, které dostanete souběžně několik vláken. PLINQ a Task Parallel Library (TPL) zadejte výchozí dělicí metody, které fungují transparentně při psaní paralelního dotazu nebo <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky. Pro pokročilejší scénáře můžete zařadit vlastní dělicí metody.  
  
## <a name="kinds-of-partitioning"></a>Druhy dělení  
 Při vytváření oddílů zdroj dat mnoha způsoby. V nejúčinnější přístupy více vláken spolupracují s cílem procesu původní zdrojové sekvence, nikoli fyzicky rozdělit zdroje do více dílčích sekvencí. Pro pole a dalších indexovat zdroje <xref:System.Collections.IList> kolekce, kde je délka předem, známo *rozsah dělení* je nejjednodušší druh rozdělení do oddílů. Každé vlákno obdrží jedinečný počáteční a koncové indexy, tak, aby jeho rozsah zdroje může zpracovat bez přepsání nebo přepsáním jiné vlákno. Pouze režie spojená s dělení rozsah je počáteční práci při vytváření oblastí; Po, není nutná žádná další synchronizace. Tak dlouho, dokud zatížení je rozděleno rovnoměrně, je proto poskytují dobrý výkon. Rozsah oddíly tu nevýhodu, že pokud jedno vlákno skončí již v rané fázi, nemůže pomoct jiná vlákna dokončit práci.  
  
 Propojené seznamy nebo jiné kolekce, jejichž délka není znám, můžete použít *bloku dělení*. V bloku oddílů, každé vlákno nebo úloha v paralelní smyčky nebo dotaz, využívá některé počet zdrojové elementy v jednom bloku, je zpracuje a pak zpátky na další prvky načíst. Dělicí metody zajistí, že všechny elementy distribuované a že neexistují žádné duplicity. Bloku dat může mít libovolnou velikost. Například dělicí metody, která je znázorněna v [postupy: implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md) vytvoří bloky dat, které obsahují pouze jeden prvek. Také bloky dat nejsou moc velká, je tento druh dělení ze své podstaty Vyrovnávání zatížení protože přiřazení elementů vláken není předem určené. Ale dělicí metody nesnižuje režii synchronizace pokaždé, když vlákno potřebuje získat jiného bloku. Množství synchronizace vám účtovány v těchto případech je nepřímo úměrná velikosti bloky dat.  
  
 Obecně platí vytváření oddílů rozsah je pouze rychlejší pokud doba provádění delegáta je malé a střední, zdroj má velký počet elementů a celkový objem práce každý oddíl je zhruba odpovídá. Rozdělení do oddílů bloku je proto obecně rychlejší ve většině případů. Na zdroje s malý počet elementů nebo delší doby provádění pro delegáta pak výkon bloku a rozdělení do oddílů rozsah je o stejné.  
  
 Dělicí metody TPL také podporují dynamické počet oddílů. To znamená, že můžete například vytvořit oddíly na průběžně, když <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky vytvoří novou úlohu. Tato funkce umožňuje dělicí metody škálování společně s smyčky sám sebe. Dynamické dělicí metody jsou také ze své podstaty Vyrovnávání zatížení. Když vytvoříte vlastní dělicí metody, musí podporovat dynamické rozdělení být použití z <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky.  
  
### <a name="configuring-load-balancing-partitioners-for-plinq"></a>Konfigurace služby dělicí metody pro PLINQ Vyrovnávání zatížení  
 Některé přetížení <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metoda umožňují vytvářet dělicí metody pro pole nebo <xref:System.Collections.IList> zdroje a určete, jestli mají pokusit o k vyrovnávání zátěže mezi vláken. Pokud dělicí metody je nakonfigurovaná pro vyrovnávání zatížení, vytváření oddílů bloku se používá a elementy jsou předávána každý oddíl malé bloky budou požadované. Tento přístup pomáhá zajistit, aby všechny oddíly mají prvky zpracovat až celý smyčky a dokončení dotazu. Další přetížení slouží k poskytování Vyrovnávání zatížení dělení všech <xref:System.Collections.IEnumerable> zdroje.  
  
 Obecně platí Vyrovnávání zatížení vyžaduje oddíly, které mají požádat elementy poměrně často dělicí metody. Naopak dělicí metody, která provádí statické dělení můžete přiřadit elementy každý dělicí metody všechny najednou pomocí rozsah nebo blok dělení. To vyžaduje menší nároky na než Vyrovnávání zatížení, ale může trvat déle, než se spustit, pokud jedno vlákno končí výrazně další práci než jiné. Ve výchozím nastavení při je předán objekt IList nebo pole, PLINQ vždy používá rozsah dělení bez vyrovnávání zatížení. Pokud chcete povolit Vyrovnávání zatížení pro PLINQ, použijte `Partitioner.Create` metoda, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
 [!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]  
  
 Nejlepší způsob, jak určit, zda použít zatížení vyrovnávání v jakékoli této situaci je experiment a měří, jak dlouho trvalo na dokončení pod reprezentativní zatížení a konfiguracích počítačů operací. Například statické dělení může poskytovat významné zrychlení vícejádrové počítače, který má jenom několik jader, ale může způsobit zpomalení na počítačích, které mají relativně velký počet jader.  
  
 V následující tabulce jsou uvedeny dostupné přetížení <xref:System.Collections.Concurrent.Partitioner.Create%2A> metoda. Tyto dělicí metody nejsou omezeny pouze pomocí PLINQ nebo <xref:System.Threading.Tasks.Task>. Můžete také používají se všechny vlastní paralelní konstrukce.  
  
|Přetížení|Používá Vyrovnávání zatížení|  
|--------------|-------------------------|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Vždy|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Pokud je zadán parametr Boolean argument jako true|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Pokud je zadán parametr Boolean argument jako true|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|Nikdy|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|Nikdy|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|Nikdy|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|Nikdy|  
  
### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Konfiguraci rozsahu statické dělicí metody pro Parallel.ForEach  
 V <xref:System.Threading.Tasks.Parallel.For%2A> smyčky, do těla smyčky je poskytnutá metodě jako delegáta. Náklady na vyvolání tento delegát je o stejný jako volání virtuální metody. V některých případech může být dostatečně malé, že náklady na každé iteraci smyčky volání delegáta se významné text paralelní smyčky. V takových situacích můžete použít jednu z <xref:System.Collections.Concurrent.Partitioner.Create%2A> přetížení pro vytvoření <xref:System.Collections.Generic.IEnumerable%601> rozsah oddílů přes zdrojové elementy. Pak můžete předat tuto kolekci do rozsahů <xref:System.Threading.Tasks.Parallel.ForEach%2A> metoda, jehož subjekt se skládá z běžný `for` smyčky. Výhodou tohoto přístupu je, že delegáta volání náklady nabíhají pouze jednou za rozsahu, nikoli jednou za element. Následující příklad ukazuje základní vzor.  
  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Každé vlákno ve smyčce obdrží vlastní <xref:System.Tuple%602> obsahující počáteční a koncové hodnoty indexu v zadaném rozsahu dílčí. Vnitřní `for` cykly používá `fromInclusive` a `toExclusive` hodnoty do pole opakovací smyčku nebo <xref:System.Collections.IList> přímo.  
  
 Jeden z <xref:System.Collections.Concurrent.Partitioner.Create%2A> přetížení slouží k určení velikosti oddíly a počet oddílů. Toto přetížení lze použít ve scénářích kde je práce za element nízkou tak, že volání i jeden virtuální metody za element má znatelný dopad na výkon.  
  
## <a name="custom-partitioners"></a>Vlastní dělicí metody  
 V některých případech může být smysl nebo i vyžadují k implementaci vlastní dělicí metody. Například můžete mít třídu vlastní kolekce, která může efektivnější než výchozí dělicí metody můžete podle vašich znalostí interní třídy oddílu. Nebo můžete chtít vytvořit rozsah oddílů různou velikost podle znalosti o tom, jak dlouho bude trvat proces elementy v různých umístěních ve zdrojové kolekci.  
  
 Pokud chcete vytvořit základní vlastní dělicí metody, odvození třídy z <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> a přepsat virtuální metody, jak je popsáno v následující tabulce.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Tato metoda volá se jednou prostřednictvím hlavního vlákna a vrátí IList(IEnumerator(TSource)). Každý pracovní vlákno ve smyčce nebo dotazu můžete volat `GetEnumerator` v seznamu můžete načíst <xref:System.Collections.Generic.IEnumerator%601> přes odlišné oddílu.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Vrátí `true` Pokud implementujete <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, jinak `false`.|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|Pokud <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> je `true`, tuto metodu lze volat volitelně místo <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Pokud výsledky musí být řazení nebo vyžadovat indexovaný přístup do elementy, pak odvozena od <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> a přepsat její virtuální metody, jak je popsáno v následující tabulce.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Tato metoda volá se jednou prostřednictvím hlavního vlákna a vrátí `IList(IEnumerator(TSource))`. Každý pracovní vlákno ve smyčce nebo dotazu můžete volat `GetEnumerator` v seznamu můžete načíst <xref:System.Collections.Generic.IEnumerator%601> přes odlišné oddílu.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Vrátí `true` Pokud implementujete <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>, jinak hodnota false.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|Obvykle to právě volá <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|Pokud <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> je `true`, tuto metodu lze volat volitelně místo <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Následující tabulka obsahuje další podrobnosti o tři druhy implementace dělicí metody vyrovnávání zatížení <xref:System.Collections.Concurrent.OrderablePartitioner%601> třídy.  
  
|Metoda nebo vlastnost|IList / pole bez vyrovnávání zatížení|IList / pole se službou Vyrovnávání zatížení|Rozhraní IEnumerable|  
|----------------------|-------------------------------------------|----------------------------------------|-----------------|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Používá rozsah dělení|Vytváření oddílů datových dávek používá optimalizované pro seznamy pro partitionCount zadaný|Vytváření oddílů datových dávek používá vytvořením statické počet oddílů.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|Výjimka vyvolává není podporována|Vytváření oddílů datových dávek používá optimalizované pro seznamy a dynamických oddílů|Vytváření oddílů datových dávek používá vytvořením dynamické počet oddílů.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|Vrátí `true`|Vrátí `true`|Vrátí `true`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|Vrátí `true`|Vrátí `false`|Vrátí `false`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|Vrátí `true`|Vrátí `true`|Vrátí `true`|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Vrátí `false`|Vrátí `true`|Vrátí `true`|  
  
### <a name="dynamic-partitions"></a>Dynamických oddílů  
 Pokud máte v úmyslu dělicí metody pro použití v <xref:System.Threading.Tasks.Parallel.ForEach%2A> metodu, musí být moct vrátit dynamické počet oddílů. To znamená, že dělicí metody můžete zadat enumerátor pro nový oddíl na vyžádání v průběhu provádění smyčky. V podstatě vždy, když smyčky přidá nové paralelní úlohy, vyžádá nový oddíl pro tuto úlohu. Pokud budete potřebovat data, která mají být CR, pak odvozena od <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> tak, aby každá položka v každém oddílu je přiřazen jedinečný index.  
  
 Další informace a příklad najdete v tématu [postupy: implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
### <a name="contract-for-partitioners"></a>Kontrakt pro dělicí metody  
 Při implementaci vlastní dělicí metody, postupujte podle těchto pokynů, abyste zajistili správné interakci s PLINQ a <xref:System.Threading.Tasks.Parallel.ForEach%2A> v TPL:  
  
-   Pokud <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> je názvem s parametrem 0 nebo menší pro `partitionsCount`, throw <xref:System.ArgumentOutOfRangeException>. I když PLINQ a TPL se nikdy předat `partitionCount` rovná 0, přesto doporučujeme vám ochrany proti možnosti.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> a <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> musí vracet vždycky `partitionsCount` počet oddílů. Pokud dělicí metody dojde data a nelze vytvořit libovolný počet oddílů, jak si vyžádal, metoda by měla vrátit enumerátor prázdná pro každý zbývající oddílů. Jinak vyvolá výjimku PLINQ a TPL <xref:System.InvalidOperationException>.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>, <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, a <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> by měla vrátit nikdy `null` (`Nothing` v jazyce Visual Basic). Pokud tomu tak je, PLINQ / vyvolá TPL <xref:System.InvalidOperationException>.  
  
-   Metody, které vracejí oddíly musí vracet vždycky, oddíly, které můžete plně a jednoznačně výčet zdroj dat. Měla by existovat žádné duplicity v zdroj dat nebo přeskočené položky Pokud konkrétně vyžadováno záměrné dělicí metody. Pokud toto pravidlo nedodržíte, může výstup pořadí kódována.  
  
-   Následující metody getter Boolean musí vracet vždy přesně následující hodnoty, tak, aby pořadí výstup není kódována:  
  
    -   `KeysOrderedInEachPartition`: Každý oddíl vrátí elementy se zvýšeným klíče indexy.  
  
    -   `KeysOrderedAcrossPartitions`: Pro všechny oddíly, které jsou vráceny klíče indexy v oddílu *i* jsou vyšší, než klíče indexy v oddílu *i*-1.  
  
    -   `KeysNormalized`: Všechna klíče indexy, které jsou rovnoměrně zvýšení bez mezer, od nuly.  
  
-   Všechny indexy, které musí být jedinečný. Nesmí existovat duplicitní indexy. Pokud toto pravidlo nedodržíte, může výstup pořadí kódována.  
  
-   Všechny indexy, které musí být nezáporná. Pokud toto pravidlo nedodržíte, může vyvolat PLINQ/TPL výjimky.  
  
## <a name="see-also"></a>Viz také  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 [Postupy: Implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)  
 [Postupy: Implementace rozdělovače pro statické dělení](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
