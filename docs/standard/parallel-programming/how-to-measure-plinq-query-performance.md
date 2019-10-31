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
ms.openlocfilehash: 91b6165be2f4f464626fb25f7152de68de9d86e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124997"
---
# <a name="how-to-measure-plinq-query-performance"></a>Postupy: Měření výkonu dotazu PLINQ
Tento příklad ukazuje, jak použít třídu <xref:System.Diagnostics.Stopwatch> k měření doby potřebné k provedení dotazu PLINQ.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je použita prázdná smyčka `foreach` (`For Each` v Visual Basic) pro měření doby potřebné k provedení dotazu. Ve skutečném kódu smyčka obvykle obsahuje další kroky zpracování, které se přidávají do celkové doby provádění dotazu. Všimněte si, že Stopwatch není spuštěn, dokud není těsně před smyčkou, protože to je, když je zahájeno provádění dotazu. Pokud potřebujete přesnější měření, můžete místo `ElapsedMilliseconds`použít vlastnost `ElapsedTicks`.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Celková doba spuštění je užitečnou metrikou při experimentování s implementacemi dotazů, ale nikdy neříká celému článku. Chcete-li získat hlubší a širší pohled na interakci s vlákny dotazů mezi sebou a s jinými běžícími procesy, použijte Vizualizátor souběžnosti. Další informace najdete v tématu [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Viz také:

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
