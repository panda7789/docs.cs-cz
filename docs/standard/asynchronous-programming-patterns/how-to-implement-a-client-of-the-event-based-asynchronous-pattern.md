---
title: 'Postupy: Implementace klienta asynchronního vzoru založeného na událostech'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
ms.openlocfilehash: d0253745d4d2ee90f355364ed1b1b0d9b74d0fc1
ms.sourcegitcommit: b78018c850590dfc0348301e1748b779c28604cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89379184"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="448c1-102">Postupy: Implementace klienta asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="448c1-102">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="448c1-103">Následující příklad kódu ukazuje, jak použít komponentu, která je v [přehledu asynchronního vzoru založeného na událostech](event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="448c1-103">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="448c1-104">Formulář pro tento příklad používá `PrimeNumberCalculator` komponentu popsanou v tématu [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="448c1-104">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="448c1-105">Když spustíte projekt, který používá tento příklad, zobrazí se ve formě kalkulačky "základní číslo" s mřížkou a dvěma tlačítky: **spustit novou úlohu** a **Zrušit**.</span><span class="sxs-lookup"><span data-stu-id="448c1-105">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel**.</span></span> <span data-ttu-id="448c1-106">Můžete kliknout na tlačítko **spustit novou úlohu** několikrát po úspěchu a při každém kliknutí na tuto asynchronní operaci zahájit výpočet, který určí, jestli je náhodně generované číslo testu primární.</span><span class="sxs-lookup"><span data-stu-id="448c1-106">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="448c1-107">Ve formuláři se budou pravidelně zobrazovat průběh a přírůstkové výsledky.</span><span class="sxs-lookup"><span data-stu-id="448c1-107">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="448c1-108">Každé operaci je přiřazeno jedinečné ID úlohy.</span><span class="sxs-lookup"><span data-stu-id="448c1-108">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="448c1-109">Výsledek výpočtu se zobrazí ve sloupci **výsledek** . Pokud číslo testu není primární, je označeno jako **složené** a zobrazí se jeho první dělitel.</span><span class="sxs-lookup"><span data-stu-id="448c1-109">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="448c1-110">Můžete zrušit všechny probíhající operace tlačítkem **Storno** .</span><span class="sxs-lookup"><span data-stu-id="448c1-110">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="448c1-111">Je možné provést vícenásobné výběry.</span><span class="sxs-lookup"><span data-stu-id="448c1-111">Multiple selections can be made.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="448c1-112">Většina čísel nebude primární.</span><span class="sxs-lookup"><span data-stu-id="448c1-112">Most numbers will not be prime.</span></span> <span data-ttu-id="448c1-113">Pokud jste nenašli základní číslo po několika dokončených operacích, stačí spustit více úkolů a nakonec najít některá hlavní čísla.</span><span class="sxs-lookup"><span data-stu-id="448c1-113">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="448c1-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="448c1-114">Example</span></span>  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="448c1-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="448c1-115">See also</span></span>

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
