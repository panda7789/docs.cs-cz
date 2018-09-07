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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29da081784c06d8cd467f0566f9d4db92a130b53
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087271"
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Postupy: Zápis jednoduché smyčky Parallel.For
Toto téma obsahuje dva příklady, které ukazují <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody. První použití <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> přetížení metody a druhý používá <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> přetížení, dvě přetížení Nejjednodušší <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metody. Můžete použít tyto dvě přetížení <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metodu, když není potřeba zrušit smyčky, přerušit ze smyčky iterace nebo udržovat jakýkoli stav místního vlákna.  
  
> [!NOTE]
>  Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 První příklad vypočítá velikost souborů v jednom adresáři. Druhý vypočítá součin dvou matice.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je jednoduchého nástroje příkazového řádku, který vypočítá celková velikost souborů v adresáři. Očekává jako argument jeden adresář cestu a hlásí počet a celkovou velikost souborů v tomto adresáři. Po ověření, že adresář existuje, použije <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metodu pro vytvoření výčtu souborů v adresáři a určit jejich velikosti souborů. Velikost každého souboru se pak přidá do `totalSize` proměnné. Všimněte si, že přidání se provádí pomocí volání <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> tak, aby přidání se provádí jako atomickou operaci. V opačném případě by se mohl pokusit více úkolů aktualizovat `totalSize` proměnné současně.  
  
 [!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
 [!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metodu za účelem výpočtu součin dvou matice. Také ukazuje způsob použití <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> třídy porovnat výkon jednotlivých paralelní smyčky pomocí jiné paralelní smyčky. Všimněte si, že, protože to může generovat velké objemy výstup, v příkladu umožňuje výstup přesměrovat do souboru.  
  
 [!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
 [!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]  
  
 Paralelní provádění jakýkoli kód, včetně smyčky, jedním z cílů důležité je využívat co nejlépe bez procesory přes paralelním zpracováním bod, ve kterém nároky pro paralelní zpracování Neguje veškeré výhody výkonu. V tomto konkrétním příkladu je pouze vnější smyčka paralelizována, protože není k dispozici hodně práce provedené v vnitřní smyčku. Kombinace malé množství práce a mezipaměti nežádoucí účinky může způsobit snížení výkonu v paralelních smyčkách vnořené. Paralelní provádění vnější smyčky pouze tedy nejlepší způsob, jak zvýšit výhody souběžnosti ve většině systémů.  
  
## <a name="the-delegate"></a>Delegát  
 Třetí parametr toto přetížení <xref:System.Threading.Tasks.Parallel.For%2A> je delegát typu `Action<int>` v jazyce C# nebo `Action(Of Integer)` v jazyce Visual Basic. `Action` Delegáta, zda má nula, jeden nebo parametry šestnáct typu, vždy vrátí hodnotu typu void. V jazyce Visual Basic, chování `Action` je definována s `Sub`. Příklad používá výraz lambda k vytvoření delegáta, ale můžete vytvořit delegáta i jinými způsoby. Další informace najdete v tématu [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="the-iteration-value"></a>Hodnota iterace  
 Delegát používá jeden vstupní parametr, jehož hodnota je aktuální iterace. Hodnotu této iterace poskytuje modul runtime a jeho výchozí hodnota je index prvního prvku v segmentu (oddíl) zdroje, které jsou zpracovávány v aktuálním vláknu.  
  
 Pokud potřebujete větší kontrolu nad úroveň souběžnosti, použijte jednu z přetížení, která přijímá <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> vstupní parametr, jako například: <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>.  
  
## <a name="return-value-and-exception-handling"></a>Návratová hodnota a zpracování výjimek  
 <xref:System.Threading.Tasks.Parallel.For%2A> Vrátí <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> objekt po dokončení všech vláken. To vrátit hodnota je užitečná, když jsou zastavení nebo přerušení smyčky iterace ručně, protože <xref:System.Threading.Tasks.ParallelLoopResult> ukládá informace, jako je poslední iterace, který byl dokončen. Pokud na jedno z vláken, dojde k jedné nebo více výjimek <xref:System.AggregateException?displayProperty=nameWithType> bude vyvolána výjimka.  
  
 V kódu v tomto příkladu, návratová hodnota <xref:System.Threading.Tasks.Parallel.For%2A> se nepoužívá.  
  
## <a name="analysis-and-performance"></a>Analýzy a výkonu  
 Průvodce výkonem můžete použít k zobrazení využití procesoru ve vašem počítači. Jako experiment zvyšte počet sloupců a řádků v matricí. Čím větší matice, tím větší rozdíly ve výkonnosti mezi paralelní a sekvenční verze výpočtu. Při malém matice sekvenční verze budou pracovat rychleji z důvodu režie nastavení paralelní smyčky.  
  
 Synchronní volání sdílené prostředky, jako jsou konzole nebo systému souborů, se výrazně snížit výkon paralelní smyčky. Při měření výkonu, snažte se vyhnout volání, jako <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> v rámci smyčky.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Zkopírujte a vložte tento kód do projektu sady Visual Studio 2010.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Tasks.Parallel.For%2A>  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
