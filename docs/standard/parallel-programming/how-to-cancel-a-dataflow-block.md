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
ms.openlocfilehash: 530c231deeaba007975849ab6dc41f4da6a859ea
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285544"
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="3cdf5-102">Postupy: Zrušení bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="3cdf5-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="3cdf5-103">Tento dokument ukazuje, jak povolit zrušení ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="3cdf5-104">V tomto příkladu se používá model Windows Forms k zobrazení, kde jsou pracovní položky aktivní v kanálu toku dat a také důsledky zrušení.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="3cdf5-105">Vytvoření aplikace model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3cdf5-105">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="3cdf5-106">Vytvořte projekt aplikace v jazyce C# nebo Visual Basic **model Windows Forms** .</span><span class="sxs-lookup"><span data-stu-id="3cdf5-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="3cdf5-107">V následujících krocích se projekt jmenuje `CancellationWinForms` .</span><span class="sxs-lookup"><span data-stu-id="3cdf5-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2. <span data-ttu-id="3cdf5-108">V návrháři formuláře pro hlavní formulář Form1.cs (Form1. vb pro Visual Basic) přidejte <xref:System.Windows.Forms.ToolStrip> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3. <span data-ttu-id="3cdf5-109">Přidejte <xref:System.Windows.Forms.ToolStripButton> ovládací prvek do <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="3cdf5-110">Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a vlastnost, <xref:System.Windows.Forms.ToolStripItem.Text%2A> Chcete-li **Přidat pracovní položky**.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4. <span data-ttu-id="3cdf5-111">Přidejte <xref:System.Windows.Forms.ToolStripButton> k <xref:System.Windows.Forms.ToolStrip> ovládacímu prvku druhý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="3cdf5-112">Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost na vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> , kterou <xref:System.Windows.Forms.ToolStripItem.Text%2A> chcete **Zrušit**, a <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> vlastnost na hodnotu `False` .</span><span class="sxs-lookup"><span data-stu-id="3cdf5-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5. <span data-ttu-id="3cdf5-113">Přidejte <xref:System.Windows.Forms.ToolStripProgressBar> do <xref:System.Windows.Forms.ToolStrip> ovládacího prvku čtyři objekty.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="3cdf5-114">Vytvoření kanálu toku dat</span><span class="sxs-lookup"><span data-stu-id="3cdf5-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="3cdf5-115">Tato část popisuje, jak vytvořit kanál toku dat, který zpracovává pracovní položky a aktualizuje indikátory průběhu.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="3cdf5-116">Vytvoření kanálu toku dat</span><span class="sxs-lookup"><span data-stu-id="3cdf5-116">To Create the Dataflow Pipeline</span></span>  
  
1. <span data-ttu-id="3cdf5-117">V projektu přidejte odkaz na System. Threading. Tasks. Dataflow. dll.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="3cdf5-118">Ujistěte se, že Form1.cs (Form1. vb pro Visual Basic) obsahuje následující `using` příkazy ( `Imports` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="3cdf5-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. <span data-ttu-id="3cdf5-119">Přidejte `WorkItem` třídu jako vnitřní typ `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. <span data-ttu-id="3cdf5-120">Přidejte do třídy následující datové členy `Form1` .</span><span class="sxs-lookup"><span data-stu-id="3cdf5-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. <span data-ttu-id="3cdf5-121">Přidejte následující metodu `CreatePipeline` do `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="3cdf5-122">Vzhledem k tomu, že `incrementProgress` `decrementProgress` bloky a tok dat fungují na uživatelském rozhraní, je důležité, aby tyto akce probíhaly ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="3cdf5-123">K tomu je potřeba během vytváření těchto objektů vytvořit <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavenou na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3cdf5-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3cdf5-124"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>Metoda vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provádí práci na aktuálním kontextu synchronizace.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="3cdf5-125">Vzhledem k tomu `Form1` , že je konstruktor volán z vlákna uživatelského rozhraní, jsou akce pro `incrementProgress` `decrementProgress` bloky a tok dat také spouštěny ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="3cdf5-126">Tento příklad nastaví <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost při sestavování členů kanálu.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="3cdf5-127">Vzhledem k tomu <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> , že vlastnost trvale zruší provádění bloku toku dat, musí být celý kanál znovu vytvořen poté, co uživatel operaci zruší a pak chce do kanálu přidat další pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="3cdf5-128">Příklad, který ukazuje alternativní způsob, jak zrušit blok toku dat, aby bylo možné provést další práci po zrušení operace, naleznete v tématu [Návod: použití toku dat v aplikaci model Windows Forms](walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="3cdf5-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="3cdf5-129">Připojení kanálu toku dat k uživatelskému rozhraní</span><span class="sxs-lookup"><span data-stu-id="3cdf5-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="3cdf5-130">Tato část popisuje, jak propojit kanál toku dat s uživatelským rozhraním.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="3cdf5-131">Vytvoření kanálu a přidání pracovních položek do kanálu jsou ovládány obslužnou rutinou události pro tlačítko **Přidat pracovní položky** .</span><span class="sxs-lookup"><span data-stu-id="3cdf5-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="3cdf5-132">Zrušení je iniciováno tlačítkem **Zrušit** .</span><span class="sxs-lookup"><span data-stu-id="3cdf5-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="3cdf5-133">Když uživatel klikne na jedno z těchto tlačítek, je vhodná akce iniciována asynchronním způsobem.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="3cdf5-134">Připojení kanálu toku dat k uživatelskému rozhraní</span><span class="sxs-lookup"><span data-stu-id="3cdf5-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1. <span data-ttu-id="3cdf5-135">V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> událost pro tlačítko **Přidat pracovní položky** .</span><span class="sxs-lookup"><span data-stu-id="3cdf5-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2. <span data-ttu-id="3cdf5-136">Implementujte <xref:System.Windows.Forms.ToolStripItem.Click> událost pro tlačítko **Přidat pracovní položky** .</span><span class="sxs-lookup"><span data-stu-id="3cdf5-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. <span data-ttu-id="3cdf5-137">V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> obslužnou rutinu události pro tlačítko **Storno** .</span><span class="sxs-lookup"><span data-stu-id="3cdf5-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="3cdf5-138">Implementujte <xref:System.Windows.Forms.ToolStripItem.Click> obslužnou rutinu události pro tlačítko **Storno** .</span><span class="sxs-lookup"><span data-stu-id="3cdf5-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="3cdf5-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="3cdf5-139">Example</span></span>  
 <span data-ttu-id="3cdf5-140">Následující příklad ukazuje úplný kód pro Form1.cs (Form1. vb pro Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="3cdf5-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="3cdf5-141">Následující ilustrace znázorňuje běžící aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3cdf5-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="3cdf5-142">![Aplikace model Windows Forms](media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="3cdf5-142">![The Windows Forms Application](media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="3cdf5-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="3cdf5-143">See also</span></span>

- [<span data-ttu-id="3cdf5-144">Tok dat</span><span class="sxs-lookup"><span data-stu-id="3cdf5-144">Dataflow</span></span>](dataflow-task-parallel-library.md)
