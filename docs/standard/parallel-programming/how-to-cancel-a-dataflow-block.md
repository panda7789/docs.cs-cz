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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140090"
---
# <a name="how-to-cancel-a-dataflow-block"></a>Postupy: Zrušení bloku toku dat
Tento dokument ukazuje, jak povolit zrušení ve vaší aplikaci. Tento příklad používá Windows Forms k zobrazení, kde jsou aktivní pracovní položky v kanálu toku dat a také účinky zrušení.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Vytvoření aplikace windows forms  
  
1. Vytvořte projekt aplikace C# nebo Visual Basic **Forms Application.** V následujících krocích je `CancellationWinForms`projekt pojmenován .  
  
2. V návrháři formuláře pro hlavní formulář, Form1.cs (Form1.vb <xref:System.Windows.Forms.ToolStrip> pro visual basic), přidejte ovládací prvek.  
  
3. Přidejte <xref:System.Windows.Forms.ToolStripButton> ovládací <xref:System.Windows.Forms.ToolStrip> prvek do ovládacího prvku. Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **přidat pracovní položky**.  
  
4. Přidejte <xref:System.Windows.Forms.ToolStripButton> druhý ovládací <xref:System.Windows.Forms.ToolStrip> prvek do ovládacího prvku. Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>na <xref:System.Windows.Forms.ToolStripItem.Text%2A> , vlastnost **cancel** <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> a `False`vlastnost na .  
  
5. Přidejte <xref:System.Windows.Forms.ToolStripProgressBar> do <xref:System.Windows.Forms.ToolStrip> ovládacího prvku čtyři objekty.  
  
## <a name="creating-the-dataflow-pipeline"></a>Vytvoření kanálu toku dat  
 Tato část popisuje, jak vytvořit kanál toku dat, který zpracovává pracovní položky a aktualizuje indikátory průběhu.  
  
### <a name="to-create-the-dataflow-pipeline"></a>Vytvoření kanálu toku dat  
  
1. V projektu přidejte odkaz na System.Threading.Tasks.Dataflow.dll.  
  
2. Ujistěte se, že Form1.cs (Form1.vb `using` pro`Imports` visual basic) obsahuje následující příkazy ( v jazyce Visual Basic).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. Přidejte `WorkItem` třídu jako vnitřní `Form1` typ třídy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. Přidejte následující datové `Form1` členy do třídy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. Přidejte následující `CreatePipeline`metodu `Form1` , do třídy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Vzhledem `incrementProgress` `decrementProgress` k tomu, že bloky a tok dat působí na uživatelské rozhraní, je důležité, aby tyto akce dojít ve vlákně uživatelského rozhraní. Chcete-li to provést, během <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> konstrukce tyto <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> objekty <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>každý poskytnout objekt, který má vlastnost nastavena na . Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provádí práci na aktuálním kontextu synchronizace. Vzhledem `Form1` k tomu, že konstruktor je volána `incrementProgress` `decrementProgress` z vlákna uživatelského rozhraní, akce pro bloky a tok dat také spustit ve vlákně uživatelského rozhraní.  
  
 Tento příklad <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> nastaví vlastnost při konstrukci členy kanálu. Vzhledem <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> k tomu, že vlastnost trvale zruší spuštění bloku toku dat, celý kanál musí být znovu vytvořen poté, co uživatel zruší operaci a pak chce přidat další pracovní položky do kanálu. Příklad, který ukazuje alternativní způsob zrušení bloku toku dat tak, aby bylo možné provést další práci po zrušení operace, naleznete v [návodu: Použití toku dat v aplikaci Windows Forms .](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Připojení kanálu toku dat k uživatelskému rozhraní  
 Tato část popisuje, jak připojit kanál toku dat k uživatelskému rozhraní. Vytvoření kanálu a přidání pracovních položek do kanálu jsou řízeny obslužnou rutinou události pro tlačítko **Přidat pracovní položky.** Zrušení je iniciováno tlačítkem **Storno.** Když uživatel klepne na některou z těchto tlačítek, příslušná akce je zahájena asynchronním způsobem.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Připojení kanálu toku dat k uživatelskému rozhraní  
  
1. V návrháři formuláře pro hlavní formulář vytvořte <xref:System.Windows.Forms.ToolStripItem.Click> obslužnou rutinu události pro tlačítko **Přidat pracovní položky.**  
  
2. Implementujte <xref:System.Windows.Forms.ToolStripItem.Click> událost pro tlačítko **Přidat pracovní položky.**  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. V návrháři formuláře pro hlavní formulář vytvořte <xref:System.Windows.Forms.ToolStripItem.Click> obslužnou rutinu události pro obslužnou rutinu události pro tlačítko **Storno.**  
  
4. Implementujte <xref:System.Windows.Forms.ToolStripItem.Click> obslužnou rutinu události pro tlačítko **Storno.**  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje úplný kód pro Form1.cs (Form1.vb pro visual basic).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Následující obrázek znázorňuje spuštěnou aplikaci.  
  
 ![Aplikace Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Viz také

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
