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
ms.openlocfilehash: 2abac1ccf45fc9c9c28e27c132e72fe483a24d75
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122222"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a><span data-ttu-id="6bbef-102">Postupy: Určení plánovače úloh v bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="6bbef-102">How to: Specify a Task Scheduler in a Dataflow Block</span></span>
<span data-ttu-id="6bbef-103">Tento dokument ukazuje, jak přidružit konkrétní Plánovač úloh při použití toku dat ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6bbef-103">This document demonstrates how to associate a specific task scheduler when you use dataflow in your application.</span></span> <span data-ttu-id="6bbef-104">V příkladu se používá třída <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> v model Windows Forms aplikaci k zobrazení, když jsou úlohy čtecího zařízení aktivní a když je aktivní úkol zapisovače.</span><span class="sxs-lookup"><span data-stu-id="6bbef-104">The example uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> class in a Windows Forms application to show when reader tasks are active and when a writer task is active.</span></span> <span data-ttu-id="6bbef-105">Používá také metodu <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> k umožnění spuštění bloku toku dat ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6bbef-105">It also uses the <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method to enable a dataflow block to run on the user-interface thread.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="6bbef-106">Vytvoření aplikace model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6bbef-106">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="6bbef-107">Vytvořte projekt aplikace C# Visual nebo Visual Basic **model Windows Forms** .</span><span class="sxs-lookup"><span data-stu-id="6bbef-107">Create a Visual C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="6bbef-108">V následujících krocích se projekt jmenuje `WriterReadersWinForms`.</span><span class="sxs-lookup"><span data-stu-id="6bbef-108">In the following steps, the project is named `WriterReadersWinForms`.</span></span>  
  
2. <span data-ttu-id="6bbef-109">V návrháři formuláře pro hlavní formulář Form1.cs (Form1. vb pro Visual Basic) přidejte čtyři ovládací prvky <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="6bbef-109">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add four <xref:System.Windows.Forms.CheckBox> controls.</span></span> <span data-ttu-id="6bbef-110">Vlastnost <xref:System.Windows.Forms.Control.Text%2A> nastavte na **Reader 1** pro `checkBox1`, **reader 2** pro `checkBox2`, **Reader 3** pro `checkBox3`a **zapisovač** pro `checkBox4`.</span><span class="sxs-lookup"><span data-stu-id="6bbef-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to **Reader 1** for `checkBox1`, **Reader 2** for `checkBox2`, **Reader 3** for `checkBox3`, and **Writer** for `checkBox4`.</span></span> <span data-ttu-id="6bbef-111">Nastavte vlastnost <xref:System.Windows.Forms.Control.Enabled%2A> pro každý ovládací prvek na `False`.</span><span class="sxs-lookup"><span data-stu-id="6bbef-111">Set the <xref:System.Windows.Forms.Control.Enabled%2A> property for each control to `False`.</span></span>  
  
3. <span data-ttu-id="6bbef-112">Přidejte ovládací prvek <xref:System.Windows.Forms.Timer> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="6bbef-112">Add a <xref:System.Windows.Forms.Timer> control to the form.</span></span> <span data-ttu-id="6bbef-113">Vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> nastavte na hodnotu `2500`.</span><span class="sxs-lookup"><span data-stu-id="6bbef-113">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `2500`.</span></span>  
  
## <a name="adding-dataflow-functionality"></a><span data-ttu-id="6bbef-114">Přidání funkce toku dat</span><span class="sxs-lookup"><span data-stu-id="6bbef-114">Adding Dataflow Functionality</span></span>  
 <span data-ttu-id="6bbef-115">V této části se dozvíte, jak vytvořit bloky toku dat, které se účastní aplikace, a jak je přidružit k Plánovači úloh.</span><span class="sxs-lookup"><span data-stu-id="6bbef-115">This section describes how to create the dataflow blocks that participate in the application and how to associate each one with a task scheduler.</span></span>  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a><span data-ttu-id="6bbef-116">Přidání funkce toku dat do aplikace</span><span class="sxs-lookup"><span data-stu-id="6bbef-116">To Add Dataflow Functionality to the Application</span></span>  
  
