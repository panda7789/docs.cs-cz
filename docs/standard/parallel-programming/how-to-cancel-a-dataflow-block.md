---
title: 'Postupy: Zrušení bloku toku dat'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eece4992deecbf30299d6e9e96fa8c2faf16d3ab
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-cancel-a-dataflow-block"></a>Postupy: Zrušení bloku toku dat
Tento dokument ukazuje, jak povolit zrušení ve vaší aplikaci. Tento příklad používá Windows Forms k zobrazení, kde jsou aktivní v kanálu toku dat a také důsledky zrušení pracovních položek.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>K vytvoření Windows Forms aplikace  
  
1.  Vytvoření C# nebo Visual Basic **formulářové aplikace Windows** projektu. V následujících krocích projektu jmenuje `CancellationWinForms`.  
  
2.  V návrháři formuláře pro hlavní formulář Form1.cs (Form1.vb jazyka Visual Basic), přidejte <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.  
  
3.  Přidat <xref:System.Windows.Forms.ToolStripButton> řídit k <xref:System.Windows.Forms.ToolStrip> ovládacího prvku. Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **přidat pracovní položky**.  
  
4.  Přidejte druhý <xref:System.Windows.Forms.ToolStripButton> řídit k <xref:System.Windows.Forms.ToolStrip> ovládacího prvku. Nastavit <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **zrušit**a <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> vlastnost `False`.  
  
5.  Přidat čtyři <xref:System.Windows.Forms.ToolStripProgressBar> objekty ke <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.  
  
## <a name="creating-the-dataflow-pipeline"></a>Vytvoření kanálu toku dat  
 Tato část popisuje postup vytvoření kanálu toku dat, který zpracovává pracovních položek a aktualizuje indikátory průběhu.  
  
### <a name="to-create-the-dataflow-pipeline"></a>K vytvoření kanálu toku dat  
  
1.  Ve vašem projektu přidejte odkaz na System.Threading.Tasks.Dataflow.dll.  
  
2.  Ujistěte se, že Form1.cs (Form1.vb jazyka Visual Basic) obsahuje následující `using` příkazy (`Imports` v jazyce Visual Basic).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  Přidat `WorkItem` třídu jako typ vnitřní `Form1` třídy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  Přidejte následující členy dat tak, aby `Form1` třídy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  Přidejte následující metodu `CreatePipeline`, na `Form1` třídy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Protože `incrementProgress` a `decrementProgress` toku dat bloky fungují v uživatelském rozhraní, je důležité, aby tyto akce se provedou ve vláknu uživatelského rozhraní. K tomu během vytváření tyto objekty každý poskytují <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavena na hodnotu <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provede práci v aktuálním kontextu synchronizace. Protože `Form1` konstruktor je volat z vlákna uživatelského rozhraní, akce `incrementProgress` a `decrementProgress` bloků toku dat taky spustit ve vláknu uživatelského rozhraní.  
  
 Tento příklad nastaví <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost, když se vytvoří členy kanálu. Protože <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost trvale zruší spuštění bloku toku dat, celého kanálu musí být znovu vytvořen po uživatel operaci zruší a pak se chce přidat další pracovní položky do kanálu. Příklad, alternativní způsob zrušení bloku toku dat tak, aby jinou práci lze provést po operace je zrušená, naleznete v části [návod: použití toku dat ve formulářové aplikaci Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Připojování k uživatelské rozhraní kanálu toku dat  
 Tato část popisuje postup připojení kanálu toku dat s uživatelským rozhraním. Vytvoření kanálu i přidávání pracovních položek do kanálu jsou řízeny obslužné rutiny události pro **přidat pracovní položky** tlačítko. Zrušení se spouští pomocí **zrušit** tlačítko. Po kliknutí na tato tlačítka, je v asynchronním režimu inicioval příslušnou akci.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Pro připojení kanálu toku dat s uživatelským rozhraním  
  
1.  V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> události **přidat pracovní položky** tlačítko.  
  
2.  Implementace <xref:System.Windows.Forms.ToolStripItem.Click> události **přidat pracovní položky** tlačítko.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutiny události pro **zrušit** tlačítko.  
  
4.  Implementace <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutiny události pro **zrušit** tlačítko.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje kód dokončení pro Form1.cs (Form1.vb jazyka Visual Basic).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Následující obrázek znázorňuje běžící aplikaci.  
  
 ![Windows Forms aplikace](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Viz také  
 [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
