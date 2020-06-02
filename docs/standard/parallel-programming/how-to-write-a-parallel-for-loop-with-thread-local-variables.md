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
ms.openlocfilehash: bb6ac1a64c3a71646946d1af894d1124b12e4769
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290756"
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu
Tento příklad ukazuje, jak použít proměnné místního vlákna k ukládání a načítání stavu v každé samostatné úloze, která je vytvořena <xref:System.Threading.Tasks.Parallel.For%2A> smyčkou. Pomocí místních dat vlákna se můžete vyhnout režie synchronizace velkého počtu přístupů ke sdílenému stavu. Místo psaní do sdíleného prostředku v každé iteraci vypočítáte a uložíte hodnotu, dokud nebudou všechny iterace úlohy dokončeny. Nakonec můžete zapsat konečný výsledek do sdíleného prostředku nebo ho předat jiné metodě.  
  
## <a name="example"></a>Příklad  
 Následující příklad volá <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metodu pro výpočet součtu hodnot v poli, které obsahuje prvky 1 000 000. Hodnota každého prvku se rovná jeho indexu.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 První dva parametry každé <xref:System.Threading.Tasks.Parallel.For%2A> metody určují počáteční a koncovou hodnotu iterace. V tomto přetížení metody třetí parametr je místo, kde inicializujete svůj místní stav. V tomto kontextu znamená místní stav proměnnou, jejíž životnost přesahuje těsně před první iterací smyčky v aktuálním vlákně, a to bezprostředně za poslední iterací.  
  
 Typ třetího parametru je, <xref:System.Func%601> kde `TResult` je typ proměnné, která bude ukládat místní stav vlákna. Jeho typ je definován argumentem obecného typu zadaným při volání obecné <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metody, která v tomto případě je <xref:System.Int64> . Argument typu instruuje kompilátor typ dočasné proměnné, která bude použita k uložení místního stavu vlákna. V tomto příkladu výraz `() => 0` (nebo `Function() 0` v Visual Basic) inicializuje proměnnou místního vlákna na hodnotu nula. Pokud je argumentem obecného typu typ odkazu nebo uživatelsky definovaný typ hodnoty, výraz by vypadal takto:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Čtvrtý parametr definuje logiku smyčky. Musí se jednat o delegáta nebo výraz lambda, jehož signatura je `Func<int, ParallelLoopState, long, long>` v jazyce C# nebo `Func(Of Integer, ParallelLoopState, Long, Long)` v Visual Basic. První parametr je hodnota čítače smyčky pro tuto iteraci smyčky. Druhým je <xref:System.Threading.Tasks.ParallelLoopState> objekt, který lze použít k přerušení smyčky; tento objekt je poskytován <xref:System.Threading.Tasks.Parallel> třídou pro každý výskyt smyčky. Třetí parametr je proměnná lokální pro vlákno. Poslední parametr je návratový typ. V tomto případě je typ <xref:System.Int64> , protože se jedná o typ, který jsme určili v <xref:System.Threading.Tasks.Parallel.For%2A> argumentu typu. Tato proměnná je pojmenována `subtotal` a je vrácena výrazem lambda. Návratová hodnota se používá k inicializaci `subtotal` při každé další iteraci smyčky. Tento poslední parametr si také můžete představit jako hodnotu, která je předána každé iteraci a poté předána `localFinally` delegátovi po dokončení poslední iterace.  
  
 Pátý parametr definuje metodu, která je volána jednou, po dokončení všech iterací v konkrétním vlákně. Typ vstupního argumentu znovu odpovídá argumentu typu <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metody a typu vrácené výrazem lambda těla. V tomto příkladu je hodnota přidána do proměnné v rozsahu třídy v bezpečném způsobu vlákna voláním <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> metody. Pomocí proměnné místního vlákna se při každé iteraci smyčky vyhneme psaní do této proměnné třídy.  
  
 Další informace o použití výrazů lambda naleznete v tématu [lambda výrazy v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Viz také

- [Datový paralelismus](data-parallelism-task-parallel-library.md)
- [Paralelní programování](index.md)
- [Task Parallel Library (TPL)](task-parallel-library-tpl.md)
- [Výrazy lambda v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md)
