---
title: 'Postupy: Zrušení bloku toku dat'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b95f0a3535716c4a01dae52abe38eb850f080cf0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345193"
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="8d07d-102">Postupy: Zrušení bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="8d07d-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="8d07d-103">Tento dokument ukazuje, jak povolit zrušení ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d07d-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="8d07d-104">Tento příklad používá Windows Forms k zobrazení, ve kterém jsou aktivní v kanálu toku dat a také vlivu zrušení pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="8d07d-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="8d07d-105">Chcete-li vytvořit Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="8d07d-105">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="8d07d-106">Vytvoření jazyka C# nebo Visual Basic **formulářová aplikace Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="8d07d-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="8d07d-107">V následujících krocích se projekt s názvem `CancellationWinForms`.</span><span class="sxs-lookup"><span data-stu-id="8d07d-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2. <span data-ttu-id="8d07d-108">V návrháři formuláře pro hlavní formulář Form1.cs (Form1.vb pro jazyk Visual Basic), přidejte <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8d07d-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3. <span data-ttu-id="8d07d-109">Přidat <xref:System.Windows.Forms.ToolStripButton> ovládací prvek <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8d07d-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="8d07d-110">Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **přidat pracovní položky**.</span><span class="sxs-lookup"><span data-stu-id="8d07d-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4. <span data-ttu-id="8d07d-111">Přidejte druhý <xref:System.Windows.Forms.ToolStripButton> ovládací prvek <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8d07d-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="8d07d-112">Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **zrušit**a <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> vlastnost `False`.</span><span class="sxs-lookup"><span data-stu-id="8d07d-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5. <span data-ttu-id="8d07d-113">Přidejte čtyři <xref:System.Windows.Forms.ToolStripProgressBar> objektů <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8d07d-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="8d07d-114">Vytvoření kanálu toku dat</span><span class="sxs-lookup"><span data-stu-id="8d07d-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="8d07d-115">Tato část popisuje postup vytvoření kanálu toku dat, která zpracovává pracovních položek a aktualizuje indikátory průběhu.</span><span class="sxs-lookup"><span data-stu-id="8d07d-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="8d07d-116">K vytvoření kanálu toku dat</span><span class="sxs-lookup"><span data-stu-id="8d07d-116">To Create the Dataflow Pipeline</span></span>  
  
1. <span data-ttu-id="8d07d-117">Ve vašem projektu přidejte odkaz na System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="8d07d-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="8d07d-118">Ujistěte se, že Form1.cs (Form1.vb pro jazyk Visual Basic) obsahuje následující `using` příkazy (`Imports` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="8d07d-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. <span data-ttu-id="8d07d-119">Přidat `WorkItem` třídu jako vnitřní typ `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="8d07d-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. <span data-ttu-id="8d07d-120">Přidejte následující datové členy do `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="8d07d-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. <span data-ttu-id="8d07d-121">Přidejte následující metodu `CreatePipeline`, možnosti `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="8d07d-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="8d07d-122">Vzhledem k tomu, `incrementProgress` a `decrementProgress` toku dat bloky fungovat na uživatelské rozhraní, je důležité, že provedou tyto akce ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8d07d-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="8d07d-123">Jak toho dosáhnout, během vytváření těchto objektů, zadejte každou <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> nastavenou na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8d07d-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8d07d-124"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provede práci na aktuálním kontextu synchronizace.</span><span class="sxs-lookup"><span data-stu-id="8d07d-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="8d07d-125">Vzhledem k tomu, `Form1` konstruktoru se volá z vlákna uživatelského rozhraní, akce, `incrementProgress` a `decrementProgress` bloků toku dat také spustit ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8d07d-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="8d07d-126">Tento příklad nastaví <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost vytvoří členy kanálu.</span><span class="sxs-lookup"><span data-stu-id="8d07d-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="8d07d-127">Vzhledem k tomu, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost trvale zruší spuštění bloku toku dat, celý kanál musí být znovu vytvořena po uživatel operaci zruší a pak se chce přidat další pracovní položky do kanálu.</span><span class="sxs-lookup"><span data-stu-id="8d07d-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="8d07d-128">Příklad, který ukazuje alternativu ke zrušení bloku toku dat tak, že další práce lze provést po zrušení operace, najdete v části [názorný postup: Použití toku dat v Windows Forms aplikace](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="8d07d-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="8d07d-129">Připojení kanálu toku dat v uživatelském rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d07d-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="8d07d-130">Tato část popisuje postup připojení kanálu toku dat v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8d07d-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="8d07d-131">Vytváření kanálu a přidávání pracovních položek do kanálu se řídí obslužnou rutinu události pro **přidat pracovní položky** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8d07d-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="8d07d-132">Zrušení inicializuje **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8d07d-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="8d07d-133">Po kliknutí na některý z těchto tlačítek, vyvolání příslušné akce v asynchronním režimu.</span><span class="sxs-lookup"><span data-stu-id="8d07d-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="8d07d-134">Připojení kanálu toku dat v uživatelském rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d07d-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1. <span data-ttu-id="8d07d-135">V návrháři formuláře pro hlavní formulář, vytvořit obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> události **přidat pracovní položky** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8d07d-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2. <span data-ttu-id="8d07d-136">Implementace <xref:System.Windows.Forms.ToolStripItem.Click> událost pro **přidat pracovní položky** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8d07d-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. <span data-ttu-id="8d07d-137">V návrháři formuláře pro hlavní formulář, vytvořit obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutiny události pro **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8d07d-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="8d07d-138">Implementace <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutiny události pro **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8d07d-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="8d07d-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d07d-139">Example</span></span>  
 <span data-ttu-id="8d07d-140">Následující příklad ukazuje kompletní kód pro Form1.cs (Form1.vb pro jazyk Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="8d07d-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="8d07d-141">Následující obrázek znázorňuje spuštěné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d07d-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="8d07d-142">![Aplikaci Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="8d07d-142">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="8d07d-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d07d-143">See also</span></span>

- [<span data-ttu-id="8d07d-144">Tok dat</span><span class="sxs-lookup"><span data-stu-id="8d07d-144">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
