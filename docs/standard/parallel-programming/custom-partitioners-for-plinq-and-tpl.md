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
ms.openlocfilehash: 8caea6d8a97b8c0daf7c59718479ea2e12a52d78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141565"
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>Vlastní dělicí metody pro PLINQ a TPL

Chcete-li paralelizovat operaci na zdroj dat, jedním ze základních kroků je *rozdělení* zdroje do více oddílů, které lze přistupovat souběžně více vláken. PLINQ a paralelní knihovna úloh (TPL) poskytují výchozí rozdělovače, <xref:System.Threading.Tasks.Parallel.ForEach%2A> které pracují transparentně při psaní paralelnídotaz nebo smyčky. Pro pokročilejší scénáře můžete připojit vlastní rozdělovač.

## <a name="kinds-of-partitioning"></a>Druhy dělení

Existuje mnoho způsobů, jak rozdělit zdroj dat. V nejúčinnějších přístupech více vláken spolupracují na zpracování původní zdrojové sekvence, nikoli fyzicky oddělující zdroj do více dílčích sekvencí. Pro pole a další indexované <xref:System.Collections.IList> zdroje, jako jsou kolekce, kde je délka známa předem, *dělení rozsahu* je nejjednodušší druh dělení. Každé vlákno obdrží jedinečné počáteční a koncové indexy, takže může zpracovat svůj rozsah zdroje bez přepsání nebo přepsání jiným vláknem. Jedinou režií, která se podílí na dělení rozsahu, je počáteční práce při vytváření rozsahů; po dokončení není nutná žádná další synchronizace. Proto může poskytovat dobrý výkon tak dlouho, dokud je pracovní vytížení rozděleno rovnoměrně. Nevýhodou dělení rozsahu je, že pokud jedno vlákno dokončí brzy, nemůže pomoci ostatním vláknům dokončit jejich práci.

Pro propojené seznamy nebo jiné kolekce, jejichž délka není známa, můžete použít *dělení bloku*. V oddílování bloku, každý podproces nebo úlohu v paralelní smyčce nebo dotazspotřebovává určitý počet zdrojových prvků v jednom bloku, zpracuje je a pak se vrátí k načtení dalších prvků. Rozdělovač zajišťuje, že všechny prvky jsou distribuovány a že neexistují žádné duplikáty. Blok může mít libovolnou velikost. Například partitioner, který je znázorněno v [Jak: Implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md) vytvoří bloky, které obsahují pouze jeden prvek. Tak dlouho, dokud bloky nejsou příliš velké, tento druh dělení je ze své podstaty vyrovnávání zatížení, protože přiřazení prvků do podprocesů není předem určena. Však partitioner vynaloží režii synchronizace pokaždé, když vlákno potřebuje získat další blok. Množství synchronizace vzniklé v těchto případech je nepřímo úměrná velikosti bloků.

Obecně platí, že dělení rozsahu je pouze rychlejší, když je doba provádění delegáta malé až střední a zdroj má velký počet prvků a celková práce každého oddílu je zhruba ekvivalentní. Rozdělení bloku je proto obecně rychlejší ve většině případů. Na zdroje s malým počtem prvků nebo delší doby provádění pro delegáta, pak výkon bloku a rozsah dělení je přibližně stejné.

TPL partitioners také podporují dynamický počet oddílů. To znamená, že mohou vytvářet oddíly průběžně, <xref:System.Threading.Tasks.Parallel.ForEach%2A> například když smyčka vytvoří nový úkol. Tato funkce umožňuje rozdělovač škálovat spolu se samotnou smyčkou. Dynamické rozdělovače jsou také ze své podstaty vyrovnávání zatížení. Při vytváření vlastního rozdělovače je nutné podporovat dynamické dělení, <xref:System.Threading.Tasks.Parallel.ForEach%2A> aby bylo spotřební ze smyčky.

### <a name="configuring-load-balancing-partitioners-for-plinq"></a>Konfigurace rozdělovačů vyrovnávání zatížení pro PLINQ

Některá přetížení <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metody umožňují vytvořit rozdělovač pro <xref:System.Collections.IList> pole nebo zdroj a určit, zda by se měl pokusit vyvážit zatížení mezi vlákny. Když je rozdělovač nakonfigurován tak, aby vyvažoval zatížení, používá se rozdělení bloků dat a prvky jsou předávány každému oddílu v malých blocích, jak jsou požadovány. Tento přístup pomáhá zajistit, že všechny oddíly mají prvky ke zpracování, dokud nebude dokončena celá smyčka nebo dotaz. Další přetížení lze použít k zajištění vyrovnávání zatížení <xref:System.Collections.IEnumerable> dělení libovolného zdroje.

