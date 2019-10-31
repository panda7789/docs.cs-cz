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
ms.openlocfilehash: aa175d95f27fcbf28c3f3da3eaa7b8f7988681e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140090"
---
# <a name="how-to-cancel-a-dataflow-block"></a>Postupy: Zrušení bloku toku dat
Tento dokument ukazuje, jak povolit zrušení ve vaší aplikaci. V tomto příkladu se používá model Windows Forms k zobrazení, kde jsou pracovní položky aktivní v kanálu toku dat a také důsledky zrušení.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Vytvoření aplikace model Windows Forms  
  
1. Vytvořte projekt C# **aplikace model Windows Forms** nebo Visual Basic. V následujících krocích se projekt jmenuje `CancellationWinForms`.  
  
2. V návrháři formuláře pro hlavní formulář Form1.cs (Form1. vb pro Visual Basic) přidejte ovládací prvek <xref:System.Windows.Forms.ToolStrip>.  
  
3. Přidejte ovládací prvek <xref:System.Windows.Forms.ToolStripButton> do ovládacího prvku <xref:System.Windows.Forms.ToolStrip>. Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a vlastnost <xref:System.Windows.Forms.ToolStripItem.Text%2A> pro **Přidání pracovních položek**.  
  
4. Přidejte druhý ovládací prvek <xref:System.Windows.Forms.ToolStripButton> k ovládacímu prvku <xref:System.Windows.Forms.ToolStrip>. Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, vlastnost <xref:System.Windows.Forms.ToolStripItem.Text%2A> na **Storno**a vlastnost <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> na `False`.  
  
5. Přidejte čtyři objekty <xref:System.Windows.Forms.ToolStripProgressBar> k ovládacímu prvku <xref:System.Windows.Forms.ToolStrip>.  
  
## <a name="creating-the-dataflow-pipeline"></a>Vytvoření kanálu toku dat  
 Tato část popisuje, jak vytvořit kanál toku dat, který zpracovává pracovní položky a aktualizuje indikátory průběhu.  
  
### <a name="to-create-the-dataflow-pipeline"></a>Vytvoření kanálu toku dat  
  
1. V projektu přidejte odkaz na System. Threading. Tasks. Dataflow. dll.  
  
2. Ujistěte se, že Form1.cs (Form1. vb pro Visual Basic) obsahuje následující příkazy `using` (`Imports` v Visual Basic).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. Přidejte třídu `WorkItem` jako vnitřní typ `Form1` třídy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. Do třídy `Form1` přidejte následující datové členy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. Do `Form1` třídy přidejte následující metodu `CreatePipeline`.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Vzhledem k tomu, že bloky toku dat `incrementProgress` a `decrementProgress` fungují na uživatelském rozhraní, je důležité, aby tyto akce probíhaly ve vlákně uživatelského rozhraní. Chcete-li to provést, během konstrukce těchto objektů poskytuje objekt <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>, který má vlastnost <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> nastavena na hodnotu <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> vytvoří objekt <xref:System.Threading.Tasks.TaskScheduler>, který provádí práci na aktuálním kontextu synchronizace. Vzhledem k tomu, že konstruktor `Form1` je volán z vlákna uživatelského rozhraní, akce pro bloky toku dat `incrementProgress` a `decrementProgress` jsou také spouštěny ve vlákně uživatelského rozhraní.  
  
 Tento příklad nastavuje vlastnost <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> při sestavování členů kanálu. Vzhledem k tomu, že vlastnost <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> trvale zruší provádění bloku toku dat, je nutné znovu vytvořit celý kanál poté, co uživatel operaci zruší a pak chce do kanálu přidat další pracovní položky. Příklad, který ukazuje alternativní způsob, jak zrušit blok toku dat, aby bylo možné provést další práci po zrušení operace, naleznete v tématu [Návod: použití toku dat v aplikaci model Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Připojení kanálu toku dat k uživatelskému rozhraní  
 Tato část popisuje, jak propojit kanál toku dat s uživatelským rozhraním. Vytvoření kanálu a přidání pracovních položek do kanálu jsou ovládány obslužnou rutinou události pro tlačítko **Přidat pracovní položky** . Zrušení je iniciováno tlačítkem **Zrušit** . Když uživatel klikne na jedno z těchto tlačítek, je vhodná akce iniciována asynchronním způsobem.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Připojení kanálu toku dat k uživatelskému rozhraní  
  
1. V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.ToolStripItem.Click> pro tlačítko **Přidat pracovní položky** .  
  
2. Implementujte událost <xref:System.Windows.Forms.ToolStripItem.Click> pro tlačítko **Přidat pracovní položky** .  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro obslužnou rutinu události <xref:System.Windows.Forms.ToolStripItem.Click> pro tlačítko **Storno** .  
  
4. Implementujte obslužnou rutinu události <xref:System.Windows.Forms.ToolStripItem.Click> pro tlačítko **Storno** .  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje úplný kód pro Form1.cs (Form1. vb pro Visual Basic).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Následující ilustrace znázorňuje běžící aplikaci.  
  
 ![Aplikace model Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
