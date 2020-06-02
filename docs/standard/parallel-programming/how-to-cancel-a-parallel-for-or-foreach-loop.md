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
ms.openlocfilehash: d29137127dd47844f8f08d3ac689cf2827d9efe2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288222"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Postupy: Zrušení smyček Parallel.For nebo ForEach
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>Metody a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> podporují zrušení pomocí tokenů zrušení. Další informace o zrušení obecně naleznete v tématu [zrušení](../threading/cancellation-in-managed-threads.md). V paralelní smyčce můžete zadat <xref:System.Threading.CancellationToken> metodu do <xref:System.Threading.Tasks.ParallelOptions> parametru a potom uzavřít paralelní volání do bloku try-catch.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zrušit volání <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> . Můžete použít stejný přístup ke <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> volání.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Pokud token, který signalizuje zrušení, je stejný token, který je určen v <xref:System.Threading.Tasks.ParallelOptions> instanci, pak paralelní smyčka vyvolá jednu <xref:System.OperationCanceledException> při zrušení. Pokud nějaký jiný token způsobí zrušení, smyčka vyvolá výjimku <xref:System.AggregateException> s <xref:System.OperationCanceledException> jako InnerException.  
  
## <a name="see-also"></a>Viz také

- [Datový paralelismus](data-parallelism-task-parallel-library.md)
- [Výrazy lambda v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md)
