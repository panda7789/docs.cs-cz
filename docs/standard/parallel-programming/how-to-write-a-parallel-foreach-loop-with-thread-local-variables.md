---
title: "Postupy: Zápis smyčky Parallel.ForEach pomocí proměnných v místním vláknu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4c65edd8959cbf5f83e3353770f71cad130953d1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-write-a-parallelforeach-loop-with-thread-local-variables"></a>Postupy: Zápis smyčky Parallel.ForEach pomocí proměnných v místním vláknu
Následující příklad znázorňuje, jakým způsobem lze zapisovat metodu <xref:System.Threading.Tasks.Parallel.ForEach%2A>, která používá místní proměnné vlákna. Při provedení smyčky <xref:System.Threading.Tasks.Parallel.ForEach%2A> dochází k rozdělení kolekce prostředků na několik oddílů. Jednotlivé oddíly obdrží vlastní kopii „místní proměnné vlákna“. (Termín „místní proměnné vlákna“ je mírně nepřesný, protože v některých případech mohou být na stejném vlákně spuštěny dva oddíly.)  
  
 Kód a parametry uvedené v tomto příkladu se velmi podobají příslušné metodě <xref:System.Threading.Tasks.Parallel.For%2A>. Další informace najdete v tématu [postupy: zápis smyčky Parallel.For pomocí proměnných Thread-Local](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md).  
  
 Pro použití v místní proměnné <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky, musí volat jeden z přetížení metody, která přebírá dva parametry typu. První parametr typu `TSource`, určuje typ source element a druhý parametr typu `TLocal`, určuje typ místní proměnné.  
  
## <a name="example"></a>Příklad  
 Následující příklad volání <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> přetížení výpočetní součet pole jeden milión elementů. Toto přetížení má čtyři parametry:  
  
-   `source`, což je zdroj dat. Musí implementovat <xref:System.Collections.Generic.IEnumerable%601>. Zdroj dat v našem příkladu je člen jeden milión `IEnumerable<Int32>` objekt vrácený <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> metoda.  
  
-   `localInit`, nebo funkci, která inicializuje místní proměnné. Tato funkce je volána jednou pro každý oddíl, ve kterém <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> provede operaci. Náš příklad inicializuje místní proměnné na hodnotu nula.  
  
-   `body`, <xref:System.Func%604> je vyvolané paralelní smyčky v každé iteraci smyčky. Podpis je `Func\<TSource, ParallelLoopState, TLocal, TLocal>`. Zadejte kód pro delegáta a předá smyčky vstupní parametry, které jsou:  
  
    -   Aktuální elementu <xref:System.Collections.Generic.IEnumerable%601>.  
  
    -   A <xref:System.Threading.Tasks.ParallelLoopState> proměnné používané v kódu tohoto delegáta pro zjištění stavu smyčky.  
  
    -   Místní proměnná.  
  
     Delegát vrátí místní proměnné, který se potom předá do další iterace smyčky, který se spustí v konkrétní oddílu. Každý oddíl smyčky udržuje samostatnou instanci této proměnné.  
  
     V příkladu delegát přidá do místní proměnné, který udržuje spuštěný hodnotu každý celé číslo celkový počet hodnot prvků celé číslo v oddílu.  
  
-   `localFinally`, `Action<TLocal>` delegáta, který <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> vyvolá po dokončení opakování operace v každém oddílu. <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> Metoda předává vaše `Action<TLocal>` delegáta konečná hodnota místní proměnné pro tuto přístup z více vláken (nebo smyčky oddílu), a zadejte kód, který provádí požadované akce pro kombinování výsledek z tohoto oddílu s výsledky z jiných oddílů. Tento delegát lze vyvolat souběžně s několika úkoly. Z toho důvodu se používá v příkladu <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> k synchronizaci přístup k `total` proměnné. Vzhledem k tomu, že delegát je typu <xref:System.Action%601>, neexistuje žádná návratová hodnota.  
  
 [!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
 [!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]  
  
## <a name="see-also"></a>Viz také  
 [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)  
 [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
