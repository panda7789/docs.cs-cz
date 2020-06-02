---
title: 'Postupy: Zrušení úlohy a podřízených elementů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
ms.openlocfilehash: ca6b5f10840d935aa45cb660da86685d1c90554b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290029"
---
# <a name="how-to-cancel-a-task-and-its-children"></a><span data-ttu-id="d8191-102">Postupy: Zrušení úlohy a podřízených elementů</span><span class="sxs-lookup"><span data-stu-id="d8191-102">How to: Cancel a Task and Its Children</span></span>
<span data-ttu-id="d8191-103">Tyto příklady znázorňují, jak provádět následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="d8191-103">These examples show how to perform the following tasks:</span></span>  
  
1. <span data-ttu-id="d8191-104">Vytvořit a spustit zrušitelný úkol.</span><span class="sxs-lookup"><span data-stu-id="d8191-104">Create and start a cancelable task.</span></span>  
  
2. <span data-ttu-id="d8191-105">Předat token zrušení do uživatelského delegáta a volitelně do instance úlohy.</span><span class="sxs-lookup"><span data-stu-id="d8191-105">Pass a cancellation token to your user delegate and optionally to the task instance.</span></span>  
  
3. <span data-ttu-id="d8191-106">Zaznamenat a odpovědět na požadavek na zrušení v uživatelském delegátu.</span><span class="sxs-lookup"><span data-stu-id="d8191-106">Notice and respond to the cancellation request in your user delegate.</span></span>  
  
4. <span data-ttu-id="d8191-107">Volitelně oznámit na volajícím vlákně, že byl úkol zrušen.</span><span class="sxs-lookup"><span data-stu-id="d8191-107">Optionally notice on the calling thread that the task was canceled.</span></span>  
  
 <span data-ttu-id="d8191-108">Volající vlákno nevynucuje ukončení úkolu, ale pouze signalizuje, že je požadováno zrušení.</span><span class="sxs-lookup"><span data-stu-id="d8191-108">The calling thread does not forcibly end the task; it only signals that cancellation is requested.</span></span> <span data-ttu-id="d8191-109">Pokud je úkol již spuštěn, musí žádost oznámit a přiměřeně na ni zareagovat uživatelský delegát.</span><span class="sxs-lookup"><span data-stu-id="d8191-109">If the task is already running, it is up to the user delegate to notice the request and respond appropriately.</span></span> <span data-ttu-id="d8191-110">Pokud je zrušení požadováno před spuštěním úlohy, není uživatelský delegát nikdy spuštěn a objekt úlohy přejde do stavu Zrušeno.</span><span class="sxs-lookup"><span data-stu-id="d8191-110">If cancellation is requested before the task runs, then the user delegate is never executed and the task object transitions into the Canceled state.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8191-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d8191-111">Example</span></span>  
 <span data-ttu-id="d8191-112">Tento příklad znázorňuje způsob ukončení úlohy <xref:System.Threading.Tasks.Task> a příslušných podřízených položek v reakci na požadavek zrušení.</span><span class="sxs-lookup"><span data-stu-id="d8191-112">This example shows how to terminate a <xref:System.Threading.Tasks.Task> and its children in response to a cancellation request.</span></span> <span data-ttu-id="d8191-113">Znázorňuje také situaci, že pokud je uživatelský delegát ukončen vyvoláním výjimky <xref:System.Threading.Tasks.TaskCanceledException>, může volající vlákno při čekání na dokončení úloh volitelně použít metodu <xref:System.Threading.Tasks.Task.Wait%2A> nebo metodu <xref:System.Threading.Tasks.Task.WaitAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8191-113">It also shows that when a user delegate terminates by throwing a <xref:System.Threading.Tasks.TaskCanceledException>, the calling thread can optionally use the <xref:System.Threading.Tasks.Task.Wait%2A> method or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the tasks to finish.</span></span> <span data-ttu-id="d8191-114">V tomto případě je nutné použít blok `try/catch`, který zpracuje výjimky na volajícím vlákně.</span><span class="sxs-lookup"><span data-stu-id="d8191-114">In this case, you must use a `try/catch` block to handle the exceptions on the calling thread.</span></span>  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <span data-ttu-id="d8191-115">Třída <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> je plně integrována s modelem zrušení, který je založen na typech <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> a <xref:System.Threading.CancellationToken?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d8191-115">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class is fully integrated with the cancellation model that is based on the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="d8191-116">Další informace naleznete v tématu [zrušení ve spravovaných vláknech](../threading/cancellation-in-managed-threads.md) a [zrušení úlohy](task-cancellation.md).</span><span class="sxs-lookup"><span data-stu-id="d8191-116">For more information, see [Cancellation in Managed Threads](../threading/cancellation-in-managed-threads.md) and [Task Cancellation](task-cancellation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8191-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8191-117">See also</span></span>

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [<span data-ttu-id="d8191-118">Asynchronní programování založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="d8191-118">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="d8191-119">Připojené a odpojené podřízené úlohy</span><span class="sxs-lookup"><span data-stu-id="d8191-119">Attached and Detached Child Tasks</span></span>](attached-and-detached-child-tasks.md)
- [<span data-ttu-id="d8191-120">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="d8191-120">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
