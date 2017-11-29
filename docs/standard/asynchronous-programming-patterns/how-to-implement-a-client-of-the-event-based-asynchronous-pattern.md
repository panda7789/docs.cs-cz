---
title: "Postupy: Implementace klienta asynchronního vzoru založeného na událostech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b70d4ba205d39ad8fcbc7c7f6fa1f5b34a36c98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="43789-102">Postupy: Implementace klienta asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="43789-102">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="43789-103">Následující příklad kódu ukazuje, jak používat komponenty, která dodržuje [na základě událostí přehled asynchronních vzorů](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="43789-103">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="43789-104">Formulář pro tento příklad používá `PrimeNumberCalculator` komponenty popsané v [postupy: implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="43789-104">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="43789-105">Když spouštíte projekt, který používá tento příklad, uvidíte formulář "Číslo Prime kalkulačky" s mřížka a dvě tlačítka: **spustit novou úlohu** a **zrušit**.</span><span class="sxs-lookup"><span data-stu-id="43789-105">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel**.</span></span> <span data-ttu-id="43789-106">Můžete kliknout na **spustit novou úlohu** tlačítko několikrát za sebou a pro každou klikněte na asynchronní operaci se začnou výpočet lze zjistit, je prime testovací náhodně generované číslo.</span><span class="sxs-lookup"><span data-stu-id="43789-106">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="43789-107">Formulář pravidelně zobrazí průběh a přírůstkové výsledky.</span><span class="sxs-lookup"><span data-stu-id="43789-107">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="43789-108">Každý je přiřazena ID jedinečný úkolu.</span><span class="sxs-lookup"><span data-stu-id="43789-108">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="43789-109">Výsledek výpočet se zobrazí v **výsledek** sloupci; Pokud číslo test není prvotní, je označeno jako **složený,** a zobrazí se jeho první dělitel.</span><span class="sxs-lookup"><span data-stu-id="43789-109">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="43789-110">Všechny čekající operace se dají zrušit s **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="43789-110">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="43789-111">Můžete provedeny více výběrů.</span><span class="sxs-lookup"><span data-stu-id="43789-111">Multiple selections can be made.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43789-112">Většina čísla nebudou prime.</span><span class="sxs-lookup"><span data-stu-id="43789-112">Most numbers will not be prime.</span></span> <span data-ttu-id="43789-113">Pokud číslo prime nebyly nalezeny po několik operací dokončené, jednoduše spusťte další informace o úlohách a nakonec najdete některé prvočísel.</span><span class="sxs-lookup"><span data-stu-id="43789-113">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43789-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="43789-114">Example</span></span>  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="43789-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="43789-115">See Also</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
