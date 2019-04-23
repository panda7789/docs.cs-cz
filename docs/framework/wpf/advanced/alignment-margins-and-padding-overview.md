---
title: Přehled zarovnání, okrajů a odsazení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- margins [WPF]
- padding [WPF]
- aligning [WPF]
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
ms.openlocfilehash: 58af8848a6b8a5e4ded453831f5a7ef985548492
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209161"
---
# <a name="alignment-margins-and-padding-overview"></a>Přehled zarovnání, okrajů a odsazení
<xref:System.Windows.FrameworkElement> Třída zveřejňuje několik vlastností, které se používají k přesné umístění podřízených elementů. Toto téma popisuje čtyři z nejdůležitějších vlastností: <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>. Účinek z těchto vlastností je důležité pochopit, protože poskytují základ pro řízení umístění prvků v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací.  

<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>Úvod do umístění elementu  
 Existuje mnoho způsobů, pokud chcete umístit prvky pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Nicméně dosažení ideální rozložení přesahuje jednoduše Volba správného <xref:System.Windows.Controls.Panel> elementu. Přesné řízení umístění nutné znalosti toho, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnosti.  
  
 Následující obrázek znázorňuje rozložení scénáře, který využívá několik vlastností umístění.  
  
 ![WPF umístění vlastnosti vzorku](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 Na první pohled <xref:System.Windows.Controls.Button> může zdát, že prvky na tomto obrázku umístit náhodně. Pozice jsou ale ve skutečnosti přesně řídit ho jde pomocí kombinace okrajů, zarovnání a odsazení.  
  
 Následující příklad popisuje, jak vytvořit rozložení v předchozí ilustraci. A <xref:System.Windows.Controls.Border> zapouzdřuje nadřazený element <xref:System.Windows.Controls.StackPanel>, s <xref:System.Windows.Controls.Border.Padding%2A> hodnotu pixelech nezávislých na 15 zařízení. To účty pro úzký <xref:System.Windows.Media.Brushes.LightBlue%2A> pruh, který obklopuje podřízené <xref:System.Windows.Controls.StackPanel>. Podřízené prvky <xref:System.Windows.Controls.StackPanel> se používají pro ilustraci různých umístění vlastnosti, které jsou popsané v tomto tématu. Tři <xref:System.Windows.Controls.Button> elementy se používají k předvedení jak <xref:System.Windows.FrameworkElement.Margin%2A> a <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnosti.  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Následující diagram představuje prohlédnout různé vlastnosti umístění, které se používají v předchozím příkladu. Následující části v tomto tématu podrobněji popisují způsob použití každou vlastnost umístění.  
  
 ![Vlastnosti umístění s volání obrazovky&#45;výpisů](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>Principy vlastnosti zarovnání  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnosti popisují, jak podřízený element by měl být umístěn v rámci nadřazeného elementu přidělené rozložení adresního prostoru. Pomocí těchto vlastností společně, můžete přesně umísťovat podřízené prvky. Například podřízené prvky <xref:System.Windows.Controls.DockPanel> můžete zadat čtyři různé vodorovné zarovnání: <xref:System.Windows.HorizontalAlignment.Left>, <xref:System.Windows.HorizontalAlignment.Right>, nebo <xref:System.Windows.HorizontalAlignment.Center>, nebo <xref:System.Windows.HorizontalAlignment.Stretch> tak, aby vyplnil dostupné místo. Podobně jako hodnoty jsou k dispozici pro svislé umístění.  
  
> [!NOTE]
>  Explicitně sady <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti v elementu přednost před <xref:System.Windows.HorizontalAlignment.Stretch> hodnotu vlastnosti. Pokus o nastavení <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>a <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> hodnotu `Stretch` vede `Stretch` žádostí bude ignorována.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>HorizontalAlignment – vlastnost  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Vlastnost deklaruje vlastnosti vodorovného zarovnání, které chcete použít pro podřízené prvky. V následující tabulce jsou uvedeny všech možných hodnot <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Podřízené prvky je zarovnán nalevo od místo přidělené rozložení nadřazeného elementu.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Podřízené prvky je zarovnán do centra pro místo přidělené rozložení nadřazeného elementu.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Podřízené prvky jsou zarovnaná vpravo od nadřazeného elementu místo přidělené rozložení.|  
|<xref:System.Windows.HorizontalAlignment.Stretch> (Výchozí)|Podřízené prvky jsou roztažený tak, aby vyplnil místo přidělené rozložení nadřazeného elementu. Explicitní <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> hodnoty přednost.|  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost <xref:System.Windows.Controls.Button> elementy. Každá hodnota atributu se zobrazí, abychom vám lépe předvedli různé chování vykreslování.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Předchozí kód provede rozložení podobně jako na následujícím obrázku. Umístění účinky jednotlivých <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> hodnota jsou viditelné na obrázku.  
  
 ![Ukázka HorizontalAlignment](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>VerticalAlignment – vlastnost  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> Vlastnost popisuje charakteristiky svislého zarovnání, které chcete použít pro podřízené prvky. V následující tabulce jsou uvedeny všechny možné hodnoty pro <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnost.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Podřízené prvky jsou zarovnány k hornímu okraji nadřazeného elementu místo přidělené rozložení.|  
|<xref:System.Windows.VerticalAlignment.Center>|Podřízené prvky je zarovnán do centra pro místo přidělené rozložení nadřazeného elementu.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Podřízené prvky jsou zarovnány k dolnímu okraji nadřazeného elementu místo přidělené rozložení.|  
|<xref:System.Windows.VerticalAlignment.Stretch> (Výchozí)|Podřízené prvky jsou roztažený tak, aby vyplnil místo přidělené rozložení nadřazeného elementu. Explicitní <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> hodnoty přednost.|  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnost <xref:System.Windows.Controls.Button> elementy. Každá hodnota atributu se zobrazí, abychom vám lépe předvedli různé chování vykreslování. Pro účely tohoto příkladu <xref:System.Windows.Controls.Grid> element s viditelné Mřížka slouží jako nadřazenou třídou, abychom vám lépe předvedli rozložení chování všechny hodnoty vlastností.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Předchozí kód provede rozložení podobně jako na následujícím obrázku. Umístění účinky jednotlivých <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> hodnota jsou viditelné na obrázku.  
  
 ![Vlastnost VerticalAlignment – ukázka](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>Principy vlastnosti okraj  
 <xref:System.Windows.FrameworkElement.Margin%2A> Vlastnost popisuje vzdálenost mezi prvek a jeho podřízené nebo partnerské uzly. <xref:System.Windows.FrameworkElement.Margin%2A> hodnoty mohou být jednotné, pomocí syntaxe jako `Margin="20"`. Pomocí této syntaxe jednotné <xref:System.Windows.FrameworkElement.Margin%2A> 20 zařízení nezávislých na pixelech se použijí pro úhradu elementu. <xref:System.Windows.FrameworkElement.Margin%2A> hodnoty můžete také využít formuláře čtyři různé hodnoty, každá hodnota popisující různé okraj vyrovnat vlevo nahoře, vpravo a dole (v uvedeném pořadí), jako je `Margin="0,10,5,25"`. Pro účely řádné využívání <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost umožní velice přesné řízení pozici vykreslení elementu a pozici vykreslení jeho prvků sousední a podřízené položky.  
  
> [!NOTE]
>  Okraj nenulové použije místo vně elementu <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A>.  
  
 Následující příklad ukazuje, jak použít jednotné okraje kolem skupiny <xref:System.Windows.Controls.Button> elementy. <xref:System.Windows.Controls.Button> Prvky jsou rovnoměrně s vyrovnávací pamětí okraj deset pixel v každém směru.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 V mnoha případech není vhodné jednotné okraj. V těchto případech je možné použít nerovnoměrné mezery. Následující příklad ukazuje, jak použít nerovnoměrné okraj mezery pro podřízené prvky. Okraje jsou popsané v tomto pořadí: levý, horní, klikněte pravým tlačítkem myši, bottom.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## <a name="understanding-the-padding-property"></a>Principy vlastnost odsazení  
 Odsazení se podobá <xref:System.Windows.FrameworkElement.Margin%2A> ve většině ohledech. Vlastnost Padding zpřístupněn na jenom na několik tříd, především pro potřeby: <xref:System.Windows.Documents.Block>, <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Control>, a <xref:System.Windows.Controls.TextBlock> příklady tříd, které zprostředkovávají vlastnost Padding. <xref:System.Windows.Controls.Border.Padding%2A> Vlastnost zvětší efektivní velikost podřízeného elementu zadaný <xref:System.Windows.Thickness> hodnotu.  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Controls.Border.Padding%2A> s nadřazenou položkou <xref:System.Windows.Controls.Border> elementu.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Použití zarovnání, okrajů a odsazení v aplikaci  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> zadejte umístění ovládacího prvku potřebné k vytvoření komplexní [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Účinky jednotlivých vlastností můžete změnit podřízený element umístění a poskytuje flexibilitu při vytváření dynamických aplikací a uživatelů.  
  
 Následující příklad ukazuje, každý s koncepty, které jsou popsané v tomto tématu. Staví na infrastrukturou v první příklad v tomto tématu, v tomto příkladu přidá <xref:System.Windows.Controls.Grid> element jako podřízený objekt <xref:System.Windows.Controls.Border> v první ukázce. <xref:System.Windows.Controls.Border.Padding%2A> platí pro nadřazený <xref:System.Windows.Controls.Border> elementu. <xref:System.Windows.Controls.Grid> Se používá k rozdělení prostoru mezi tří podřízených <xref:System.Windows.Controls.StackPanel> elementy. <xref:System.Windows.Controls.Button> prvky jsou znovu použity k zobrazit různé účinky <xref:System.Windows.FrameworkElement.Margin%2A> a <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>. <xref:System.Windows.Controls.TextBlock> prvky jsou přidány do každé <xref:System.Windows.Controls.ColumnDefinition> a lépe tak definovat různé vlastnosti u <xref:System.Windows.Controls.Button> prvky v jednotlivých sloupcích.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Při kompilaci, výsledkem předchozí žádosti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vypadá podobně jako na následujícím obrázku. Účinek různých hodnot vlastností je zřejmé ve mezery mezi elementy a hodnoty vlastností významné prvků v každém sloupci jsou uvedeny v rámci <xref:System.Windows.Controls.TextBlock> elementy.  
  
 ![Několik vlastností umístění v jedné aplikaci](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>Co se chystá  
 Vlastnosti určené umístění <xref:System.Windows.FrameworkElement> třídy povolení přesné řízení umístění prvku v rámci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací. Teď máte několik technik, které vám umožní lépe umístění elementů pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Jsou k dispozici další prostředky, které popisují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení podrobněji. [Přehled panelů](../controls/panels-overview.md) téma obsahuje další podrobnosti o jednotlivých <xref:System.Windows.Controls.Panel> elementy. Téma [názorný postup: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md) přináší pokročilé techniky, které používají pro nastavení pozice komponenty a jejich akce svázat zdroje dat elementů rozložení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Přehled panelu](../controls/panels-overview.md)
- [Rozložení](layout.md)
- [Ukázky WPF rozložení galerie](https://go.microsoft.com/fwlink/?LinkID=160054)
