---
title: 'Postupy: Určení plánovače úloh v bloku toku dat'
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
ms.openlocfilehash: 76c9e75f787c28657af143b46bb22d08039e2dc4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288131"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a><span data-ttu-id="28bd6-102">Postupy: Určení plánovače úloh v bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="28bd6-102">How to: Specify a Task Scheduler in a Dataflow Block</span></span>
<span data-ttu-id="28bd6-103">Tento dokument ukazuje, jak přidružit konkrétní Plánovač úloh při použití toku dat ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="28bd6-103">This document demonstrates how to associate a specific task scheduler when you use dataflow in your application.</span></span> <span data-ttu-id="28bd6-104">V příkladu se používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> Třída v aplikaci model Windows Forms k zobrazení, když jsou úlohy čtecího zařízení aktivní a když je aktivní úkol zapisovače.</span><span class="sxs-lookup"><span data-stu-id="28bd6-104">The example uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> class in a Windows Forms application to show when reader tasks are active and when a writer task is active.</span></span> <span data-ttu-id="28bd6-105">Také používá <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> metodu pro povolení bloku toku dat pro spuštění v vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="28bd6-105">It also uses the <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method to enable a dataflow block to run on the user-interface thread.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="28bd6-106">Vytvoření aplikace model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="28bd6-106">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="28bd6-107">Vytvořte projekt aplikace Visual C# nebo Visual Basic **model Windows Forms** .</span><span class="sxs-lookup"><span data-stu-id="28bd6-107">Create a Visual C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="28bd6-108">V následujících krocích se projekt jmenuje `WriterReadersWinForms` .</span><span class="sxs-lookup"><span data-stu-id="28bd6-108">In the following steps, the project is named `WriterReadersWinForms`.</span></span>  
  
2. <span data-ttu-id="28bd6-109">V návrháři formuláře pro hlavní formulář Form1.cs (Form1. vb pro Visual Basic) přidejte čtyři <xref:System.Windows.Forms.CheckBox> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="28bd6-109">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add four <xref:System.Windows.Forms.CheckBox> controls.</span></span> <span data-ttu-id="28bd6-110">Nastavte <xref:System.Windows.Forms.Control.Text%2A> vlastnost na **Reader 1** pro `checkBox1` , **Reader 2** pro `checkBox2` , **Reader 3** pro `checkBox3` a **zapisovač** pro `checkBox4` .</span><span class="sxs-lookup"><span data-stu-id="28bd6-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to **Reader 1** for `checkBox1`, **Reader 2** for `checkBox2`, **Reader 3** for `checkBox3`, and **Writer** for `checkBox4`.</span></span> <span data-ttu-id="28bd6-111">Nastavte <xref:System.Windows.Forms.Control.Enabled%2A> vlastnost pro každý ovládací prvek na `False` .</span><span class="sxs-lookup"><span data-stu-id="28bd6-111">Set the <xref:System.Windows.Forms.Control.Enabled%2A> property for each control to `False`.</span></span>  
  
3. <span data-ttu-id="28bd6-112">Přidejte <xref:System.Windows.Forms.Timer> ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="28bd6-112">Add a <xref:System.Windows.Forms.Timer> control to the form.</span></span> <span data-ttu-id="28bd6-113">Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost na hodnotu `2500` .</span><span class="sxs-lookup"><span data-stu-id="28bd6-113">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `2500`.</span></span>  
  
## <a name="adding-dataflow-functionality"></a><span data-ttu-id="28bd6-114">Přidání funkce toku dat</span><span class="sxs-lookup"><span data-stu-id="28bd6-114">Adding Dataflow Functionality</span></span>  
 <span data-ttu-id="28bd6-115">V této části se dozvíte, jak vytvořit bloky toku dat, které se účastní aplikace, a jak je přidružit k Plánovači úloh.</span><span class="sxs-lookup"><span data-stu-id="28bd6-115">This section describes how to create the dataflow blocks that participate in the application and how to associate each one with a task scheduler.</span></span>  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a><span data-ttu-id="28bd6-116">Přidání funkce toku dat do aplikace</span><span class="sxs-lookup"><span data-stu-id="28bd6-116">To Add Dataflow Functionality to the Application</span></span>  
  
