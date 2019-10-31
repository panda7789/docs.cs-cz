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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140090"
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="c28e9-102">Postupy: Zrušení bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="c28e9-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="c28e9-103">Tento dokument ukazuje, jak povolit zrušení ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c28e9-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="c28e9-104">V tomto příkladu se používá model Windows Forms k zobrazení, kde jsou pracovní položky aktivní v kanálu toku dat a také důsledky zrušení.</span><span class="sxs-lookup"><span data-stu-id="c28e9-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="c28e9-105">Vytvoření aplikace model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c28e9-105">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="c28e9-106">Vytvořte projekt C# **aplikace model Windows Forms** nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c28e9-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="c28e9-107">V následujících krocích se projekt jmenuje `CancellationWinForms`.</span><span class="sxs-lookup"><span data-stu-id="c28e9-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2. <span data-ttu-id="c28e9-108">V návrháři formuláře pro hlavní formulář Form1.cs (Form1. vb pro Visual Basic) přidejte ovládací prvek <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="c28e9-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3. <span data-ttu-id="c28e9-109">Přidejte ovládací prvek <xref:System.Windows.Forms.ToolStripButton> do ovládacího prvku <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="c28e9-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="c28e9-110">Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a vlastnost <xref:System.Windows.Forms.ToolStripItem.Text%2A> pro **Přidání pracovních položek**.</span><span class="sxs-lookup"><span data-stu-id="c28e9-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4. <span data-ttu-id="c28e9-111">Přidejte druhý ovládací prvek <xref:System.Windows.Forms.ToolStripButton> k ovládacímu prvku <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="c28e9-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="c28e9-112">Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, vlastnost <xref:System.Windows.Forms.ToolStripItem.Text%2A> na **Storno**a vlastnost <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> na `False`.</span><span class="sxs-lookup"><span data-stu-id="c28e9-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5. <span data-ttu-id="c28e9-113">Přidejte čtyři objekty <xref:System.Windows.Forms.ToolStripProgressBar> k ovládacímu prvku <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="c28e9-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="c28e9-114">Vytvoření kanálu toku dat</span><span class="sxs-lookup"><span data-stu-id="c28e9-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="c28e9-115">Tato část popisuje, jak vytvořit kanál toku dat, který zpracovává pracovní položky a aktualizuje indikátory průběhu.</span><span class="sxs-lookup"><span data-stu-id="c28e9-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="c28e9-116">Vytvoření kanálu toku dat</span><span class="sxs-lookup"><span data-stu-id="c28e9-116">To Create the Dataflow Pipeline</span></span>  
  
1. <span data-ttu-id="c28e9-117">V projektu přidejte odkaz na System. Threading. Tasks. Dataflow. dll.</span><span class="sxs-lookup"><span data-stu-id="c28e9-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="c28e9-118">Ujistěte se, že Form1.cs (Form1. vb pro Visual Basic) obsahuje následující příkazy `using` (`Imports` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c28e9-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. <span data-ttu-id="c28e9-119">Přidejte třídu `WorkItem` jako vnitřní typ `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="c28e9-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. <span data-ttu-id="c28e9-120">Do třídy `Form1` přidejte následující datové členy.</span><span class="sxs-lookup"><span data-stu-id="c28e9-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. <span data-ttu-id="c28e9-121">Do `Form1` třídy přidejte následující metodu `CreatePipeline`.</span><span class="sxs-lookup"><span data-stu-id="c28e9-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="c28e9-122">Vzhledem k tomu, že bloky toku dat `incrementProgress` a `decrementProgress` fungují na uživatelském rozhraní, je důležité, aby tyto akce probíhaly ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c28e9-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="c28e9-123">Chcete-li to provést, během konstrukce těchto objektů poskytuje objekt <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>, který má vlastnost <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> nastavena na hodnotu <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c28e9-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c28e9-124">Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> vytvoří objekt <xref:System.Threading.Tasks.TaskScheduler>, který provádí práci na aktuálním kontextu synchronizace.</span><span class="sxs-lookup"><span data-stu-id="c28e9-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="c28e9-125">Vzhledem k tomu, že konstruktor `Form1` je volán z vlákna uživatelského rozhraní, akce pro bloky toku dat `incrementProgress` a `decrementProgress` jsou také spouštěny ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c28e9-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="c28e9-126">Tento příklad nastavuje vlastnost <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> při sestavování členů kanálu.</span><span class="sxs-lookup"><span data-stu-id="c28e9-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="c28e9-127">Vzhledem k tomu, že vlastnost <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> trvale zruší provádění bloku toku dat, je nutné znovu vytvořit celý kanál poté, co uživatel operaci zruší a pak chce do kanálu přidat další pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="c28e9-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="c28e9-128">Příklad, který ukazuje alternativní způsob, jak zrušit blok toku dat, aby bylo možné provést další práci po zrušení operace, naleznete v tématu [Návod: použití toku dat v aplikaci model Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="c28e9-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="c28e9-129">Připojení kanálu toku dat k uživatelskému rozhraní</span><span class="sxs-lookup"><span data-stu-id="c28e9-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="c28e9-130">Tato část popisuje, jak propojit kanál toku dat s uživatelským rozhraním.</span><span class="sxs-lookup"><span data-stu-id="c28e9-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="c28e9-131">Vytvoření kanálu a přidání pracovních položek do kanálu jsou ovládány obslužnou rutinou události pro tlačítko **Přidat pracovní položky** .</span><span class="sxs-lookup"><span data-stu-id="c28e9-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="c28e9-132">Zrušení je iniciováno tlačítkem **Zrušit** .</span><span class="sxs-lookup"><span data-stu-id="c28e9-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="c28e9-133">Když uživatel klikne na jedno z těchto tlačítek, je vhodná akce iniciována asynchronním způsobem.</span><span class="sxs-lookup"><span data-stu-id="c28e9-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="c28e9-134">Připojení kanálu toku dat k uživatelskému rozhraní</span><span class="sxs-lookup"><span data-stu-id="c28e9-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1. <span data-ttu-id="c28e9-135">V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.ToolStripItem.Click> pro tlačítko **Přidat pracovní položky** .</span><span class="sxs-lookup"><span data-stu-id="c28e9-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2. <span data-ttu-id="c28e9-136">Implementujte událost <xref:System.Windows.Forms.ToolStripItem.Click> pro tlačítko **Přidat pracovní položky** .</span><span class="sxs-lookup"><span data-stu-id="c28e9-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. <span data-ttu-id="c28e9-137">V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro obslužnou rutinu události <xref:System.Windows.Forms.ToolStripItem.Click> pro tlačítko **Storno** .</span><span class="sxs-lookup"><span data-stu-id="c28e9-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="c28e9-138">Implementujte obslužnou rutinu události <xref:System.Windows.Forms.ToolStripItem.Click> pro tlačítko **Storno** .</span><span class="sxs-lookup"><span data-stu-id="c28e9-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="c28e9-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="c28e9-139">Example</span></span>  
 <span data-ttu-id="c28e9-140">Následující příklad ukazuje úplný kód pro Form1.cs (Form1. vb pro Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c28e9-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="c28e9-141">Následující ilustrace znázorňuje běžící aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c28e9-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="c28e9-142">![Aplikace model Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="c28e9-142">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="c28e9-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c28e9-143">See also</span></span>

- [<span data-ttu-id="c28e9-144">Tok dat</span><span class="sxs-lookup"><span data-stu-id="c28e9-144">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
