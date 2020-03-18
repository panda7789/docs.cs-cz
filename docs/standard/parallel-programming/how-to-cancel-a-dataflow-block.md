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
ms.openlocfilehash: aa175d95f27fcbf28c3f3da3eaa7b8f7988681e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140090"
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="f7e45-102">Postupy: Zrušení bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="f7e45-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="f7e45-103">Tento dokument ukazuje, jak povolit zrušení ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f7e45-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="f7e45-104">Tento příklad používá Windows Forms k zobrazení, kde jsou aktivní pracovní položky v kanálu toku dat a také účinky zrušení.</span><span class="sxs-lookup"><span data-stu-id="f7e45-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="f7e45-105">Vytvoření aplikace windows forms</span><span class="sxs-lookup"><span data-stu-id="f7e45-105">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="f7e45-106">Vytvořte projekt aplikace C# nebo Visual Basic **Forms Application.**</span><span class="sxs-lookup"><span data-stu-id="f7e45-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="f7e45-107">V následujících krocích je `CancellationWinForms`projekt pojmenován .</span><span class="sxs-lookup"><span data-stu-id="f7e45-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2. <span data-ttu-id="f7e45-108">V návrháři formuláře pro hlavní formulář, Form1.cs (Form1.vb <xref:System.Windows.Forms.ToolStrip> pro visual basic), přidejte ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f7e45-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3. <span data-ttu-id="f7e45-109">Přidejte <xref:System.Windows.Forms.ToolStripButton> ovládací <xref:System.Windows.Forms.ToolStrip> prvek do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f7e45-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="f7e45-110">Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **přidat pracovní položky**.</span><span class="sxs-lookup"><span data-stu-id="f7e45-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4. <span data-ttu-id="f7e45-111">Přidejte <xref:System.Windows.Forms.ToolStripButton> druhý ovládací <xref:System.Windows.Forms.ToolStrip> prvek do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f7e45-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="f7e45-112">Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>na <xref:System.Windows.Forms.ToolStripItem.Text%2A> , vlastnost **cancel** <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> a `False`vlastnost na .</span><span class="sxs-lookup"><span data-stu-id="f7e45-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5. <span data-ttu-id="f7e45-113">Přidejte <xref:System.Windows.Forms.ToolStripProgressBar> do <xref:System.Windows.Forms.ToolStrip> ovládacího prvku čtyři objekty.</span><span class="sxs-lookup"><span data-stu-id="f7e45-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="f7e45-114">Vytvoření kanálu toku dat</span><span class="sxs-lookup"><span data-stu-id="f7e45-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="f7e45-115">Tato část popisuje, jak vytvořit kanál toku dat, který zpracovává pracovní položky a aktualizuje indikátory průběhu.</span><span class="sxs-lookup"><span data-stu-id="f7e45-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="f7e45-116">Vytvoření kanálu toku dat</span><span class="sxs-lookup"><span data-stu-id="f7e45-116">To Create the Dataflow Pipeline</span></span>  
  
