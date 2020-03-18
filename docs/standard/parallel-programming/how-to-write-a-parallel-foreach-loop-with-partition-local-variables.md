---
title: 'Postup: Zápis smyčky Parallel.ForEach s proměnnými local partition'
ms.date: 06/26/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
ms.openlocfilehash: cca48889670c3bd67366c879ccede94c89542c8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139684"
---
# <a name="how-to-write-a-parallelforeach-loop-with-partition-local-variables"></a>Postup: Zápis smyčky Parallel.ForEach s proměnnými local partition

Následující příklad ukazuje, jak <xref:System.Threading.Tasks.Parallel.ForEach%2A> napsat metodu, která používá proměnné místní oddíl. Při provedení smyčky <xref:System.Threading.Tasks.Parallel.ForEach%2A> dochází k rozdělení kolekce prostředků na několik oddílů. Každý oddíl má vlastní kopii místní proměnné oddílu. Místní proměnná oddílu je podobná [proměnné místní vlákno](xref:System.Threading.ThreadLocal%601), s tím rozdílem, že více oddílů lze spustit v jednom vlákně.

Kód a parametry uvedené v tomto příkladu se velmi podobají příslušné metodě <xref:System.Threading.Tasks.Parallel.For%2A>. Další informace naleznete v [tématu How to: Write a Parallel.For Loop with Thread-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md).

Chcete-li použít proměnnou <xref:System.Threading.Tasks.Parallel.ForEach%2A> local oddíl ve smyčce, musíte volat jednu z přetížení metody, která přebírá dva parametry typu. První parametr typu `TSource`, určuje typ zdrojového prvku a druhý `TLocal`parametr typu , určuje typ místní proměnné oddílu.

## <a name="example"></a>Příklad

Následující příklad volá <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> přetížení vypočítat součet pole jeden milion prvků. Toto přetížení má čtyři parametry:

- `source`, což je zdroj dat. Musí implementovat <xref:System.Collections.Generic.IEnumerable%601>. Zdroj dat v našem příkladu `IEnumerable<Int32>` je jeden <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> milion člen objektvrácený metodou.

- `localInit`nebo funkce, která inicializuje místní proměnnou oddílu. Tato funkce je volána jednou <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pro každý oddíl, ve kterém je operace spuštěna. Náš příklad inicializuje místní proměnnou oddílu na nulu.

- `body`, <xref:System.Func%604> který je vyvolán paralelní smyčky na každé iteraci smyčky. Jeho podpis `Func\<TSource, ParallelLoopState, TLocal, TLocal>`je . Zadáte kód delegáta a smyčka předá vstupní parametry, které jsou:

  - Aktuální prvek <xref:System.Collections.Generic.IEnumerable%601>rozhraní .

  - Proměnná, <xref:System.Threading.Tasks.ParallelLoopState> kterou můžete použít v kódu delegáta ke kontrole stavu smyčky.

  - Místní proměnná oddílu.

  Delegát vrátí místní proměnnou oddílu, která je pak předána další iteraci smyčky, která se spustí v daném oddílu. Každý oddíl smyčky udržuje samostatnou instanci této proměnné.

  V příkladu delegát přidá hodnotu každého celého čísla k místní proměnné oddílu, která udržuje průběžný součet hodnot celočíselných prvků v tomto oddílu.

- `localFinally`, `Action<TLocal>` delegát, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> který vyvolá po dokončení operací opakování v každém oddílu. Metoda <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> předá `Action<TLocal>` delegáta konečnou hodnotu místní proměnné oddílu pro tento oddíl smyčky a zadáte kód, který provede požadovanou akci pro kombinaci výsledku z tohoto oddílu s výsledky z jiných oddílů. Tento delegát lze vyvolat souběžně s několika úkoly. Z tohoto důvodu příklad <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> používá metodu k `total` synchronizaci přístupu k proměnné. Vzhledem k tomu, že delegát je typu <xref:System.Action%601>, neexistuje žádná návratová hodnota.

[!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
[!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]

## <a name="see-also"></a>Viz také

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
