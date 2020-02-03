---
title: Shromažďovat digitální inkoust
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
ms.openlocfilehash: 813a5313a6fbf83c36cdbed1f64ce69a217ad788
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747023"
---
# <a name="collect-ink"></a>Shromáždit rukopis

Platforma [Windows Presentation Foundation](../index.md) shromažďuje digitální inkoust jako základní součást jeho funkcí. Toto téma popisuje metody pro kolekci rukopisu v Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Předpoklady

Chcete-li použít následující příklady, je nutné nejprve nainstalovat aplikaci Visual Studio a Windows SDK. Měli byste také pochopit, jak psát aplikace pro WPF. Další informace o tom, jak začít používat WPF, najdete v tématu [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="use-the-inkcanvas-element"></a>Použití elementu InkCanvas

Element <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> poskytuje nejjednodušší způsob, jak v WPF shromažďovat rukopis. Použijte prvek <xref:System.Windows.Controls.InkCanvas> pro příjem a zobrazení vstupu rukopisu. Obvykle zadáváte inkoust pomocí stylusu, který komunikuje s digitizérem, aby vytvořil tahy perem. Kromě toho lze použít myš místo stylusu. Vytvořené tahy jsou reprezentovány jako <xref:System.Windows.Ink.Stroke> objekty a lze je manipulovat programově i uživatelským vstupem. <xref:System.Windows.Controls.InkCanvas> umožňuje uživatelům vybrat, upravit nebo odstranit existující <xref:System.Windows.Ink.Stroke>.

Pomocí jazyka XAML můžete nastavit kolekci rukopisu jako snadnou přidáním prvku **InkCanvas** do stromu. Následující příklad přidá <xref:System.Windows.Controls.InkCanvas> do výchozího projektu WPF vytvořeného v aplikaci Visual Studio:

[!code-xaml[DigitalInkTopics#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

Element **InkCanvas** může také obsahovat podřízené prvky, což umožňuje přidat možnosti rukopisné poznámky pro téměř jakýkoli typ elementu XAML. Chcete-li například přidat možnosti psaní do textového prvku, stačí vytvořit podřízený objekt <xref:System.Windows.Controls.InkCanvas>:

[!code-xaml[DigitalInkTopics#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

Přidání podpory pro označení obrázku pomocí rukopisu je stejně snadné:

[!code-xaml[DigitalInkTopics#7](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a>InkCollection režimy

<xref:System.Windows.Controls.InkCanvas> poskytuje podporu pro různé vstupní režimy prostřednictvím její vlastnosti <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>.

### <a name="manipulate-ink"></a>Manipulace s inkoustem

<xref:System.Windows.Controls.InkCanvas> poskytuje podporu pro mnoho operací úpravy rukopisu. Například <xref:System.Windows.Controls.InkCanvas> podporuje mazání zezadu a k přidání funkce do prvku není potřeba žádný další kód.

#### <a name="selection"></a>Výběr

Nastavení režimu výběru je jednoduché, protože nastavení vlastnosti <xref:System.Windows.Controls.InkCanvasEditingMode> na hodnotu **Vybrat**.

Následující kód nastaví režim úprav na základě hodnoty <xref:System.Windows.Forms.CheckBox>:

[!code-csharp[DigitalInkTopics#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a>DrawingAttributes

Chcete-li změnit vzhled tahů perem, použijte vlastnost <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>. Například člen <xref:System.Windows.Ink.DrawingAttributes.Color%2A> <xref:System.Windows.Ink.DrawingAttributes> nastavuje barvu vykresleného <xref:System.Windows.Ink.Stroke>.

Následující příklad změní barvu vybraných tahů na červenou:

[!code-csharp[DigitalInkTopics#9](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes

Vlastnost <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> poskytuje přístup k vlastnostem, jako je výška, Šířka a barva tahů, které mají být vytvořeny v <xref:System.Windows.Controls.InkCanvas>. Po změně <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>jsou všechny budoucí tahy zadané do <xref:System.Windows.Controls.InkCanvas> vykresleny s novými hodnotami vlastností.

Kromě změny <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> v souboru kódu na pozadí lze použít syntaxi XAML pro určení <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>ch vlastností.

Další příklad ukazuje, jak nastavit vlastnost <xref:System.Windows.Ink.DrawingAttributes.Color%2A>. Chcete-li použít tento kód, vytvořte nový projekt WPF nazvaný "HelloInkCanvas" v aplikaci Visual Studio. Nahraďte kód v souboru *MainWindow. XAML* následujícím kódem:

[!code-xaml[HelloInkCanvas#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

Dále přidejte následující obslužné rutiny událostí tlačítka do souboru kódu na pozadí uvnitř třídy MainWindow:

[!code-csharp[HelloInkCanvas#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

Po zkopírování tohoto kódu stiskněte klávesu **F5** v aplikaci Visual Studio a spusťte program v ladicím programu.

Všimněte si, jak <xref:System.Windows.Controls.StackPanel> umístí tlačítka nad <xref:System.Windows.Controls.InkCanvas>. Pokud se pokusíte použít rukopis v horní části tlačítek, <xref:System.Windows.Controls.InkCanvas> shromažďuje a vykresluje rukopis za tlačítky. Důvodem je to, že tlačítka jsou na stejné <xref:System.Windows.Controls.InkCanvas> na rozdíl od podřízených. Tlačítka jsou také vyšší v pořadí vykreslování, takže rukopis je vykreslen za sebou.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>
