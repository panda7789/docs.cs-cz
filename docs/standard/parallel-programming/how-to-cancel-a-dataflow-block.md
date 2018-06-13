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
ms.openlocfilehash: 2684473f82eb156bf8762c9797503324f318632d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584902"
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="df1b3-102">Postupy: Zrušení bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="df1b3-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="df1b3-103">Tento dokument ukazuje, jak povolit zrušení ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="df1b3-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="df1b3-104">Tento příklad používá Windows Forms k zobrazení, kde jsou aktivní v kanálu toku dat a také důsledky zrušení pracovních položek.</span><span class="sxs-lookup"><span data-stu-id="df1b3-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="df1b3-105">K vytvoření Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="df1b3-105">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="df1b3-106">Vytvoření C# nebo Visual Basic **formulářové aplikace Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="df1b3-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="df1b3-107">V následujících krocích projektu jmenuje `CancellationWinForms`.</span><span class="sxs-lookup"><span data-stu-id="df1b3-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2.  <span data-ttu-id="df1b3-108">V návrháři formuláře pro hlavní formulář Form1.cs (Form1.vb jazyka Visual Basic), přidejte <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="df1b3-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3.  <span data-ttu-id="df1b3-109">Přidat <xref:System.Windows.Forms.ToolStripButton> řídit k <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="df1b3-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="df1b3-110">Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **přidat pracovní položky**.</span><span class="sxs-lookup"><span data-stu-id="df1b3-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4.  <span data-ttu-id="df1b3-111">Přidejte druhý <xref:System.Windows.Forms.ToolStripButton> řídit k <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="df1b3-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="df1b3-112">Nastavit <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **zrušit**a <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> vlastnost `False`.</span><span class="sxs-lookup"><span data-stu-id="df1b3-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5.  <span data-ttu-id="df1b3-113">Přidat čtyři <xref:System.Windows.Forms.ToolStripProgressBar> objekty ke <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="df1b3-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="df1b3-114">Vytvoření kanálu toku dat</span><span class="sxs-lookup"><span data-stu-id="df1b3-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="df1b3-115">Tato část popisuje postup vytvoření kanálu toku dat, který zpracovává pracovních položek a aktualizuje indikátory průběhu.</span><span class="sxs-lookup"><span data-stu-id="df1b3-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="df1b3-116">K vytvoření kanálu toku dat</span><span class="sxs-lookup"><span data-stu-id="df1b3-116">To Create the Dataflow Pipeline</span></span>  
  
1.  <span data-ttu-id="df1b3-117">Ve vašem projektu přidejte odkaz na System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="df1b3-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="df1b3-118">Ujistěte se, že Form1.cs (Form1.vb jazyka Visual Basic) obsahuje následující `using` příkazy (`Imports` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="df1b3-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="df1b3-119">Přidat `WorkItem` třídu jako typ vnitřní `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="df1b3-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="df1b3-120">Přidejte následující členy dat tak, aby `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="df1b3-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="df1b3-121">Přidejte následující metodu `CreatePipeline`, na `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="df1b3-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="df1b3-122">Protože `incrementProgress` a `decrementProgress` toku dat bloky fungují v uživatelském rozhraní, je důležité, aby tyto akce se provedou ve vláknu uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="df1b3-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="df1b3-123">K tomu během vytváření tyto objekty každý poskytují <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavena na hodnotu <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="df1b3-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="df1b3-124"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provede práci v aktuálním kontextu synchronizace.</span><span class="sxs-lookup"><span data-stu-id="df1b3-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="df1b3-125">Protože `Form1` konstruktor je volat z vlákna uživatelského rozhraní, akce `incrementProgress` a `decrementProgress` bloků toku dat taky spustit ve vláknu uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="df1b3-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="df1b3-126">Tento příklad nastaví <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost, když se vytvoří členy kanálu.</span><span class="sxs-lookup"><span data-stu-id="df1b3-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="df1b3-127">Protože <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost trvale zruší spuštění bloku toku dat, celého kanálu musí být znovu vytvořen po uživatel operaci zruší a pak se chce přidat další pracovní položky do kanálu.</span><span class="sxs-lookup"><span data-stu-id="df1b3-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="df1b3-128">Příklad, alternativní způsob zrušení bloku toku dat tak, aby jinou práci lze provést po operace je zrušená, naleznete v části [návod: použití toku dat ve formulářové aplikaci Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="df1b3-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="df1b3-129">Připojování k uživatelské rozhraní kanálu toku dat</span><span class="sxs-lookup"><span data-stu-id="df1b3-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="df1b3-130">Tato část popisuje postup připojení kanálu toku dat s uživatelským rozhraním.</span><span class="sxs-lookup"><span data-stu-id="df1b3-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="df1b3-131">Vytvoření kanálu i přidávání pracovních položek do kanálu jsou řízeny obslužné rutiny události pro **přidat pracovní položky** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="df1b3-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="df1b3-132">Zrušení se spouští pomocí **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="df1b3-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="df1b3-133">Po kliknutí na tato tlačítka, je v asynchronním režimu inicioval příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="df1b3-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="df1b3-134">Pro připojení kanálu toku dat s uživatelským rozhraním</span><span class="sxs-lookup"><span data-stu-id="df1b3-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1.  <span data-ttu-id="df1b3-135">V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> události **přidat pracovní položky** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="df1b3-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2.  <span data-ttu-id="df1b3-136">Implementace <xref:System.Windows.Forms.ToolStripItem.Click> události **přidat pracovní položky** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="df1b3-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  <span data-ttu-id="df1b3-137">V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutiny události pro **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="df1b3-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="df1b3-138">Implementace <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutiny události pro **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="df1b3-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="df1b3-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="df1b3-139">Example</span></span>  
 <span data-ttu-id="df1b3-140">Následující příklad ukazuje kód dokončení pro Form1.cs (Form1.vb jazyka Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="df1b3-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="df1b3-141">Následující obrázek znázorňuje běžící aplikaci.</span><span class="sxs-lookup"><span data-stu-id="df1b3-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="df1b3-142">![Windows Forms aplikace](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="df1b3-142">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="df1b3-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="df1b3-143">See Also</span></span>  
 [<span data-ttu-id="df1b3-144">Tok dat</span><span class="sxs-lookup"><span data-stu-id="df1b3-144">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
