---
title: "Postupy: Rozbalení vnořené úlohy"
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
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 06d54efe5c8bac58746a1e01a194af55fde901b1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="e14af-102">Postupy: Rozbalení vnořené úlohy</span><span class="sxs-lookup"><span data-stu-id="e14af-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="e14af-103">Vrátí úlohu z metody a potom můžete čekat na nebo pokračovat od této úlohy, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e14af-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="e14af-104">V předchozím příkladu <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost je typu `string` (`String` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="e14af-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="e14af-105">Ale v některých scénářích, můžete k vytvoření úlohy v rámci jiné úlohy a pak se vraťte vnořené úlohy.</span><span class="sxs-lookup"><span data-stu-id="e14af-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="e14af-106">V takovém případě `TResult` ohraničující úlohy je sám úlohou.</span><span class="sxs-lookup"><span data-stu-id="e14af-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="e14af-107">V následujícím příkladu je vlastnost výsledek `Task<Task<string>>` v jazyce C# nebo `Task(Of Task(Of String))` v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e14af-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="e14af-108">Přestože je možné napsat kód pro rozbalení vnější úlohy a načtení původní úlohy a její <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost, takový kód není usnadňuje zapisovat, protože je nutné zpracovat výjimky a také žádosti o zrušení.</span><span class="sxs-lookup"><span data-stu-id="e14af-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="e14af-109">V takovém případě doporučujeme použít jednu z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> rozšiřující metody, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e14af-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="e14af-110"><xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Metody lze použít k transformaci libovolného `Task<Task>` nebo `Task<Task<TResult>>` (`Task(Of Task)` nebo `Task(Of Task(Of TResult))` v jazyce Visual Basic) k `Task` nebo `Task<TResult>` (`Task(Of TResult)` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="e14af-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="e14af-111">Nová úloha plně představuje vnitřní vnořené úlohy a zahrnuje stav zrušení a všechny výjimky.</span><span class="sxs-lookup"><span data-stu-id="e14af-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e14af-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e14af-112">Example</span></span>  
 <span data-ttu-id="e14af-113">Následující příklad ukazuje, jak používat <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="e14af-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="e14af-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e14af-114">See Also</span></span>  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
 [<span data-ttu-id="e14af-115">Asynchronní programování založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="e14af-115">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
