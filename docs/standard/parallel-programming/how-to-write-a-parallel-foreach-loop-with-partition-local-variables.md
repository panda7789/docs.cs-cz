---
title: 'Postupy: zápis smyčky Parallel.ForEach pomocí proměnných oddílu místní'
ms.date: 06/26/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: edcc390014cfc70f4da4f72270c7dd53f9b9423b
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37076265"
---
# <a name="how-to-write-a-parallelforeach-loop-with-partition-local-variables"></a>Postupy: zápis smyčky Parallel.ForEach pomocí proměnných oddílu místní
Následující příklad ukazuje, jak napsat <xref:System.Threading.Tasks.Parallel.ForEach%2A> metoda, která používá oddílu místní proměnné. Při provedení smyčky <xref:System.Threading.Tasks.Parallel.ForEach%2A> dochází k rozdělení kolekce prostředků na několik oddílů. Každý oddíl má svou vlastní kopii oddílu místní proměnné. Je podobná oddílu místní proměnné [místní proměnné](xref:System.Threading.ThreadLocal%601), s výjimkou toho, aby více oddílů na jedno vlákno.
  
 Kód a parametry uvedené v tomto příkladu se velmi podobají příslušné metodě <xref:System.Threading.Tasks.Parallel.For%2A>. Další informace najdete v tématu [postupy: zápis smyčky Parallel.For pomocí proměnných Thread-Local](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md).  
  
 Pro použití v oddílu místní proměnné <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky, musí volat jeden z přetížení metody, která přebírá dva parametry typu. První parametr typu `TSource`, určuje typ source element a druhý parametr typu `TLocal`, určuje typ oddílu místní proměnné.  
  
## <a name="example"></a>Příklad  
 Následující příklad volání <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> přetížení výpočetní součet pole jeden milión elementů. Toto přetížení má čtyři parametry:  
  
-   `source`, což je zdroj dat. Musí implementovat <xref:System.Collections.Generic.IEnumerable%601>. Zdroj dat v našem příkladu je člen jeden milión `IEnumerable<Int32>` objekt vrácený <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> metoda.  
  
-   `localInit`, nebo funkci, která inicializuje proměnnou místního oddílu. Tato funkce je volána jednou pro každý oddíl, ve kterém <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> provede operaci. Náš příklad inicializuje oddílu místní proměnné na hodnotu nula.  
  
-   `body`, <xref:System.Func%604> je vyvolané paralelní smyčky v každé iteraci smyčky. Podpis je `Func\<TSource, ParallelLoopState, TLocal, TLocal>`. Zadejte kód pro delegáta a předá smyčky vstupní parametry, které jsou:  
  
    -   Aktuální elementu <xref:System.Collections.Generic.IEnumerable%601>.
  
    -   A <xref:System.Threading.Tasks.ParallelLoopState> proměnné používané v kódu tohoto delegáta pro zjištění stavu smyčky.  
  
    -   Oddíl místní proměnné.  
  
     Delegát vrátí proměnnou místního oddílu, který se potom předá do další iterace smyčky, který se spustí v konkrétní oddílu. Každý oddíl smyčky udržuje samostatnou instanci této proměnné.  
  
     V příkladu delegát přidá hodnotu každý celé číslo oddílu místní proměnné, který udržuje spuštěný celkový počet hodnot prvků celé číslo v oddílu.  
  
-   `localFinally`, `Action<TLocal>` delegáta, který <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> vyvolá po dokončení opakování operace v každém oddílu. <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> Metoda předává vaše `Action<TLocal>` delegovat konečná hodnota proměnné místního oddílu pro tento oddíl smyčky, a zadejte kód, který provádí požadované akce pro kombinování výsledek z tohoto oddílu se výsledky z ostatní oddíly. Tento delegát lze vyvolat souběžně s několika úkoly. Z toho důvodu se používá v příkladu <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> k synchronizaci přístup k `total` proměnné. Vzhledem k tomu, že delegát je typu <xref:System.Action%601>, neexistuje žádná návratová hodnota.  
  
 [!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
 [!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]  
  
## <a name="see-also"></a>Viz také  
 [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)  
 [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
