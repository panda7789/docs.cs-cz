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
ms.openlocfilehash: 50553aab30d5a1bc5880ae0fe39c34508e57d0e5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276722"
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>Vlastní dělicí metody pro PLINQ a TPL

Jedním z podstatných kroků, aby se paralelizovat operace na zdroj dat, je *rozdělit* zdroj do několika oddílů, ke kterým lze současně přihlédnout více vlákny. PLINQ a Task Parallel Library (TPL) poskytují výchozí oddíly, které fungují transparentně při psaní paralelního dotazu nebo <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky. V případě pokročilejších scénářů můžete připojit vlastní rozdělovač.

## <a name="kinds-of-partitioning"></a>Typy dělení

Existuje mnoho způsobů, jak zdroj dat rozdělit. V nejúčinnějších metodách spolupracuje více vláken na zpracování původní zdrojové sekvence, nikoli fyzické oddělení zdroje do více dílčích sekvencí. U polí a dalších indexovaných zdrojů, jako jsou například <xref:System.Collections.IList> kolekce, kde je délka známa předem, je *vytváření oddílů rozsahu* nejjednodušším druhem dělení. Každé vlákno obdrží jedinečné počáteční a koncové indexy, aby mohla zpracovat jeho rozsah zdroje bez přepsání nebo přepsání jiným vláknem. Jediná režie při dělení rozsahu je počáteční práce při vytváření rozsahů. Po této instalaci se nevyžaduje žádná další synchronizace. Proto může poskytovat dobrý výkon, pokud je zatížení rovnoměrně rozděleno. Nevýhodou dělení rozsahu je to, že pokud jedno vlákno dokončí včas, nemůže ostatním vláknům docílit práci.

U propojených seznamů nebo jiných kolekcí, jejichž délka není známá, můžete použít *dělení bloků dat*. V dělení bloků dat každý podproces nebo úloha v paralelní smyčce nebo dotazu spotřebovává určitý počet zdrojových prvků v jednom bloku, zpracuje je a pak se vrátí k načtení dalších prvků. Rozdělovač zajišťuje distribuci všech prvků a neexistují žádné duplicity. Blok může být libovolná velikost. Například dělicí metoda, která je znázorněna v tématu [Postupy: Implementace dynamických oddílů](how-to-implement-dynamic-partitions.md) vytvoří bloky, které obsahují pouze jeden prvek. Pokud bloky nejsou příliš velké, je tento druh dělení vyrovnává zatížení, protože přiřazení prvků k vláknům není předem určeno. Dělicí metoda ale účtuje režii synchronizace pokaždé, když vlákno potřebuje získat další blok. Velikost synchronizace vzniklá v těchto případech je naopak úměrná velikosti bloků dat.

Obecně platí, že dělení rozsahu je rychlejší pouze v případě, že je doba provádění delegáta malá a střední a zdroj má velký počet prvků a celková práce každého oddílu je zhruba ekvivalentní. Vytváření oddílů bloků dat je proto ve většině případů všeobecně rychlejší. V případě zdrojů s malým počtem prvků nebo delší dobu provádění pro delegáta se bude výkon dělení bloků dat a rozsahu rovnat.

Oddíly TPL podporují také dynamický počet oddílů. To znamená, že můžou vytvářet oddíly průběžně, například když <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčka vytvoří nový úkol. Tato funkce umožňuje rozdělovači škálovat společně se smyčkou. Dynamické dělicí metody jsou také z vlastního vyrovnávání zatížení. Když vytváříte vlastní rozdělovač, musíte podporovat dynamické dělení, aby bylo možné je ze smyčky obpracovat <xref:System.Threading.Tasks.Parallel.ForEach%2A> .

### <a name="configuring-load-balancing-partitioners-for-plinq"></a>Konfigurace oddílů pro vyrovnávání zatížení pro PLINQ

Některá přetížení <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metody umožňují vytvořit rozdělovač pro pole nebo <xref:System.Collections.IList> zdroj a určit, zda se má pokusit vyrovnávat zatížení mezi vlákny. Když je rozdělovač nakonfigurovaný pro vyrovnávání zatížení, použije se dělení na oddíly a prvky se předají do každého oddílu v malých blocích, jak jsou požadovány. Tento přístup pomáhá zajistit, že všechny oddíly mají prvky, které mají být zpracovány, dokud není dokončena celá smyčka nebo dotaz. Další přetížení lze použít k zajištění dělení vyrovnávání zatížení libovolného <xref:System.Collections.IEnumerable> zdroje.

Vyrovnávání zatížení obecně vyžaduje, aby oddíly vyžádaly prvky relativně často od rozdělovače. Naproti tomu dělicí metoda, která provádí statické dělení, může každému oddílu přiřadit všechny prvky najednou pomocí kteréhokoli rozsahu nebo dělení bloků dat. To vyžaduje nižší režii než vyrovnávání zatížení, ale spuštění může trvat déle, pokud jedno vlákno skončí s větším množstvím práce než s ostatními. Ve výchozím nastavení, když se předává objektu IList nebo Array, PLINQ vždy používá dělení rozsahu bez vyrovnávání zatížení. Chcete-li povolit vyrovnávání zatížení pro PLINQ, použijte `Partitioner.Create` metodu, jak je znázorněno v následujícím příkladu.

