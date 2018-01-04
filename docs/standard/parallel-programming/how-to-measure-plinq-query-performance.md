---
title: "Postupy: Měření výkonu dotazu PLINQ"
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
helpviewer_keywords: PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fe19fd6ae7730a30a9ccc8a39b99a31981f838fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-measure-plinq-query-performance"></a>Postupy: Měření výkonu dotazu PLINQ
Tento příklad ukazuje, jak používat <xref:System.Diagnostics.Stopwatch> třída k měření doby potřebné pro PLINQ dotazu provést.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá prázdnou `foreach` smyčky (`For Each` v jazyce Visual Basic) k měření doby potřebné k provedení dotazu. V kódu reálného smyčky obvykle obsahuje další zpracování kroky, které přidat do doba provádění dotazu na celkový počet. Všimněte si, že stopky není spustit, dokud nebude jen před smyčky, protože se jedná, kdy se zahájí spuštění dotazu. Pokud budete potřebovat další podrobných měření, můžete použít `ElapsedTicks` vlastnost místo `ElapsedMilliseconds`.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Celková doba provádění je užitečné metriky, když testujete implementace dotazu, ale jeho není vždy všechno. Chcete-li získat podrobnější a bohatší zobrazení interakce vláken dotazu sebou a s jinými spuštěné procesy, použijte vizualizér souběžnosti. Další informace najdete v tématu [vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Viz také  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
