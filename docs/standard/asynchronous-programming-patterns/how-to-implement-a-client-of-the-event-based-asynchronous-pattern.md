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
ms.openlocfilehash: 50aa36d2caf774638ad20323813f0de3703aab2f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950720"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="e7294-102">Postupy: Implementace klienta asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="e7294-102">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="e7294-103">Následující příklad kódu ukazuje, jak použít komponentu, která je v [přehledu asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e7294-103">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="e7294-104">Formulář pro tento příklad používá `PrimeNumberCalculator` komponentu popsanou v [tématu How to: Implementujte komponentu, která podporuje asynchronní vzor](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)založený na událostech.</span><span class="sxs-lookup"><span data-stu-id="e7294-104">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="e7294-105">Při spuštění projektu, který používá tento příklad, se zobrazí formulář "Kalkulačka" s mřížkou a dvěma tlačítky: **Spusťte nový úkol** a **zrušte akci**.</span><span class="sxs-lookup"><span data-stu-id="e7294-105">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel**.</span></span> <span data-ttu-id="e7294-106">Můžete kliknout na tlačítko **spustit novou úlohu** několikrát po úspěchu a při každém kliknutí na tuto asynchronní operaci zahájit výpočet, který určí, jestli je náhodně generované číslo testu primární.</span><span class="sxs-lookup"><span data-stu-id="e7294-106">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="e7294-107">Ve formuláři se budou pravidelně zobrazovat průběh a přírůstkové výsledky.</span><span class="sxs-lookup"><span data-stu-id="e7294-107">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="e7294-108">Každé operaci je přiřazeno jedinečné ID úlohy.</span><span class="sxs-lookup"><span data-stu-id="e7294-108">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="e7294-109">Výsledek výpočtu se zobrazí ve sloupci **výsledek** . Pokud číslo testu není primární, je označeno jako **složené** a zobrazí se jeho první dělitel.</span><span class="sxs-lookup"><span data-stu-id="e7294-109">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="e7294-110">Můžete zrušit všechny probíhající operace tlačítkem **Storno** .</span><span class="sxs-lookup"><span data-stu-id="e7294-110">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="e7294-111">Je možné provést vícenásobné výběry.</span><span class="sxs-lookup"><span data-stu-id="e7294-111">Multiple selections can be made.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7294-112">Většina čísel nebude primární.</span><span class="sxs-lookup"><span data-stu-id="e7294-112">Most numbers will not be prime.</span></span> <span data-ttu-id="e7294-113">Pokud jste nenašli základní číslo po několika dokončených operacích, stačí spustit více úkolů a nakonec najít některá hlavní čísla.</span><span class="sxs-lookup"><span data-stu-id="e7294-113">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7294-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7294-114">Example</span></span>  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="e7294-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7294-115">See also</span></span>

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
