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
ms.openlocfilehash: b18e110b86389dd5d28bbc370e207aaaf7571aaf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290730"
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Postupy: Zápis jednoduché smyčky Parallel.For

Toto téma obsahuje dva příklady, které ilustrují <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metodu. První používá <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> přetížení metody a druhá používá <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> přetížení, což je dvě nejjednodušší přetížení <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody. Tato dvě přetížení metody lze použít <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> , pokud není nutné smyčku zrušit, rozdělit iterace smyčky nebo zachovat místní stav vlákna.

> [!NOTE]
> Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md).

V prvním příkladu je vypočtena velikost souborů v jednom adresáři. Druhá Vypočítá součin dvou matic.

## <a name="directory-size-example"></a>Příklad velikosti adresáře

V tomto příkladu je jednoduchý nástroj příkazového řádku, který vypočítá celkovou velikost souborů v adresáři. Očekává jako argument jednu cestu k adresáři a vypíše počet a celkovou velikost souborů v tomto adresáři. Po ověření, že adresář existuje, používá <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metodu k vytvoření výčtu souborů v adresáři a určení jejich velikostí souborů. Každá velikost souboru se pak přidá do `totalSize` proměnné. Všimněte si, že přidání je provedeno voláním, <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> aby se přidání provádělo jako atomická operace. V opačném případě může více úloh zkusit aktualizovat `totalSize` proměnnou současně.

[!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
[!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]

## <a name="matrix-and-stopwatch-example"></a>Příklad Matrixu a Stopwatch

Tento příklad používá <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metodu k výpočtu součinu dvou matic. Také ukazuje, jak použít <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> třídu k porovnání výkonu paralelní smyčky s neparalelní smyčkou. Všimněte si, že vzhledem k tomu, že může dojít k vygenerování velkého objemu výstupu, příklad umožňuje přesměrování výstupu do souboru.

[!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
[!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]

Při virtuálního jakéhokoli kódu, včetně smyček, je jedním z důležitých cílů použití procesorů co nejvíc, aniž by došlo k překročení virtuálního na místo, kde režie pro paralelní zpracování negace všech výhod výkonu. V tomto konkrétním příkladu je paralelní pouze vnější smyčka, protože ve vnitřní smyčce není provedeno příliš mnoho práce. Kombinace malého množství práce a nežádoucích účinků mezipaměti může způsobit snížení výkonu ve vnořených paralelních smyčkách. Proto virtuálního pouze vnější smyčka je nejlepším způsobem, jak maximalizovat výhody souběžnosti ve většině systémů.

## <a name="the-delegate"></a>Delegát

Třetí parametr tohoto přetížení <xref:System.Threading.Tasks.Parallel.For%2A> je delegát typu `Action<int>` v jazyce C# nebo `Action(Of Integer)` v Visual Basic. `Action`Delegát bez ohledu na to, jestli má nula, jeden nebo šestnáct parametrů typu, vždycky vrátí void. V Visual Basic chování `Action` je definováno pomocí `Sub` . V příkladu se používá výraz lambda pro vytvoření delegáta, ale můžete také vytvořit delegáta jiným způsobem. Další informace naleznete v tématu [lambda výrazy v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md).

## <a name="the-iteration-value"></a>Hodnota iterace

Delegát přijímá jeden vstupní parametr, jehož hodnota je aktuální iterace. Hodnota této iterace je poskytována modulem runtime a její počáteční hodnota je index prvního prvku v segmentu (oddílu) zdroje, který je zpracováván v aktuálním vlákně.

Pokud potřebujete větší kontrolu nad úrovní souběžnosti, použijte jedno z přetížení, které přebírají <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> vstupní parametr, například: <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType> .

## <a name="return-value-and-exception-handling"></a>Vrácení hodnoty a zpracování výjimek

<xref:System.Threading.Tasks.Parallel.For%2A>Vrátí <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> objekt po dokončení všech vláken. Tato návratová hodnota je užitečná v případě, že iterace smyčky nebo rušíte ručně, protože <xref:System.Threading.Tasks.ParallelLoopResult> ukládá informace, jako například poslední iterace, která proběhla po dokončení. Pokud dojde k jedné nebo více výjimkám v jednom z vláken, <xref:System.AggregateException?displayProperty=nameWithType> bude vyvolána výjimka.

V kódu v tomto příkladu není použita návratová hodnota <xref:System.Threading.Tasks.Parallel.For%2A> .

## <a name="analysis-and-performance"></a>Analýza a výkon

K zobrazení využití procesoru v počítači můžete použít Průvodce výkonem. V rámci experimentu zvyšte počet sloupců a řádků v maticích. Čím větší matrice, tím větší je rozdíl mezi paralelními a sekvenčními verzemi výpočtu. Když je matice malá, sekvenční verze se spustí rychleji z důvodu režie v nastavení paralelní smyčky.

Synchronní volání sdílených prostředků, jako je konzola nebo systém souborů, významně sníží výkon paralelní smyčky. Při měření výkonu se snažte vyhnout volání jako <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> v rámci smyčky.

## <a name="compile-the-code"></a>Kompilovat kód

Zkopírujte a vložte tento kód do projektu sady Visual Studio.

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Tasks.Parallel.For%2A>
- <xref:System.Threading.Tasks.Parallel.ForEach%2A>
- [Datový paralelismus](data-parallelism-task-parallel-library.md)
- [Paralelní programování](index.md)
