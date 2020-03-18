---
title: Jemné doladění asynchronní aplikace (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: cff50e62ff62b70e97e7ea6e03714326d774e407
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73970232"
---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="6a1c5-102">Jemné doladění asynchronní aplikace (C#)</span><span class="sxs-lookup"><span data-stu-id="6a1c5-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="6a1c5-103">Můžete přidat přesnost a flexibilitu asynchronní aplikace pomocí metod <xref:System.Threading.Tasks.Task> a vlastností, které typ zpřístupňuje.</span><span class="sxs-lookup"><span data-stu-id="6a1c5-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="6a1c5-104">Témata v této části ukazují <xref:System.Threading.CancellationToken> příklady, které používají a důležité `Task` metody, jako <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> jsou a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6a1c5-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="6a1c5-105">Pomocí `WhenAny` aplikace `WhenAll`a můžete snadněji spustit více úkolů a čekat na jejich dokončení sledováním jednoho úkolu.</span><span class="sxs-lookup"><span data-stu-id="6a1c5-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="6a1c5-106">`WhenAny`vrátí úlohu, která se dokončí po dokončení libovolné úlohy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="6a1c5-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="6a1c5-107">Příklady, které `WhenAny`používají , naleznete v [tématu Zrušení zbývajících asynchronních úloh po dokončení jednoho (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) a [spuštění více asynchronních úloh a jejich zpracování po dokončení (C#).](./start-multiple-async-tasks-and-process-them-as-they-complete.md)</span><span class="sxs-lookup"><span data-stu-id="6a1c5-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="6a1c5-108">`WhenAll`vrátí úkol, který se dokončí po dokončení všech úkolů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="6a1c5-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="6a1c5-109">Další informace a příklad, `WhenAll`který používá , naleznete [v tématu Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="6a1c5-109">For more information and an example that uses `WhenAll`, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="6a1c5-110">Tato část obsahuje následující příklady.</span><span class="sxs-lookup"><span data-stu-id="6a1c5-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="6a1c5-111">[Zrušte asynchronní úlohu nebo seznam úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="6a1c5-111">[Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="6a1c5-112">Zrušit asynchronní úkoly po časovém období (C#)</span><span class="sxs-lookup"><span data-stu-id="6a1c5-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="6a1c5-113">Zrušit zbývající asynchronní úlohy po dokončení jedné (C#)</span><span class="sxs-lookup"><span data-stu-id="6a1c5-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="6a1c5-114">Spuštění více asynchronních úloh a jejich zpracování po dokončení (C#)</span><span class="sxs-lookup"><span data-stu-id="6a1c5-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> <span data-ttu-id="6a1c5-115">Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="6a1c5-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="6a1c5-116">Projekty vytvořit uzpole, která obsahuje tlačítko, které spustí proces a tlačítko, které jej zruší, jak ukazuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="6a1c5-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="6a1c5-117">Tlačítka jsou `startButton` pojmenována a `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="6a1c5-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="6a1c5-118">![Okno WPF s tlačítkem Storno](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialogové okno s tlačítkem Start a Stop")</span><span class="sxs-lookup"><span data-stu-id="6a1c5-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="6a1c5-119">Můžete si stáhnout kompletní Windows Presentation Foundation (WPF) projekty z [Async Ukázka: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="6a1c5-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a1c5-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a1c5-120">See also</span></span>

- [<span data-ttu-id="6a1c5-121">Asynchronní programování s asynchronní a await (C#)</span><span class="sxs-lookup"><span data-stu-id="6a1c5-121">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
