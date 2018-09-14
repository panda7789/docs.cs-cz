---
title: Shromáždění rukopisu v aplikacích WPF
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
ms.openlocfilehash: 25f9c0141a97d8e52e0883b14fd3e1f4574a05ea
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527721"
---
# <a name="collect-ink"></a>Shromáždění inkoustu

[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platformy shromažďuje digitálních inkoust jeho funkce v rámci jádra. Toto téma popisuje metody pro kolekci rukopis ve Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Požadavky

Pokud chcete použít v následujících příkladech, je třeba nejprve nainstalovat Visual Studio a [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Musíte taky vědět, jak pro psaní aplikací pro WPF. Další informace o zahájení práce s WPF naleznete v tématu [návod: Moje první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="use-the-inkcanvas-element"></a>Použít inkcanvas – Element

<xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> Element poskytuje nejjednodušší způsob, jak shromažďovat rukopisu v subsystému WPF. Použití <xref:System.Windows.Controls.InkCanvas> – element pro příjem a zobrazení vstupu rukopisu. Běžně vstupu inkoustu pomocí pera, která komunikuje s digitizéru k vytvoření inkoustových tahů. Kromě toho je možné místo stylus myši. Vytvořený tahy jsou reprezentovány ve formě <xref:System.Windows.Ink.Stroke> objekty a jejich lze ovládat jak prostřednictvím kódu programu a uživatelem vstup. <xref:System.Windows.Controls.InkCanvas> Umožňuje uživatelům vybrat, upravit nebo odstranit existující <xref:System.Windows.Ink.Stroke>.

Pomocí XAML můžete nastavit kolekce inkoustů stejně snadno, jako přidávání **InkCanvas** element vaše stromové struktury. Následující příklad přidá <xref:System.Windows.Controls.InkCanvas> do projektu WPF výchozí vytvořeného v sadě Visual Studio:

[!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

**InkCanvas** element může také obsahovat podřízené prvky, což umožňuje přidat poznámky funkce inkoustu na téměř libovolný typ elementu XAML. Například pro přidání možností rukopisu do textu elementu, stačí udělat podřízeným z <xref:System.Windows.Controls.InkCanvas>:

[!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

Přidání podpory pro označení image s rukopisem je stejně jednoduché:

[!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a>Režimy InkCollection

<xref:System.Windows.Controls.InkCanvas> Poskytuje podporu pro různé vstupní režimy prostřednictvím jeho <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> vlastnost.

### <a name="manipulate-ink"></a>Zpracování inkoustu

<xref:System.Windows.Controls.InkCanvas> Poskytuje podporu pro mnoho inkoustu operace úprav. Například <xref:System.Windows.Controls.InkCanvas> vymazat podporuje back sady pera a bez dalšího kódu, je potřeba přidat funkce do elementu.

#### <a name="selection"></a>Výběr

Nastavení režimu výběru je stejně jednoduché jako nastavení <xref:System.Windows.Controls.InkCanvasEditingMode> vlastnost **vyberte**.

Následující kód nastaví režim úprav podle hodnoty <xref:System.Windows.Forms.CheckBox>:

[!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a>DrawingAttributes

Použití <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> vlastnost změnit vzhled inkoustových tahů. Například <xref:System.Windows.Ink.DrawingAttributes.Color%2A> členem <xref:System.Windows.Ink.DrawingAttributes> nastavuje barvu vygenerované <xref:System.Windows.Ink.Stroke>.

Následující příklad změní barvu vybraných tahů na červený:

[!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes

<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> Poskytuje přístup k vlastnosti, jako je výšku, šířku a barvu tahů bude vytvořena ve vlastnosti <xref:System.Windows.Controls.InkCanvas>. Po změně <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, všechny budoucí tahy do <xref:System.Windows.Controls.InkCanvas> jsou generovány s novými hodnotami vlastností.

Spolu s prováděním změn <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> v souboru kódu na pozadí, můžete použít syntaxe XAML pro určení <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> vlastnosti.

Následující příklad ukazuje, jak nastavit <xref:System.Windows.Ink.DrawingAttributes.Color%2A> vlastnost. Chcete-li tento kód použít, vytvořte nový projekt WPF s názvem "HelloInkCanvas" v sadě Visual Studio. Nahraďte kód v *souboru MainWindow.xaml* souboru následujícím kódem:

[!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

Pak přidejte do souboru uvnitř třídy hlavního okna MainWindow kódu obslužné rutiny událostí následující tlačítka:

[!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

Po zkopírování tento kód, stiskněte klávesu **F5** v sadě Visual Studio ke spuštění programu v ladicím programu.

Všimněte si, že jak <xref:System.Windows.Controls.StackPanel> umístí tlačítka v horní části <xref:System.Windows.Controls.InkCanvas>. Pokud se pokusíte rukopisu v horní části na tlačítka, <xref:System.Windows.Controls.InkCanvas> shromažďuje a vykreslí rukopis za tlačítka. Důvodem je, že tlačítka jsou na stejné úrovni <xref:System.Windows.Controls.InkCanvas> na rozdíl od podřízené položky. Tlačítka jsou také, výše v pořadí vykreslování, takže se vykreslí rukopis za nimi stojí.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>