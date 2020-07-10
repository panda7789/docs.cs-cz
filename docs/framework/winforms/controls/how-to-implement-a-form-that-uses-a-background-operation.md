---
title: 'Postupy: Implementace formuláře, který používá operaci na pozadí'
description: Naučte se implementovat formulář Windows, který používá operaci na pozadí, aby jedna operace mohla pokračovat v běhu, zatímco jiná operace pokračuje.
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
ms.openlocfilehash: 23bf4bc02fbf998d92dfce6d84e4e337cbefe7d9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174520"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="2cb5b-103">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="2cb5b-103">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="2cb5b-104">Následující vzorový program vytvoří formulář, který vypočítá Fibonacci čísla.</span><span class="sxs-lookup"><span data-stu-id="2cb5b-104">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="2cb5b-105">Výpočet se spustí ve vlákně, které je oddělené od vlákna uživatelského rozhraní, takže uživatelské rozhraní bude během výpočtu pokračovat bez prodlev.</span><span class="sxs-lookup"><span data-stu-id="2cb5b-105">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="2cb5b-106">Existuje Rozsáhlá podpora pro tento úkol v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2cb5b-106">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="2cb5b-107">Viz také [Návod: Implementace formuláře, který používá operaci na pozadí](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="2cb5b-107">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cb5b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="2cb5b-108">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2cb5b-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2cb5b-109">Compiling the Code</span></span>  
 <span data-ttu-id="2cb5b-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="2cb5b-110">This example requires:</span></span>  
  
- <span data-ttu-id="2cb5b-111">Odkazy na sestavení System, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="2cb5b-111">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2cb5b-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="2cb5b-112">Robust Programming</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="2cb5b-113">Při použití multithreadingu s více vlákny můžete vystavit hodně závažných a složitých chyb.</span><span class="sxs-lookup"><span data-stu-id="2cb5b-113">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="2cb5b-114">Před implementací jakéhokoli řešení, které používá multithreading, si Projděte [osvědčené postupy spravovaného vlákna](../../../standard/threading/managed-threading-best-practices.md) .</span><span class="sxs-lookup"><span data-stu-id="2cb5b-114">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb5b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="2cb5b-115">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="2cb5b-116">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="2cb5b-116">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="2cb5b-117">Doporučené postupy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="2cb5b-117">Managed Threading Best Practices</span></span>](../../../standard/threading/managed-threading-best-practices.md)
