---
title: Doladění aplikace s modifikátorem Async (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 3e9a6d02ec4948103b892ae012b8c51f66dd06c4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624734"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="d0dea-102">Doladění aplikace s modifikátorem Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0dea-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="d0dea-103">Přidáte přesnost a flexibilitu asynchronním aplikací pomocí metody a vlastnosti, která <xref:System.Threading.Tasks.Task> typu bude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d0dea-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="d0dea-104">Témata v této části obsahují příklady používající <xref:System.Threading.CancellationToken> a důležité `Task` metody jako <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d0dea-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="d0dea-105">S použitím `WhenAny` a `WhenAll`, můžete snadněji spustit více úkolů a Vyčkávat na jejich dokončení při sledování jednoho úkolu.</span><span class="sxs-lookup"><span data-stu-id="d0dea-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="d0dea-106">`WhenAny` Vrátí úlohu, která se dokončí při dokončení libovolné úlohy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d0dea-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="d0dea-107">Příklady, které používají `WhenAny`, naleznete v tématu [zrušení zbývajících asynchronních úloh po jeden je úplná (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)a [spuštění více úloh s modifikátorem Async a proces je jako jejich kompletní (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="d0dea-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="d0dea-108">`WhenAll` Vrátí úlohu, která se dokončí po dokončení všech úloh v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d0dea-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="d0dea-109">Další informace a příklad použití `WhenAll`, naleznete v tématu [jak: Rozšíření návodu asynchronních úloh pomocí metody Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="d0dea-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="d0dea-110">Tato část obsahuje následující příklady.</span><span class="sxs-lookup"><span data-stu-id="d0dea-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="d0dea-111">[Zrušení asynchronní úlohy nebo seznamu úkolů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="d0dea-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="d0dea-112">Zrušení asynchronních úloh po určitou dobu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0dea-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="d0dea-113">Zrušení zbývajících asynchronních úloh po jedné z nich kompletní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0dea-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="d0dea-114">Zahájení více úloh s modifikátorem Async a jejich zpracování po dokončení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0dea-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="d0dea-115">Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="d0dea-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="d0dea-116">Projekty vytvářejí uživatelské rozhraní, která obsahuje tlačítko, které zahájí proces a tlačítko, které ho ruší, jak ukazuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="d0dea-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="d0dea-117">Tlačítka jsou pojmenována `startButton` a `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="d0dea-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="d0dea-118">![Okno WPF s tlačítkem Storno](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "dialogové okno s tlačítkem spouštění a zastavování")</span><span class="sxs-lookup"><span data-stu-id="d0dea-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="d0dea-119">Můžete si stáhnout kompletní projektů Windows Presentation Foundation (WPF) z [asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="d0dea-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0dea-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0dea-120">See also</span></span>

- [<span data-ttu-id="d0dea-121">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0dea-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
