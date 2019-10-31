---
title: 'Postupy: Použití toku dat ve formulářové aplikaci Windows'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
ms.openlocfilehash: b6f4b933f76834f48d522d9c97fb0c9b5c24e13d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139915"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>Postupy: Použití toku dat ve formulářové aplikaci Windows
Tento dokument ukazuje, jak vytvořit síť bloků toku dat, které provádějí zpracování imagí v aplikaci model Windows Forms.  
  
 Tento příklad načte soubory obrázků ze zadané složky, vytvoří složený obrázek a zobrazí výsledek. V příkladu se používá model toku dat ke směrování imagí přes síť. V modelu toku dat vzájemně komunikují nezávislé součásti programu a odesílají zprávy. Když komponenta obdrží zprávu, provede nějakou akci a pak výsledek předá do jiné komponenty. Porovnejte je s modelem toku řízení, ve kterém aplikace používá řídicí struktury, například podmíněné příkazy, smyčky a tak dále, k řízení pořadí operací v programu.  
  
## <a name="prerequisites"></a>Požadavky  
 Před zahájením tohoto návodu Přečtěte [tok](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dat.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a>Oddíly  
 Tento návod obsahuje následující oddíly:  
  
- [Vytvoření aplikace model Windows Forms](#winforms)  
  
- [Vytváření sítě toku dat](#network)  
  
- [Propojení sítě toku dat s uživatelským rozhraním](#ui)  
  
- [Úplný příklad](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a>Vytvoření aplikace model Windows Forms  
 Tato část popisuje, jak vytvořit základní aplikaci model Windows Forms a jak přidat ovládací prvky do hlavního formuláře.  
  
### <a name="to-create-the-windows-forms-application"></a>Vytvoření aplikace model Windows Forms  
  
1. V aplikaci Visual Studio vytvořte projekt aplikace C# visual nebo Visual Basic **model Windows Forms** . V tomto dokumentu má projekt název `CompositeImages`.  
  
2. V návrháři formuláře pro hlavní formulář Form1.cs (Form1. vb pro Visual Basic) přidejte ovládací prvek <xref:System.Windows.Forms.ToolStrip>.  
  
3. Přidejte ovládací prvek <xref:System.Windows.Forms.ToolStripButton> do ovládacího prvku <xref:System.Windows.Forms.ToolStrip>. Vlastnost <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> nastavte na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a vlastnost <xref:System.Windows.Forms.ToolStripItem.Text%2A> na **Zvolit složku**.  
  
4. Přidejte druhý ovládací prvek <xref:System.Windows.Forms.ToolStripButton> k ovládacímu prvku <xref:System.Windows.Forms.ToolStrip>. Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, vlastnost <xref:System.Windows.Forms.ToolStripItem.Text%2A> na **Storno**a vlastnost <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> na `False`.  
  
5. Přidejte objekt <xref:System.Windows.Forms.PictureBox> do hlavního formuláře. Vlastnost <xref:System.Windows.Forms.Control.Dock%2A> nastavte na hodnotu <xref:System.Windows.Forms.DockStyle.Fill>.  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>Vytváření sítě toku dat  
 Tato část popisuje, jak vytvořit síť toku dat, která provádí zpracování bitové kopie.  
  
### <a name="to-create-the-dataflow-network"></a>Vytvoření sítě toku dat  
  
1. Do projektu přidejte odkaz na System. Threading. Tasks. Dataflow. dll.  
  
2. Ujistěte se, že Form1.cs (Form1. vb pro Visual Basic) obsahuje následující příkazy `using` (`Using` v Visual Basic):  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3. Do třídy `Form1` přidejte následující datové členy:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4. Do `Form1` třídy přidejte následující metodu `CreateImageProcessingNetwork`. Tato metoda vytvoří síť pro zpracování imagí.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5. Implementujte metodu `LoadBitmaps`.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6. Implementujte metodu `CreateCompositeBitmap`.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    > C# Verze metody `CreateCompositeBitmap` používá ukazatele k umožnění efektivního zpracování objektů <xref:System.Drawing.Bitmap?displayProperty=nameWithType>. Proto je nutné povolit možnost **Povolit nezabezpečený kód** v projektu, aby bylo možné použít klíčové slovo [unsafe](../../csharp/language-reference/keywords/unsafe.md) . Další informace o tom, jak povolit nezabezpečený kód ve C# vizuálním projektu, naleznete na [stránce sestavení,C#Návrhář projektu ()](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
 V následující tabulce jsou popsány členové sítě.  
  
|Člen|Typ|Popis|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Bere jako vstup cestu ke složce a vytvoří kolekci objektů <xref:System.Drawing.Bitmap> jako výstup.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Provede kolekci objektů <xref:System.Drawing.Bitmap> jako vstup a vytvoří složený rastrový obrázek jako výstup.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zobrazí složený rastrový obrázek ve formuláři.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zobrazí obrázek, který indikuje, že operace je zrušená a umožňuje uživateli vybrat jinou složku.|  
  
 Tento příklad používá metodu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> k propojení bloků toku dat za účelem vytvoření sítě. Metoda <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> obsahuje přetíženou verzi, která přebírá objekt <xref:System.Predicate%601>, který určuje, zda cílový blok přijímá nebo odmítá zprávu. Tento mechanismus filtrování umožňuje blokům zpráv přijímat pouze určité hodnoty. V tomto příkladu může síť větvit jedním ze dvou způsobů. Hlavní větev načte obrázky z disku, vytvoří složený obrázek a zobrazí tento obrázek ve formuláři. Alternativní větev zruší aktuální operaci. Objekty <xref:System.Predicate%601> umožňují, aby tok dat v rámci hlavní větve přepnul na alternativní větev tím, že odmítne určité zprávy. Například pokud uživatel operaci zruší, vytvoří blok toku dat `createCompositeBitmap` `null` (`Nothing` v Visual Basic) jako svůj výstup. Blok toku dat `displayCompositeBitmap` odmítá `null` vstupní hodnoty, a proto se tato zpráva nabídne `operationCancelled`. Blok toku dat `operationCancelled` přijímá všechny zprávy, a proto zobrazí obrázek, který označuje, že operace byla zrušena.  
  
 Následující ilustrace znázorňuje síť pro zpracování imagí:  
  
 ![Obrázek znázorňující síť pro zpracování obrázků.](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 Vzhledem k tomu, že bloky toku dat `displayCompositeBitmap` a `operationCancelled` fungují na uživatelském rozhraní, je důležité, aby tyto akce probíhaly ve vlákně uživatelského rozhraní. Aby to bylo možné provést během konstrukce, poskytují tyto objekty objekt <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>, který má vlastnost <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> nastavena na hodnotu <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> vytvoří objekt <xref:System.Threading.Tasks.TaskScheduler>, který provádí práci na aktuálním kontextu synchronizace. Vzhledem k tomu, že metoda `CreateImageProcessingNetwork` je volána z obslužné rutiny tlačítka **Zvolit složku** , která je spuštěna v vlákně uživatelského rozhraní, jsou také v vláknu uživatelského rozhraní spouštěny i akce bloků toku dat `displayCompositeBitmap` a `operationCancelled`.  
  
 V tomto příkladu se používá sdílený token zrušení namísto nastavení vlastnosti <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>, protože vlastnost <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> trvale zruší provádění bloku toku dat. Token zrušení umožňuje v tomto příkladu znovu použít stejnou síť toku dat, a to i v případě, že uživatel zruší jednu nebo více operací. Příklad, který používá <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> k trvalému zrušení provádění bloku toku dat, naleznete v tématu [How to: Canceling The Dataflow Block](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Propojení sítě toku dat s uživatelským rozhraním  
 Tato část popisuje, jak propojit síť toku dat s uživatelským rozhraním. Vytváření složené image a zrušení operace se spouští z tlačítek **Zvolit složku** a **Zrušit** . Když uživatel zvolí některé z těchto tlačítek, je vhodná akce iniciována asynchronním způsobem.  
  
### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Připojení sítě toku dat k uživatelskému rozhraní  
  
1. V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.ToolStripItem.Click> pro tlačítko **Vybrat složku** .  
  
2. Implementujte událost <xref:System.Windows.Forms.ToolStripItem.Click> pro tlačítko **Vybrat složku** .  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3. V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.ToolStripItem.Click> pro tlačítko **Storno** .  
  
4. Implementujte událost <xref:System.Windows.Forms.ToolStripItem.Click> pro tlačítko **Storno** .  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní kód pro tento návod.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Následující ilustrace znázorňuje typický výstup pro běžné složky \Samples \ obrázky \.  
  
 ![Aplikace model Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