1. <span data-ttu-id="28bd6-117">V projektu přidejte odkaz na System. Threading. Tasks. Dataflow. dll.</span><span class="sxs-lookup"><span data-stu-id="28bd6-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="28bd6-118">Ujistěte se, že Form1.cs (Form1. vb pro Visual Basic) obsahuje následující `using` příkazy ( `Imports` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="28bd6-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. <span data-ttu-id="28bd6-119">Přidejte <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> datový člen do `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="28bd6-119">Add a <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> data member to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. <span data-ttu-id="28bd6-120">V `Form1` konstruktoru po volání metody `InitializeComponent` vytvořte <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který přepíná stav <xref:System.Windows.Forms.CheckBox> objektů.</span><span class="sxs-lookup"><span data-stu-id="28bd6-120">In the `Form1` constructor, after the call to `InitializeComponent`, create an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that toggles the state of <xref:System.Windows.Forms.CheckBox> objects.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. <span data-ttu-id="28bd6-121">V `Form1` konstruktoru vytvořte <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objekt a čtyři <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekty, jeden <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt pro každý <xref:System.Windows.Forms.CheckBox> objekt.</span><span class="sxs-lookup"><span data-stu-id="28bd6-121">In the `Form1` constructor, create a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object and four <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objects, one <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object for each <xref:System.Windows.Forms.CheckBox> object.</span></span> <span data-ttu-id="28bd6-122">Pro každý <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt určete <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavenou na <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> vlastnost pro čtenáře, a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> vlastnost pro zapisovač.</span><span class="sxs-lookup"><span data-stu-id="28bd6-122">For each <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object, specify a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> property for the readers, and the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> property for the writer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. <span data-ttu-id="28bd6-123">V `Form1` konstruktoru spusťte <xref:System.Windows.Forms.Timer> objekt.</span><span class="sxs-lookup"><span data-stu-id="28bd6-123">In the `Form1` constructor, start the <xref:System.Windows.Forms.Timer> object.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. <span data-ttu-id="28bd6-124">V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.Timer.Tick> událost časovače.</span><span class="sxs-lookup"><span data-stu-id="28bd6-124">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
8. <span data-ttu-id="28bd6-125">Implementujte <xref:System.Windows.Forms.Timer.Tick> událost pro časovač.</span><span class="sxs-lookup"><span data-stu-id="28bd6-125">Implement the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 <span data-ttu-id="28bd6-126">Vzhledem k `toggleCheckBox` tomu, že blok toku dat funguje na uživatelském rozhraní, je důležité, aby tato akce probíhala ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="28bd6-126">Because the `toggleCheckBox` dataflow block acts on the user interface, it is important that this action occur on the user-interface thread.</span></span> <span data-ttu-id="28bd6-127">Chcete-li to provést, během vytváření tohoto objektu poskytuje <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavenou na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="28bd6-127">To accomplish this, during construction this object provides a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="28bd6-128"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A>Metoda vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provádí práci na aktuálním kontextu synchronizace.</span><span class="sxs-lookup"><span data-stu-id="28bd6-128">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="28bd6-129">Vzhledem k tomu `Form1` , že je konstruktor volán z vlákna uživatelského rozhraní, je akce pro `toggleCheckBox` blok toku dat spuštěna také ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="28bd6-129">Because the `Form1` constructor is called from the user-interface thread, the action for the `toggleCheckBox` dataflow block also runs on the user-interface thread.</span></span>  
  
 <span data-ttu-id="28bd6-130">Tento příklad také používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> třídu k tomu, aby mohly některé bloky toku dat fungovat souběžně, a další blok toku dat, který bude fungovat výhradně s ohledem na všechny ostatní bloky toku dat, které jsou spuštěny na stejném <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objektu.</span><span class="sxs-lookup"><span data-stu-id="28bd6-130">This example also uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> class to enable some dataflow blocks to act concurrently, and another dataflow block to act exclusive with respect to all other dataflow blocks that run on the same <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object.</span></span> <span data-ttu-id="28bd6-131">Tato technika je užitečná, když více bloků toku dat sdílí prostředek a vyžaduje výhradní přístup k tomuto prostředku, protože eliminuje požadavek na ruční synchronizaci přístupu k tomuto prostředku.</span><span class="sxs-lookup"><span data-stu-id="28bd6-131">This technique is useful when multiple dataflow blocks share a resource and some require exclusive access to that resource, because it eliminates the requirement to manually synchronize access to that resource.</span></span> <span data-ttu-id="28bd6-132">Odstranění ruční synchronizace může zvýšit efektivitu kódu.</span><span class="sxs-lookup"><span data-stu-id="28bd6-132">The elimination of manual synchronization can make code more efficient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28bd6-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="28bd6-133">Example</span></span>  
 <span data-ttu-id="28bd6-134">Následující příklad ukazuje úplný kód pro Form1.cs (Form1. vb pro Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="28bd6-134">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="28bd6-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="28bd6-135">See also</span></span>

- [<span data-ttu-id="28bd6-136">Tok dat</span><span class="sxs-lookup"><span data-stu-id="28bd6-136">Dataflow</span></span>](dataflow-task-parallel-library.md)
