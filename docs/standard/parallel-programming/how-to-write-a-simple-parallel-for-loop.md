---
title: 'Postupy: Zápis jednoduché smyčky Parallel.For'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Parallel.For, How to Write
- for loop, parallel construction in .NET
- parallel for loops, how to use
ms.assetid: 9029ba7f-a9d1-4526-8c84-c88716dba5d4
ms.openlocfilehash: 78f07a4f0118c6bce7a043f111988281ddd6add0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139666"
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Postupy: Zápis jednoduché smyčky Parallel.For

Toto téma obsahuje dva <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> příklady, které ilustrují metodu. První používá <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> přetížení metody a druhý <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> používá přetížení, dvě nejjednodušší přetížení <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody. Můžete použít tyto dvě přetížení <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody, pokud není nutné zrušit smyčku, přerušit iterací smyčky nebo udržovat místní stav vlákna.

> [!NOTE]
> Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, naleznete [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

První příklad vypočítá velikost souborů v jednom adresáři. Druhý vypočítá součin dvou matic.

## <a name="directory-size-example"></a>Příklad velikosti adresáře

Tento příklad je jednoduchý nástroj příkazového řádku, který vypočítá celkovou velikost souborů v adresáři. Očekává jednu cestu k adresáři jako argument a hlásí počet a celkovou velikost souborů v tomto adresáři. Po ověření, zda adresář existuje, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> použije metodu k vytvoření výčtu souborů v adresáři a určení jejich velikosti souborů. Každá velikost souboru je `totalSize` pak přidána do proměnné. Všimněte si, že sčítání <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> se provádí voláním tak, aby sčítání se provádí jako atomické operace. V opačném případě by se `totalSize` více úloh mohlo pokusit aktualizovat proměnnou současně.

[!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
[!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]

## <a name="matrix-and-stopwatch-example"></a>Příklad matice a stopek

Tento příklad <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> používá metodu k výpočtu součin dvou matic. Také ukazuje, jak <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> použít třídu k porovnání výkonu paralelní smyčky s neparalelní smyčkou. Všimněte si, že vzhledem k tomu, že může generovat velký objem výstupu, příklad umožňuje přesměrovat výstup do souboru.

[!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
[!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]

Při paralelizaci libovolný kód, včetně smyčky, jedním důležitým cílem je využít procesory co nejvíce bez přes paralelizaci do bodu, kde režie pro paralelní zpracování neguje všechny výhody výkonu. V tomto konkrétním příkladu je paralelizována pouze vnější smyčka, protože ve vnitřní smyčce není příliš mnoho práce. Kombinace malého množství práce a nežádoucí efekty mezipaměti může mít za následek snížení výkonu v vnořených paralelních smyček. Proto paralelizace pouze vnější smyčky je nejlepší způsob, jak maximalizovat výhody souběžnosti ve většině systémů.

## <a name="the-delegate"></a>Delegát

Třetí parametr tohoto přetížení <xref:System.Threading.Tasks.Parallel.For%2A> je delegát `Action<int>` typu v `Action(Of Integer)` jazyce C# nebo v jazyce Visual Basic. Delegát, `Action` zda má parametry typu nula, jeden nebo šestnáct, vždy vrátí hodnotu void. V jazyce Visual Basic `Action` je chování `Sub`aplikace definované pomocí . Příklad používá výraz lambda k vytvoření delegáta, ale delegáta můžete vytvořit i jinými způsoby. Další informace naleznete [v tématu Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="the-iteration-value"></a>Hodnota iterace

Delegát přebírá jeden vstupní parametr, jehož hodnota je aktuální iterace. Tato hodnota iterace je dodávána za běhu a jeho počáteční hodnota je index prvního prvku v segmentu (oddílu) zdroje, který je zpracováván v aktuálním vlákně.

Pokud požadujete větší kontrolu nad úrovní souběžnosti, použijte jedno <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> z přetížení, <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>které přebírá vstupní parametr, například: .

## <a name="return-value-and-exception-handling"></a>Zpracování vrácené hodnoty a výjimek

<xref:System.Threading.Tasks.Parallel.For%2A>vrátí <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> objekt po dokončení všech vláken. Tato vrácená hodnota je užitečná, když zastavujete nebo přerušujete iteraci smyčky ručně, protože <xref:System.Threading.Tasks.ParallelLoopResult> ukládá informace, jako je například poslední iterace, která byla spuštěna do dokončení. Pokud dojde k jedné nebo více výjimek <xref:System.AggregateException?displayProperty=nameWithType> v jednom z vláken, bude vyvolána.

V kódu v tomto příkladu <xref:System.Threading.Tasks.Parallel.For%2A> se nepoužívá vrácená hodnota.

## <a name="analysis-and-performance"></a>Analýza a výkon

Pomocí Průvodce výkonem můžete zobrazit využití procesoru v počítači. Jako experiment zvyšte počet sloupců a řádků v maticích. Čím větší matice, tím větší je rozdíl výkonu mezi paralelní a sekvenční verze výpočtu. Pokud je matice malá, sekvenční verze poběží rychleji z důvodu režie při nastavování paralelní smyčky.

Synchronní volání sdílených prostředků, jako je konzola nebo systém souborů, výrazně sníží výkon paralelní smyčky. Při měření výkonu se snažte <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> vyhnout volání, například v rámci smyčky.

## <a name="compile-the-code"></a>Kompilace kódu

Zkopírujte a vložte tento kód do projektu sady Visual Studio.

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Tasks.Parallel.For%2A>
- <xref:System.Threading.Tasks.Parallel.ForEach%2A>
- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
