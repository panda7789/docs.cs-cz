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
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Postupy: Určení plánovače úloh v bloku toku dat
Tento dokument ukazuje, jak přidružit konkrétní plánovač úloh při použití toku dat v aplikaci. Příklad používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> třídu v aplikaci Windows Forms k zobrazení, kdy jsou úlohy čtečky aktivní a když je aktivní úloha zapisovače. Používá také <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> metodu povolit bloku toku dat ke spuštění ve vlákně uživatelského rozhraní.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Vytvoření aplikace windows forms  
  
1. Vytvořte projekt aplikace Visual C# nebo Visual Basic **Windows Forms Application.** V následujících krocích je `WriterReadersWinForms`projekt pojmenován .  
  
2. V návrháři formuláře pro hlavní formulář, Form1.cs (Form1.vb <xref:System.Windows.Forms.CheckBox> pro visual basic), přidejte čtyři ovládací prvky. Nastavte <xref:System.Windows.Forms.Control.Text%2A> vlastnost na Reader `checkBox1` **1** for `checkBox2`, Reader **2** for `checkBox4`, Reader **3** for `checkBox3`a **Writer** for . Nastavte <xref:System.Windows.Forms.Control.Enabled%2A> vlastnost pro každý `False`ovládací prvek na .  
  
3. Přidejte <xref:System.Windows.Forms.Timer> ovládací prvek do formuláře. Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost `2500`na .  
  
## <a name="adding-dataflow-functionality"></a>Přidání funkcí toku dat  
 Tato část popisuje, jak vytvořit bloky toku dat, které se účastní aplikace a jak přidružit každý z nich s plánovačem úloh.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Přidání funkcí toku dat do aplikace  
  
1. V projektu přidejte odkaz na System.Threading.Tasks.Dataflow.dll.  
  
2. Ujistěte se, že Form1.cs (Form1.vb `using` pro`Imports` visual basic) obsahuje následující příkazy ( v jazyce Visual Basic).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. Přidejte <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> datový člen `Form1` do třídy.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. V `Form1` konstruktoru po volání `InitializeComponent`vytvořte <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který přepíná stav <xref:System.Windows.Forms.CheckBox> objektů.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. V `Form1` <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> konstruktoru vytvořte objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> a <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> čtyři objekty, jeden objekt pro každý <xref:System.Windows.Forms.CheckBox> objekt. Pro <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> každý objekt <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> zadejte objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavenou <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> na vlastnost pro čtenáře a vlastnost pro zapisovače.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. V `Form1` konstruktoru spusťte <xref:System.Windows.Forms.Timer> objekt.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. V návrháři formuláře pro hlavní formulář vytvořte <xref:System.Windows.Forms.Timer.Tick> obslužnou rutinu události pro událost pro časovač.  
  
8. Implementujte <xref:System.Windows.Forms.Timer.Tick> událost pro časovač.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Vzhledem `toggleCheckBox` k tomu, že blok toku dat funguje v uživatelském rozhraní, je důležité, aby tato akce došlo ve vlákně uživatelského rozhraní. Chcete-li to provést, během <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> konstrukce tento <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> objekt <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>poskytuje objekt, který má vlastnost nastavena na . Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provádí práci na aktuálním kontextu synchronizace. Vzhledem `Form1` k tomu, že konstruktor je volána `toggleCheckBox` z vlákna uživatelského rozhraní, akce pro blok toku dat také běží na vlákno uživatelského rozhraní.  
  
 Tento příklad také <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> používá třídu povolit některé bloky toku dat jednat souběžně a jiný blok toku dat <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> jednat výhradně s ohledem na všechny ostatní bloky toku dat, které běží na stejném objektu. Tato technika je užitečná, když více bloků toku dat sdílet prostředek a některé vyžadují výhradní přístup k tomuto prostředku, protože eliminuje požadavek na ruční synchronizaci přístupu k tomuto prostředku. Eliminace ruční synchronizace může zefektivnit kód.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje úplný kód pro Form1.cs (Form1.vb pro visual basic).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Viz také

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
