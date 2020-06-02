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
ms.openlocfilehash: 9a69fa42da41ee4a071a6571042fd96fb5a009d2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288027"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="d2e1c-102">Postupy: Rozbalení vnořené úlohy</span><span class="sxs-lookup"><span data-stu-id="d2e1c-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="d2e1c-103">Můžete vrátit úlohu z metody a pak počkat nebo pokračovat v této úloze, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d2e1c-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="d2e1c-104">V předchozím příkladu <xref:System.Threading.Tasks.Task%601.Result%2A> je vlastnost typu `string` ( `String` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d2e1c-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="d2e1c-105">V některých scénářích je však vhodné vytvořit úlohu v rámci jiné úlohy a pak vrátit vnořenou úlohu.</span><span class="sxs-lookup"><span data-stu-id="d2e1c-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="d2e1c-106">V tomto případě `TResult` je nadřazený úkol sám úkolem.</span><span class="sxs-lookup"><span data-stu-id="d2e1c-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="d2e1c-107">V následujícím příkladu je vlastnost Result `Task<Task<string>>` v jazyce C# nebo `Task(Of Task(Of String))` v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d2e1c-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="d2e1c-108">I když je možné napsat kód, který rozbalí vnější úlohu a načte původní úlohu a její <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost, takový kód nelze snadno zapsat, protože je nutné zpracovat výjimky a také požadavky na zrušení.</span><span class="sxs-lookup"><span data-stu-id="d2e1c-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="d2e1c-109">V této situaci doporučujeme použít jednu z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> rozšiřujících metod, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d2e1c-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="d2e1c-110"><xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>Metody lze použít k transformaci libovolného `Task<Task>` nebo `Task<Task<TResult>>` ( `Task(Of Task)` nebo `Task(Of Task(Of TResult))` v Visual Basic) na `Task` nebo `Task<TResult>` ( `Task(Of TResult)` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d2e1c-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="d2e1c-111">Nová úloha plně reprezentuje vnitřní vnořenou úlohu a obsahuje stav zrušení a všechny výjimky.</span><span class="sxs-lookup"><span data-stu-id="d2e1c-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2e1c-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2e1c-112">Example</span></span>  
 <span data-ttu-id="d2e1c-113">Následující příklad ukazuje, jak použít <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="d2e1c-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="d2e1c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2e1c-114">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [<span data-ttu-id="d2e1c-115">Asynchronní programování založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="d2e1c-115">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
