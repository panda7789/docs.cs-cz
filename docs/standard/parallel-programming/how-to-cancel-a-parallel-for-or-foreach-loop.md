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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce9b8b0864f3ed30c2ff03866abdb0d5d07991db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Postupy: Zrušení smyček Parallel.For nebo ForEach
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody podporují zrušení prostřednictvím zrušení tokenů. Další informace o zrušení obecně platí, najdete v části [zrušení](../../../docs/standard/threading/cancellation-in-managed-threads.md). V paralelní smyčky, zadáte <xref:System.Threading.CancellationToken> metodu v <xref:System.Threading.Tasks.ParallelOptions> parametr a potom uzavřete paralelní volání do bloku try-catch.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zrušit volání <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Můžete použít ve stejný přístup k <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> volání.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Pokud je token, který signalizuje zrušení stejný token, který je určen v <xref:System.Threading.Tasks.ParallelOptions> instance, pak paralelní smyčky vyvolá jedinou <xref:System.OperationCanceledException> na zrušení. Pokud jiný token zrušení způsobí, že opakování ve smyčce vyvolá <xref:System.AggregateException> s <xref:System.OperationCanceledException> jako InnerException.  
  
## <a name="see-also"></a>Viz také  
 [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
