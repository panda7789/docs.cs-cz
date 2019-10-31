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
ms.openlocfilehash: 14f4f1402f564d38bb508e893521a3951c1509f4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139710"
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu
Tento příklad ukazuje, jak použít proměnné místního vlákna k ukládání a načítání stavu v každé samostatné úloze, která je vytvořena pomocí smyčky <xref:System.Threading.Tasks.Parallel.For%2A>. Pomocí místních dat vlákna se můžete vyhnout režie synchronizace velkého počtu přístupů ke sdílenému stavu. Místo psaní do sdíleného prostředku v každé iteraci vypočítáte a uložíte hodnotu, dokud nebudou všechny iterace úlohy dokončeny. Nakonec můžete zapsat konečný výsledek do sdíleného prostředku nebo ho předat jiné metodě.  
  
## <a name="example"></a>Příklad  
 Následující příklad volá metodu <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> pro výpočet součtu hodnot v poli, které obsahuje prvky 1 000 000. Hodnota každého prvku se rovná jeho indexu.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 První dva parametry každé metody <xref:System.Threading.Tasks.Parallel.For%2A> určují počáteční a koncovou hodnotu iterace. V tomto přetížení metody třetí parametr je místo, kde inicializujete svůj místní stav. V tomto kontextu znamená místní stav proměnnou, jejíž životnost přesahuje těsně před první iterací smyčky v aktuálním vlákně, a to bezprostředně za poslední iterací.  
  
 Typ třetího parametru je <xref:System.Func%601>, kde `TResult` je typ proměnné, která bude ukládat místní stav vlákna. Jeho typ je definován argumentem obecného typu zadaným při volání obecné metody <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29>, která v tomto případě je <xref:System.Int64>. Argument typu instruuje kompilátor typ dočasné proměnné, která bude použita k uložení místního stavu vlákna. V tomto příkladu výraz `() => 0` (nebo `Function() 0` v Visual Basic) inicializuje místní proměnnou vlákna na nulu. Pokud je argumentem obecného typu typ odkazu nebo uživatelsky definovaný typ hodnoty, výraz by vypadal takto:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Čtvrtý parametr definuje logiku smyčky. Musí se jednat o delegáta nebo výraz lambda, jehož signatura C# je `Func<int, ParallelLoopState, long, long>` v nebo `Func(Of Integer, ParallelLoopState, Long, Long)` v Visual Basic. První parametr je hodnota čítače smyčky pro tuto iteraci smyčky. Druhým je objekt <xref:System.Threading.Tasks.ParallelLoopState>, který lze použít k přerušení smyčky; Tento objekt je poskytován třídou <xref:System.Threading.Tasks.Parallel> pro všechny výskyty smyčky. Třetí parametr je proměnná lokální pro vlákno. Poslední parametr je návratový typ. V tomto případě je typ <xref:System.Int64>, protože se jedná o typ, který jsme určili v argumentu typu <xref:System.Threading.Tasks.Parallel.For%2A>. Tato proměnná je pojmenována `subtotal` a je vrácena výrazem lambda. Návratová hodnota se používá k inicializaci `subtotal` při každé další iteraci smyčky. Tento poslední parametr můžete také považovat za hodnotu, která je předána každé iteraci a poté předána `localFinally` delegátovi po dokončení poslední iterace.  
  
 Pátý parametr definuje metodu, která je volána jednou, po dokončení všech iterací v konkrétním vlákně. Typ vstupního argumentu znovu odpovídá argumentu typu metody <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> a typu vrácené výrazem lambda těla. V tomto příkladu je hodnota přidána do proměnné v rozsahu třídy v bezpečném způsobu vlákna voláním metody <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType>. Pomocí proměnné místního vlákna se při každé iteraci smyčky vyhneme psaní do této proměnné třídy.  
  
 Další informace o použití výrazů lambda naleznete v tématu [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Viz také:

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
