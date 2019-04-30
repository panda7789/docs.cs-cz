---
title: 'Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel for loops, how to use local state
ms.assetid: 68384064-7ee7-41e2-90e3-71f00bde01bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ffac3df82268399aa35ff494e462e2b23c3894b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61915541"
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu
Tento příklad ukazuje způsob použití místní proměnné vlákna k ukládání a načítání stavu v každé samostatné úlohy, který je vytvořen pomocí <xref:System.Threading.Tasks.Parallel.For%2A> smyčky. Pomocí dat thread local se můžete vyhnout nároky na velký počet přístupů na sdílený stav synchronizace. Místo psaní ke sdíleným prostředkům při každé iteraci, compute a uložte hodnotu, dokud nejsou dokončeny všechny iterace pro úlohu. Můžete napsat konečný výsledek jednou ke sdílenému prostředku nebo předávat na jinou metodu.  
  
## <a name="example"></a>Příklad  
 Následující příklad volá <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metodu pro výpočet součtu hodnot v poli, který obsahuje prvky jednoho milionu. Hodnota každého prvku je rovna jeho index.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 První dva parametry každé <xref:System.Threading.Tasks.Parallel.For%2A> metody zadejte počáteční a koncové hodnoty iterace. V tomto přetížení metody třetí parametr je, kde bude inicializovat místní stavu. V tomto kontextu označuje stav místní proměnná, jehož doba života sahá od těsně před první iteraci smyčky v aktuálním vláknu, jenom po poslední iteraci.  
  
 Typ třetí parametr je <xref:System.Func%601> kde `TResult` je typ proměnné, ve kterém bude uložený stav místního vlákna. Jeho typ je definován zadaný při volání metody obecný argument obecného typu <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metodu, která v tomto případě je <xref:System.Int64>. Argument typu instruuje kompilátor, typ dočasné proměnné, který se použije k uložení stavu místního vlákna. V tomto příkladu výraz `() => 0` (nebo `Function() 0` v jazyce Visual Basic) inicializuje proměnná místního vlákna na nulu. Pokud argument obecného typu je typem odkazu nebo typ uživatelem definovanou hodnotu, bude výraz vypadat takto:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Čtvrtý parametr definuje logiky smyčky. Musí být delegát nebo lambda výraz, jehož předpis je `Func<int, ParallelLoopState, long, long>` v jazyce C# nebo `Func(Of Integer, ParallelLoopState, Long, Long)` v jazyce Visual Basic. První parametr je hodnota čítače cyklů pro danou iteraci smyčky. Druhým je <xref:System.Threading.Tasks.ParallelLoopState> objektu, který je možné přerušit ze smyčky; tento objekt je poskytována <xref:System.Threading.Tasks.Parallel> třídu pro všechny výskyty smyčky. Třetí parametr je proměnná místního vlákna. Poslední parametr je návratovým typem. V takovém případě je typ <xref:System.Int64> vzhledem k tomu, který je typem jsme uvedli v <xref:System.Threading.Tasks.Parallel.For%2A> argument typu. Tato proměnná je s názvem `subtotal` a je vrácený výraz lambda. Vrácená hodnota je použita k inicializaci `subtotal` při každé další iteraci smyčky. Tento poslední parametr také můžete představit jako hodnotu, která je předána každé iterace a potom předány `localFinally` delegovat po dokončení se poslední iteraci.  
  
 Definuje pátého parametru metody, která je volána, po dokončení všech iterací na konkrétní vlákno. Typ vstupní argument znovu odpovídá argument typu <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metoda a typ vrácený tělo výrazu lambda. V tomto příkladu hodnota se přidá do proměnné v oboru třídy bezpečným způsobem vlákno voláním <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> metody. Pomocí proměnná místního vlákna, můžeme mít vyhnout zápis do proměnné této třídy v každé iteraci smyčky.  
  
 Další informace o tom, jak použít výrazy lambda naleznete v tématu [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Viz také:

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
