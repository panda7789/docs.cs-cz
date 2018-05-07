---
title: 'Postupy: Použití toku dat ve formulářové aplikaci Windows'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 919dc097d32451c6123e68f8bf4b8f41808f89da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>Postupy: Použití toku dat ve formulářové aplikaci Windows
Tento dokument ukazuje, jak vytvořit síť bloků toku dat, které provádějí zpracování obrázků v aplikaci Windows Forms.  
  
 Tento příklad načte soubory bitové kopie ze zadané složky, vytváří složené bitovou kopii a zobrazí výsledek. V příkladu je model toku dat trasy Image přes síť. V modelu toku dat nezávislé komponenty programu vzájemnou komunikaci odesláním zprávy. Když součást přijme zprávu o, provádí některé akce a poté předá výsledek jiné součásti. Toto porovnání s model toku řízení, ve kterém aplikace využívá řídicí struktury, například, podmíněné příkazy, smyčky a tak dále, řídit pořadí operací v programu.  
  
## <a name="prerequisites"></a>Požadavky  
 Čtení [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) před spuštěním tohoto průvodce.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a>Oddíly  
 Tento názorný postup obsahuje následující části:  
  
-   [Vytvoření aplikace Windows Forms](#winforms)  
  
-   [Vytvoření sítě toku dat](#network)  
  
-   [Připojování k uživatelské rozhraní sítě toku dat](#ui)  
  
-   [Úplný příklad](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a>Vytvoření aplikace Windows Forms  
 Tato část popisuje, jak vytvořit základní aplikaci Windows Forms a přidání ovládacích prvků do hlavní formulář.  
  
#### <a name="to-create-the-windows-forms-application"></a>K vytvoření Windows Forms aplikace  
  
1.  V sadě Visual Studio vytvořit Visual C# nebo Visual Basic **formulářové aplikace Windows** projektu. V tomto dokumentu je projekt s názvem `CompositeImages`.  
  
2.  V návrháři formuláře pro hlavní formulář Form1.cs (Form1.vb jazyka Visual Basic), přidejte <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.  
  
3.  Přidat <xref:System.Windows.Forms.ToolStripButton> řídit k <xref:System.Windows.Forms.ToolStrip> ovládacího prvku. Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **zvolte složku**.  
  
4.  Přidejte druhý <xref:System.Windows.Forms.ToolStripButton> řídit k <xref:System.Windows.Forms.ToolStrip> ovládacího prvku. Nastavit <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **zrušit**a <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> vlastnost `False`.  
  
5.  Přidat <xref:System.Windows.Forms.PictureBox> objekt, který má hlavní formulář. Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>Vytvoření sítě toku dat  
 Tato část popisuje, jak vytvořit síť toku dat, která provádí zpracování obrázků.  
  
#### <a name="to-create-the-dataflow-network"></a>Vytvoření sítě toku dat  
  
1.  Přidáte odkaz na System.Threading.Tasks.Dataflow.dll do projektu.  
  
2.  Ujistěte se, že Form1.cs (Form1.vb jazyka Visual Basic) obsahuje následující `using` (`Using` v jazyce Visual Basic) příkazy:  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3.  Přidejte následující členy dat tak, aby `Form1` třídy:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4.  Přidejte následující metodu `CreateImageProcessingNetwork`, na `Form1` třídy. Tato metoda vytvoří síť zpracování bitové kopie.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5.  Implementace `LoadBitmaps` metoda.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6.  Implementace `CreateCompositeBitmap` metoda.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  C# verzi `CreateCompositeBitmap` metoda používá ukazatele umožňující efektivní zpracování <xref:System.Drawing.Bitmap?displayProperty=nameWithType> objekty. Proto je nutné povolit **povolit nezabezpečený kód** možnost ve vašem projektu, aby bylo možné používat [unsafe](~/docs/csharp/language-reference/keywords/unsafe.md) – klíčové slovo. Další informace o tom, jak povolit nezabezpečený kód v projektu jazyka Visual C#, najdete v části [stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
 Následující tabulka popisuje členy sítě.  
  
|Člen|Typ|Popis|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Má jako vstup cestu složky a vytvoří kolekci <xref:System.Drawing.Bitmap> objekty jako výstup.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Vezme kolekci <xref:System.Drawing.Bitmap> objekty jako vstup a vytváří složené rastrový obrázek jako výstup.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zobrazí složené rastrového obrázku na formuláři.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zobrazí obrázek, který má znamenat, že operace je zrušená a umožňuje uživateli vybrat jinou složku.|  
  
 Používá pro připojení bloků toku dat a vytvořit síť, v tomto příkladu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metoda. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Metoda obsahuje přetížené verze, která přijímá <xref:System.Predicate%601> objekt, který určuje, zda cílový blok přijme nebo odmítne zprávy. Tento mechanismus filtrování umožňuje bloky zpráv přijímat jenom určité hodnoty. V tomto příkladu můžete větev sítě v jednom ze dvou způsobů. Hlavní větve načte bitové kopie z disku, vytvoří bitovou kopii složené a zobrazí této bitové kopie na formuláři. Alternativní větev zruší aktuální operace. <xref:System.Predicate%601> Objekty povolit bloků toku dat společně hlavní větve přepnout do alternativní větve odmítnutím některé zprávy. Například, pokud uživatel zruší operaci bloku toku dat `createCompositeBitmap` vytváří `null` (`Nothing` v jazyce Visual Basic) jako výstup. Bloku toku dat `displayCompositeBitmap` odmítne `null` vstupní hodnoty a proto zpráva se nabízí na `operationCancelled`. Bloku toku dat `operationCancelled` přijímá všechny zprávy a proto zobrazí obrázek, který se označuje, že operace je zrušená.  
  
 Následující ilustrace znázorňuje sítě pro zpracování bitové kopie.  
  
 ![Obrázek sítě pro zpracování](../../../docs/standard/parallel-programming/media/dataflowwinforms.png "DataflowWinForms")  
  
 Protože `displayCompositeBitmap` a `operationCancelled` toku dat bloky fungují v uživatelském rozhraní, je důležité, aby tyto akce se provedou ve vláknu uživatelského rozhraní. K tomu během vytváření, zadejte tyto objekty každý <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavena na hodnotu <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provede práci v aktuálním kontextu synchronizace. Protože `CreateImageProcessingNetwork` metoda je volána z obslužné rutiny **vybrat složku** tlačítko, které běží v uživatelském rozhraní vláken, akce `displayCompositeBitmap` a `operationCancelled` bloků toku dat spustit také na vlákna uživatelského rozhraní.  
  
 Tento příklad používá token zrušení sdílené nikoli nastavení <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost protože <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost trvale zruší spuštění bloku toku dat. Token zrušení umožňuje tento příklad opakovaně použít stejnou síť toku dat vícekrát, i když uživatel zruší jednu nebo více operací. Pro příklad, který používá <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> trvale zrušit provádění bloku toku dat, najdete v části [postupy: zrušení bloku toku dat](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Připojování k uživatelské rozhraní sítě toku dat  
 Tato část popisuje, jak připojit síť toku dat s uživatelským rozhraním. Vytváření složených bitové kopie a zrušení operace byla inicializována z **vybrat složku** a **zrušit** tlačítka. Když uživatel vybere jednu z těchto tlačítek, je v asynchronním režimu inicioval příslušnou akci.  
  
#### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Pro připojení sítě toku dat s uživatelským rozhraním  
  
1.  V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> události **vybrat složku** tlačítko.  
  
2.  Implementace <xref:System.Windows.Forms.ToolStripItem.Click> události **zvolte složku** tlačítko.  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3.  V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> události **zrušit** tlačítko.  
  
4.  Implementace <xref:System.Windows.Forms.ToolStripItem.Click> události **zrušit** tlačítko.  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní kód v tomto návodu.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Následující obrázek znázorňuje typické výstup pro běžné \Sample Pictures\ složku.  
  
 ![Windows Forms aplikace](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>Viz také  
 [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
