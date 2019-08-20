---
title: Vyladění asynchronní aplikace (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: 4a37966566d701e7070c33248d6ff4187a26e9f1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595817"
---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="0a57b-102">Vyladění asynchronní aplikace (C#)</span><span class="sxs-lookup"><span data-stu-id="0a57b-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="0a57b-103">Můžete přidat přesnost a flexibilitu pro asynchronní aplikace pomocí metod a vlastností, které <xref:System.Threading.Tasks.Task> typ zpřístupňuje.</span><span class="sxs-lookup"><span data-stu-id="0a57b-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="0a57b-104">Témata v této části obsahují příklady, které používají <xref:System.Threading.CancellationToken> a důležité `Task` metody, jako <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> jsou <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>a.</span><span class="sxs-lookup"><span data-stu-id="0a57b-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="0a57b-105">Pomocí `WhenAny` a`WhenAll`můžete snadněji spustit více úkolů a očekávat jejich dokončení monitorováním jedné úlohy.</span><span class="sxs-lookup"><span data-stu-id="0a57b-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="0a57b-106">`WhenAny`Vrátí úkol, který se dokončí po dokončení libovolné úlohy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="0a57b-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="0a57b-107">Příklady použití `WhenAny`naleznete v tématu [zrušení zbývajících asynchronních úloh po dokončení jedné z nichC#()](./cancel-remaining-async-tasks-after-one-is-complete.md) a [spuštění několika asynchronních úloh a jejich zpracování po dokončeníC#()](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="0a57b-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="0a57b-108">`WhenAll`Vrátí úkol, který se dokončí po dokončení všech úloh v kolekci.</span><span class="sxs-lookup"><span data-stu-id="0a57b-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="0a57b-109">Další informace a příklad, který používá `WhenAll`, naleznete v tématu [How to: Pomocí Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)rozšíříte asynchronní návod.</span><span class="sxs-lookup"><span data-stu-id="0a57b-109">For more information and an example that uses `WhenAll`, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="0a57b-110">Tato část obsahuje následující příklady.</span><span class="sxs-lookup"><span data-stu-id="0a57b-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="0a57b-111">[Zrušení asynchronní úlohy nebo seznamu úkolůC#()](./cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="0a57b-111">[Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="0a57b-112">Zrušení asynchronních úloh po uplynutí časového intervalu (C#)</span><span class="sxs-lookup"><span data-stu-id="0a57b-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="0a57b-113">Zrušení zbývajících asynchronních úloh po dokončení jedné zC#nich ()</span><span class="sxs-lookup"><span data-stu-id="0a57b-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="0a57b-114">Spuštění několika asynchronních úloh a jejich zpracování po dokončení (C#)</span><span class="sxs-lookup"><span data-stu-id="0a57b-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="0a57b-115">Chcete-li spustit příklady, je nutné mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="0a57b-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="0a57b-116">Projekty vytvoří uživatelské rozhraní, které obsahuje tlačítko, které spustí proces, a tlačítko, které ho zruší, jak ukazuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="0a57b-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="0a57b-117">Tlačítka jsou `startButton` pojmenována `cancelButton`a.</span><span class="sxs-lookup"><span data-stu-id="0a57b-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="0a57b-118">![Okno WPF s tlačítkem Storno](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialogové okno s tlačítkem Spustit a zastavit")</span><span class="sxs-lookup"><span data-stu-id="0a57b-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="0a57b-119">Kompletní projekty Windows Presentation Foundation (WPF) si můžete stáhnout z [Async Sample: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)</span><span class="sxs-lookup"><span data-stu-id="0a57b-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a57b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a57b-120">See also</span></span>

- [<span data-ttu-id="0a57b-121">Asynchronní programování s modifikátorem Async aC#operátoru Await ()</span><span class="sxs-lookup"><span data-stu-id="0a57b-121">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
