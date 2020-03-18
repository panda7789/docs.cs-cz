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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73122222"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a><span data-ttu-id="e9a81-102">Postupy: Určení plánovače úloh v bloku toku dat</span><span class="sxs-lookup"><span data-stu-id="e9a81-102">How to: Specify a Task Scheduler in a Dataflow Block</span></span>
<span data-ttu-id="e9a81-103">Tento dokument ukazuje, jak přidružit konkrétní plánovač úloh při použití toku dat v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e9a81-103">This document demonstrates how to associate a specific task scheduler when you use dataflow in your application.</span></span> <span data-ttu-id="e9a81-104">Příklad používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> třídu v aplikaci Windows Forms k zobrazení, kdy jsou úlohy čtečky aktivní a když je aktivní úloha zapisovače.</span><span class="sxs-lookup"><span data-stu-id="e9a81-104">The example uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> class in a Windows Forms application to show when reader tasks are active and when a writer task is active.</span></span> <span data-ttu-id="e9a81-105">Používá také <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> metodu povolit bloku toku dat ke spuštění ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e9a81-105">It also uses the <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method to enable a dataflow block to run on the user-interface thread.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="e9a81-106">Vytvoření aplikace windows forms</span><span class="sxs-lookup"><span data-stu-id="e9a81-106">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="e9a81-107">Vytvořte projekt aplikace Visual C# nebo Visual Basic **Windows Forms Application.**</span><span class="sxs-lookup"><span data-stu-id="e9a81-107">Create a Visual C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="e9a81-108">V následujících krocích je `WriterReadersWinForms`projekt pojmenován .</span><span class="sxs-lookup"><span data-stu-id="e9a81-108">In the following steps, the project is named `WriterReadersWinForms`.</span></span>  
  
2. <span data-ttu-id="e9a81-109">V návrháři formuláře pro hlavní formulář, Form1.cs (Form1.vb <xref:System.Windows.Forms.CheckBox> pro visual basic), přidejte čtyři ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="e9a81-109">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add four <xref:System.Windows.Forms.CheckBox> controls.</span></span> <span data-ttu-id="e9a81-110">Nastavte <xref:System.Windows.Forms.Control.Text%2A> vlastnost na Reader `checkBox1` **1** for `checkBox2`, Reader **2** for `checkBox4`, Reader **3** for `checkBox3`a **Writer** for .</span><span class="sxs-lookup"><span data-stu-id="e9a81-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to **Reader 1** for `checkBox1`, **Reader 2** for `checkBox2`, **Reader 3** for `checkBox3`, and **Writer** for `checkBox4`.</span></span> <span data-ttu-id="e9a81-111">Nastavte <xref:System.Windows.Forms.Control.Enabled%2A> vlastnost pro každý `False`ovládací prvek na .</span><span class="sxs-lookup"><span data-stu-id="e9a81-111">Set the <xref:System.Windows.Forms.Control.Enabled%2A> property for each control to `False`.</span></span>  
  
3. <span data-ttu-id="e9a81-112">Přidejte <xref:System.Windows.Forms.Timer> ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="e9a81-112">Add a <xref:System.Windows.Forms.Timer> control to the form.</span></span> <span data-ttu-id="e9a81-113">Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost `2500`na .</span><span class="sxs-lookup"><span data-stu-id="e9a81-113">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `2500`.</span></span>  
  
## <a name="adding-dataflow-functionality"></a><span data-ttu-id="e9a81-114">Přidání funkcí toku dat</span><span class="sxs-lookup"><span data-stu-id="e9a81-114">Adding Dataflow Functionality</span></span>  
 <span data-ttu-id="e9a81-115">Tato část popisuje, jak vytvořit bloky toku dat, které se účastní aplikace a jak přidružit každý z nich s plánovačem úloh.</span><span class="sxs-lookup"><span data-stu-id="e9a81-115">This section describes how to create the dataflow blocks that participate in the application and how to associate each one with a task scheduler.</span></span>  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a><span data-ttu-id="e9a81-116">Přidání funkcí toku dat do aplikace</span><span class="sxs-lookup"><span data-stu-id="e9a81-116">To Add Dataflow Functionality to the Application</span></span>  
  