[!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
[!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]

Nejlepším způsobem, jak určit, jestli se má vyrovnávání zatížení v kterémkoli scénáři použít, je experimentovat a měřit, jak dlouho trvá operace v rámci reprezentativních zátěží a konfigurací počítačů. Statické dělení můžou například poskytovat významné zrychlení počítače, které mají jenom několik jader, ale můžou způsobit zpomalení v počítačích, které mají relativně mnoho jader.

Následující tabulka uvádí dostupná přetížení <xref:System.Collections.Concurrent.Partitioner.Create%2A> metody. Tyto dělicí metody nejsou omezeny pouze na použití s PLINQ nebo <xref:System.Threading.Tasks.Task> . Lze je také použít spolu s libovolnou vlastní paralelní konstrukcí.

|Metody|Používá Vyrovnávání zatížení|
|--------------|-------------------------|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Vždy|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Pokud je argument Boolean zadán jako true|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Pokud je argument Boolean zadán jako true|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|Nikdy|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|Nikdy|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|Nikdy|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|Nikdy|

### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Konfigurace statických oddílů rozsahu pro Parallel. ForEach

Ve <xref:System.Threading.Tasks.Parallel.For%2A> smyčce je tělo smyčky k dispozici metodě jako delegát. Náklady na vyvolání tohoto delegáta jsou přibližně stejné jako volání virtuální metody. V některých scénářích může být obsah paralelní smyčky dostatečně malý, protože náklady na vyvolání delegáta v každé iteraci smyčky budou významné. V takových situacích můžete použít jedno z <xref:System.Collections.Concurrent.Partitioner.Create%2A> přetížení k vytvoření <xref:System.Collections.Generic.IEnumerable%601> oddílu rozsahu přes zdrojové prvky. Pak můžete tuto kolekci rozsahů předat <xref:System.Threading.Tasks.Parallel.ForEach%2A> metodě, jejíž tělo se skládá z regulární `for` smyčky. Výhodou tohoto přístupu je, že náklady na vyvolání delegáta se účtují jenom jednou za rozsah, nikoli jednou pro každý prvek. Následující příklad ukazuje základní vzor.

[!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
[!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]

Každé vlákno ve smyčce obdrží vlastní <xref:System.Tuple%602> , který obsahuje hodnoty počáteční a koncového indexu v zadaném dílčím rozsahu. Vnitřní `for` smyčka používá `fromInclusive` hodnoty a `toExclusive` k cyklickému vykonání pole nebo <xref:System.Collections.IList> přímo.

Jedno z <xref:System.Collections.Concurrent.Partitioner.Create%2A> přetížení umožňuje určit velikost oddílů a počet oddílů. Toto přetížení lze použít ve scénářích, kde práce na prvek je tak nízká, takže i jedno volání virtuální metody na prvek má znatelný dopad na výkon.

## <a name="custom-partitioners"></a>Vlastní dělicí metody

V některých scénářích to může být vhodné nebo dokonce nutné implementovat vlastní rozdělovač. Můžete mít například vlastní třídu kolekce, kterou lze efektivněji rozdělit, než výchozí oddíly mohou být založeny na vašich znalostech vnitřní struktury třídy. Nebo můžete chtít vytvořit oddíly rozsahu různých velikostí na základě vašich znalostí o tom, jak dlouho bude trvat zpracování prvků v různých umístěních ve zdrojové kolekci.

Chcete-li vytvořit základní vlastní rozdělovač, odvodit třídu z <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> a přepsat virtuální metody, jak je popsáno v následující tabulce.

|||
|-|-|
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Tato metoda je volána jednou hlavním vláknem a vrací objekt IList (IEnumerator (TSource)). Každý pracovní podproces ve smyčce nebo dotaz může zavolat `GetEnumerator` na seznam a získat tak <xref:System.Collections.Generic.IEnumerator%601> přes samostatný oddíl.|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Vrátí `true` se, Pokud implementujete <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A> , jinak `false` .|
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|Pokud <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> je `true` , tato metoda může být volitelně volána namísto <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> .|

Pokud se výsledky musí seřadit, nebo potřebujete indexovaný přístup k prvkům, odvodit z <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> a přepsat své virtuální metody, jak je popsáno v následující tabulce.

|||
|-|-|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Tato metoda je volána jednou hlavním vláknem a vrací `IList(IEnumerator(TSource))` . Každý pracovní podproces ve smyčce nebo dotaz může zavolat `GetEnumerator` na seznam a získat tak <xref:System.Collections.Generic.IEnumerator%601> přes samostatný oddíl.|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Vrátí `true` se, Pokud implementujete, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A> v opačném případě false.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|Obvykle toto volá pouze <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> .|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|Pokud <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> je `true` , tato metoda může být volitelně volána namísto <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> .|

Následující tabulka poskytuje další podrobnosti o tom, jak tři druhy oddílů vyrovnávání zatížení tuto třídu implementují <xref:System.Collections.Concurrent.OrderablePartitioner%601> .

|Metoda/vlastnost|IList/Array bez vyrovnávání zatížení|IList/Array s vyrovnáváním zatížení|Rozhraní|
|----------------------|-------------------------------------------|----------------------------------------|-----------------|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Používá dělení rozsahu|Používá pro seznamy pro partitionCount zadanou optimalizaci dělení na bloky dat|Pomocí dělení bloků dat vytvoří statický počet oddílů.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|Vyvolá výjimku nepodporovanou|Používá dělení bloků dat optimalizované pro seznamy a dynamické oddíly.|Vytváření oddílů pomocí bloků dat vytvořením dynamického počtu oddílů.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|Vrátí`true`|Vrátí`true`|Vrátí`true`|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|Vrátí`true`|Vrátí`false`|Vrátí`false`|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|Vrátí`true`|Vrátí`true`|Vrátí`true`|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Vrátí`false`|Vrátí`true`|Vrátí`true`|

### <a name="dynamic-partitions"></a>Dynamické oddíly

Pokud máte v úmyslu použít rozdělovač v <xref:System.Threading.Tasks.Parallel.ForEach%2A> metodě, je nutné, abyste mohli vrátit dynamický počet oddílů. To znamená, že dělicí metoda může během provádění smyčky kdykoli dodat enumerátor pro nový oddíl na vyžádání. V podstatě pokaždé, když smyčka přidá novou paralelní úlohu, požádá o nový oddíl této úlohy. Pokud požadujete, aby se data daly seřadit, pak je odvodit z toho <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> , aby každá položka v každém oddílu byla přiřazená jedinečný index.

Další informace a příklad naleznete v tématu [How to: Implementing Dynamic Partitions](how-to-implement-dynamic-partitions.md).

### <a name="contract-for-partitioners"></a>Kontrakt pro rozdělovače

Při implementaci vlastního rozdělovače použijte následující pokyny, které vám pomohou zajistit správnou interakci s PLINQ a <xref:System.Threading.Tasks.Parallel.ForEach%2A> v TPL:

- Pokud <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> je volána s argumentem nula nebo menším pro `partitionsCount` , throw <xref:System.ArgumentOutOfRangeException> . I když PLINQ a TPL nikdy neprojde jako `partitionCount` 0, doporučujeme vám, abyste před touto možností chráněni.

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>a <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> měly by vždycky vracet `partitionsCount` počet oddílů. Pokud rozdělovač vyčerpá data a nemůže vytvořit tolik oddílů jako požadovaný, pak by metoda měla vrátit prázdný enumerátor pro každý ze zbývajících oddílů. V opačném případě by PLINQ i TPL vyvolaly <xref:System.InvalidOperationException> .

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> , <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A> a <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> by nikdy neměly vracet `null` ( `Nothing` v Visual Basic). Pokud k tomu dojde, PLINQ/TPL vyvolá výjimku <xref:System.InvalidOperationException> .

- Metody, které vracejí oddíly, by měly vždy vracet oddíly, které mohou plně a jednoznačně vytvořit výčet zdroje dat. Ve zdroji dat nebo vynechaných položkách by neměly být žádné duplicity, pokud to není konkrétně vyžadováno návrhem rozdělovače. Pokud toto pravidlo není následováno, bude možné zakódovat výstupní objednávku.

- Následující booleovské metody getter musí vždy přesně vracet následující hodnoty, aby výstupní pořadí nebylo zakódováno:

  - `KeysOrderedInEachPartition`: Každý oddíl vrátí prvky se zvýšením indexů klíčů.

  - `KeysOrderedAcrossPartitions`: U všech vrácených oddílů jsou klíčové indexy v oddílu *i* vyšší než klíčové indexy v oddílu *i*-1.

  - `KeysNormalized`: Všechny indexy klíčů se rovnoměrně zvětšující bez mezer, od nuly.

- Všechny indexy musí být jedinečné. Pravděpodobně neexistují duplicitní indexy. Pokud toto pravidlo není následováno, bude možné zakódovat výstupní objednávku.

- Všechny indexy musí být nezáporné. Pokud toto pravidlo není následováno, může PLINQ/TPL vyvolat výjimky.

## <a name="see-also"></a>Viz také

- [Paralelní programování](index.md)
- [Postupy: Implementace dynamických oddílů](how-to-implement-dynamic-partitions.md)
- [Postupy: Implementace rozdělovače pro statické dělení](how-to-implement-a-partitioner-for-static-partitioning.md)
