---
title: 'Postupy: Zápis smyčky Parallel. ForEach s proměnnými místně rozdělenými na oddíly'
description: Podívejte se na příklad vytvoření smyčky Parallel. ForEach, která používá místní proměnné oddílu v rozhraní .NET.
ms.date: 06/26/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
ms.openlocfilehash: f598955fb2d6800f81bce050bdf474fc63bfb554
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599773"
---
# <a name="how-to-write-a-parallelforeach-loop-with-partition-local-variables"></a>Postupy: Zápis smyčky Parallel. ForEach s proměnnými místně rozdělenými na oddíly

Následující příklad ukazuje, jak napsat <xref:System.Threading.Tasks.Parallel.ForEach%2A> metodu, která používá místní proměnné oddílu. Při provedení smyčky <xref:System.Threading.Tasks.Parallel.ForEach%2A> dochází k rozdělení kolekce prostředků na několik oddílů. Každý oddíl má svou vlastní kopii místní proměnné oddílu. Místní proměnná oddílu je podobná [místní proměnné vlákna](xref:System.Threading.ThreadLocal%601)s tím rozdílem, že více oddílů může být spuštěno v jednom vlákně.

Kód a parametry uvedené v tomto příkladu se velmi podobají příslušné metodě <xref:System.Threading.Tasks.Parallel.For%2A>. Další informace naleznete v tématu [How to: Write a Parallel. for smyčke s proměnnými místními vlákny](how-to-write-a-parallel-for-loop-with-thread-local-variables.md).

Chcete-li použít místní proměnnou oddílu ve <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčce, je nutné zavolat jedno z přetížení metody, které přebírají dva parametry typu. První parametr typu, `TSource` , určuje typ zdrojového elementu a druhý parametr typu, `TLocal` Určuje typ místní proměnné oddílu.

## <a name="example"></a>Příklad

Následující příklad volá <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> přetížení pro výpočet součtu pole 1 000 000 prvků. Toto přetížení má čtyři parametry:

- `source`, což je zdroj dat. Musí implementovat <xref:System.Collections.Generic.IEnumerable%601> . Zdroj dat v našem příkladu je členský `IEnumerable<Int32>` objekt 1 000 000 vrácený <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> metodou.

- `localInit`nebo funkce, která inicializuje místní proměnnou oddílu. Tato funkce se volá jednou pro každý oddíl, ve kterém se <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> operace spouští. Náš příklad inicializuje místní proměnnou oddílu na nulu.

- `body`, <xref:System.Func%604> který je vyvolán paralelní smyčkou pro každou iteraci smyčky. Jeho signatura je `Func\<TSource, ParallelLoopState, TLocal, TLocal>` . Zadáte kód delegáta a smyčka projde vstupními parametry, které jsou:

  - Aktuální prvek <xref:System.Collections.Generic.IEnumerable%601> .

  - <xref:System.Threading.Tasks.ParallelLoopState>Proměnná, kterou můžete použít v kódu delegáta k prohlédnutí stavu smyčky.

  - Místní proměnná oddílu.

  Váš delegát vrátí místní proměnnou oddílu, která je poté předána do další iterace smyčky, která se spustí v daném oddílu. Každý oddíl Loop udržuje samostatnou instanci této proměnné.

  V tomto příkladu delegát přidá hodnotu každé celé číslo do místní proměnné oddílu, která udržuje průběžný součet hodnot celočíselných prvků v tomto oddílu.

- `localFinally`, `Action<TLocal>` delegát, který <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> vyvolá při dokončení operací smyčky v jednotlivých oddílech. <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>Metoda předá `Action<TLocal>` delegáta konečnou hodnotu místní proměnné oddílu pro tento oddíl smyčky a poskytnete kód, který provede požadovanou akci pro kombinování výsledků z tohoto oddílu s výsledky z ostatních oddílů. Tento delegát lze vyvolat souběžně s několika úkoly. Z tohoto důvodu příklad používá <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> metodu k synchronizaci přístupu k `total` proměnné. Vzhledem k tomu, že delegát je typu <xref:System.Action%601>, neexistuje žádná návratová hodnota.

[!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
[!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]

## <a name="see-also"></a>Viz také

- [Datový paralelismus](data-parallelism-task-parallel-library.md)
- [Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu](how-to-write-a-parallel-for-loop-with-thread-local-variables.md)
- [Výrazy lambda v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md)