1. <span data-ttu-id="e9a81-117">V projektu přidejte odkaz na System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="e9a81-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="e9a81-118">Ujistěte se, že Form1.cs (Form1.vb `using` pro`Imports` visual basic) obsahuje následující příkazy ( v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="e9a81-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. <span data-ttu-id="e9a81-119">Přidejte <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> datový člen `Form1` do třídy.</span><span class="sxs-lookup"><span data-stu-id="e9a81-119">Add a <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> data member to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. <span data-ttu-id="e9a81-120">V `Form1` konstruktoru po volání `InitializeComponent`vytvořte <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který přepíná stav <xref:System.Windows.Forms.CheckBox> objektů.</span><span class="sxs-lookup"><span data-stu-id="e9a81-120">In the `Form1` constructor, after the call to `InitializeComponent`, create an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that toggles the state of <xref:System.Windows.Forms.CheckBox> objects.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. <span data-ttu-id="e9a81-121">V `Form1` <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> konstruktoru vytvořte objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> a <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> čtyři objekty, jeden objekt pro každý <xref:System.Windows.Forms.CheckBox> objekt.</span><span class="sxs-lookup"><span data-stu-id="e9a81-121">In the `Form1` constructor, create a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object and four <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objects, one <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object for each <xref:System.Windows.Forms.CheckBox> object.</span></span> <span data-ttu-id="e9a81-122">Pro <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> každý objekt <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> zadejte objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavenou <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> na vlastnost pro čtenáře a vlastnost pro zapisovače.</span><span class="sxs-lookup"><span data-stu-id="e9a81-122">For each <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object, specify a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> property for the readers, and the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> property for the writer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. <span data-ttu-id="e9a81-123">V `Form1` konstruktoru spusťte <xref:System.Windows.Forms.Timer> objekt.</span><span class="sxs-lookup"><span data-stu-id="e9a81-123">In the `Form1` constructor, start the <xref:System.Windows.Forms.Timer> object.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. <span data-ttu-id="e9a81-124">V návrháři formuláře pro hlavní formulář vytvořte <xref:System.Windows.Forms.Timer.Tick> obslužnou rutinu události pro událost pro časovač.</span><span class="sxs-lookup"><span data-stu-id="e9a81-124">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
8. <span data-ttu-id="e9a81-125">Implementujte <xref:System.Windows.Forms.Timer.Tick> událost pro časovač.</span><span class="sxs-lookup"><span data-stu-id="e9a81-125">Implement the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 <span data-ttu-id="e9a81-126">Vzhledem `toggleCheckBox` k tomu, že blok toku dat funguje v uživatelském rozhraní, je důležité, aby tato akce došlo ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e9a81-126">Because the `toggleCheckBox` dataflow block acts on the user interface, it is important that this action occur on the user-interface thread.</span></span> <span data-ttu-id="e9a81-127">Chcete-li to provést, během <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> konstrukce tento <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> objekt <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>poskytuje objekt, který má vlastnost nastavena na .</span><span class="sxs-lookup"><span data-stu-id="e9a81-127">To accomplish this, during construction this object provides a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e9a81-128">Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provádí práci na aktuálním kontextu synchronizace.</span><span class="sxs-lookup"><span data-stu-id="e9a81-128">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="e9a81-129">Vzhledem `Form1` k tomu, že konstruktor je volána `toggleCheckBox` z vlákna uživatelského rozhraní, akce pro blok toku dat také běží na vlákno uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e9a81-129">Because the `Form1` constructor is called from the user-interface thread, the action for the `toggleCheckBox` dataflow block also runs on the user-interface thread.</span></span>  
  
 <span data-ttu-id="e9a81-130">Tento příklad také <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> používá třídu povolit některé bloky toku dat jednat souběžně a jiný blok toku dat <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> jednat výhradně s ohledem na všechny ostatní bloky toku dat, které běží na stejném objektu.</span><span class="sxs-lookup"><span data-stu-id="e9a81-130">This example also uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> class to enable some dataflow blocks to act concurrently, and another dataflow block to act exclusive with respect to all other dataflow blocks that run on the same <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object.</span></span> <span data-ttu-id="e9a81-131">Tato technika je užitečná, když více bloků toku dat sdílet prostředek a některé vyžadují výhradní přístup k tomuto prostředku, protože eliminuje požadavek na ruční synchronizaci přístupu k tomuto prostředku.</span><span class="sxs-lookup"><span data-stu-id="e9a81-131">This technique is useful when multiple dataflow blocks share a resource and some require exclusive access to that resource, because it eliminates the requirement to manually synchronize access to that resource.</span></span> <span data-ttu-id="e9a81-132">Eliminace ruční synchronizace může zefektivnit kód.</span><span class="sxs-lookup"><span data-stu-id="e9a81-132">The elimination of manual synchronization can make code more efficient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9a81-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9a81-133">Example</span></span>  
 <span data-ttu-id="e9a81-134">Následující příklad ukazuje úplný kód pro Form1.cs (Form1.vb pro visual basic).</span><span class="sxs-lookup"><span data-stu-id="e9a81-134">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="e9a81-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9a81-135">See also</span></span>

- [<span data-ttu-id="e9a81-136">Tok dat</span><span class="sxs-lookup"><span data-stu-id="e9a81-136">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
