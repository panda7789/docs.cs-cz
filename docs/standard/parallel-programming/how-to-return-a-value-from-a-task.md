---
title: 'Postupy: Vrácení hodnoty z úlohy'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: 495f68114bfe960b8182be4ab76b72043b2d0cc7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141670"
---
# <a name="how-to-return-a-value-from-a-task"></a>Postupy: Vrácení hodnoty z úlohy
Tento příklad znázorňuje používání typu <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> pro vrácení hodnoty z vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A>. Vyžaduje, aby adresář C:\Users\Public\Pictures\Sample Pictures\ existoval a aby obsahoval soubory.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 Vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A> blokuje volající vlákno, dokud úkol neskončí.  
  
 Chcete-li zjistit, jak předat výsledek jednoho <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> k úloze pokračování, přečtěte si téma [zřetězení úloh pomocí úloh pokračování](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní programování založené na úlohách](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
