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
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Postupy: Určení plánovače úloh v bloku toku dat
Tento dokument ukazuje, jak přidružit konkrétní Plánovač úloh při použití toku dat ve vaší aplikaci. V příkladu se používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> Třída v aplikaci model Windows Forms k zobrazení, když jsou úlohy čtecího zařízení aktivní a když je aktivní úkol zapisovače. Také používá <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> metodu pro povolení bloku toku dat pro spuštění v vlákně uživatelského rozhraní.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Vytvoření aplikace model Windows Forms  
  
1. Vytvořte projekt aplikace Visual C# nebo Visual Basic **model Windows Forms** . V následujících krocích se projekt jmenuje `WriterReadersWinForms` .  
  
2. V návrháři formuláře pro hlavní formulář Form1.cs (Form1. vb pro Visual Basic) přidejte čtyři <xref:System.Windows.Forms.CheckBox> ovládací prvky. Nastavte <xref:System.Windows.Forms.Control.Text%2A> vlastnost na **Reader 1** pro `checkBox1` , **Reader 2** pro `checkBox2` , **Reader 3** pro `checkBox3` a **zapisovač** pro `checkBox4` . Nastavte <xref:System.Windows.Forms.Control.Enabled%2A> vlastnost pro každý ovládací prvek na `False` .  
  
3. Přidejte <xref:System.Windows.Forms.Timer> ovládací prvek do formuláře. Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost na hodnotu `2500` .  
  
## <a name="adding-dataflow-functionality"></a>Přidání funkce toku dat  
 V této části se dozvíte, jak vytvořit bloky toku dat, které se účastní aplikace, a jak je přidružit k Plánovači úloh.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Přidání funkce toku dat do aplikace  
  
1. V projektu přidejte odkaz na System. Threading. Tasks. Dataflow. dll.  
  
2. Ujistěte se, že Form1.cs (Form1. vb pro Visual Basic) obsahuje následující `using` příkazy ( `Imports` v Visual Basic).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. Přidejte <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> datový člen do `Form1` třídy.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. V `Form1` konstruktoru po volání metody `InitializeComponent` vytvořte <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který přepíná stav <xref:System.Windows.Forms.CheckBox> objektů.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. V `Form1` konstruktoru vytvořte <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objekt a čtyři <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekty, jeden <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt pro každý <xref:System.Windows.Forms.CheckBox> objekt. Pro každý <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt určete <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavenou na <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> vlastnost pro čtenáře, a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> vlastnost pro zapisovač.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. V `Form1` konstruktoru spusťte <xref:System.Windows.Forms.Timer> objekt.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.Timer.Tick> událost časovače.  
  
8. Implementujte <xref:System.Windows.Forms.Timer.Tick> událost pro časovač.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Vzhledem k `toggleCheckBox` tomu, že blok toku dat funguje na uživatelském rozhraní, je důležité, aby tato akce probíhala ve vlákně uživatelského rozhraní. Chcete-li to provést, během vytváření tohoto objektu poskytuje <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavenou na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> . <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A>Metoda vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provádí práci na aktuálním kontextu synchronizace. Vzhledem k tomu `Form1` , že je konstruktor volán z vlákna uživatelského rozhraní, je akce pro `toggleCheckBox` blok toku dat spuštěna také ve vlákně uživatelského rozhraní.  
  
 Tento příklad také používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> třídu k tomu, aby mohly některé bloky toku dat fungovat souběžně, a další blok toku dat, který bude fungovat výhradně s ohledem na všechny ostatní bloky toku dat, které jsou spuštěny na stejném <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objektu. Tato technika je užitečná, když více bloků toku dat sdílí prostředek a vyžaduje výhradní přístup k tomuto prostředku, protože eliminuje požadavek na ruční synchronizaci přístupu k tomuto prostředku. Odstranění ruční synchronizace může zvýšit efektivitu kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje úplný kód pro Form1.cs (Form1. vb pro Visual Basic).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Viz také

- [Tok dat](dataflow-task-parallel-library.md)
