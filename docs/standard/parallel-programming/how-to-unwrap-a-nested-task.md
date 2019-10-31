---
title: 'Postupy: Rozbalení vnořené úlohy'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: c72654a2bc21035fe706d76018bb163d8ba01ee8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106906"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="14076-102">Postupy: Rozbalení vnořené úlohy</span><span class="sxs-lookup"><span data-stu-id="14076-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="14076-103">Můžete vrátit úlohu z metody a pak počkat nebo pokračovat v této úloze, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="14076-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="14076-104">V předchozím příkladu je vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A> typu `string` (`String` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="14076-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="14076-105">V některých scénářích je však vhodné vytvořit úlohu v rámci jiné úlohy a pak vrátit vnořenou úlohu.</span><span class="sxs-lookup"><span data-stu-id="14076-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="14076-106">V tomto případě je `TResult` ohraničující úlohy samotný úkol.</span><span class="sxs-lookup"><span data-stu-id="14076-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="14076-107">V následujícím příkladu je vlastnost Result `Task<Task<string>>` v C# nebo `Task(Of Task(Of String))` v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="14076-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="14076-108">I když je možné napsat kód, který rozbalí vnější úlohu a načte původní úlohu a její vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A>, takový kód se nedá snadno zapsat, protože je nutné zpracovat výjimky a také požadavky na zrušení.</span><span class="sxs-lookup"><span data-stu-id="14076-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="14076-109">V takové situaci doporučujeme použít jednu z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> rozšiřujících metod, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="14076-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="14076-110">Metody <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> lze použít k transformaci jakýchkoli `Task<Task>` nebo `Task<Task<TResult>>` (`Task(Of Task)` nebo `Task(Of Task(Of TResult))` v Visual Basic) na `Task` nebo `Task<TResult>` (`Task(Of TResult)` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="14076-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="14076-111">Nová úloha plně reprezentuje vnitřní vnořenou úlohu a obsahuje stav zrušení a všechny výjimky.</span><span class="sxs-lookup"><span data-stu-id="14076-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14076-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="14076-112">Example</span></span>  
 <span data-ttu-id="14076-113">Následující příklad ukazuje, jak použít metody rozšíření <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="14076-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="14076-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14076-114">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [<span data-ttu-id="14076-115">Asynchronní programování založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="14076-115">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
