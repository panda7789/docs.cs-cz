---
title: 'Postupy: Použití toku dat ve formulářové aplikaci Windows'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
ms.openlocfilehash: 794253514edf63f02276e1ece21c60a85c534390
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159764"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>Postupy: Použití toku dat ve formulářové aplikaci Windows
Tento dokument ukazuje, jak vytvořit síť bloků toku dat, které provádějí zpracování obrazu v aplikaci Windows Forms.  
  
 Tento příklad načte obrazové soubory ze zadané složky, vytvoří složený obraz a zobrazí výsledek. Příklad používá model toku dat ke směrování obrazů v síti. V modelu toku dat nezávislé součásti programu komunikovat mezi sebou odesíláním zpráv. Když komponenta obdrží zprávu, provede nějakou akci a pak předá výsledek jiné součásti. Porovnejte to s modelem toku řízení, ve kterém aplikace používá řídicí struktury, například podmíněné příkazy, smyčky a tak dále, k řízení pořadí operací v programu.  
  
## <a name="prerequisites"></a>Požadavky  
 Před spuštěním tohoto návodu si přečtěte [tok dat.](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a>Oddíly  
 Tento návod obsahuje následující části:  
  
- [Vytvoření aplikace windows forms](#winforms)  
  
- [Vytvoření sítě toku dat](#network)  
  
- [Připojení sítě toku dat k uživatelskému rozhraní](#ui)  
  
- [Kompletní příklad](#complete)  
  
<a name="winforms"></a>
## <a name="creating-the-windows-forms-application"></a>Vytvoření aplikace windows forms  
 Tato část popisuje, jak vytvořit základní aplikaci Windows Forms a přidat ovládací prvky do hlavního formuláře.  
  
### <a name="to-create-the-windows-forms-application"></a>Vytvoření aplikace windows forms  
  
1. V sadě Visual Studio vytvořte projekt aplikace Visual C# nebo Visual Basic **Windows Forms Application.** V tomto dokumentu je `CompositeImages`projekt pojmenován .  
  
2. V návrháři formuláře pro hlavní formulář, Form1.cs (Form1.vb <xref:System.Windows.Forms.ToolStrip> pro visual basic), přidejte ovládací prvek.  
  
3. Přidejte <xref:System.Windows.Forms.ToolStripButton> ovládací <xref:System.Windows.Forms.ToolStrip> prvek do ovládacího prvku. Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **zvolit složku**.  
  
4. Přidejte <xref:System.Windows.Forms.ToolStripButton> druhý ovládací <xref:System.Windows.Forms.ToolStrip> prvek do ovládacího prvku. Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>na <xref:System.Windows.Forms.ToolStripItem.Text%2A> , vlastnost **cancel** <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> a `False`vlastnost na .  
  
5. Přidejte <xref:System.Windows.Forms.PictureBox> objekt do hlavního formuláře. Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>na .  
  
<a name="network"></a>
## <a name="creating-the-dataflow-network"></a>Vytvoření sítě toku dat  
 Tato část popisuje, jak vytvořit síť toku dat, která provádí zpracování obrazu.  
  
### <a name="to-create-the-dataflow-network"></a>Vytvoření sítě toku dat  
  
1. Přidejte odkaz na system.threading.tasks.dataflow.dll do projektu.  
  
2. Ujistěte se, že Form1.cs (Form1.vb `using` `Using` pro visual basic) obsahuje následující (v jazyce Visual Basic) příkazy:  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3. Přidejte do třídy `Form1` následující datové členy:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4. Přidejte následující `CreateImageProcessingNetwork`metodu `Form1` , do třídy. Tato metoda vytvoří síť pro zpracování obrazu.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5. Implementujte `LoadBitmaps` metodu.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6. Implementujte `CreateCompositeBitmap` metodu.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    > Verze `CreateCompositeBitmap` metody C# používá ukazatele pro povolení efektivního zpracování <xref:System.Drawing.Bitmap?displayProperty=nameWithType> objektů. Proto je nutné povolit **možnost Povolit nebezpečný kód** v projektu, aby bylo možné použít [nebezpečné](../../csharp/language-reference/keywords/unsafe.md) klíčové slovo. Další informace o povolení nebezpečného kódu v projektu Visual C# naleznete v [tématu Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
 Následující tabulka popisuje členy sítě.  
  
|Člen|Typ|Popis|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Trvá cestu ke složce jako vstup <xref:System.Drawing.Bitmap> a vytvoří kolekci objektů jako výstup.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Vezme kolekci <xref:System.Drawing.Bitmap> objektů jako vstup a vytvoří složený bitmap jako výstup.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zobrazí složený bitmapu ve formuláři.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zobrazí obrázek označující, že operace je zrušena, a umožňuje uživateli vybrat jinou složku.|  
  
 Chcete-li připojit bloky toku dat k <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> vytvoření sítě, tento příklad používá metodu. Metoda <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> obsahuje přetíženou verzi, <xref:System.Predicate%601> která přebírá objekt, který určuje, zda cílový blok přijme nebo odmítne zprávu. Tento mechanismus filtrování umožňuje bloky zpráv přijímat pouze určité hodnoty. V tomto příkladu může síť větvit jedním ze dvou způsobů. Hlavní větev načte obrazy z disku, vytvoří složený obraz a zobrazí tento obraz ve formuláři. Alternativní větev zruší aktuální operaci. Objekty <xref:System.Predicate%601> umožňují bloky toku dat podél hlavní větve přepnout na alternativní větev odmítnutím určité zprávy. Například pokud uživatel zruší operaci, blok `createCompositeBitmap` toku `null` dat`Nothing` vytvoří (v jazyce Visual Basic) jako výstup. Blok `displayCompositeBitmap` toku dat `null` odmítne vstupní hodnoty, a proto `operationCancelled`je zpráva nabízena . Blok `operationCancelled` toku dat přijímá všechny zprávy a proto zobrazí obrázek označující, že operace je zrušena.  
  
 Následující obrázek znázorňuje síť pro zpracování obrazu:  
  
 ![Obrázek znázorňuje síť pro zpracování obrazu.](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 Vzhledem `displayCompositeBitmap` `operationCancelled` k tomu, že bloky a tok dat působí na uživatelské rozhraní, je důležité, aby tyto akce dojít ve vlákně uživatelského rozhraní. Chcete-li to provést, během konstrukce, tyto objekty každý poskytují <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavena na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provádí práci na aktuálním kontextu synchronizace. Vzhledem `CreateImageProcessingNetwork` k tomu, že metoda je volána z obslužné rutiny `displayCompositeBitmap` `operationCancelled` tlačítka **Zvolit složku,** která běží ve vlákně uživatelského rozhraní, akce pro bloky a tok dat jsou spuštěny také ve vlákně uživatelského rozhraní.  
  
 Tento příklad používá sdílený token zrušení <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> namísto <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> nastavení vlastnosti, protože vlastnost trvale zruší spuštění bloku toku dat. Token zrušení umožňuje tento příklad znovu použít stejnou síť toku dat vícekrát, i když uživatel zruší jednu nebo více operací. Příklad, který <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> se používá k trvalému zrušení spuštění bloku toku dat, najdete v tématu [Postup: Zrušení bloku toku dat](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).  
  
<a name="ui"></a>
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Připojení sítě toku dat k uživatelskému rozhraní  
 Tato část popisuje, jak připojit síť toku dat k uživatelskému rozhraní. Vytvoření složeného obrázku a zrušení operace jsou zahájeny z **tlačítka Zvolit složku** a **Zrušit.** Když uživatel zvolí některá z těchto tlačítek, příslušná akce je zahájena asynchronním způsobem.  
  
### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Připojení sítě toku dat k uživatelskému rozhraní  
  
1. V návrháři formuláře pro hlavní formulář vytvořte <xref:System.Windows.Forms.ToolStripItem.Click> obslužnou rutinu události pro tlačítko **Zvolit složku.**  
  
2. Implementujte <xref:System.Windows.Forms.ToolStripItem.Click> událost pro tlačítko **Zvolit složku.**  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3. V návrháři formuláře pro hlavní formulář vytvořte <xref:System.Windows.Forms.ToolStripItem.Click> obslužnou rutinu události pro tlačítko **Storno.**  
  
4. Implementujte <xref:System.Windows.Forms.ToolStripItem.Click> událost pro tlačítko **Storno.**  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje úplný kód pro tento návod.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Následující obrázek znázorňuje typický výstup pro společnou složku \Sample Pictures\.  
  
 ![Aplikace Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>Viz také

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
