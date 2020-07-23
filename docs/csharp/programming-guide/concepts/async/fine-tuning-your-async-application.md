---
title: Vyladění aplikace s modifikátorem Async (C#)
description: Tyto příklady jazyka C# používají CancellationToken a důležité metody úloh, jako je Task. WhenAll a Task. WhenAny pro vyladění asynchronních aplikací.
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: 46457f889a78932e306d2bd21dca666625d744eb
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925316"
---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="ed657-103">Vyladění aplikace s modifikátorem Async (C#)</span><span class="sxs-lookup"><span data-stu-id="ed657-103">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="ed657-104">Můžete přidat přesnost a flexibilitu pro asynchronní aplikace pomocí metod a vlastností, které <xref:System.Threading.Tasks.Task> typ zpřístupňuje.</span><span class="sxs-lookup"><span data-stu-id="ed657-104">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="ed657-105">Témata v této části obsahují příklady, které používají <xref:System.Threading.CancellationToken> a důležité `Task` metody, jako jsou <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ed657-105">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="ed657-106">Pomocí `WhenAny` a `WhenAll` můžete snadněji spustit více úkolů a očekávat jejich dokončení monitorováním jedné úlohy.</span><span class="sxs-lookup"><span data-stu-id="ed657-106">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="ed657-107">`WhenAny`Vrátí úkol, který se dokončí po dokončení libovolné úlohy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ed657-107">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="ed657-108">Příklady použití `WhenAny` naleznete v tématu [zrušení zbývajících asynchronních úloh po dokončení jedné z nich (c#)](./cancel-remaining-async-tasks-after-one-is-complete.md) a [spuštění několika asynchronních úloh a jejich zpracování po dokončení (c#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="ed657-108">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="ed657-109">`WhenAll`Vrátí úkol, který se dokončí po dokončení všech úloh v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ed657-109">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="ed657-110">Další informace a příklad, který používá `WhenAll` , najdete v tématu [postup rozšiřování asynchronního návodu pomocí Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="ed657-110">For more information and an example that uses `WhenAll`, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="ed657-111">Tato část obsahuje následující příklady.</span><span class="sxs-lookup"><span data-stu-id="ed657-111">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="ed657-112">[Zrušení asynchronní úlohy nebo seznamu úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="ed657-112">[Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="ed657-113">Zrušení asynchronních úloh po určitém časovém intervalu (C#)</span><span class="sxs-lookup"><span data-stu-id="ed657-113">Cancel Async Tasks after a Period of Time (C#)</span></span>](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="ed657-114">Zrušení zbývajících asynchronních úloh po dokončení jedné z nich (C#)</span><span class="sxs-lookup"><span data-stu-id="ed657-114">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="ed657-115">Spuštění více asynchronních úloh a jejich zpracování po dokončení (C#)</span><span class="sxs-lookup"><span data-stu-id="ed657-115">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> <span data-ttu-id="ed657-116">Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="ed657-116">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="ed657-117">Projekty vytvoří uživatelské rozhraní, které obsahuje tlačítko, které spustí proces, a tlačítko, které ho zruší, jak ukazuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="ed657-117">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="ed657-118">Tlačítka jsou pojmenována `startButton` a `cancelButton` .</span><span class="sxs-lookup"><span data-stu-id="ed657-118">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="ed657-119">![Okno WPF s tlačítkem Storno](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialogové okno s tlačítkem Spustit a zastavit")</span><span class="sxs-lookup"><span data-stu-id="ed657-119">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="ed657-120">Z Async Sample si můžete stáhnout kompletní projekty Windows Presentation Foundation (WPF) [: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="ed657-120">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed657-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed657-121">See also</span></span>

- [<span data-ttu-id="ed657-122">Asynchronní programování s modifikátorem Async a operátoru Await (C#)</span><span class="sxs-lookup"><span data-stu-id="ed657-122">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
