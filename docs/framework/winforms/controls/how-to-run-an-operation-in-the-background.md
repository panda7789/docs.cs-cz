---
title: 'Postupy: Spuštění operace na pozadí'
description: Naučte se používat třídu BackgroundWorker ke spuštění časově náročného model Windows Forms operace na pozadí.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
ms.openlocfilehash: 6b2a97f5acf1e906dfe141aee62e99a4e50dca9f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621571"
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="04cc3-103">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="04cc3-103">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="04cc3-104">Pokud máte operaci, která bude trvat dlouhou dobu, a nechcete ve svém uživatelském rozhraní způsobovat prodlevy, můžete použít <xref:System.ComponentModel.BackgroundWorker> třídu ke spuštění operace v jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="04cc3-104">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="04cc3-105">Následující příklad kódu ukazuje, jak spustit časově náročnou operaci na pozadí.</span><span class="sxs-lookup"><span data-stu-id="04cc3-105">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="04cc3-106">Formulář obsahuje tlačítka **Spustit** a **Storno** .</span><span class="sxs-lookup"><span data-stu-id="04cc3-106">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="04cc3-107">Kliknutím na tlačítko **Spustit** spusťte asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="04cc3-107">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="04cc3-108">Kliknutím na tlačítko **Storno** zastavíte spuštěnou asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="04cc3-108">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="04cc3-109">Výsledek každé operace se zobrazí v <xref:System.Windows.Forms.MessageBox> .</span><span class="sxs-lookup"><span data-stu-id="04cc3-109">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="04cc3-110">Existuje Rozsáhlá podpora pro tento úkol v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="04cc3-110">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="04cc3-111">Viz také [Návod: spuštění operace na pozadí](walkthrough-running-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="04cc3-111">Also see [Walkthrough: Running an Operation in the Background](walkthrough-running-an-operation-in-the-background.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04cc3-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="04cc3-112">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="04cc3-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="04cc3-113">Compiling the Code</span></span>  
 <span data-ttu-id="04cc3-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="04cc3-114">This example requires:</span></span>  
  
- <span data-ttu-id="04cc3-115">Odkazy na sestavení System, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="04cc3-115">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04cc3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04cc3-116">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="04cc3-117">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="04cc3-117">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="04cc3-118">Komponenta BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="04cc3-118">BackgroundWorker Component</span></span>](backgroundworker-component.md)
