---
title: "Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu"
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
helpviewer_keywords: parallel for loops, how to use local state
ms.assetid: 68384064-7ee7-41e2-90e3-71f00bde01bb
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e0b3e28c95d9ccfb0ecd1954e16960576d8f115
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu
Tento příklad ukazuje, jak používat k ukládání a načítání stavu v každé samostatné úloze, který vytváří lokální proměnné vláken <xref:System.Threading.Tasks.Parallel.For%2A> smyčky. Pomocí místní data, se můžete vyhnout nároky na velký počet přístupů do sdíleného stavu synchronizace. Místo na každé iteraci zápis do sdíleného prostředku, výpočty a uložení hodnoty, dokud nebudou dokončeny všechny iterace pro úlohu. Potom můžete zapisovat konečný výsledek jednou sdílený prostředek nebo předejte ji na jinou metodu.  
  
## <a name="example"></a>Příklad  
 Následující příklad volání <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metodu pro výpočet součet hodnot v pole obsahující jeden milión elementy. Hodnota jednotlivých prvků se rovná její index.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 První dva parametry každých <xref:System.Threading.Tasks.Parallel.For%2A> metoda zadejte počáteční a koncové hodnoty iterací. Toto přetížení metody je třetí parametr kde inicializovat lokálního stavu. V tomto kontextu místní stav znamená proměnnou, jejichž doba platnosti rozšiřuje z těsně před první iteraci smyčky na aktuální vlákno těsně po poslední iteraci.  
  
 Typ třetího parametru je <xref:System.Func%601> kde `TResult` je typ proměnné, které se uloží místní stav. Typ je definované argument obecného typu zadaný při volání metody obecná <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metodu, která v tomto případě je <xref:System.Int64>. Argument typu říká kompilátoru typ dočasné proměnné, která se použije k uložení místní stav. V tomto příkladu výraz `() => 0` (nebo `Function() 0` v jazyce Visual Basic) inicializuje místní proměnné na hodnotu nula. Pokud je argument obecného typu odkaz nebo hodnotu definovanou uživatelem typem, bude výraz vypadat takto:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Čtvrtého parametru definuje logiku smyčky. Musí být výraz delegáta nebo lambda, jejichž podpis je `Func<int, ParallelLoopState, long, long>` v jazyce C# nebo `Func(Of Integer, ParallelLoopState, Long, Long)` v jazyce Visual Basic. První parametr je hodnota čítače smyčky pro tento iteraci smyčky. Druhý <xref:System.Threading.Tasks.ParallelLoopState> objektu, který slouží k přerušení mimo smyčku; tento objekt poskytuje <xref:System.Threading.Tasks.Parallel> třída pro všechny výskyty smyčky. Třetí parametr není místní proměnné. Poslední parametr je návratový typ. V takovém případě je typ <xref:System.Int64> vzhledem k tomu, který je typem jsme uvedli v <xref:System.Threading.Tasks.Parallel.For%2A> argument typu. Tuto proměnnou jmenuje `subtotal` a vrátí výrazu lambda. Návratová hodnota se používá k chybě při inicializaci `subtotal` na každé následné iteraci smyčky. Si můžete také představit tento poslední parametr jako hodnotu, která je předán každé iteraci a pak předá do `localFinally` delegovat po dokončení posledního iterací.  
  
 Definuje pátého parametru metody, která je volána jednou, po dokončení všech iterací na konkrétní vlákno. Typ vstupní argument znovu odpovídá typu argument <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metoda a typ vrácený výrazem lambda textu. V tomto příkladu je přidána hodnota proměnné v oboru třída bezpečným způsobem vlákno voláním <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> metoda. Pomocí místní proměnné budeme mít předejde zápis do této třídy proměnné v každé iteraci smyčky.  
  
 Další informace o tom, jak použití výrazů lambda najdete v tématu [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Viz také  
 [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
