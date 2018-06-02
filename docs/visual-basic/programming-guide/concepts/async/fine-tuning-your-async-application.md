---
title: Vyladění s modifikátorem Async aplikace (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 6e919d3998719186d0355b9bd187782fcb0e5332
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696673"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="88250-102">Vyladění s modifikátorem Async aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88250-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="88250-103">Přesnost a flexibilitu můžete přidat do aplikací asynchronní pomocí metody a vlastnosti, která <xref:System.Threading.Tasks.Task> typu, bude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="88250-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="88250-104">Témata v této části ukazují příklady, které používají <xref:System.Threading.CancellationToken> a důležitých `Task` metody, jako <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="88250-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="88250-105">Pomocí `WhenAny` a `WhenAll`, můžete snadno zahájení více úloh a operátoru await jejich dokončení sledováním jeden úkol.</span><span class="sxs-lookup"><span data-stu-id="88250-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="88250-106">`WhenAny` Vrátí úlohu, která se dokončí při dokončení všech úloh v kolekci.</span><span class="sxs-lookup"><span data-stu-id="88250-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="88250-107">Příklady, které používají `WhenAny`, najdete v části [zrušení zbývajících asynchronních úloh po jedné je úplná (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)a [spuštění více úloh s modifikátorem Async a proces je jako jejich dokončení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="88250-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="88250-108">`WhenAll` Vrátí úlohu, která je dokončena po dokončení všech úloh v kolekci.</span><span class="sxs-lookup"><span data-stu-id="88250-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="88250-109">Další informace a příklad, který používá `WhenAll`, najdete v části [postupy: rozšíření návodu asynchronních podle pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="88250-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="88250-110">Tato část obsahuje následující příklady.</span><span class="sxs-lookup"><span data-stu-id="88250-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="88250-111">[Zrušení asynchronní úlohy nebo seznamu úloh (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="88250-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="88250-112">Zrušení asynchronních úloh po uplynutí časového intervalu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88250-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="88250-113">Zrušení zbývajících asynchronních úloh po jedné z nich dokončení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88250-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="88250-114">Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88250-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="88250-115">Pro spuštění příkladů, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaný ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="88250-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="88250-116">Projekty vytvoření uživatelského rozhraní, která obsahuje tlačítko, které zahájí proces a tlačítko, které se zruší, jak ukazuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="88250-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="88250-117">Tlačítka jsou pojmenované `startButton` a `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="88250-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="88250-118">![Okno WPF s tlačítko Zrušit](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "zrušení")</span><span class="sxs-lookup"><span data-stu-id="88250-118">![WPF window with Cancel button](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancellation")</span></span>  
  
 <span data-ttu-id="88250-119">Si můžete stáhnout kompletní projekty Windows Presentation Foundation (WPF) z [asynchronní ukázka: jemné ladění vaše aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="88250-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88250-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="88250-120">See Also</span></span>  
 [<span data-ttu-id="88250-121">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88250-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
