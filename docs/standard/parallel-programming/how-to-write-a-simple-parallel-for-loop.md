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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139666"
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Postupy: Zápis jednoduché smyčky Parallel.For

Toto téma obsahuje dva příklady, které ilustrují metodu <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>. První používá přetížení metody <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> a druhá používá přetížení <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType>, dvě nejjednodušší přetížení metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>. Tato dvě přetížení metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> můžete použít, pokud nepotřebujete cyklus zrušit, rozdělit iterace smyčky nebo zachovat místní stav vlákna.

> [!NOTE]
> Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

V prvním příkladu je vypočtena velikost souborů v jednom adresáři. Druhá Vypočítá součin dvou matic.

## <a name="directory-size-example"></a>Příklad velikosti adresáře

V tomto příkladu je jednoduchý nástroj příkazového řádku, který vypočítá celkovou velikost souborů v adresáři. Očekává jako argument jednu cestu k adresáři a vypíše počet a celkovou velikost souborů v tomto adresáři. Po ověření, že adresář existuje, používá metodu <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> k vytvoření výčtu souborů v adresáři a určení jejich velikostí souborů. Každá velikost souboru se pak přidá do proměnné `totalSize`. Všimněte si, že přidání je provedeno voláním <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType>, aby se přidání provádělo jako atomická operace. V opačném případě se více úloh může pokusit aktualizovat proměnnou `totalSize` současně.

[!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
[!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]

## <a name="matrix-and-stopwatch-example"></a>Příklad Matrixu a Stopwatch

Tento příklad používá metodu <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> k výpočtu součinu dvou matic. Také ukazuje, jak použít třídu <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> pro porovnání výkonu paralelní smyčky s neparalelní smyčkou. Všimněte si, že vzhledem k tomu, že může dojít k vygenerování velkého objemu výstupu, příklad umožňuje přesměrování výstupu do souboru.

[!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
[!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]

Při virtuálního jakéhokoli kódu, včetně smyček, je jedním z důležitých cílů použití procesorů co nejvíc, aniž by došlo k překročení virtuálního na místo, kde režie pro paralelní zpracování negace všech výhod výkonu. V tomto konkrétním příkladu je paralelní pouze vnější smyčka, protože ve vnitřní smyčce není provedeno příliš mnoho práce. Kombinace malého množství práce a nežádoucích účinků mezipaměti může způsobit snížení výkonu ve vnořených paralelních smyčkách. Proto virtuálního pouze vnější smyčka je nejlepším způsobem, jak maximalizovat výhody souběžnosti ve většině systémů.

## <a name="the-delegate"></a>Delegát

Třetí parametr tohoto přetížení <xref:System.Threading.Tasks.Parallel.For%2A> je delegát typu `Action<int>` v C# nebo `Action(Of Integer)` v Visual Basic. Delegát `Action`, bez ohledu na to, jestli má nula, jeden nebo šestnáct parametrů typu, vždycky vrátí void. V Visual Basic je chování `Action` definováno pomocí `Sub`. V příkladu se používá výraz lambda pro vytvoření delegáta, ale můžete také vytvořit delegáta jiným způsobem. Další informace naleznete v tématu [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="the-iteration-value"></a>Hodnota iterace

Delegát přijímá jeden vstupní parametr, jehož hodnota je aktuální iterace. Hodnota této iterace je poskytována modulem runtime a její počáteční hodnota je index prvního prvku v segmentu (oddílu) zdroje, který je zpracováván v aktuálním vlákně.

Pokud potřebujete větší kontrolu nad úrovní souběžnosti, použijte jedno z přetížení, které přebírají vstupní parametr <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType>, například: <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>.

## <a name="return-value-and-exception-handling"></a>Vrácení hodnoty a zpracování výjimek

<xref:System.Threading.Tasks.Parallel.For%2A> vrátí objekt <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> po dokončení všech vláken. Tato návratová hodnota je užitečná, když provádíte ruční zastavení nebo ukončení iterace, protože <xref:System.Threading.Tasks.ParallelLoopResult> ukládá informace, jako je například poslední iterace, která proběhla po dokončení. Pokud dojde k jedné nebo více výjimkám v jednom z vláken, bude vyvolána <xref:System.AggregateException?displayProperty=nameWithType>.

V kódu v tomto příkladu se nepoužívá návratová hodnota <xref:System.Threading.Tasks.Parallel.For%2A>.

## <a name="analysis-and-performance"></a>Analýza a výkon

K zobrazení využití procesoru v počítači můžete použít Průvodce výkonem. V rámci experimentu zvyšte počet sloupců a řádků v maticích. Čím větší matrice, tím větší je rozdíl mezi paralelními a sekvenčními verzemi výpočtu. Když je matice malá, sekvenční verze se spustí rychleji z důvodu režie v nastavení paralelní smyčky.

Synchronní volání sdílených prostředků, jako je konzola nebo systém souborů, významně sníží výkon paralelní smyčky. Při měření výkonu se snažte vyhnout volání, jako je například <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> v rámci smyčky.

## <a name="compile-the-code"></a>Kompilovat kód

Zkopírujte a vložte tento kód do projektu sady Visual Studio.

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Tasks.Parallel.For%2A>
- <xref:System.Threading.Tasks.Parallel.ForEach%2A>
- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
