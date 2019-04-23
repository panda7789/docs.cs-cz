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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 681c0f1f918c8991ed2544189488d1ea25547834
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345843"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Postupy: Určení plánovače úloh v bloku toku dat
Tento dokument ukazuje, jak přiřadit určitým plánovačem úloh, při použití toku dat ve vaší aplikaci. V příkladu se používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> třídy v aplikaci Windows Forms k zobrazení, čtečky úkoly, které mají aktivní a pokud je aktivní úlohy zapisovače. Využívá také <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> způsob povolení bloku toku dat pro spuštění ve vlákně uživatelského rozhraní.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Chcete-li vytvořit Windows Forms aplikace  
  
1. Vytvoření aplikace Visual C# nebo Visual Basic **formulářová aplikace Windows** projektu. V následujících krocích se projekt s názvem `WriterReadersWinForms`.  
  
2. V návrháři formuláře pro hlavní formulář Form1.cs (Form1.vb pro jazyk Visual Basic), přidejte čtyři <xref:System.Windows.Forms.CheckBox> ovládacích prvků. Nastavte <xref:System.Windows.Forms.Control.Text%2A> vlastnost **čtečky 1** pro `checkBox1`, **čtečky 2** pro `checkBox2`, **čtečky 3** pro `checkBox3`, a  **Zapisovač** pro `checkBox4`. Nastavte <xref:System.Windows.Forms.Control.Enabled%2A> vlastnost pro každý ovládací prvek na `False`.  
  
3. Přidat <xref:System.Windows.Forms.Timer> ovládacího prvku na formuláři. Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost `2500`.  
  
## <a name="adding-dataflow-functionality"></a>Přidání funkce toku dat  
 Tato část popisuje postup vytvoření bloků toku dat, které se účastní v aplikaci a jak přidružit každý z nich pomocí plánovače úloh.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Přidání funkčnosti toku dat do aplikace  
  
1. Ve vašem projektu přidejte odkaz na System.Threading.Tasks.Dataflow.dll.  
  
2. Ujistěte se, že Form1.cs (Form1.vb pro jazyk Visual Basic) obsahuje následující `using` příkazy (`Imports` v jazyce Visual Basic).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. Přidat <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> datový člen do `Form1` třídy.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. V `Form1` konstruktor po volání `InitializeComponent`, vytvoření <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu, která přepíná stav <xref:System.Windows.Forms.CheckBox> objekty.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. V `Form1` konstruktoru, vytvořit <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objektu a čtyři <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekty, jeden <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt pro každou <xref:System.Windows.Forms.CheckBox> objektu. Pro každou <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu, zadejte <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavena na hodnotu <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> vlastnost pro čtení a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> vlastnost pro modul pro zápis.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. V `Form1` konstruktoru, start <xref:System.Windows.Forms.Timer> objektu.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. V návrháři formuláře pro hlavní formulář, vytvořit obslužnou rutinu události pro <xref:System.Windows.Forms.Timer.Tick> událost časovače.  
  
8. Implementace <xref:System.Windows.Forms.Timer.Tick> událost časovače.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Vzhledem k tomu, `toggleCheckBox` funguje bloku toku dat v uživatelském rozhraní, je důležité, tato akce vyskytovat ve vlákně uživatelského rozhraní. K tomu, během konstrukce, které obsahuje tento objekt <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> nastavenou na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> Metoda vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provede práci na aktuálním kontextu synchronizace. Vzhledem k tomu, `Form1` konstruktoru se volá z vlákna uživatelského rozhraní, akce pro `toggleCheckBox` bloku toku dat také běží na vlákně uživatelského rozhraní.  
  
 Tento příklad také používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> třídy umožňující některé bloků toku dat tak, aby fungoval současně a jiného bloku toku dat tak, aby fungoval s ohledem na všechny ostatní bloků toku dat, které běží na stejné exkluzivní <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objektu. Tato technika je užitečná, když více bloků toku dat sdílet prostředek a některé vyžadují výhradní přístup k prostředku, protože eliminuje nutnost ručně synchronizovat přístup k prostředku. Eliminace ruční synchronizace může být efektivnější kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje kompletní kód pro Form1.cs (Form1.vb pro jazyk Visual Basic).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