Obecně platí vyrovnávání zatížení vyžaduje oddíly požadovat prvky poměrně často z partitioner. Naproti tomu partitioner, který provádí statické dělení můžete přiřadit prvky každý partitioner najednou pomocí rozsahu nebo bloku dělení. To vyžaduje menší režii než vyrovnávání zatížení, ale může trvat déle, pokud jedno vlákno skončí s výrazně více práce než ostatní. Ve výchozím nastavení, když je předán IList nebo pole, PLINQ vždy používá dělení rozsahu bez vyrovnávání zatížení. Chcete-li povolit vyrovnávání zatížení `Partitioner.Create` pro PLINQ, použijte metodu, jak je znázorněno v následujícím příkladu.

[!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
[!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]

Nejlepší způsob, jak zjistit, zda použít vyrovnávání zatížení v daném scénáři je experimentovat a měřit, jak dlouho trvá operace k dokončení pod reprezentativní zatížení a konfigurace počítače. Statické dělení může například poskytnout významné zrychlení v počítači s více jádry, který má pouze několik jader, ale může mít za následek zpomalení v počítačích, které mají relativně mnoho jader.

V následující tabulce jsou uvedeny <xref:System.Collections.Concurrent.Partitioner.Create%2A> dostupné přetížení metody. Tyto rozdělovače nejsou omezeny na použití <xref:System.Threading.Tasks.Task>pouze s PLINQ nebo . Mohou být také použity s libovolnou vlastní paralelní konstrukci.

|Přetížení|Používá vyrovnávání zatížení|
|--------------|-------------------------|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Vždy|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Pokud je logický argument zadán jako true|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Pokud je logický argument zadán jako true|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|Never (Nikdy)|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|Never (Nikdy)|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|Never (Nikdy)|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|Never (Nikdy)|

### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Konfigurace rozdělovačů statického rozsahu pro parallel.foreach

Ve <xref:System.Threading.Tasks.Parallel.For%2A> smyčce je tělo smyčky k dispozici metodě jako delegát. Náklady na vyvolání tohoto delegáta jsou přibližně stejné jako volání virtuální metody. V některých scénářích může být tělo paralelní smyčky dostatečně malé, aby se náklady na vyvolání delegáta v každé iteraci smyčky stanou významnými. V takových situacích můžete použít <xref:System.Collections.Concurrent.Partitioner.Create%2A> jeden z <xref:System.Collections.Generic.IEnumerable%601> přetížení k vytvoření oddíly rozsahu přes zdrojové prvky. Potom můžete předat tuto kolekci rozsahů metodě, <xref:System.Threading.Tasks.Parallel.ForEach%2A> jejíž `for` tělo se skládá z pravidelné smyčky. Výhodou tohoto přístupu je, že náklady na vyvolání delegáta vznikají pouze jednou za rozsah, nikoli jednou za prvek. Následující příklad ukazuje základní vzor.

[!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
[!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]

Každé vlákno ve smyčce <xref:System.Tuple%602> obdrží vlastní, která obsahuje počáteční a koncové hodnoty indexu v zadaném dílčím rozsahu. Vnitřní `for` smyčka používá `fromInclusive` `toExclusive` hodnoty a pro smyčku přes pole nebo <xref:System.Collections.IList> přímo.

Jeden z <xref:System.Collections.Concurrent.Partitioner.Create%2A> přetížení umožňuje určit velikost oddílů a počet oddílů. Toto přetížení lze použít ve scénářích, kde práce na prvek je tak nízká, že i jeden volání virtuální metody na prvek má znatelný dopad na výkon.

## <a name="custom-partitioners"></a>Vlastní šmeječky

V některých scénářích může být užitečné nebo dokonce nutné implementovat vlastní partitioner. Můžete mít například vlastní třídu kolekce, kterou můžete rozdělit efektivněji než výchozí rozdělovače, na základě vašich znalostí vnitřní struktury třídy. Nebo můžete chtít vytvořit oddíly rozsahu různých velikostí na základě znalosti o tom, jak dlouho bude trvat zpracování prvků na různých místech ve zdrojové kolekci.

Chcete-li vytvořit základní vlastní partitioner, odvodit třídu z <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> a přepsat virtuální metody, jak je popsáno v následující tabulce.

|||
|-|-|
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Tato metoda je volána jednou hlavním vláknem a vrátí IList(IEnumerator(TSource)). Každý pracovní podproces ve smyčce nebo dotazu můžete volat `GetEnumerator` v seznamu načíst <xref:System.Collections.Generic.IEnumerator%601> přes odlišný oddíl.|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Vraťte `true` se, pokud implementujete <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, jinak . `false`|
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|Pokud <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> `true`je , tato metoda může <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>být volitelně volána namísto .|

Pokud výsledky musí být seřaditelné nebo potřebujete indexovaný <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> přístup k prvkům, odvodte a přepište jeho virtuální metody, jak je popsáno v následující tabulce.

|||
|-|-|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Tato metoda je volána jednou hlavním `IList(IEnumerator(TSource))`vláknem a vrátí . Každý pracovní podproces ve smyčce nebo dotazu můžete volat `GetEnumerator` v seznamu načíst <xref:System.Collections.Generic.IEnumerator%601> přes odlišný oddíl.|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Vraťte `true` se, pokud implementujete <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>; jinak false.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|Obvykle to jen <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>volá .|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|Pokud <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> `true`je , tato metoda může <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>být volitelně volána namísto .|

Následující tabulka obsahuje další podrobnosti o tom, jak tři <xref:System.Collections.Concurrent.OrderablePartitioner%601> druhy vyrovnávání zatížení partitioners implementovat třídu.

|Metoda/vlastnost|IList / Array bez vyrovnávání zatížení|IList / Array s vyrovnáváním zatížení|Ienumerable|
|----------------------|-------------------------------------------|----------------------------------------|-----------------|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Používá dělení rozsahu|Používá dělení bloku optimalizované pro seznamy pro zadaný partitionCount.|Používá dělení bloku vytvořením statického počtu oddílů.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|Vyvolá nepodporovanou výjimku.|Používá rozdělení bloku dat optimalizované pro seznamy a dynamické oddíly.|Používá dělení bloku vytvořením dynamického počtu oddílů.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|Vrátí`true`|Vrátí`true`|Vrátí`true`|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|Vrátí`true`|Vrátí`false`|Vrátí`false`|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|Vrátí`true`|Vrátí`true`|Vrátí`true`|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Vrátí`false`|Vrátí`true`|Vrátí`true`|

### <a name="dynamic-partitions"></a>Dynamické oddíly

Pokud máte v úmyslu partitioner, <xref:System.Threading.Tasks.Parallel.ForEach%2A> který má být použit v metodě, musíte být schopni vrátit dynamický počet oddílů. To znamená, že partitioner můžete zadat čítač pro nový oddíl na vyžádání kdykoli během spuštění smyčky. V podstatě vždy, když smyčka přidá nový paralelní úkol, požaduje nový oddíl pro tento úkol. Pokud požadujete, aby byla data uspořádaná, odvoděte <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> je tak, aby každé položce v každém oddílu byl přiřazen jedinečný index.

Další informace a příklad naleznete v [tématu How to: Implement dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).

### <a name="contract-for-partitioners"></a>Smlouva pro šmeječky

Při implementaci vlastního rozdělovače postupujte podle následujících pokynů, <xref:System.Threading.Tasks.Parallel.ForEach%2A> abyste zajistili správnou interakci s PLINQ a v TPL:

- Pokud <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> je volána s argumentem `partitionsCount`nula nebo méně pro , throw <xref:System.ArgumentOutOfRangeException>. Přestože PLINQ a TPL `partitionCount` nikdy neprojdou v rovných 0, doporučujeme vám, abyste se před možností chránili.

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>a <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> měl `partitionsCount` by vždy vrátit počet oddílů. Pokud partitioner vyčerpá data a nemůže vytvořit tolik oddílů, jak je požadováno, pak metoda by měla vrátit prázdný čítač výčtu pro každý ze zbývajících oddílů. V opačném případě budou plinq <xref:System.InvalidOperationException>i TPL hodit .

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> , a `null` `Nothing` nikdy by se neměla vracet (v jazyce Visual Basic). Pokud ano, PLINQ / TPL <xref:System.InvalidOperationException>bude hodit .

- Metody, které vracejí oddíly by měly vždy vrátit oddíly, které mohou plně a jedinečně výčet zdroje dat. Ve zdroji dat nebo přeskočených položkách by neměla být žádná duplikace, pokud to výslovně nevyžaduje návrh rozdělovače. Pokud toto pravidlo není dodrženo, může být výstupní pořadí zakódováno.

- Následující logické hodnoty musí vždy přesně vrátit následující hodnoty, aby výstupní pořadí nebylo zakódováno:

  - `KeysOrderedInEachPartition`: Každý oddíl vrátí prvky s rostoucími indexy klíčů.

  - `KeysOrderedAcrossPartitions`: Pro všechny oddíly, které jsou vráceny, jsou klíčové indexy v oddílu *i* vyšší než klíčové indexy v oddílu *i*-1.

  - `KeysNormalized`: Všechny klíčové indexy se monotonicky zvětšují bez mezer, počínaje nulou.

- Všechny indexy musí být jedinečné. Nemusí existovat duplicitní indexy. Pokud toto pravidlo není dodrženo, může být výstupní pořadí zakódováno.

- Všechny indexy musí být nezáporné. Pokud toto pravidlo není dodrženo, pak PLINQ/TPL může vyvolat výjimky.

## <a name="see-also"></a>Viz také

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Postupy: Implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)
- [Postupy: Implementace rozdělovače pro statické dělení](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
