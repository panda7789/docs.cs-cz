---
title: 'Postupy: Zrušení bloku toku dat'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: b95f0a3535716c4a01dae52abe38eb850f080cf0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59345193"
---
# <a name="how-to-cancel-a-dataflow-block"></a>Postupy: Zrušení bloku toku dat
Tento dokument ukazuje, jak povolit zrušení ve vaší aplikaci. Tento příklad používá Windows Forms k zobrazení, ve kterém jsou aktivní v kanálu toku dat a také vlivu zrušení pracovní položky.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Chcete-li vytvořit Windows Forms aplikace  
  
1. Vytvoření jazyka C# nebo Visual Basic **formulářová aplikace Windows** projektu. V následujících krocích se projekt s názvem `CancellationWinForms`.  
  
2. V návrháři formuláře pro hlavní formulář Form1.cs (Form1.vb pro jazyk Visual Basic), přidejte <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.  
  
3. Přidat <xref:System.Windows.Forms.ToolStripButton> ovládací prvek <xref:System.Windows.Forms.ToolStrip> ovládacího prvku. Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **přidat pracovní položky**.  
  
4. Přidejte druhý <xref:System.Windows.Forms.ToolStripButton> ovládací prvek <xref:System.Windows.Forms.ToolStrip> ovládacího prvku. Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **zrušit**a <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> vlastnost `False`.  
  
5. Přidejte čtyři <xref:System.Windows.Forms.ToolStripProgressBar> objektů <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.  
  
## <a name="creating-the-dataflow-pipeline"></a>Vytvoření kanálu toku dat  
 Tato část popisuje postup vytvoření kanálu toku dat, která zpracovává pracovních položek a aktualizuje indikátory průběhu.  
  
### <a name="to-create-the-dataflow-pipeline"></a>K vytvoření kanálu toku dat  
  
1. Ve vašem projektu přidejte odkaz na System.Threading.Tasks.Dataflow.dll.  
  
2. Ujistěte se, že Form1.cs (Form1.vb pro jazyk Visual Basic) obsahuje následující `using` příkazy (`Imports` v jazyce Visual Basic).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. Přidat `WorkItem` třídu jako vnitřní typ `Form1` třídy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. Přidejte následující datové členy do `Form1` třídy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. Přidejte následující metodu `CreatePipeline`, možnosti `Form1` třídy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Vzhledem k tomu, `incrementProgress` a `decrementProgress` toku dat bloky fungovat na uživatelské rozhraní, je důležité, že provedou tyto akce ve vlákně uživatelského rozhraní. Jak toho dosáhnout, během vytváření těchto objektů, zadejte každou <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> nastavenou na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provede práci na aktuálním kontextu synchronizace. Vzhledem k tomu, `Form1` konstruktoru se volá z vlákna uživatelského rozhraní, akce, `incrementProgress` a `decrementProgress` bloků toku dat také spustit ve vlákně uživatelského rozhraní.  
  
 Tento příklad nastaví <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost vytvoří členy kanálu. Vzhledem k tomu, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost trvale zruší spuštění bloku toku dat, celý kanál musí být znovu vytvořena po uživatel operaci zruší a pak se chce přidat další pracovní položky do kanálu. Příklad, který ukazuje alternativu ke zrušení bloku toku dat tak, že další práce lze provést po zrušení operace, najdete v části [názorný postup: Použití toku dat v Windows Forms aplikace](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Připojení kanálu toku dat v uživatelském rozhraní  
 Tato část popisuje postup připojení kanálu toku dat v uživatelském rozhraní. Vytváření kanálu a přidávání pracovních položek do kanálu se řídí obslužnou rutinu události pro **přidat pracovní položky** tlačítko. Zrušení inicializuje **zrušit** tlačítko. Po kliknutí na některý z těchto tlačítek, vyvolání příslušné akce v asynchronním režimu.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Připojení kanálu toku dat v uživatelském rozhraní  
  
1. V návrháři formuláře pro hlavní formulář, vytvořit obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> události **přidat pracovní položky** tlačítko.  
  
2. Implementace <xref:System.Windows.Forms.ToolStripItem.Click> událost pro **přidat pracovní položky** tlačítko.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. V návrháři formuláře pro hlavní formulář, vytvořit obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutiny události pro **zrušit** tlačítko.  
  
4. Implementace <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutiny události pro **zrušit** tlačítko.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje kompletní kód pro Form1.cs (Form1.vb pro jazyk Visual Basic).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Následující obrázek znázorňuje spuštěné aplikaci.  
  
 ![Aplikaci Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
