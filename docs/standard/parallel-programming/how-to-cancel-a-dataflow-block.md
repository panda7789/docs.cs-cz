---
title: "Postupy: Zrušení bloku toku dat"
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
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 321b4a01b4ce6445ac43cffcc14cb68f29db050d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="e972c-102">Postupy: Zrušení bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="e972c-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="e972c-103">Tento dokument ukazuje, jak povolit zrušení ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e972c-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="e972c-104">Tento příklad používá Windows Forms k zobrazení, kde jsou aktivní v kanálu toku dat a také důsledky zrušení pracovních položek.</span><span class="sxs-lookup"><span data-stu-id="e972c-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="e972c-105">Knihovna toku dat TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> oboru názvů) není distribuované s [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e972c-105">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="e972c-106">K instalaci <xref:System.Threading.Tasks.Dataflow> obor názvů, otevřete projekt v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], zvolte **spravovat balíčky NuGet** z nabídky projektu a vyhledejte online `Microsoft.Tpl.Dataflow` balíčku.</span><span class="sxs-lookup"><span data-stu-id="e972c-106">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
### <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="e972c-107">K vytvoření Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="e972c-107">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="e972c-108">Vytvoření C# nebo Visual Basic **formulářové aplikace Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="e972c-108">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="e972c-109">V následujících krocích projektu jmenuje `CancellationWinForms`.</span><span class="sxs-lookup"><span data-stu-id="e972c-109">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2.  <span data-ttu-id="e972c-110">V návrháři formuláře pro hlavní formulář, Form1.cs (Form1.vb pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), přidejte <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e972c-110">On the form designer for the main form, Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3.  <span data-ttu-id="e972c-111">Přidat <xref:System.Windows.Forms.ToolStripButton> řídit k <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e972c-111">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="e972c-112">Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **přidat pracovní položky**.</span><span class="sxs-lookup"><span data-stu-id="e972c-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4.  <span data-ttu-id="e972c-113">Přidejte druhý <xref:System.Windows.Forms.ToolStripButton> řídit k <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e972c-113">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="e972c-114">Nastavit <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **zrušit**a <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> vlastnost `False`.</span><span class="sxs-lookup"><span data-stu-id="e972c-114">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5.  <span data-ttu-id="e972c-115">Přidat čtyři <xref:System.Windows.Forms.ToolStripProgressBar> objekty ke <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e972c-115">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="e972c-116">Vytvoření kanálu toku dat</span><span class="sxs-lookup"><span data-stu-id="e972c-116">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="e972c-117">Tato část popisuje postup vytvoření kanálu toku dat, který zpracovává pracovních položek a aktualizuje indikátory průběhu.</span><span class="sxs-lookup"><span data-stu-id="e972c-117">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
#### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="e972c-118">K vytvoření kanálu toku dat</span><span class="sxs-lookup"><span data-stu-id="e972c-118">To Create the Dataflow Pipeline</span></span>  
  
1.  <span data-ttu-id="e972c-119">Ve vašem projektu přidejte odkaz na System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="e972c-119">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="e972c-120">Ujistěte se, že Form1.cs (Form1.vb pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) obsahuje následující `using` příkazy (`Imports` v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="e972c-120">Ensure that Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contains the following `using` statements (`Imports` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="e972c-121">Přidat `WorkItem` třídu jako typ vnitřní `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="e972c-121">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="e972c-122">Přidejte následující členy dat tak, aby `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="e972c-122">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="e972c-123">Přidejte následující metodu `CreatePipeline`, na `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="e972c-123">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="e972c-124">Protože `incrementProgress` a `decrementProgress` toku dat bloky fungují v uživatelském rozhraní, je důležité, aby tyto akce se provedou ve vláknu uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e972c-124">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="e972c-125">K tomu během vytváření tyto objekty každý poskytují <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavena na hodnotu <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e972c-125">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e972c-126"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provede práci v aktuálním kontextu synchronizace.</span><span class="sxs-lookup"><span data-stu-id="e972c-126">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="e972c-127">Protože `Form1` konstruktor je volat z vlákna uživatelského rozhraní, akce `incrementProgress` a `decrementProgress` bloků toku dat taky spustit ve vláknu uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e972c-127">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="e972c-128">Tento příklad nastaví <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost, když se vytvoří členy kanálu.</span><span class="sxs-lookup"><span data-stu-id="e972c-128">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="e972c-129">Protože <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost trvale zruší spuštění bloku toku dat, celého kanálu musí být znovu vytvořen po uživatel operaci zruší a pak se chce přidat další pracovní položky do kanálu.</span><span class="sxs-lookup"><span data-stu-id="e972c-129">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="e972c-130">Příklad, alternativní způsob zrušení bloku toku dat tak, aby jinou práci lze provést po operace je zrušená, naleznete v části [návod: použití toku dat ve formulářové aplikaci Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="e972c-130">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="e972c-131">Připojování k uživatelské rozhraní kanálu toku dat</span><span class="sxs-lookup"><span data-stu-id="e972c-131">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="e972c-132">Tato část popisuje postup připojení kanálu toku dat s uživatelským rozhraním.</span><span class="sxs-lookup"><span data-stu-id="e972c-132">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="e972c-133">Vytvoření kanálu i přidávání pracovních položek do kanálu jsou řízeny obslužné rutiny události pro **přidat pracovní položky** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e972c-133">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="e972c-134">Zrušení se spouští pomocí **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e972c-134">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="e972c-135">Po kliknutí na tato tlačítka, je v asynchronním režimu inicioval příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="e972c-135">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
#### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="e972c-136">Pro připojení kanálu toku dat s uživatelským rozhraním</span><span class="sxs-lookup"><span data-stu-id="e972c-136">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1.  <span data-ttu-id="e972c-137">V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> události **přidat pracovní položky** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e972c-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2.  <span data-ttu-id="e972c-138">Implementace <xref:System.Windows.Forms.ToolStripItem.Click> události **přidat pracovní položky** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e972c-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  <span data-ttu-id="e972c-139">V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutiny události pro **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e972c-139">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="e972c-140">Implementace <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutiny události pro **zrušit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e972c-140">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="e972c-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="e972c-141">Example</span></span>  
 <span data-ttu-id="e972c-142">Následující příklad ukazuje kód dokončení pro Form1.cs (Form1.vb pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="e972c-142">The following example shows the complete code for Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="e972c-143">Následující obrázek znázorňuje běžící aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e972c-143">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="e972c-144">![Windows Forms aplikace](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="e972c-144">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e972c-145">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="e972c-145">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e972c-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="e972c-146">See Also</span></span>  
 [<span data-ttu-id="e972c-147">Tok dat</span><span class="sxs-lookup"><span data-stu-id="e972c-147">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
