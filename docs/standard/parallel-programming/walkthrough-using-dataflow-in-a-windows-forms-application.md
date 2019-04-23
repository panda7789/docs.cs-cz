---
title: 'Návod: Použití toku dat ve formulářové aplikaci Windows'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd75bd14b2393d9b316d90070894f214dfa60c88
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344374"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>Návod: Použití toku dat ve formulářové aplikaci Windows
Tento dokument ukazuje, jak vytvořit síť bloků toku dat, které provádějí zpracování obrázků v aplikaci Windows Forms.  
  
 Tento příklad načte soubory obrázků ve složce zadané, vytvoří bitovou kopii složené a zobrazí výsledek. V příkladu používá model toku dat pro trasu Image přes síť. V toku dat modelu nezávislé komponenty aplikace mezi sebou komunikovat odesíláním zpráv. Když komponenta obdrží zprávu, provede určitou akci a jinou součást pak předá výsledek. Porovnejte s model řízení toku, ve které aplikace používá řídicí struktury, například, podmíněné příkazy, smyčky a tak dále, k řízení pořadí operací v programu.  
  
## <a name="prerequisites"></a>Požadavky  
 Čtení [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) před zahájením tohoto návodu.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a>Oddíly  
 Tento návod obsahuje následující části:  
  
-   [Vytvoření aplikace Windows Forms](#winforms)  
  
-   [Vytvoření sítě toku dat](#network)  
  
-   [Připojení sítě toku dat v uživatelském rozhraní](#ui)  
  
-   [Kompletní příklad](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a>Vytvoření aplikace Windows Forms  
 Tato část popisuje, jak vytvořit základní aplikaci Windows Forms a přidání ovládacích prvků do hlavního formuláře.  
  
#### <a name="to-create-the-windows-forms-application"></a>Chcete-li vytvořit Windows Forms aplikace  
  
1. V sadě Visual Studio, vytvořit Visual C# nebo Visual Basic **formulářová aplikace Windows** projektu. V tomto dokumentu má projekt název `CompositeImages`.  
  
2. V návrháři formuláře pro hlavní formulář Form1.cs (Form1.vb pro jazyk Visual Basic), přidejte <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.  
  
3. Přidat <xref:System.Windows.Forms.ToolStripButton> ovládací prvek <xref:System.Windows.Forms.ToolStrip> ovládacího prvku. Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **vybrat složku**.  
  
4. Přidejte druhý <xref:System.Windows.Forms.ToolStripButton> ovládací prvek <xref:System.Windows.Forms.ToolStrip> ovládacího prvku. Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost **zrušit**a <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> vlastnost `False`.  
  
5. Přidat <xref:System.Windows.Forms.PictureBox> objektu do hlavního formuláře. Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>Vytvoření sítě toku dat  
 Tato část popisuje postup vytvoření sítě toku dat, který provádí zpracování obrázků.  
  
#### <a name="to-create-the-dataflow-network"></a>Pokud chcete vytvořit síť toku dat  
  
1. Do projektu přidejte odkaz na System.Threading.Tasks.Dataflow.dll.  
  
2. Ujistěte se, že Form1.cs (Form1.vb pro jazyk Visual Basic) obsahuje následující `using` (`Using` v jazyce Visual Basic) příkazy:  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3. Přidejte následující datové členy do `Form1` třídy:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4. Přidejte následující metodu `CreateImageProcessingNetwork`, možnosti `Form1` třídy. Tato metoda vytvoří sítě pro zpracování obrazu.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5. Implementace `LoadBitmaps` metody.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6. Implementace `CreateCompositeBitmap` metody.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  C# verze `CreateCompositeBitmap` metoda využívá k zajištění efektivní zpracování ukazatele <xref:System.Drawing.Bitmap?displayProperty=nameWithType> objekty. Proto je nutné povolit **povolit nezabezpečený kód** možnost ve vašem projektu, aby bylo možné používat [nebezpečné](~/docs/csharp/language-reference/keywords/unsafe.md) – klíčové slovo. Další informace o tom, jak povolit nezabezpečený kód v projektu jazyka Visual C# najdete v tématu [stránku sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
 Následující tabulka popisuje členy v síti.  
  
|Člen|Type|Popis|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Přijímá jako vstup cestu ke složce a vytvoří kolekci <xref:System.Drawing.Bitmap> objekty jako výstup.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Vezme kolekci <xref:System.Drawing.Bitmap> objekty jako vstup a vytvoří složené rastrového obrázku jako výstup.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Složený rastrový obrázek se zobrazí ve formuláři.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zobrazí obrázek k označení, že operace je zrušena a umožňuje uživateli vybrat jinou složku.|  
  
 Pro připojení bloků toku dat pro formulář k síti, v tomto příkladu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metody. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Metoda obsahuje přetížené verze, která přijímá <xref:System.Predicate%601> objekt, který určuje, zda cílový blok přijme nebo odmítne zprávy. Tento mechanismus filtrování umožňuje blokům zpráv přijímat jenom konkrétní hodnoty. V tomto příkladu můžete větvit sítě v jednom ze dvou způsobů. Hlavní větev načte obrázky z disku, vytvoří složené bitovou kopii a této bitové kopie se zobrazí ve formuláři. Alternativní větev zruší aktuální operaci. <xref:System.Predicate%601> Objekty povolit bloků toku dat podél hlavní větve, přepnout na větev alternativní odmítnutím některé zprávy. Například, pokud uživatel zruší operaci bloku toku dat `createCompositeBitmap` vytváří `null` (`Nothing` v jazyce Visual Basic) jako výstup. Blok toku dat `displayCompositeBitmap` odmítne `null` vstupní hodnoty a proto zprávy se nabízí na `operationCancelled`. Blok toku dat `operationCancelled` přijímá všechny zprávy a proto se zobrazí obrázek k označení, že operace je zrušená.  
  
 Následující ilustrace znázorňuje sítě pro zpracování obrazu:  
  
 ![Ilustrace znázorňující sítě pro zpracování obrazu.](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 Vzhledem k tomu, `displayCompositeBitmap` a `operationCancelled` toku dat bloky fungovat na uživatelské rozhraní, je důležité, že provedou tyto akce ve vlákně uživatelského rozhraní. Provedete to, že během konstrukce tyto objekty každý poskytují <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> vlastnost nastavena na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda vytvoří <xref:System.Threading.Tasks.TaskScheduler> objekt, který provede práci na aktuálním kontextu synchronizace. Protože `CreateImageProcessingNetwork` metoda je volána z obslužné rutiny **vybrat složku** tlačítko, které běží v uživatelském rozhraní vlákna, akce `displayCompositeBitmap` a `operationCancelled` bloků toku dat spustit také na vlákna uživatelského rozhraní.  
  
 Tento příklad používá token zrušení sdílené místo nastavení <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost protože <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnost trvale zruší tok dat zablokovat spuštění. Token zrušení umožňuje znovu použít stejné síti toku dat více než jednou, i když uživatel zruší jednu nebo více operací v tomto příkladu. Příklad, který používá <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> trvale zrušit provádění bloku toku dat, naleznete v tématu [jak: Zrušení bloku toku dat](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Připojení sítě toku dat v uživatelském rozhraní  
 Tato část popisuje, jak připojit síť toku dat v uživatelském rozhraní. Vytvoření složeného image a zrušení operace inicializována z **vybrat složku** a **zrušit** tlačítka. Když uživatel zvolí jednu z těchto tlačítek, vyvolání příslušné akce v asynchronním režimu.  
  
#### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>K připojení sítě toku dat v uživatelském rozhraní  
  
1. V návrháři formuláře pro hlavní formulář, vytvořit obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> události **vybrat složku** tlačítko.  
  
2. Implementace <xref:System.Windows.Forms.ToolStripItem.Click> událost pro **vybrat složku** tlačítko.  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3. V návrháři formuláře pro hlavní formulář, vytvořit obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> události **zrušit** tlačítko.  
  
4. Implementace <xref:System.Windows.Forms.ToolStripItem.Click> událost pro **zrušit** tlačítko.  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní kód v tomto návodu.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Následující obrázek znázorňuje příklad typického výstupu pro běžné \Sample Pictures\ složku.  
  
 ![Aplikaci Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
