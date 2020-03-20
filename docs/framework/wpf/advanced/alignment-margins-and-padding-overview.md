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
ms.openlocfilehash: bec2d9cd224febb650e2de67bb7406365d075963
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145472"
---
# <a name="alignment-margins-and-padding-overview"></a>Přehled zarovnání, okrajů a odsazení
Třída <xref:System.Windows.FrameworkElement> zveřejňuje několik vlastností, které se používají k přesnému umístění podřízených prvků. Toto téma popisuje čtyři nejdůležitější <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>vlastnosti: , <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>. Účinky těchto vlastností jsou důležité pochopit, protože poskytují základ pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] řízení polohy prvků v aplikacích.  

<a name="wcpsdk_layout_amp_introduction"></a>
## <a name="introduction-to-element-positioning"></a>Úvod do umístění prvku  
 Existuje mnoho způsobů, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umístit prvky pomocí . Dosažení ideálního rozložení však přesahuje <xref:System.Windows.Controls.Panel> pouhé vybírání správného prvku. Jemné řízení polohování vyžaduje pochopení <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.Margin%2A>vlastností , <xref:System.Windows.Controls.Border.Padding%2A>, a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastností.  
  
 Následující obrázek znázorňuje scénář rozložení, který využívá několik vlastností umístění.  
  
 ![Ukázka vlastností umístění WPF](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 Na první pohled <xref:System.Windows.Controls.Button> se mohou prvky na tomto obrázku jevit jako náhodně umístěné. Jejich pozice jsou však ve skutečnosti přesně řízeny pomocí kombinace okrajů, zarovnání a odsazení.  
  
 Následující příklad popisuje, jak vytvořit rozložení na předchozím obrázku. Prvek <xref:System.Windows.Controls.Border> zapouzdřuje <xref:System.Windows.Controls.StackPanel>nadřazený prvek s hodnotou <xref:System.Windows.Controls.Border.Padding%2A> 15 pixelů nezávislých na zařízení. To odpovídá úzkému <xref:System.Windows.Media.Brushes.LightBlue%2A> pásmu, <xref:System.Windows.Controls.StackPanel>které obklopuje dítě . Podřízené prvky <xref:System.Windows.Controls.StackPanel> slouží k ilustraci každé z různých vlastností umístění, které jsou podrobně popsány v tomto tématu. Tři <xref:System.Windows.Controls.Button> prvky se používají <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> k prokázání vlastnosti a vlastnosti.  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 Následující diagram poskytuje detailní pohled na různé vlastnosti umístění, které se používají v předchozím vzorku. Následující oddíly v tomto tématu popisují podrobněji, jak používat jednotlivé vlastnosti umístění.  
  
 ![Vlastnosti umístění pomocí&#45;výdeje volání obrazovky](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>
## <a name="understanding-alignment-properties"></a>Principy vlastností zarovnání  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Vlastnosti <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> a popisují, jak by měl být podřízený prvek umístěn v přiděleném prostoru rozložení nadřazeného prvku. Pomocí těchto vlastností společně můžete umístit podřízené prvky přesně. <xref:System.Windows.Controls.DockPanel> Podřízené prvky a mohou například určit <xref:System.Windows.HorizontalAlignment.Left>čtyři <xref:System.Windows.HorizontalAlignment.Right>různé <xref:System.Windows.HorizontalAlignment.Center>vodorovné <xref:System.Windows.HorizontalAlignment.Stretch> trasy: , , nebo , nebo vyplnit volné místo. Podobné hodnoty jsou k dispozici pro vertikální polohování.  
  
> [!NOTE]
> Explicitně <xref:System.Windows.FrameworkElement.Height%2A> nastavené a <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti prvku <xref:System.Windows.HorizontalAlignment.Stretch> mají přednost před hodnotou vlastnosti. Pokus o <xref:System.Windows.FrameworkElement.Height%2A>nastavení <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a `Stretch` hodnotu `Stretch` výsledků v požadavku ignorovány.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>
### <a name="horizontalalignment-property"></a>Vlastnost HorizontalAlignment  
 Vlastnost <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> deklaruje vlastnosti vodorovné zarovnání, které se použijí na podřízené prvky. V následující tabulce jsou uvedeny <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> všechny možné hodnoty vlastnosti.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Podřízené prvky jsou zarovnány vlevo od přiděleného prostoru rozložení nadřazeného prvku.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Podřízené prvky jsou zarovnány ke středu přiděleného prostoru rozložení nadřazeného prvku.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Podřízené prvky jsou zarovnány vpravo od přiděleného prostoru rozložení nadřazeného prvku.|  
|<xref:System.Windows.HorizontalAlignment.Stretch>(Výchozí)|Podřízené prvky jsou roztaženy tak, aby vyplnily přidělené prostory rozložení nadřazeného prvku. Explicitní <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> a hodnoty mají přednost.|  
  
 Následující příklad ukazuje, jak <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> použít <xref:System.Windows.Controls.Button> vlastnost na prvky. Každá hodnota atributu je zobrazena, aby lépe ilustrovala různé chování vykreslování.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 Předchozí kód poskytuje rozložení podobné následujícímu obrázku. Polohovací efekty <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> každé hodnoty jsou viditelné na obrázku.  
  
 ![Ukázka vodorovného ustavování](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>
### <a name="verticalalignment-property"></a>Vlastnost VerticalAlignment  
 Vlastnost <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> popisuje svislé charakteristiky zarovnání, které se mají použít pro podřízené prvky. V následující tabulce jsou uvedeny <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> všechny možné hodnoty vlastnosti.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Podřízené prvky jsou zarovnány do horní části přiděleného prostoru rozložení nadřazeného prvku.|  
|<xref:System.Windows.VerticalAlignment.Center>|Podřízené prvky jsou zarovnány ke středu přiděleného prostoru rozložení nadřazeného prvku.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Podřízené prvky jsou zarovnány do dolní části přiděleného prostoru rozložení nadřazeného prvku.|  
|<xref:System.Windows.VerticalAlignment.Stretch>(Výchozí)|Podřízené prvky jsou roztaženy tak, aby vyplnily přidělené prostory rozložení nadřazeného prvku. Explicitní <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> a hodnoty mají přednost.|  
  
 Následující příklad ukazuje, jak <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> použít <xref:System.Windows.Controls.Button> vlastnost na prvky. Každá hodnota atributu je zobrazena, aby lépe ilustrovala různé chování vykreslování. Pro účely této ukázky <xref:System.Windows.Controls.Grid> prvek s viditelné mřížky se používá jako nadřazený, pro lepší ilustraci chování rozložení každé hodnoty vlastnosti.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 Předchozí kód poskytuje rozložení podobné následujícímu obrázku. Polohovací efekty <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> každé hodnoty jsou viditelné na obrázku.  
  
 ![Ukázka vlastnosti VerticalAlignment](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>
## <a name="understanding-margin-properties"></a>Principy vlastností okraje  
 Vlastnost <xref:System.Windows.FrameworkElement.Margin%2A> popisuje vzdálenost mezi elementem a jeho podřízeným prvkem nebo partnery. <xref:System.Windows.FrameworkElement.Margin%2A>hodnoty mohou být jednotné, `Margin="20"`pomocí syntaxe jako . S touto syntaxí <xref:System.Windows.FrameworkElement.Margin%2A> by se na prvek použila stejnokorát20 pixelů nezávislých na zařízení. <xref:System.Windows.FrameworkElement.Margin%2A>hodnoty mohou mít také podobu čtyř odlišných hodnot, přičemž každá hodnota popisuje odlišný okraj, který se `Margin="0,10,5,25"`má použít na levý, horní, pravý a dolní (v tomto pořadí), jako je . Správné použití <xref:System.Windows.FrameworkElement.Margin%2A> vlastnosti umožňuje velmi jemnou kontrolu vykreslovací polohy prvku a vykreslovací polohy sousedních prvků a podřízených prvků.  
  
> [!NOTE]
> Nenulová marže použije mezeru mimo <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A>prvek a .  
  
 Následující příklad ukazuje, jak použít jednotné okraje <xref:System.Windows.Controls.Button> kolem skupiny prvků. Prvky <xref:System.Windows.Controls.Button> jsou rozmístěny rovnoměrně s vyrovnávací pamětí okraje deseti pixelů v každém směru.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 V mnoha případech není vhodné jednotné rozpětí. V těchto případech lze použít nerovnoměrné rozteče. Následující příklad ukazuje, jak použít nerovnoměrné rozestupy okrajů na podřízené prvky. Okraje jsou popsány v tomto pořadí: vlevo, nahoře, vpravo, dole.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>
## <a name="understanding-the-padding-property"></a>Principy vlastnosti odsazení  
 Polstrování je <xref:System.Windows.FrameworkElement.Margin%2A> podobné ve většině ohledů. Odsazení Vlastnost je vystavena pouze na několik <xref:System.Windows.Documents.Block>tříd, <xref:System.Windows.Controls.Control>především <xref:System.Windows.Controls.TextBlock> pro pohodlí: , <xref:System.Windows.Controls.Border>, a jsou ukázky tříd, které zveřejňují odsazení vlastnost. Vlastnost <xref:System.Windows.Controls.Border.Padding%2A> zvětší efektivní velikost podřízeného prvku <xref:System.Windows.Thickness> o zadanou hodnotu.  
  
 Následující příklad ukazuje, <xref:System.Windows.Controls.Border.Padding%2A> jak použít <xref:System.Windows.Controls.Border> na nadřazený prvek.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Použití zarovnání, okraje a odsazení v aplikaci  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> a poskytují ovládací prvek polohování [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]nezbytné k vytvoření komplexu . Efekty každé vlastnosti můžete použít ke změně umístění podřízeného prvku, což umožňuje flexibilitu při vytváření dynamických aplikací a uživatelských prostředí.  
  
 Následující příklad ukazuje každý z konceptů, které jsou podrobně popsány v tomto tématu. V návaznosti na infrastrukturu nalezené v první ukázce v tomto tématu, tento příklad přidá <xref:System.Windows.Controls.Grid> prvek jako podřízený <xref:System.Windows.Controls.Border> v první ukázce. <xref:System.Windows.Controls.Border.Padding%2A>se použije na <xref:System.Windows.Controls.Border> nadřazený prvek. Slouží <xref:System.Windows.Controls.Grid> k rozdělení mezery <xref:System.Windows.Controls.StackPanel> mezi tři podřízené prvky. <xref:System.Windows.Controls.Button>prvky se opět používají k <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>zobrazení různých účinků a . <xref:System.Windows.Controls.TextBlock>prvky jsou <xref:System.Windows.Controls.ColumnDefinition> přidány do každého lépe definovat <xref:System.Windows.Controls.Button> různé vlastnosti aplikované na prvky v každém sloupci.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Při kompilaci předchozí aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dává, který vypadá jako na následujícím obrázku. Účinky různých hodnot vlastností jsou patrné v mezery mezi prvky a významné hodnoty <xref:System.Windows.Controls.TextBlock> vlastností pro prvky v každém sloupci jsou zobrazeny v rámci prvků.  
  
 ![Několik polohovacích vlastností v jedné aplikaci](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>
## <a name="whats-next"></a>Co bude dál  
 Polohovací vlastnosti <xref:System.Windows.FrameworkElement> definované třídou umožňují jemné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řízení umístění prvku v aplikacích. Nyní máte několik technik, které můžete [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]použít k lepšímu umístění prvků pomocí .  
  
 K dispozici jsou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] další zdroje informací, které vysvětlují rozložení podrobněji. Téma [Přehled panelů](../controls/panels-overview.md) obsahuje více <xref:System.Windows.Controls.Panel> podrobností o různých prvcích. Téma [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md) zavádí pokročilé techniky, které používají prvky rozložení k umístění součástí a svázání jejich akcí se zdroji dat.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Přehled panelu](../controls/panels-overview.md)
- [Rozložení](layout.md)
- [Ukázka galerie rozložení WPF](https://go.microsoft.com/fwlink/?LinkID=160054)
