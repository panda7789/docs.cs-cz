---
title: 'Postupy: Implementace formuláře, který používá operaci na pozadí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: e06b18558f6b3fa3cef47613bbaef16fb7c740f0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046191"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="266be-102">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="266be-102">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="266be-103">Následující vzorový program vytvoří formulář, který vypočítá Fibonacci čísla.</span><span class="sxs-lookup"><span data-stu-id="266be-103">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="266be-104">Výpočet se spustí ve vlákně, které je oddělené od vlákna uživatelského rozhraní, takže uživatelské rozhraní bude během výpočtu pokračovat bez prodlev.</span><span class="sxs-lookup"><span data-stu-id="266be-104">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="266be-105">Existuje Rozsáhlá podpora pro tento úkol v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="266be-105">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="266be-106">Viz [také návod: Implementace formuláře, který používá operaci](walkthrough-implementing-a-form-that-uses-a-background-operation.md)na pozadí.</span><span class="sxs-lookup"><span data-stu-id="266be-106">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="266be-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="266be-107">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="266be-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="266be-108">Compiling the Code</span></span>  
 <span data-ttu-id="266be-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="266be-109">This example requires:</span></span>  
  
- <span data-ttu-id="266be-110">Odkazy na sestavení System, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="266be-110">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="266be-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="266be-111">Robust Programming</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="266be-112">Při použití multithreadingu s více vlákny můžete vystavit hodně závažných a složitých chyb.</span><span class="sxs-lookup"><span data-stu-id="266be-112">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="266be-113">Před implementací jakéhokoli řešení, které používá multithreading, si Projděte [osvědčené postupy spravovaného vlákna](../../../standard/threading/managed-threading-best-practices.md) .</span><span class="sxs-lookup"><span data-stu-id="266be-113">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="266be-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="266be-114">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="266be-115">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="266be-115">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="266be-116">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="266be-116">Managed Threading Best Practices</span></span>](../../../standard/threading/managed-threading-best-practices.md)
