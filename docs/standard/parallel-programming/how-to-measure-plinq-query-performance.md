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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd9e3a0ead62450e87225212f4fc6ecec6ec9489
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43867226"
---
# <a name="how-to-measure-plinq-query-performance"></a>Postupy: Měření výkonu dotazu PLINQ
Tento příklad ukazuje způsob použití <xref:System.Diagnostics.Stopwatch> třídy k měření čas potřebný k provedení PLINQ dotazu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu prázdný `foreach` smyčky (`For Each` v jazyce Visual Basic) k měření čas potřebný pro dotaz můžete spustit. V reálné kód smyčky obvykle obsahuje další kroky, které aplikacím dodávají doba provádění dotazu na celkový počet. Všimněte si, že je stopky spustit, až bude vždy před provedením smyčky, vzhledem k tomu, že začne provádění dotazu. Pokud budete potřebovat další jemné měření, můžete použít `ElapsedTicks` vlastnosti namísto `ElapsedMilliseconds`.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Celkové doby provádění je užitečné metriky, když jsou experimentování s implementacemi dotazu, ale to není vždy poskytují kompletní představu. Chcete-li získat podrobnější a bohatší zobrazení interakce vláken dotazů mezi sebou a s ostatními spuštěné procesy, použijte Vizualizátor souběžnosti. Další informace najdete v tématu [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Viz také:

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
