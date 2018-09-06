---
title: 'Postupy: Určení plánovače úloh v bloku toku dat'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9338d06cf7774e1451a0c470c7e078cdb17510ae
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43879074"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a><span data-ttu-id="ae373-102">Postupy: Určení plánovače úloh v bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="ae373-102">How to: Specify a Task Scheduler in a Dataflow Block</span></span>
<span data-ttu-id="ae373-103">Tento dokument ukazuje, jak přiřadit určitým plánovačem úloh, při použití toku dat ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ae373-103">This document demonstrates how to associate a specific task scheduler when you use dataflow in your application.</span></span> <span data-ttu-id="ae373-104">V příkladu se používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> třídy v aplikaci Windows Forms k zobrazení, čtečky úkoly, které mají aktivní a pokud je aktivní úlohy zapisovače.</span><span class="sxs-lookup"><span data-stu-id="ae373-104">The example uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> class in a Windows Forms application to show when reader tasks are active and when a writer task is active.</span></span> <span data-ttu-id="ae373-105">Využívá také <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> způsob povolení bloku toku dat pro spuštění ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ae373-105">It also uses the <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method to enable a dataflow block to run on the user-interface thread.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="ae373-106">Chcete-li vytvořit Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="ae373-106">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="ae373-107">Vytvoření aplikace Visual C# nebo Visual Basic **formulářová aplikace Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="ae373-107">Create a Visual C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="ae373-108">V následujících krocích se projekt s názvem `WriterReadersWinForms`.</span><span class="sxs-lookup"><span data-stu-id="ae373-108">In the following steps, the project is named `WriterReadersWinForms`.</span></span>  
  
2.  <span data-ttu-id="ae373-109">V návrháři formuláře pro hlavní formulář Form1.cs (Form1.vb pro jazyk Visual Basic), přidejte čtyři <xref:System.Windows.Forms.CheckBox> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ae373-109">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add four <xref:System.Windows.Forms.CheckBox> controls.</span></span> <span data-ttu-id="ae373-110">Nastavte <xref:System.Windows.Forms.Control.Text%2A> vlastnost **čtečky 1** pro `checkBox1`, **čtečky 2** pro `checkBox2`, **čtečky 3** pro `checkBox3`, a  **Zapisovač** pro `checkBox4`.</span><span class="sxs-lookup"><span data-stu-id="ae373-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to **Reader 1** for `checkBox1`, **Reader 2** for `checkBox2`, **Reader 3** for `checkBox3`, and **Writer** for `checkBox4`.</span></span> <span data-ttu-id="ae373-111">Nastavte <xref:System.Windows.Forms.Control.Enabled%2A> vlastnost pro každý ovládací prvek na `False`.</span><span class="sxs-lookup"><span data-stu-id="ae373-111">Set the <xref:System.Windows.Forms.Control.Enabled%2A> property for each control to `False`.</span></span>  
  
3.  <span data-ttu-id="ae373-112">Přidat <xref:System.Windows.Forms.Timer> ovládacího prvku na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ae373-112">Add a <xref:System.Windows.Forms.Timer> control to the form.</span></span> <span data-ttu-id="ae373-113">Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost `2500`.</span><span class="sxs-lookup"><span data-stu-id="ae373-113">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `2500`.</span></span>  
  
## <a name="adding-dataflow-functionality"></a><span data-ttu-id="ae373-114">Přidání funkce toku dat</span><span class="sxs-lookup"><span data-stu-id="ae373-114">Adding Dataflow Functionality</span></span>  
 <span data-ttu-id="ae373-115">Tato část popisuje postup vytvoření bloků toku dat, které se účastní v aplikaci a jak přidružit každý z nich pomocí plánovače úloh.</span><span class="sxs-lookup"><span data-stu-id="ae373-115">This section describes how to create the dataflow blocks that participate in the application and how to associate each one with a task scheduler.</span></span>  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a><span data-ttu-id="ae373-116">Přidání funkčnosti toku dat do aplikace</span><span class="sxs-lookup"><span data-stu-id="ae373-116">To Add Dataflow Functionality to the Application</span></span>  
  
