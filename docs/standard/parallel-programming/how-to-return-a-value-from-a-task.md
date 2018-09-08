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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af0f82e66da1c8db5e17863dfad861c8a7d195e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44217214"
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="d9b43-102">Postupy: Vrácení hodnoty z úlohy</span><span class="sxs-lookup"><span data-stu-id="d9b43-102">How to: Return a Value from a Task</span></span>
<span data-ttu-id="d9b43-103">Tento příklad znázorňuje používání typu <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> pro vrácení hodnoty z vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A>.</span><span class="sxs-lookup"><span data-stu-id="d9b43-103">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="d9b43-104">Vyžaduje, aby adresář C:\Users\Public\Pictures\Sample Pictures\ existoval a aby obsahoval soubory.</span><span class="sxs-lookup"><span data-stu-id="d9b43-104">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9b43-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9b43-105">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="d9b43-106">Vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A> blokuje volající vlákno, dokud úkol neskončí.</span><span class="sxs-lookup"><span data-stu-id="d9b43-106">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="d9b43-107">Informace o tom, k předání výsledku jedné vlastnosti <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> úkolu pokračování naleznete v tématu [řetězení úloh pomocí úloh pokračování používání](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="d9b43-107">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b43-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9b43-108">See also</span></span>

- [<span data-ttu-id="d9b43-109">Asynchronní programování založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="d9b43-109">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
- [<span data-ttu-id="d9b43-110">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="d9b43-110">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
