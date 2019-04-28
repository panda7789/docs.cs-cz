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
ms.openlocfilehash: 7cdb6e059fb1c7001bbe4da60e2936b1ad40cc1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638889"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Postupy: Zrušení smyček Parallel.For nebo ForEach
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metody podporují zrušení prostřednictvím použití tokenů zrušení. Další informace o zrušení obecné naleznete v tématu [zrušení](../../../docs/standard/threading/cancellation-in-managed-threads.md). V paralelních smyčkách, zadáte <xref:System.Threading.CancellationToken> v metodě <xref:System.Threading.Tasks.ParallelOptions> parametr a potom uzavřete paralelní volání do bloku try-catch.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zrušit volání <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Můžete použít stejný přístup k <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> volání.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Pokud je token, který signalizuje zrušení stejný token, který je uveden v <xref:System.Threading.Tasks.ParallelOptions> instance, pak paralelní smyčky vyvolá jedinou <xref:System.OperationCanceledException> na zrušení. Pokud způsobí jiný token zrušení, vyvolá výjimku smyčky <xref:System.AggregateException> s <xref:System.OperationCanceledException> jako InnerException.  
  
## <a name="see-also"></a>Viz také:

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