1.  <span data-ttu-id="ae373-117">Ve vašem projektu přidejte odkaz na System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="ae373-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="ae373-118">Ujistěte se, že Form1.cs (Form1.vb pro jazyk Visual Basic) obsahuje následující `using` příkazy (`Imports` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ae373-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="ae373-119">Přidat <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> datový člen do `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="ae373-119">Add a <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> data member to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="ae373-120">V `Form1` konstruktor po volání `InitializeComponent`, vytvoření <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu, která přepíná stav <xref:System.Windows.Forms.CheckBox> objekty.</span><span class="sxs-lookup"><span data-stu-id="ae373-120">In the `Form1` constructor, after the call to `InitializeComponent`, create an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that toggles the state of <xref:System.Windows.Forms.CheckBox> objects.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="ae373-121">V `Form1` konstruktoru, vytvořit <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objektu a čtyři <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekty, jeden <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt pro každou <xref:System.Windows.Forms.CheckBox> objektu.</span><span class="sxs-lookup"><span data-stu-id="ae373-121">In the `Form1` constructor, create a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object and four <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objects, one <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object for each <xref:System.Windows.Forms.CheckBox> object.</span></span> <span data-ttu-id="ae373-122">Pro každou <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu, zadejte <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavena na hodnotu <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> vlastnost pro čtení a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> vlastnost pro modul pro zápis.</span><span class="sxs-lookup"><span data-stu-id="ae373-122">For each <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object, specify a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> property for the readers, and the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> property for the writer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6.  <span data-ttu-id="ae373-123">V `Form1` konstruktoru, start <xref:System.Windows.Forms.Timer> objektu.</span><span class="sxs-lookup"><span data-stu-id="ae373-123">In the `Form1` constructor, start the <xref:System.Windows.Forms.Timer> object.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7.  <span data-ttu-id="ae373-124">V návrháři formuláře pro hlavní formulář, vytvořit obslužnou rutinu události pro <xref:System.Windows.Forms.Timer.Tick> událost časovače.</span><span class="sxs-lookup"><span data-stu-id="ae373-124">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
8.  <span data-ttu-id="ae373-125">Implementace <xref:System.Windows.Forms.Timer.Tick> událost časovače.</span><span class="sxs-lookup"><span data-stu-id="ae373-125">Implement the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 <span data-ttu-id="ae373-126">Vzhledem k tomu, `toggleCheckBox` funguje bloku toku dat v uživatelském rozhraní, je důležité, tato akce vyskytovat ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ae373-126">Because the `toggleCheckBox` dataflow block acts on the user interface, it is important that this action occur on the user-interface thread.</span></span> <span data-ttu-id="ae373-127">K tomu, během konstrukce, které obsahuje tento objekt <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> nastavenou na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ae373-127">To accomplish this, during construction this object provides a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ae373-128"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> Metoda vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provede práci na aktuálním kontextu synchronizace.</span><span class="sxs-lookup"><span data-stu-id="ae373-128">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="ae373-129">Vzhledem k tomu, `Form1` konstruktoru se volá z vlákna uživatelského rozhraní, akce pro `toggleCheckBox` bloku toku dat také běží na vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ae373-129">Because the `Form1` constructor is called from the user-interface thread, the action for the `toggleCheckBox` dataflow block also runs on the user-interface thread.</span></span>  
  
 <span data-ttu-id="ae373-130">Tento příklad také používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> třídy umožňující některé bloků toku dat tak, aby fungoval současně a jiného bloku toku dat tak, aby fungoval s ohledem na všechny ostatní bloků toku dat, které běží na stejné exkluzivní <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objektu.</span><span class="sxs-lookup"><span data-stu-id="ae373-130">This example also uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> class to enable some dataflow blocks to act concurrently, and another dataflow block to act exclusive with respect to all other dataflow blocks that run on the same <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object.</span></span> <span data-ttu-id="ae373-131">Tato technika je užitečná, když více bloků toku dat sdílet prostředek a některé vyžadují výhradní přístup k prostředku, protože eliminuje nutnost ručně synchronizovat přístup k prostředku.</span><span class="sxs-lookup"><span data-stu-id="ae373-131">This technique is useful when multiple dataflow blocks share a resource and some require exclusive access to that resource, because it eliminates the requirement to manually synchronize access to that resource.</span></span> <span data-ttu-id="ae373-132">Eliminace ruční synchronizace může být efektivnější kódu.</span><span class="sxs-lookup"><span data-stu-id="ae373-132">The elimination of manual synchronization can make code more efficient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae373-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae373-133">Example</span></span>  
 <span data-ttu-id="ae373-134">Následující příklad ukazuje kompletní kód pro Form1.cs (Form1.vb pro jazyk Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ae373-134">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="ae373-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae373-135">See also</span></span>

- [<span data-ttu-id="ae373-136">Tok dat</span><span class="sxs-lookup"><span data-stu-id="ae373-136">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
