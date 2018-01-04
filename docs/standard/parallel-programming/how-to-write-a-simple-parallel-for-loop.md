---
title: "Postupy: Zápis jednoduché smyčky Parallel.For"
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
helpviewer_keywords:
- Parallel.For, How to Write
- for loop, parallel construction in .NET
- parallel for loops, how to use
ms.assetid: 9029ba7f-a9d1-4526-8c84-c88716dba5d4
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3a70dcb5e3811a18e23aeb2ebf0940d2c52f49a9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Postupy: Zápis jednoduché smyčky Parallel.For
Toto téma obsahuje dva příklady, které ilustrují <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metoda. První používá <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> přetížení metody a druhý používá <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> přetížení, dva nejjednodušší přetížení <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metoda. Můžete použít tyto dvě přetížení <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metoda, když není potřeba zrušit smyčky, rozdělit mimo iterace smyčky nebo udržovat žádné místní stav.  
  
> [!NOTE]
>  Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s výrazy lambda v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 V prvním příkladu vypočítá velikost souborů v jednom adresáři. Druhou je výpočet součin dvou matice.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je jednoduchého nástroje příkazového řádku, která by vypočítala celková velikost souborů v adresáři. Očekává jako argument cestu jednoho adresářového a sestavy počtu a celkové velikosti souborů v tomto adresáři. Po ověření, zda adresář existuje, použije <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metodu pro vytvoření výčtu souborů v adresáři a určit jejich velikosti souborů. Velikost každého souboru se pak přidá do `totalSize` proměnné. Všimněte si, že se přidání provádí volání <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> tak, aby se provádí přidání jako atomickou operaci. Jinak hodnota mohou zkuste aktualizovat více úloh `totalSize` proměnná současně.  
  
 [!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
 [!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> metoda vypočítat součin dvou matice. Také ukazuje, jak používat <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> třída porovnat výkon paralelní smyčky pomocí jiných paralelní smyčky. Všimněte si, že, protože to může generovat značný výstupu, příklad umožňuje výstup přesměrovat do souboru.  
  
 [!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
 [!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]  
  
 Při paralelním prováděním žádný kód, včetně smyčky, jeden důležité cílem je využít co nejvíce bez procesory přes paralelním prováděním do bodu, kde režijní náklady pro paralelní zpracování Neguje žádné výhody výkonu. V tomto konkrétním příkladu je paralelizovaná pouze vnější smyčku několika málo vzhledem k tomu, že není k dispozici hodně práce v informacích o vnitřní smyčky. Kombinace malé množství práce a mezipaměti nežádoucí účinky může způsobit snížení výkonu ve vnořených paralelní smyčky. Vytváření paralelní smyčky vnější pouze tedy nejlepší způsob, jak zvýšit výhody souběžnosti u většiny systémů.  
  
## <a name="the-delegate"></a>Delegát  
 Třetí parametr funkce toto přetížení <xref:System.Threading.Tasks.Parallel.For%2A> je delegáta typu `Action<int>` v jazyce C# nebo `Action(Of Integer)` v jazyce Visual Basic. `Action` Delegáta, zda má nula, jednu nebo parametry šestnáct typu vždy vrátí prázdnou hodnotu. V jazyce Visual Basic, chování `Action` je definovaná pomocí `Sub`. Tento příklad používá k vytvoření delegát výrazu lambda, ale delegát můžete vytvořit také jiné způsoby. Další informace najdete v tématu [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="the-iteration-value"></a>Hodnota iterace  
 Delegát používá jeden vstupní parametr, jehož hodnota je aktuální. Tuto hodnotu iterace poskytuje modulem runtime a jeho výchozí hodnota je index první prvek v segmentu (oddíl) zdroje, které jsou zpracovávány v aktuální vlákno.  
  
 Pokud potřebujete větší kontrolu nad úroveň souběžnosti, použijte jednu z přetížení, která přebírá <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> vstupní parametr, jako například: <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>.  
  
## <a name="return-value-and-exception-handling"></a>Vrátí hodnotu a zpracování výjimek  
 <xref:System.Threading.Tasks.Parallel.For%2A>Vrátí <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> objektu po dokončení všech vláken. Tato vrátí hodnotu je užitečné, když chcete přestat nebo ukončování řádků pro cykly iterace ručně, protože <xref:System.Threading.Tasks.ParallelLoopResult> ukládá informace, jako jsou poslední iterace, který byl dokončen. Pokud na jednom vláken, dojde k jedné nebo několika výjimkám <xref:System.AggregateException?displayProperty=nameWithType> bude vyvolána.  
  
 V kódu v tomto příkladu návratová hodnota <xref:System.Threading.Tasks.Parallel.For%2A> nepoužívá.  
  
## <a name="analysis-and-performance"></a>Analýzy a výkonu  
 Průvodce výkonu můžete zobrazit využití procesoru ve vašem počítači. Stejně jako experimentu zvýšíte počet sloupců a řádků v matice. Větší matice, tím větší rozdíl mezi výkonem paralelní a sekvenční verzích výpočet. Při malém matice sekvenční verze bude rychlejší spustit z důvodu režijní náklady v nastavení paralelní smyčky.  
  
 Synchronní volání ke sdíleným prostředkům, jako jsou konzole nebo systému souborů, se výrazně snížit výkon paralelní smyčky. Při měření výkonu, pokuste se vyhnout volání, jako <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> v rámci smyčky.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Zkopírujte a vložte tento kód do projektu sady Visual Studio 2010.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Tasks.Parallel.For%2A>  
 <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
 [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
