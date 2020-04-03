---
title: 'Postupy: Měření výkonu dotazu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 37bd3bc464f719876b2fe13ee1a11ebca4339988
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635820"
---
# <a name="how-to-measure-plinq-query-performance"></a>Postupy: Měření výkonu dotazu PLINQ

Tento příklad ukazuje, <xref:System.Diagnostics.Stopwatch> jak použít třídu k měření času, který trvá pro spuštění dotazu PLINQ.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `foreach` prázdnou smyčku (`For Each` v jazyce Visual Basic) k měření doby, která trvá spuštění dotazu. V kódu reálného světa smyčky obvykle obsahuje další kroky zpracování, které přidávají k celkové době spuštění dotazu. Všimněte si, že stopky není spuštěna až těsně před smyčky, protože to je při spuštění dotazu. Pokud požadujete více jemně odstupňovaného `ElapsedTicks` měření, `ElapsedMilliseconds`můžete použít vlastnost namísto .  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Celková doba provádění je užitečná metrika při experimentování s implementacemi dotazů, ale ne vždy vypovídá celý příběh. Chcete-li získat hlubší a bohatší zobrazení interakce vláken dotazu mezi sebou a s jinými spuštěnými procesy, použijte [vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Viz také

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