1. <span data-ttu-id="f7e45-117">V projektu přidejte odkaz na System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="f7e45-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="f7e45-118">Ujistěte se, že Form1.cs (Form1.vb `using` pro`Imports` visual basic) obsahuje následující příkazy ( v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f7e45-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. <span data-ttu-id="f7e45-119">Přidejte `WorkItem` třídu jako vnitřní `Form1` typ třídy.</span><span class="sxs-lookup"><span data-stu-id="f7e45-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. <span data-ttu-id="f7e45-120">Přidejte následující datové `Form1` členy do třídy.</span><span class="sxs-lookup"><span data-stu-id="f7e45-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. <span data-ttu-id="f7e45-121">Přidejte následující `CreatePipeline`metodu `Form1` , do třídy.</span><span class="sxs-lookup"><span data-stu-id="f7e45-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="f7e45-122">Vzhledem `incrementProgress` `decrementProgress` k tomu, že bloky a tok dat působí na uživatelské rozhraní, je důležité, aby tyto akce dojít ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f7e45-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="f7e45-123">Chcete-li to provést, během <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> konstrukce tyto <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> objekty <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>každý poskytnout objekt, který má vlastnost nastavena na .</span><span class="sxs-lookup"><span data-stu-id="f7e45-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f7e45-124">Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provádí práci na aktuálním kontextu synchronizace.</span><span class="sxs-lookup"><span data-stu-id="f7e45-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="f7e45-125">Vzhledem `Form1` k tomu, že konstruktor je volána `incrementProgress` `decrementProgress` z vlákna uživatelského rozhraní, akce pro bloky a tok dat také spustit ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f7e45-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="f7e45-126">Tento příklad <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> nastaví vlastnost při konstrukci členy kanálu.</span><span class="sxs-lookup"><span data-stu-id="f7e45-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="f7e45-127">Vzhledem <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> k tomu, že vlastnost trvale zruší spuštění bloku toku dat, celý kanál musí být znovu vytvořen poté, co uživatel zruší operaci a pak chce přidat další pracovní položky do kanálu.</span><span class="sxs-lookup"><span data-stu-id="f7e45-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="f7e45-128">Příklad, který ukazuje alternativní způsob zrušení bloku toku dat tak, aby bylo možné provést další práci po zrušení operace, naleznete v [návodu: Použití toku dat v aplikaci Windows Forms .](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)</span><span class="sxs-lookup"><span data-stu-id="f7e45-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="f7e45-129">Připojení kanálu toku dat k uživatelskému rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7e45-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="f7e45-130">Tato část popisuje, jak připojit kanál toku dat k uživatelskému rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f7e45-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="f7e45-131">Vytvoření kanálu a přidání pracovních položek do kanálu jsou řízeny obslužnou rutinou události pro tlačítko **Přidat pracovní položky.**</span><span class="sxs-lookup"><span data-stu-id="f7e45-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="f7e45-132">Zrušení je iniciováno tlačítkem **Storno.**</span><span class="sxs-lookup"><span data-stu-id="f7e45-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="f7e45-133">Když uživatel klepne na některou z těchto tlačítek, příslušná akce je zahájena asynchronním způsobem.</span><span class="sxs-lookup"><span data-stu-id="f7e45-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="f7e45-134">Připojení kanálu toku dat k uživatelskému rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7e45-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1. <span data-ttu-id="f7e45-135">V návrháři formuláře pro hlavní formulář vytvořte <xref:System.Windows.Forms.ToolStripItem.Click> obslužnou rutinu události pro tlačítko **Přidat pracovní položky.**</span><span class="sxs-lookup"><span data-stu-id="f7e45-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2. <span data-ttu-id="f7e45-136">Implementujte <xref:System.Windows.Forms.ToolStripItem.Click> událost pro tlačítko **Přidat pracovní položky.**</span><span class="sxs-lookup"><span data-stu-id="f7e45-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. <span data-ttu-id="f7e45-137">V návrháři formuláře pro hlavní formulář vytvořte <xref:System.Windows.Forms.ToolStripItem.Click> obslužnou rutinu události pro obslužnou rutinu události pro tlačítko **Storno.**</span><span class="sxs-lookup"><span data-stu-id="f7e45-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="f7e45-138">Implementujte <xref:System.Windows.Forms.ToolStripItem.Click> obslužnou rutinu události pro tlačítko **Storno.**</span><span class="sxs-lookup"><span data-stu-id="f7e45-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="f7e45-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7e45-139">Example</span></span>  
 <span data-ttu-id="f7e45-140">Následující příklad ukazuje úplný kód pro Form1.cs (Form1.vb pro visual basic).</span><span class="sxs-lookup"><span data-stu-id="f7e45-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="f7e45-141">Následující obrázek znázorňuje spuštěnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f7e45-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="f7e45-142">![Aplikace Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="f7e45-142">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="f7e45-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7e45-143">See also</span></span>

- [<span data-ttu-id="f7e45-144">Tok dat</span><span class="sxs-lookup"><span data-stu-id="f7e45-144">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
