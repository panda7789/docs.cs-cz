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
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Postupy: Určení plánovače úloh v bloku toku dat
Tento dokument ukazuje, jak přidružit konkrétní Plánovač úloh při použití toku dat ve vaší aplikaci. V příkladu se používá třída <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> v model Windows Forms aplikaci k zobrazení, když jsou úlohy čtecího zařízení aktivní a když je aktivní úkol zapisovače. Používá také metodu <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> k umožnění spuštění bloku toku dat ve vlákně uživatelského rozhraní.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Vytvoření aplikace model Windows Forms  
  
1. Vytvořte projekt aplikace C# Visual nebo Visual Basic **model Windows Forms** . V následujících krocích se projekt jmenuje `WriterReadersWinForms`.  
  
2. V návrháři formuláře pro hlavní formulář Form1.cs (Form1. vb pro Visual Basic) přidejte čtyři ovládací prvky <xref:System.Windows.Forms.CheckBox>. Vlastnost <xref:System.Windows.Forms.Control.Text%2A> nastavte na **Reader 1** pro `checkBox1`, **reader 2** pro `checkBox2`, **Reader 3** pro `checkBox3`a **zapisovač** pro `checkBox4`. Nastavte vlastnost <xref:System.Windows.Forms.Control.Enabled%2A> pro každý ovládací prvek na `False`.  
  
3. Přidejte ovládací prvek <xref:System.Windows.Forms.Timer> do formuláře. Vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> nastavte na hodnotu `2500`.  
  
## <a name="adding-dataflow-functionality"></a>Přidání funkce toku dat  
 V této části se dozvíte, jak vytvořit bloky toku dat, které se účastní aplikace, a jak je přidružit k Plánovači úloh.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Přidání funkce toku dat do aplikace  
  
1. V projektu přidejte odkaz na System. Threading. Tasks. Dataflow. dll.  
  
2. Ujistěte se, že Form1.cs (Form1. vb pro Visual Basic) obsahuje následující příkazy `using` (`Imports` v Visual Basic).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. Přidejte datový člen <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> do třídy `Form1`.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. V konstruktoru `Form1` po volání `InitializeComponent`vytvořte objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, který přepíná stav objektů <xref:System.Windows.Forms.CheckBox>.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. V konstruktoru `Form1` vytvořte objekt <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> a čtyři objekty <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, jeden <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt pro každý objekt <xref:System.Windows.Forms.CheckBox>. Pro každý objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> určete <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má vlastnost <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> nastavenou na vlastnost <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> pro čtecí zařízení a vlastnost <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> pro modul pro zápis.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. V konstruktoru `Form1` spusťte objekt <xref:System.Windows.Forms.Timer>.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.Timer.Tick> pro časovač.  
  
8. Implementujte událost <xref:System.Windows.Forms.Timer.Tick> pro časovač.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Vzhledem k tomu, že blok toku dat `toggleCheckBox` pracuje na uživatelském rozhraní, je důležité, aby tato akce probíhala ve vlákně uživatelského rozhraní. Chcete-li to provést, během vytváření tohoto objektu poskytuje objekt <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>, který má vlastnost <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> nastavena na hodnotu <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> vytvoří objekt <xref:System.Threading.Tasks.TaskScheduler>, který provádí práci na aktuálním kontextu synchronizace. Vzhledem k tomu, že konstruktor `Form1` je volán z vlákna uživatelského rozhraní, je akce pro `toggleCheckBox` bloku toku dat spuštěna také ve vlákně uživatelského rozhraní.  
  
 Tento příklad také používá třídu <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> k tomu, aby mohly některé bloky toku dat fungovat souběžně, a jiný blok toku dat, který bude fungovat výhradně s ohledem na všechny ostatní bloky toku dat spuštěné ve stejném objektu <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>. Tato technika je užitečná, když více bloků toku dat sdílí prostředek a vyžaduje výhradní přístup k tomuto prostředku, protože eliminuje požadavek na ruční synchronizaci přístupu k tomuto prostředku. Odstranění ruční synchronizace může zvýšit efektivitu kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje úplný kód pro Form1.cs (Form1. vb pro Visual Basic).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
