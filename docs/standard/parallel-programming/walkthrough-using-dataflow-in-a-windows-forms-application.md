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
ms.openlocfilehash: 4dc433b83fd086a1e3e165a85b6bfe64b781f45b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666340"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>Návod: Použití toku dat ve formulářové aplikaci Windows
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
  
1. V aplikaci Visual Studio vytvořte projekt aplikace C# visual nebo Visual Basic **model Windows Forms** . V tomto dokumentu se projekt jmenuje `CompositeImages`.  
  
2. V návrháři formuláře pro hlavní formulář Form1.cs (Form1. vb pro Visual Basic) přidejte <xref:System.Windows.Forms.ToolStrip> ovládací prvek.  
  
3. Přidejte ovládací prvek <xref:System.Windows.Forms.ToolStrip> do ovládacího prvku. <xref:System.Windows.Forms.ToolStripButton> Nastavte vlastnost na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> a<xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost na **Zvolit složku.** <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>  
  
4. <xref:System.Windows.Forms.ToolStripButton> Přidejte<xref:System.Windows.Forms.ToolStrip> k ovládacímu prvku druhý ovládací prvek. `False` <xref:System.Windows.Forms.ToolStripItem.Enabled%2A>Nastavte vlastnost na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>vlastnost, <xref:System.Windows.Forms.ToolStripItem.Text%2A> kterou chcete zrušit, a vlastnost na hodnotu. <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>  
  
5. <xref:System.Windows.Forms.PictureBox> Přidejte objekt do hlavního formuláře. Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>Vytváření sítě toku dat  
 Tato část popisuje, jak vytvořit síť toku dat, která provádí zpracování bitové kopie.  
  
### <a name="to-create-the-dataflow-network"></a>Vytvoření sítě toku dat  
  
1. Do projektu přidejte odkaz na System. Threading. Tasks. Dataflow. dll.  
  
2. Ujistěte se, že Form1.cs (Form1. vb pro Visual Basic) obsahuje `using` následující`Using` příkazy (v Visual Basic):  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3. Do `Form1` třídy přidejte následující datové členy:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4. Přidejte následující metodu `CreateImageProcessingNetwork` `Form1` do třídy. Tato metoda vytvoří síť pro zpracování imagí.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5. Implementujte `LoadBitmaps` metodu.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6. Implementujte `CreateCompositeBitmap` metodu.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  C# Verze`CreateCompositeBitmap` metody používá ukazatele k umožnění <xref:System.Drawing.Bitmap?displayProperty=nameWithType> efektivního zpracování objektů. Proto je nutné povolit možnost **Povolit nezabezpečený kód** v projektu, aby bylo možné použít klíčové [](../../csharp/language-reference/keywords/unsafe.md) slovo unsafe. Další informace o tom, jak povolit nezabezpečený kód ve C# vizuálním projektu, naleznete na [stránce sestavení,C#Návrhář projektu ()](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
 V následující tabulce jsou popsány členové sítě.  
  
|Člen|type|Popis|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Převezme cestu ke složce jako vstup a vytvoří kolekci <xref:System.Drawing.Bitmap> objektů jako výstup.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Převezme kolekci <xref:System.Drawing.Bitmap> objektů jako vstup a vytvoří složený rastrový obrázek jako výstup.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zobrazí složený rastrový obrázek ve formuláři.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zobrazí obrázek, který indikuje, že operace je zrušená a umožňuje uživateli vybrat jinou složku.|  
  
 Chcete-li připojit bloky toku dat pro vytvoření sítě, v tomto příkladu je <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> použita metoda. Metoda obsahuje přetíženou verzi, která <xref:System.Predicate%601> přebírá objekt, který určuje, zda cílový blok přijímá nebo odmítá zprávu. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Tento mechanismus filtrování umožňuje blokům zpráv přijímat pouze určité hodnoty. V tomto příkladu může síť větvit jedním ze dvou způsobů. Hlavní větev načte obrázky z disku, vytvoří složený obrázek a zobrazí tento obrázek ve formuláři. Alternativní větev zruší aktuální operaci. <xref:System.Predicate%601> Objekty umožňují, aby tok dat v rámci hlavní větve přepnul na alternativní větev tím, že odmítne určité zprávy. Například pokud uživatel operaci zruší, vytvoří `createCompositeBitmap` `null` blok toku dat (`Nothing` v Visual Basic) jako svůj výstup. Blok `displayCompositeBitmap` toku dat `null` odmítne vstupní hodnoty `operationCancelled`. proto je zpráva nabízena. Blok `operationCancelled` toku dat akceptuje všechny zprávy, a proto zobrazí obrázek, který označuje, že operace byla zrušena.  
  
 Následující ilustrace znázorňuje síť pro zpracování imagí:  
  
 ![Obrázek znázorňující síť pro zpracování obrázků.](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 Vzhledem k `displayCompositeBitmap` tomu `operationCancelled` , že bloky a tok dat fungují na uživatelském rozhraní, je důležité, aby tyto akce probíhaly ve vlákně uživatelského rozhraní. Aby to <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>bylo možné provést během konstrukce, poskytují tyto objekty objekt, který má vlastnostnastavenouna.<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda<xref:System.Threading.Tasks.TaskScheduler> vytvoří objekt, který provádí práci na aktuálním kontextu synchronizace. Vzhledem k tomu, že `displayCompositeBitmap` `operationCancelled` Metodajevolánazobslužnérutinytlačítkazvolitsložku,kterájespuštěnavvlákněuživatelskéhorozhraní,jsouakceproblokyablokytokudattakéspouštěny`CreateImageProcessingNetwork` ve vlákně uživatelského rozhraní.  
  
 Tento příklad používá sdílený token zrušení namísto nastavení <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> vlastnosti, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> protože vlastnost trvale zruší provádění bloku toku dat. Token zrušení umožňuje v tomto příkladu znovu použít stejnou síť toku dat, a to i v případě, že uživatel zruší jednu nebo více operací. Příklad, který používá <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> k trvalému zrušení provádění bloku toku dat, naleznete v tématu [How to: Zruší blok](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)toku dat.  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Propojení sítě toku dat s uživatelským rozhraním  
 Tato část popisuje, jak propojit síť toku dat s uživatelským rozhraním. Vytváření složené image a zrušení operace se spouští z tlačítek **Zvolit složku** a **Zrušit** . Když uživatel zvolí některé z těchto tlačítek, je vhodná akce iniciována asynchronním způsobem.  
  
### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Připojení sítě toku dat k uživatelskému rozhraní  
  
1. V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> událost pro tlačítko **Vybrat složku** .  
  
2. Implementujte událost pro tlačítko **Vybrat složku.** <xref:System.Windows.Forms.ToolStripItem.Click>  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3. V návrháři formuláře pro hlavní formulář vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> událost tlačítka **Storno** .  
  
4. Implementujte událost pro tlačítko **Storno.** <xref:System.Windows.Forms.ToolStripItem.Click>  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní kód pro tento návod.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Následující ilustrace znázorňuje typický výstup pro běžné složky \Samples \ obrázky \.  
  
 ![Aplikace model Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
