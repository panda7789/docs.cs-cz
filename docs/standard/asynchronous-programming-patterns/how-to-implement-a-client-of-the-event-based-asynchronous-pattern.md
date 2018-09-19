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
ms.openlocfilehash: 4176d1a4cec91c5740b03c10d1a6d2cc263dba28
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45998809"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="b15f8-102">Postupy: Implementace klienta asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="b15f8-102">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="b15f8-103">Následující příklad kódu ukazuje, jak použít komponentu, která dodržuje [založený na událostech přehled asynchronních vzorů](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b15f8-103">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="b15f8-104">Formulář pro tento příklad používá `PrimeNumberCalculator` komponenty popsané v [postupy: implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="b15f8-104">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="b15f8-105">Při spuštění projektu, který se používá v tomto příkladu se zobrazí "Kalkulačka Prime číslo" formulář s mřížky a dvě tlačítka: **spustit novou úlohu** a **zrušit**.</span><span class="sxs-lookup"><span data-stu-id="b15f8-105">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel**.</span></span> <span data-ttu-id="b15f8-106">Můžete kliknout **spustit novou úlohu** tlačítko několikrát za sebou a pro každou klikněte na asynchronní operace se začne výpočtu k určení, zda je číslo náhodně vygenerovaného testu prime.</span><span class="sxs-lookup"><span data-stu-id="b15f8-106">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="b15f8-107">Formulář zobrazí pravidelně průběh a výsledky přírůstkové.</span><span class="sxs-lookup"><span data-stu-id="b15f8-107">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="b15f8-108">Každá operace se přiřadí ID jedinečné úkolu.</span><span class="sxs-lookup"><span data-stu-id="b15f8-108">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="b15f8-109">Výsledek výpočtu se zobrazí v **výsledek** sloupec; Pokud číslo testu není primární, je označena jako **složené,** a zobrazí se jeho první dělitel.</span><span class="sxs-lookup"><span data-stu-id="b15f8-109">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="b15f8-110">Všechny čekající operace může být zrušen pomocí **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b15f8-110">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="b15f8-111">Nelze realizovat více výběrů.</span><span class="sxs-lookup"><span data-stu-id="b15f8-111">Multiple selections can be made.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b15f8-112">Většina čísel nebude primární.</span><span class="sxs-lookup"><span data-stu-id="b15f8-112">Most numbers will not be prime.</span></span> <span data-ttu-id="b15f8-113">Pokud po několika dokončené operace s nebyla nalezena Prvočíslo, jednoduše spustit více úkolů a nakonec najdete některé prvočísel.</span><span class="sxs-lookup"><span data-stu-id="b15f8-113">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b15f8-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="b15f8-114">Example</span></span>  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="b15f8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b15f8-115">See also</span></span>

- <xref:System.ComponentModel.AsyncOperation>  
- <xref:System.ComponentModel.AsyncOperationManager>  
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
