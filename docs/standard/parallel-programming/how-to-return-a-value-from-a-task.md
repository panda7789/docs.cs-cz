---
title: 'Postupy: Vrácení hodnoty z úlohy'
description: Podívejte se, jak použít typ System. Threading. Tasks. Task <TResult> k vrácení hodnoty z vlastnosti Result v .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: 051cef7cac654e4369ec1486884876004370ba0b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767972"
---
# <a name="how-to-return-a-value-from-a-task"></a>Postupy: Vrácení hodnoty z úlohy
Tento příklad znázorňuje používání typu <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> pro vrácení hodnoty z vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A>. Vyžaduje, aby adresář C:\Users\Public\Pictures\Sample Pictures\ existoval a aby obsahoval soubory.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 Vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A> blokuje volající vlákno, dokud úkol neskončí.  
  
 Informace o tom, jak předat výsledek jedné z <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> úloh pokračování, najdete v tématu [zřetězení úloh pomocí úloh pokračování](chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Viz také

- [Asynchronní programování založené na úlohách](task-based-asynchronous-programming.md)
- [Výrazy lambda v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md)
