---
title: 'Postupy: Spuštění operace na pozadí'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e672215ac7b381175303c62f24c3881a2cce693
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="14bd0-102">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="14bd0-102">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="14bd0-103">Pokud máte operace, která bude trvat dlouhou dobu pro dokončení, a nechcete způsobit zpoždění v uživatelském rozhraní, můžete použít <xref:System.ComponentModel.BackgroundWorker> třídy spusťte operaci na jiné vlákno.</span><span class="sxs-lookup"><span data-stu-id="14bd0-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="14bd0-104">Následující příklad kódu ukazuje, jak spustit časově náročná operace na pozadí.</span><span class="sxs-lookup"><span data-stu-id="14bd0-104">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="14bd0-105">Formulář má **spustit** a **zrušit** tlačítka.</span><span class="sxs-lookup"><span data-stu-id="14bd0-105">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="14bd0-106">Klikněte **spustit** tlačítko Spustit asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="14bd0-106">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="14bd0-107">Klikněte **zrušit** tlačítko zastavení spuštění asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="14bd0-107">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="14bd0-108">Výsledek každé operace se zobrazí v <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="14bd0-108">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="14bd0-109">Rozsáhlá podpora pro tuto úlohu v sadě Visual Studio není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="14bd0-109">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="14bd0-110">Viz také [návod: spuštění operace na pozadí](http://msdn.microsoft.com/library/ms233672\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="14bd0-110">Also see [Walkthrough: Running an Operation in the Background](http://msdn.microsoft.com/library/ms233672\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="14bd0-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="14bd0-111">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="14bd0-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="14bd0-112">Compiling the Code</span></span>  
 <span data-ttu-id="14bd0-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="14bd0-113">This example requires:</span></span>  
  
-   <span data-ttu-id="14bd0-114">Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="14bd0-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="14bd0-115">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="14bd0-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="14bd0-116">Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="14bd0-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="14bd0-117">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="14bd0-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14bd0-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="14bd0-118">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [<span data-ttu-id="14bd0-119">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="14bd0-119">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="14bd0-120">Komponenta BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="14bd0-120">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
