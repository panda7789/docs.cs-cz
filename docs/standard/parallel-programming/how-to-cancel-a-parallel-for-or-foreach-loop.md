---
title: 'Postupy: Zrušení smyček Parallel.For nebo ForEach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
ms.openlocfilehash: 67f1f91f235cc88deaa97d412f368819ae0a8cda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134235"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Postupy: Zrušení smyček Parallel.For nebo ForEach
Metody <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> a podporují zrušení pomocí tokenů zrušení. Další informace o zrušení obecně naleznete v tématu [Zrušení](../../../docs/standard/threading/cancellation-in-managed-threads.md). V paralelní smyčce zadáte <xref:System.Threading.CancellationToken> metodu v <xref:System.Threading.Tasks.ParallelOptions> parametru a pak uzavřete paralelní volání do bloku try-catch.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zrušit <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>volání do . Můžete použít stejný přístup <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> k volání.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Pokud token, který signalizuje zrušení je stejný <xref:System.Threading.Tasks.ParallelOptions> token, který je zadán v <xref:System.OperationCanceledException> instanci, pak paralelní smyčky vyvolá jeden na zrušení. Pokud některé jiné token způsobí zrušení, <xref:System.AggregateException> smyčky <xref:System.OperationCanceledException> vyvolá s jako InnerException.  
  
## <a name="see-also"></a>Viz také

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