1. <span data-ttu-id="6bbef-117">V projektu přidejte odkaz na System. Threading. Tasks. Dataflow. dll.</span><span class="sxs-lookup"><span data-stu-id="6bbef-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="6bbef-118">Ujistěte se, že Form1.cs (Form1. vb pro Visual Basic) obsahuje následující příkazy `using` (`Imports` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6bbef-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. <span data-ttu-id="6bbef-119">Přidejte datový člen <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> do třídy `Form1`.</span><span class="sxs-lookup"><span data-stu-id="6bbef-119">Add a <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> data member to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. <span data-ttu-id="6bbef-120">V konstruktoru `Form1` po volání `InitializeComponent`vytvořte objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, který přepíná stav objektů <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="6bbef-120">In the `Form1` constructor, after the call to `InitializeComponent`, create an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that toggles the state of <xref:System.Windows.Forms.CheckBox> objects.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. <span data-ttu-id="6bbef-121">V konstruktoru `Form1` vytvořte objekt <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> a čtyři objekty <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, jeden <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt pro každý objekt <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="6bbef-121">In the `Form1` constructor, create a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object and four <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objects, one <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object for each <xref:System.Windows.Forms.CheckBox> object.</span></span> <span data-ttu-id="6bbef-122">Pro každý objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> určete <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má vlastnost <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> nastavenou na vlastnost <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> pro čtecí zařízení a vlastnost <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> pro modul pro zápis.</span><span class="sxs-lookup"><span data-stu-id="6bbef-122">For each <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object, specify a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> property for the readers, and the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> property for the writer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. <span data-ttu-id="6bbef-123">V konstruktoru `Form1` spusťte objekt <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="6bbef-123">In the `Form1` constructor, start the <xref:System.Windows.Forms.Timer> object.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. <span data-ttu-id="6bbef-124">V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.Timer.Tick> pro časovač.</span><span class="sxs-lookup"><span data-stu-id="6bbef-124">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
8. <span data-ttu-id="6bbef-125">Implementujte událost <xref:System.Windows.Forms.Timer.Tick> pro časovač.</span><span class="sxs-lookup"><span data-stu-id="6bbef-125">Implement the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 <span data-ttu-id="6bbef-126">Vzhledem k tomu, že blok toku dat `toggleCheckBox` pracuje na uživatelském rozhraní, je důležité, aby tato akce probíhala ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6bbef-126">Because the `toggleCheckBox` dataflow block acts on the user interface, it is important that this action occur on the user-interface thread.</span></span> <span data-ttu-id="6bbef-127">Chcete-li to provést, během vytváření tohoto objektu poskytuje objekt <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>, který má vlastnost <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> nastavena na hodnotu <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6bbef-127">To accomplish this, during construction this object provides a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6bbef-128">Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> vytvoří objekt <xref:System.Threading.Tasks.TaskScheduler>, který provádí práci na aktuálním kontextu synchronizace.</span><span class="sxs-lookup"><span data-stu-id="6bbef-128">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="6bbef-129">Vzhledem k tomu, že konstruktor `Form1` je volán z vlákna uživatelského rozhraní, je akce pro `toggleCheckBox` bloku toku dat spuštěna také ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6bbef-129">Because the `Form1` constructor is called from the user-interface thread, the action for the `toggleCheckBox` dataflow block also runs on the user-interface thread.</span></span>  
  
 <span data-ttu-id="6bbef-130">Tento příklad také používá třídu <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> k tomu, aby mohly některé bloky toku dat fungovat souběžně, a jiný blok toku dat, který bude fungovat výhradně s ohledem na všechny ostatní bloky toku dat spuštěné ve stejném objektu <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>.</span><span class="sxs-lookup"><span data-stu-id="6bbef-130">This example also uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> class to enable some dataflow blocks to act concurrently, and another dataflow block to act exclusive with respect to all other dataflow blocks that run on the same <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object.</span></span> <span data-ttu-id="6bbef-131">Tato technika je užitečná, když více bloků toku dat sdílí prostředek a vyžaduje výhradní přístup k tomuto prostředku, protože eliminuje požadavek na ruční synchronizaci přístupu k tomuto prostředku.</span><span class="sxs-lookup"><span data-stu-id="6bbef-131">This technique is useful when multiple dataflow blocks share a resource and some require exclusive access to that resource, because it eliminates the requirement to manually synchronize access to that resource.</span></span> <span data-ttu-id="6bbef-132">Odstranění ruční synchronizace může zvýšit efektivitu kódu.</span><span class="sxs-lookup"><span data-stu-id="6bbef-132">The elimination of manual synchronization can make code more efficient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bbef-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="6bbef-133">Example</span></span>  
 <span data-ttu-id="6bbef-134">Následující příklad ukazuje úplný kód pro Form1.cs (Form1. vb pro Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6bbef-134">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="6bbef-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6bbef-135">See also</span></span>

- [<span data-ttu-id="6bbef-136">Tok dat</span><span class="sxs-lookup"><span data-stu-id="6bbef-136">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
