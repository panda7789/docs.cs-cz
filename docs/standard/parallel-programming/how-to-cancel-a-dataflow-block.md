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
ms.openlocfilehash: 530c231deeaba007975849ab6dc41f4da6a859ea
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285544"
---
# <a name="how-to-cancel-a-dataflow-block"></a>Postupy: Zrušení bloku toku dat
Tento dokument ukazuje, jak povolit zrušení ve vaší aplikaci. V tomto příkladu se používá model Windows Forms k zobrazení, kde jsou pracovní položky aktivní v kanálu toku dat a také důsledky zrušení.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Vytvoření aplikace model Windows Forms  
  
1. Vytvořte projekt aplikace v jazyce C# nebo Visual Basic **model Windows Forms** . V následujících krocích se projekt jmenuje `CancellationWinForms` .  
  
2. V návrháři formuláře pro hlavní formulář Form1.cs (Form1. vb pro Visual Basic) přidejte <xref:System.Windows.Forms.ToolStrip> ovládací prvek.  
  
3. Přidejte <xref:System.Windows.Forms.ToolStripButton> ovládací prvek do <xref:System.Windows.Forms.ToolStrip> ovládacího prvku. Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a vlastnost, <xref:System.Windows.Forms.ToolStripItem.Text%2A> Chcete-li **Přidat pracovní položky**.  
  
4. Přidejte <xref:System.Windows.Forms.ToolStripButton> k <xref:System.Windows.Forms.ToolStrip> ovládacímu prvku druhý ovládací prvek. Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost na vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> , kterou <xref:System.Windows.Forms.ToolStripItem.Text%2A> chcete **Zrušit**, a <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> vlastnost na hodnotu `False` .  
  
5. Přidejte <xref:System.Windows.Forms.ToolStripProgressBar> do <xref:System.Windows.Forms.ToolStrip> ovládacího prvku čtyři objekty.  
  
## <a name="creating-the-dataflow-pipeline"></a>Vytvoření kanálu toku dat  
 Tato část popisuje, jak vytvořit kanál toku dat, který zpracovává pracovní položky a aktualizuje indikátory průběhu.  
  
### <a name="to-create-the-dataflow-pipeline"></a>Vytvoření kanálu toku dat  
  
1. V projektu přidejte odkaz na System. Threading. Tasks. Dataflow. dll.  
  
2. Ujistěte se, že Form1.cs (Form1. vb pro Visual Basic) obsahuje následující `using` příkazy ( `Imports` v Visual Basic).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. Přidejte `WorkItem` třídu jako vnitřní typ `Form1` třídy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. Přidejte do třídy následující datové členy `Form1` .  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. Přidejte následující metodu `CreatePipeline` do `Form1` třídy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Vzhledem k tomu, že `incrementProgress` `decrementProgress` bloky a tok dat fungují na uživatelském rozhraní, je důležité, aby tyto akce probíhaly ve vlákně uživatelského rozhraní. K tomu je potřeba během vytváření těchto objektů vytvořit <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavenou na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> . <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>Metoda vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provádí práci na aktuálním kontextu synchronizace. Vzhledem k tomu `Form1` , že je konstruktor volán z vlákna uživatelského rozhraní, jsou akce pro `incrementProgress` `decrementProgress` bloky a tok dat také spouštěny ve vlákně uživatelského rozhraní.  
  
 Tento příklad nastaví <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost při sestavování členů kanálu. Vzhledem k tomu <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> , že vlastnost trvale zruší provádění bloku toku dat, musí být celý kanál znovu vytvořen poté, co uživatel operaci zruší a pak chce do kanálu přidat další pracovní položky. Příklad, který ukazuje alternativní způsob, jak zrušit blok toku dat, aby bylo možné provést další práci po zrušení operace, naleznete v tématu [Návod: použití toku dat v aplikaci model Windows Forms](walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Připojení kanálu toku dat k uživatelskému rozhraní  
 Tato část popisuje, jak propojit kanál toku dat s uživatelským rozhraním. Vytvoření kanálu a přidání pracovních položek do kanálu jsou ovládány obslužnou rutinou události pro tlačítko **Přidat pracovní položky** . Zrušení je iniciováno tlačítkem **Zrušit** . Když uživatel klikne na jedno z těchto tlačítek, je vhodná akce iniciována asynchronním způsobem.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Připojení kanálu toku dat k uživatelskému rozhraní  
  
1. V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> událost pro tlačítko **Přidat pracovní položky** .  
  
2. Implementujte <xref:System.Windows.Forms.ToolStripItem.Click> událost pro tlačítko **Přidat pracovní položky** .  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> obslužnou rutinu události pro tlačítko **Storno** .  
  
4. Implementujte <xref:System.Windows.Forms.ToolStripItem.Click> obslužnou rutinu události pro tlačítko **Storno** .  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje úplný kód pro Form1.cs (Form1. vb pro Visual Basic).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Následující ilustrace znázorňuje běžící aplikaci.  
  
 ![Aplikace model Windows Forms](media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Viz také

- [Tok dat](dataflow-task-parallel-library.md)
