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
ms.openlocfilehash: 70eff35db638c5bfbc9c164dc381e3f58e18957b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541249"
---
# <a name="alignment-margins-and-padding-overview"></a>Přehled zarovnání, okrajů a odsazení
<xref:System.Windows.FrameworkElement> Třída poskytuje několik vlastností, které se používají k přesné umístění podřízené elementy. Toto téma popisuje čtyři nejdůležitější vlastnosti: <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>. Účinky tyto vlastnosti jsou důležité si uvědomit, protože poskytují základ pro řízení pozici prvků v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace.  
  
  
<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>Úvod do umístění – Element  
 Existuje mnoho způsobů na pozici elementů pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ale dosažení ideální rozložení překročí jednoduše výběr správné <xref:System.Windows.Controls.Panel> elementu. Přesného umístění vyžaduje pochopení <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnosti.  
  
 Následující obrázek znázorňuje rozložení scénáře, který využívá několik vlastností umístění.  
  
 ![WPF umístění vlastnosti vzorku](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 Na první pohled <xref:System.Windows.Controls.Button> prvky v tomto obrázku může objeví náhodně umístit. Jejich polohu jsou ve skutečnosti přesněji řídit pomocí kombinace okraje, odsazení a zarovnání.  
  
 Následující příklad popisuje postup vytvoření rozložení na předchozím obrázku. A <xref:System.Windows.Controls.Border> zapouzdří nadřazený element <xref:System.Windows.Controls.StackPanel>, s <xref:System.Windows.Controls.Border.Padding%2A> hodnotou 15 nezávislé pixelů zařízení. To účty pro úzké <xref:System.Windows.Media.Brushes.LightBlue%2A> vzdálené správy, která obklopuje podřízená <xref:System.Windows.Controls.StackPanel>. Podřízených elementů <xref:System.Windows.Controls.StackPanel> se používají ke znázornění každý z různých umísťovací vlastnosti, které jsou popsané v tomto tématu. Tři <xref:System.Windows.Controls.Button> elementy slouží k předvedení i <xref:System.Windows.FrameworkElement.Margin%2A> a <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnosti.  
  
 [!code-csharp[MPALayoutSampleIntro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Následující diagram představuje prohlédnout různé umísťovací vlastnosti, které se používají v předchozím příkladu. Následující části tohoto tématu podrobněji popisují způsob použití každou umísťovací vlastnost.  
  
 ![Vlastnosti umístění s obrazovky volání&#45;výpisů](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>Principy vlastnosti zarovnání  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnosti popisují, jak podřízeným prvkem má být umístěn v rámci nadřazeného elementu rozložení přidělené místo. Pomocí společně tyto vlastnosti, můžete přesně umístit podřízené elementy. Například podřízených elementů <xref:System.Windows.Controls.DockPanel> můžete zadat čtyři různé vodorovné zarovnání: <xref:System.Windows.HorizontalAlignment.Left>, <xref:System.Windows.HorizontalAlignment.Right>, nebo <xref:System.Windows.HorizontalAlignment.Center>, nebo <xref:System.Windows.HorizontalAlignment.Stretch> k vyplnění volné místo. Podobně jako hodnoty jsou k dispozici pro svislé umístění.  
  
> [!NOTE]
>  Explicitně set <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti u elementu, mají přednost před <xref:System.Windows.HorizontalAlignment.Stretch> hodnotu vlastnosti. Probíhá pokus o nastavení <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>a <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> hodnotu `Stretch` výsledkem `Stretch` požadavku bude ignorována.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>HorizontalAlignment – vlastnost  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Vlastnost deklaruje charakteristiky vodorovné zarovnání chcete použít pro podřízené elementy. Následující tabulka znázorňuje všechny možné hodnoty <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Podřízené elementy je zarovnán nalevo od místo přidělené rozložení nadřazeného elementu.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Podřízené elementy je zarovnán do centra místo přidělené rozložení nadřazeného elementu.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Podřízené elementy je zarovnán napravo od místo přidělené rozložení nadřazeného elementu.|  
|<xref:System.Windows.HorizontalAlignment.Stretch> (Výchozí)|Podřízené elementy jsou roztažen tak, aby vyplnění místo přidělené rozložení nadřazeného elementu. Explicitní <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> hodnoty mají přednost před.|  
  
 Následující příklad ukazuje, jak se má použít <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost <xref:System.Windows.Controls.Button> elementy. Každá hodnota atributu se zobrazí, abychom vám lépe předvedli různé chování vykreslování.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Předchozí kód vypočítá rozložení podobně jako na následujícím obrázku. Umísťovací důsledky jednotlivých <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> hodnota jsou viditelné na obrázku.  
  
 ![HorizontalAlignment – ukázka](../../../../docs/framework/wpf/advanced/media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>VerticalAlignment – vlastnost  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> Vlastnost popisuje vlastnosti svislé zarovnání chcete použít pro podřízené elementy. Následující tabulka znázorňuje všechny možné hodnoty <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnost.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Podřízené elementy je zarovnán do horní části místo přidělené rozložení nadřazeného elementu.|  
|<xref:System.Windows.VerticalAlignment.Center>|Podřízené elementy je zarovnán do centra místo přidělené rozložení nadřazeného elementu.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Podřízené elementy je zarovnán do dolní části místo přidělené rozložení nadřazeného elementu.|  
|<xref:System.Windows.VerticalAlignment.Stretch> (Výchozí)|Podřízené elementy jsou roztažen tak, aby vyplnění místo přidělené rozložení nadřazeného elementu. Explicitní <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> hodnoty mají přednost před.|  
  
 Následující příklad ukazuje, jak se má použít <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnost <xref:System.Windows.Controls.Button> elementy. Každá hodnota atributu se zobrazí, abychom vám lépe předvedli různé chování vykreslování. Pro účely tohoto příkladu <xref:System.Windows.Controls.Grid> element s viditelné mřížky slouží jako nadřazená položka, abychom vám lépe předvedli rozložení chování všechny hodnoty vlastností.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Předchozí kód vypočítá rozložení podobně jako na následujícím obrázku. Umísťovací důsledky jednotlivých <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> hodnota jsou viditelné na obrázku.  
  
 ![Vlastnost VerticalAlignment – ukázka](../../../../docs/framework/wpf/advanced/media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>Principy vlastnosti okraje  
 <xref:System.Windows.FrameworkElement.Margin%2A> Vlastnost popisuje vzdálenost mezi elementu a jeho podřízené domény nebo partnerské uzly. <xref:System.Windows.FrameworkElement.Margin%2A> hodnoty mohou být uniform, pomocí syntaxe jako `Margin="20"`. Pomocí této syntaxe uniform <xref:System.Windows.FrameworkElement.Margin%2A> 20 zařízení by bylo možné provést nezávislé pixelů do elementu. <xref:System.Windows.FrameworkElement.Margin%2A> hodnoty můžete také mít formu čtyři odlišné hodnoty, každá hodnota popisující odlišné okraj použít na levé straně, horní, pravé a dolní (v tomto pořadí), jako je `Margin="0,10,5,25"`. Řádné užívání <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost umožňuje velmi dobře kontrolu umístění prvků vykreslování a vykreslování pozici jeho sousedním elementy a podřízené položky.  
  
> [!NOTE]
>  Nulová okraj platí místa mimo elementu <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A>.  
  
 Následující příklad ukazuje, jak se má použít uniform okraje kolem skupiny <xref:System.Windows.Controls.Button> elementy. <xref:System.Windows.Controls.Button> Elementy jsou rovnoměrně rozmístěny s deset pixelů okraj vyrovnávací paměť v každém směru.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 V mnoha případech není vhodná uniform okraj. V těchto případech můžete použít neuniformní mezery. Následující příklad ukazuje, jak chcete použít pro podřízené elementy neuniformní okraj mezery. Okraje jsou popsané v tomto pořadí: vlevo, top, pravým, dolů.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## <a name="understanding-the-padding-property"></a>Principy vlastnost odsazení  
 Odsazení je podobná <xref:System.Windows.FrameworkElement.Margin%2A> ve většině ohledech. Vlastnost odsazení je vystaven na pouze na několik tříd, především pro potřeby: <xref:System.Windows.Documents.Block>, <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Control>, a <xref:System.Windows.Controls.TextBlock> jsou ukázky třídy, které vystavují vlastnost odsazení. <xref:System.Windows.Controls.Border.Padding%2A> Vlastnost zvětší efektivní velikost podřízený element zadaný <xref:System.Windows.Thickness> hodnotu.  
  
 Následující příklad ukazuje, jak se má použít <xref:System.Windows.Controls.Border.Padding%2A> s nadřazenou položkou <xref:System.Windows.Controls.Border> elementu.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Pomocí zarovnání, okraje a odsazení v aplikaci  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> poskytovat potřebné k vytvoření komplexní ovládacího prvku umísťovací [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Chcete-li změnit podřízený element umístění, povolení flexibilitu při vytváření dynamických aplikací a koncových uživatelů můžete důsledky každou vlastnost.  
  
 Následující příklad ukazuje všechny koncepty, které jsou popsané v tomto tématu. Tento příklad vychází infrastruktury nalezena v prvním vzorku v tomto tématu, přidá <xref:System.Windows.Controls.Grid> jako podřízený element <xref:System.Windows.Controls.Border> v prvním vzorku. <xref:System.Windows.Controls.Border.Padding%2A> platí pro nadřazenou <xref:System.Windows.Controls.Border> elementu. <xref:System.Windows.Controls.Grid> Se používá k oddílu mezery mezi tří podřízených <xref:System.Windows.Controls.StackPanel> elementy. <xref:System.Windows.Controls.Button> elementy znovu slouží k zobrazení různých důsledky <xref:System.Windows.FrameworkElement.Margin%2A> a <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>. <xref:System.Windows.Controls.TextBlock> elementy jsou přidána na každý <xref:System.Windows.Controls.ColumnDefinition> a lépe tak definovat různé vlastnosti použít <xref:System.Windows.Controls.Button> elementy v každém sloupci.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Při kompilaci, vypočítá předchozí aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vypadá podobně jako na následujícím obrázku. Účinky různých hodnot vlastností jsou zřejmé ve mezery mezi elementy a hodnoty vlastností významné prvků v jednotlivých sloupcích se zobrazují v rámci <xref:System.Windows.Controls.TextBlock> elementy.  
  
 ![Několik vlastností umístění v jedné aplikaci](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>Co je další  
 Vlastnosti definované umístění <xref:System.Windows.FrameworkElement> třída povolení přesné řízení, element umístění v rámci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Nyní máte několik technik, které vám pomůže lépe umístit elementů pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Další prostředky jsou k dispozici, vysvětlují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení podrobněji. [Přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md) téma obsahuje další podrobnosti o různých <xref:System.Windows.Controls.Panel> elementy. Téma [návod: Můj první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md) zavádí pokročilé techniky, využívající rozložení elementů vazby jejich akce ke zdrojům dat a umístit součásti.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.Margin%2A>  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Rozložení](../../../../docs/framework/wpf/advanced/layout.md)  
 [Ukázka Galerie rozložení WPF](http://go.microsoft.com/fwlink/?LinkID=160054)
