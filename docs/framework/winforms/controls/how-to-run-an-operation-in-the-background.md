---
title: 'Postupy: Spuštění operace na pozadí'
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
ms.openlocfilehash: 9702728631f794c0cc8f69a1117da69bc15a0836
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261762"
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="4d8ec-102">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="4d8ec-102">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="4d8ec-103">Pokud máte operace, která bude trvat dlouhou dobu pro dokončení, a nechcete způsobit prodlevy v uživatelském rozhraní, můžete použít <xref:System.ComponentModel.BackgroundWorker> má třída spustit operaci v jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="4d8ec-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="4d8ec-104">Následující příklad kódu ukazuje, jak spustit časově náročná operace na pozadí.</span><span class="sxs-lookup"><span data-stu-id="4d8ec-104">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="4d8ec-105">Formulář obsahuje **Start** a **zrušit** tlačítka.</span><span class="sxs-lookup"><span data-stu-id="4d8ec-105">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="4d8ec-106">Klikněte na tlačítko **Start** tlačítko Spustit asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="4d8ec-106">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="4d8ec-107">Klikněte na tlačítko **zrušit** tlačítko Zastavit spuštěné asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="4d8ec-107">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="4d8ec-108">Se zobrazí výsledek každé operace <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="4d8ec-108">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="4d8ec-109">Není k dispozici rozsáhlou podporu pro tuto úlohu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4d8ec-109">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="4d8ec-110">Viz také [názorný postup: Spuštění operace na pozadí](walkthrough-running-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="4d8ec-110">Also see [Walkthrough: Running an Operation in the Background](walkthrough-running-an-operation-in-the-background.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d8ec-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d8ec-111">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4d8ec-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4d8ec-112">Compiling the Code</span></span>  
 <span data-ttu-id="4d8ec-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="4d8ec-113">This example requires:</span></span>  
  
-   <span data-ttu-id="4d8ec-114">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="4d8ec-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="4d8ec-115">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4d8ec-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4d8ec-116">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="4d8ec-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d8ec-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d8ec-117">See also</span></span>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="4d8ec-118">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="4d8ec-118">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="4d8ec-119">Komponenta BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="4d8ec-119">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
