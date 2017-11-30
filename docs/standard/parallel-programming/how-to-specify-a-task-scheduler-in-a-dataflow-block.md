---
title: "Postupy: Určení plánovače úloh v bloku toku dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 20faebc8bda3b50c4f762615d84b7a449ae61c6f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Postupy: Určení plánovače úloh v bloku toku dat
Tento dokument ukazuje, jak přidružit plánovače úloh konkrétní při použití toku dat ve vaší aplikaci. V příkladu se používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> třídy v aplikaci Windows Forms k zobrazení čtečky úkoly, které mají aktivní a když je aktivní úlohu zapisovače. Používá také <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> způsob povolení bloku toku dat spustit ve vláknu uživatelského rozhraní.  
  
> [!TIP]
>  Knihovna toku dat TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> oboru názvů) není distribuované s [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. K instalaci <xref:System.Threading.Tasks.Dataflow> obor názvů, otevřete projekt v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], zvolte **spravovat balíčky NuGet** z nabídky projektu a vyhledejte online `Microsoft.Tpl.Dataflow` balíčku.  
  
### <a name="to-create-the-windows-forms-application"></a>K vytvoření Windows Forms aplikace  
  
1.  Vytvoření [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] nebo Visual Basic **formulářové aplikace Windows** projektu. V následujících krocích projektu jmenuje `WriterReadersWinForms`.  
  
2.  V návrháři formuláře pro hlavní formulář, Form1.cs (Form1.vb pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), přidejte čtyři <xref:System.Windows.Forms.CheckBox> ovládací prvky. Nastavte <xref:System.Windows.Forms.Control.Text%2A> vlastnost **čtečky 1** pro `checkBox1`, **čtečky 2** pro `checkBox2`, **čtečky 3** pro `checkBox3`, a  **Zapisovač** pro `checkBox4`. Nastavte <xref:System.Windows.Forms.Control.Enabled%2A> vlastnost pro každý ovládací prvek pro `False`.  
  
3.  Přidat <xref:System.Windows.Forms.Timer> ovládacího prvku do formuláře. Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost `2500`.  
  
## <a name="adding-dataflow-functionality"></a>Přidání funkce toku dat  
 Tato část popisuje, jak vytvořit bloků toku dat, které se účastní v aplikaci a postup přidružení každé z nich pomocí plánovače úloh.  
  
#### <a name="to-add-dataflow-functionality-to-the-application"></a>Chcete-li přidat funkce toku dat do aplikace  
  
1.  Ve vašem projektu přidejte odkaz na System.Threading.Tasks.Dataflow.dll.  
  
2.  Ujistěte se, že Form1.cs (Form1.vb pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) obsahuje následující `using` příkazy (`Imports` v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3.  Přidat <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> – datový člen k `Form1` třídy.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4.  V `Form1` konstruktor po zavolání `InitializeComponent`, vytvořit <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, který přepne stav <xref:System.Windows.Forms.CheckBox> objekty.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5.  V `Form1` konstruktoru, vytvoření <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objekt a čtyřmi <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekty, jeden <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt pro každou <xref:System.Windows.Forms.CheckBox> objektu. Pro každou <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu, zadejte <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavena na hodnotu <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> vlastnost pro čtečky a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> vlastnost pro zapisovač.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6.  V `Form1` konstruktoru, spuštění <xref:System.Windows.Forms.Timer> objektu.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7.  V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.Timer.Tick> událost pro časovač.  
  
8.  Implementace <xref:System.Windows.Forms.Timer.Tick> událost pro časovač.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Protože `toggleCheckBox` jednání bloku toku dat v uživatelském rozhraní, je důležité, aby tuto akci dojde k ve vláknu uživatelského rozhraní. K tomu, během vytváření poskytuje tento objekt <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavena na hodnotu <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> Metoda vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provede práci v aktuálním kontextu synchronizace. Protože `Form1` konstruktor je volat z vlákna uživatelského rozhraní, akce pro `toggleCheckBox` bloku toku dat je spuštěna také na vlákna uživatelského rozhraní.  
  
 Tento příklad také používá <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> třída povolit některé bloků toku dat tak, aby fungoval souběžně a jiný blok toku dat tak, aby fungoval s ohledem na všechny ostatní bloků toku dat, které běží na stejné výhradní <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> objektu. Tato metoda je užitečná, když sdílet prostředky v několika bloků toku dat a některé vyžaduje výhradní přístup k prostředku, protože eliminuje požadavek na přístup k prostředku synchronizovat ručně. Odstranění ruční synchronizace můžete nastavit kód efektivnější.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje kód dokončení pro Form1.cs (Form1.vb pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Viz také  
 [Toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
