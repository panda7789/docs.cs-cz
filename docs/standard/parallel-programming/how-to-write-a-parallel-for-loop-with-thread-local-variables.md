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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139710"
---
# <a name="how-to-write-a-parallelfor-loop-with-thread-local-variables"></a>Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu
Tento příklad ukazuje, jak použít proměnné místní vlákno k uložení a načtení <xref:System.Threading.Tasks.Parallel.For%2A> stavu v každé samostatné úlohy, která je vytvořena smyčky. Pomocí místních dat podprocesu se můžete vyhnout režii synchronizace velkého počtu přístupů ke sdílenému stavu. Namísto zápisu do sdíleného prostředku v každé iteraci vypočítáte a uložíte hodnotu, dokud nebudou dokončeny všechny iterace pro úlohu. Konečný výsledek pak můžete zapsat jednou do sdíleného prostředku nebo jej předat jiné metodě.  
  
## <a name="example"></a>Příklad  
 Následující příklad volá <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metodu k výpočtu součtu hodnot v poli, které obsahuje jeden milion prvků. Hodnota každého prvku se rovná jeho indexu.  
  
 [!code-csharp[TPL_Parallel#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/forandforeach_simple.cs#05)]
 [!code-vb[TPL_Parallel#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/forwiththreadlocal.vb#05)]  
  
 První dva parametry <xref:System.Threading.Tasks.Parallel.For%2A> každé metody určují počáteční a koncové hodnoty iterace. V tomto přetížení metody třetí parametr je, kde inicializovat místní stav. V tomto kontextu místní stav znamená proměnnou, jejíž životnost sahá od těsně před první iteraci smyčky v aktuálním vlákně, těsně po poslední iteraci.  
  
 Typ třetího parametru <xref:System.Func%601> je `TResult` kde je typ proměnné, která bude ukládat místní stav vlákna. Jeho typ je definován argumentem obecného <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> typu, který je <xref:System.Int64>zadán při volání obecné metody, což je v tomto případě . Argument typu říká kompilátoru typ dočasné proměnné, která bude použita k uložení místního stavu vlákna. V tomto příkladu `() => 0` výraz `Function() 0` (nebo v jazyce Visual Basic) inicializuje místní proměnnou vlákna na nulu. Pokud je argument obecného typu typ odkazu nebo uživatelem definovaný typ hodnoty, výraz bude vypadat takto:  
  
```csharp  
() => new MyClass()  
```  
  
```vb  
Function() new MyClass()  
```  
  
 Čtvrtý parametr definuje logiku smyčky. Musí se jednat o výraz delegáta `Func<int, ParallelLoopState, long, long>` nebo lambda, jehož podpis je v jazyce C# nebo `Func(Of Integer, ParallelLoopState, Long, Long)` v jazyce Visual Basic. První parametr je hodnota čítače smyčky pro tuto iteraci smyčky. Druhý je <xref:System.Threading.Tasks.ParallelLoopState> objekt, který lze použít k přerušení ze smyčky; tento objekt je poskytován <xref:System.Threading.Tasks.Parallel> třídou pro každý výskyt smyčky. Třetí parametr je místní proměnná podprocesu. Poslední parametr je návratový typ. V tomto případě je <xref:System.Int64> typ, protože to je <xref:System.Threading.Tasks.Parallel.For%2A> typ, který jsme zadali v argumentu typu. Tato proměnná `subtotal` je pojmenována a je vrácena výrazem lambda. Vrácená hodnota se používá `subtotal` k inicializaci při každé následující iteraci smyčky. Tento poslední parametr si můžete také myslet jako hodnotu, která je `localFinally` předána každé iteraci a poté předána delegátovi po dokončení poslední iterace.  
  
 Pátý parametr definuje metodu, která je volána jednou, po dokončení všech iterací v určitém vlákně. Typ vstupní argument opět odpovídá argument typu <xref:System.Threading.Tasks.Parallel.For%60%601%28System.Int32%2CSystem.Int32%2CSystem.Func%7B%60%600%7D%2CSystem.Func%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%600%2C%60%600%7D%2CSystem.Action%7B%60%600%7D%29> metody a typ vrácený body lambda výraz. V tomto příkladu je hodnota přidána do proměnné v oboru <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> třídy bezpečným způsobem voláním metody. Pomocí proměnné místní vlákno jsme se vyhnuli zápisu do této proměnné třídy na každé iteraci smyčky.  
  
 Další informace o používání výrazů lambda naleznete [v tématu Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="see-also"></a>Viz také

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
