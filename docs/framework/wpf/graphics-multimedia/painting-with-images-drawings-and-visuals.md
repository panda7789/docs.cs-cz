---
title: Kreslení pomocí obrázků, kreseb a vizuálních objektů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- painting [WPF], with images
- painting with visuals [WPF]
- brushes [WPF], painting with images
- brushes [WPF], painting with visuals
ms.assetid: 779aac3f-8d41-49d8-8130-768244aa2240
ms.openlocfilehash: e80132a5467f932e5569787f43427044ba2be256
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929600"
---
# <a name="painting-with-images-drawings-and-visuals"></a>Kreslení pomocí obrázků, kreseb a vizuálních objektů
Toto téma popisuje, jak použít <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush> objekty k <xref:System.Windows.Media.Drawing>vykreslení oblasti <xref:System.Windows.Media.Visual>s obrázkem, nebo.  

<a name="prereqs"></a>   
## <a name="prerequisites"></a>Požadavky  
 Pro pochopení tohoto tématu byste měli být obeznámeni s různými typy štětců [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] , které nabízí a jejich základní funkce. Úvod najdete v [přehledu štětců WPF](wpf-brushes-overview.md).  
  
<a name="image"></a>   
## <a name="paint-an-area-with-an-image"></a>Vykreslení obrázku v oblasti  
 Vykreslí oblast <xref:System.Windows.Media.ImageSource>s. <xref:System.Windows.Media.ImageBrush> Nejběžnější typ <xref:System.Windows.Media.ImageSource> pro použití <xref:System.Windows.Media.ImageBrush> s typem je <xref:System.Windows.Media.Imaging.BitmapImage>, který popisuje rastrový obrázek. Můžete použít <xref:System.Windows.Media.DrawingImage> k malování <xref:System.Windows.Media.Drawing> pomocí objektu, ale <xref:System.Windows.Media.DrawingBrush> je jednodušší použít místo něj. Další informace o <xref:System.Windows.Media.ImageSource> objektech naleznete v tématu [Přehled vytváření imagí](imaging-overview.md).  
  
 Chcete-li malovat <xref:System.Windows.Media.ImageBrush>pomocí, <xref:System.Windows.Media.Imaging.BitmapImage> vytvořte a použijte jej k načtení obsahu rastrového obrázku. Pak použijte <xref:System.Windows.Media.Imaging.BitmapImage> k <xref:System.Windows.Media.ImageBrush.ImageSource%2A> nastavení vlastnosti <xref:System.Windows.Media.ImageBrush>. Nakonec použijte <xref:System.Windows.Media.ImageBrush> u objektu, který chcete vykreslit.  V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]aplikaci můžete také <xref:System.Windows.Media.ImageBrush.ImageSource%2A> nastavit vlastnost <xref:System.Windows.Media.ImageBrush> s cestou obrázku, který se má načíst.  
  
 Podobně jako <xref:System.Windows.Media.Brush> všechny objekty <xref:System.Windows.Media.ImageBrush> lze použít k malování objektů, jako jsou tvary, panely, ovládací prvky a text. Následující ilustrace znázorňuje některé efekty, které lze dosáhnout pomocí <xref:System.Windows.Media.ImageBrush>.  
  
 ![Příklady výstupů ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Objekty vykreslené ImageBrush  
  
 Ve výchozím nastavení <xref:System.Windows.Media.ImageBrush> roztáhne jeho obrázek, aby zcela vyplnil roztaženou oblast, případně deformující obrázek, pokud má oblast namalovaného jiného poměru stran než obrázek. Toto chování můžete změnit tak, že změníte <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost z výchozí <xref:System.Windows.Media.Stretch.Fill> hodnoty na <xref:System.Windows.Media.Stretch.None>, <xref:System.Windows.Media.Stretch.Uniform>nebo <xref:System.Windows.Media.Stretch.UniformToFill>. Protože <xref:System.Windows.Media.ImageBrush> je<xref:System.Windows.Media.TileBrush>typ, můžete přesně zadat, jak štětec obrázku vyplní výstupní oblast a dokonce i vytvořit vzory. Další informace o rozšířených <xref:System.Windows.Media.TileBrush> funkcích najdete v [přehledu TileBrush](tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>   
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Příklad: Malování objektu pomocí rastrového obrázku  
 V následujícím příkladu je použit <xref:System.Windows.Media.ImageBrush> k <xref:System.Windows.Controls.Panel.Background%2A> vykreslení <xref:System.Windows.Controls.Canvas>prvku.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>   
## <a name="paint-an-area-with-a-drawing"></a>Vyplnění oblasti kresbou  
 <xref:System.Windows.Media.DrawingBrush> Umožňuje vykreslit oblast s obrazci, textem, obrázky a videem. Obrazce uvnitř kreslicího štětce mohou být vykresleny s plnou barvou, přechodem, obrázkem nebo <xref:System.Windows.Media.DrawingBrush>dokonce jiným. Následující ilustrace znázorňuje některá použití <xref:System.Windows.Media.DrawingBrush>.  
  
 ![Příklady výstupů prostředek DrawingBrush](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
Objekty vykreslené prostředek DrawingBrush  
  
 Vykreslí oblast <xref:System.Windows.Media.Drawing> s objektem. <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Drawing> Objekt popisuje viditelný obsah, jako je například tvar, rastrový obrázek, video nebo řádek textu. Různé typy kreseb popisují různé typy obsahu. Následuje seznam různých typů nakreslených objektů.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Nakreslí obrazec.  
  
- <xref:System.Windows.Media.ImageDrawing>– Nakreslí obrázek.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Kreslí text.  
  
- <xref:System.Windows.Media.VideoDrawing>– Přehraje zvukový soubor nebo videosoubor.  
  
- <xref:System.Windows.Media.DrawingGroup>– Kreslí další výkresy. K kombinování dalších kreseb do jednoho složené kresby použijte skupinu pro kreslení.  
  
 Další informace o <xref:System.Windows.Media.Drawing> objektech naleznete v tématu [Přehled nakreslených objektů](drawing-objects-overview.md).  
  
 Podobně jako <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush> , roztáhne své <xref:System.Windows.Media.DrawingBrush.Drawing%2A> výstupní oblast a vyplní ji. Toto chování můžete přepsat změnou <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnosti z výchozího <xref:System.Windows.Media.Stretch.Fill>nastavení. Další informace najdete v tématu <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost.  
  
<a name="fillingareawithdrawingbrushexample"></a>   
## <a name="example-paint-an-object-with-a-drawing"></a>Příklad: Malování objektu kresbou  
 Následující příklad ukazuje, jak vykreslit objekt s kresbou tří elips. <xref:System.Windows.Media.GeometryDrawing> Slouží k popisu elips.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>   
## <a name="paint-an-area-with-a-visual"></a>Vykreslení vizuálního objektu v oblasti  
 Nejkomplexnější a nejvýkonnější všechny štětce <xref:System.Windows.Media.VisualBrush> vykreslí oblast <xref:System.Windows.Media.Visual>s. <xref:System.Windows.Media.Visual> Je grafický typ nízké úrovně, který slouží jako předchůdce mnoha užitečných grafických komponent. Například <xref:System.Windows.Window>třídy, <xref:System.Windows.FrameworkElement>a <xref:System.Windows.Controls.Control> jsou všechny typy <xref:System.Windows.Media.Visual> objektů. Pomocí můžete malovat oblasti s téměř libovolným [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafickým objektem. <xref:System.Windows.Media.VisualBrush>  
  
> [!NOTE]
> I <xref:System.Windows.Media.VisualBrush> když je <xref:System.Windows.Freezable> typ objektu, nemůže být zmrazen (určený jen pro čtení), pokud je jeho <xref:System.Windows.Media.VisualBrush.Visual%2A> vlastnost nastavena na jinou hodnotu než `null`.  
  
 Existují dva způsoby, jak zadat <xref:System.Windows.Media.VisualBrush.Visual%2A> obsah. <xref:System.Windows.Media.VisualBrush>  
  
- Vytvořte nový <xref:System.Windows.Media.Visual> a použijte ho k <xref:System.Windows.Media.VisualBrush.Visual%2A> nastavení vlastnosti <xref:System.Windows.Media.VisualBrush>. Příklad najdete [v příkladu: Vymalujte objekt pomocí níže](#examplevisualbrush1) uvedené části vizuálu.  
  
- Použijte existující <xref:System.Windows.Media.Visual>, který vytvoří duplicitní obrázek cíle <xref:System.Windows.Media.Visual>. Pak můžete použít <xref:System.Windows.Media.VisualBrush> k vytvoření zajímavých efektů, jako je například reflexe a zvětšení. Příklad najdete [v příkladu: Vytvořte oddíl reflexe](#examplevisualbrush2) .  
  
 <xref:System.Windows.Media.VisualBrush.Visual%2A> Při definování nového <xref:System.Windows.Media.VisualBrush> pro a, který <xref:System.Windows.Media.Visual> je <xref:System.Windows.UIElement> (například <xref:System.Windows.UIElement> panel nebo ovládací prvek), se systém <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> rozložení spouští v a jeho podřízené prvky, pokud je vlastnost nastavena na `true`hodnotu. Kořen <xref:System.Windows.UIElement> je ale v podstatě izolovaný od zbytku systému: styly a externí rozložení nemůže tuto hranici permeate. Proto byste měli explicitně zadat velikost kořenového adresáře <xref:System.Windows.UIElement>, protože jeho jediný nadřazený prvek <xref:System.Windows.Media.VisualBrush> je, a proto nemůže automaticky měnit velikost pro oblast, která je právě vykreslena. Další informace o rozložení v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]nástroji najdete v části [rozložení](../advanced/layout.md).  
  
 Podobně <xref:System.Windows.Media.ImageBrush> jako <xref:System.Windows.Media.DrawingBrush>a ,<xref:System.Windows.Media.VisualBrush> roztáhne jeho obsah k vyplnění výstupní oblasti. Toto chování můžete přepsat změnou <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnosti z výchozího <xref:System.Windows.Media.Stretch.Fill>nastavení. Další informace najdete v tématu <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost.  
  
<a name="examplevisualbrush1"></a>   
## <a name="example-paint-an-object-with-a-visual"></a>Příklad: Malování objektu pomocí vizuálu  
 V následujícím příkladu se k vykreslení obdélníku používá několik ovládacích prvků a panelů.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>   
## <a name="example-create-a-reflection"></a>Příklad: Vytvoření reflexe  
 Předchozí příklad ukázal, jak vytvořit nový <xref:System.Windows.Media.Visual> pro použití jako pozadí. Můžete také použít <xref:System.Windows.Media.VisualBrush> k zobrazení existujícího vizuálu. Tato schopnost vám umožní vytvářet zajímavé vizuální efekty, jako je například odrazy a zvětšení. Následující příklad používá <xref:System.Windows.Media.VisualBrush> k vytvoření odrazu <xref:System.Windows.Controls.Border> , který obsahuje několik prvků. Následující obrázek ukazuje výstup, který tento příklad vytvoří.  
  
 ![Odrazný vizuální objekt](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Odrazný vizuální objekt  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Další příklady, které ukazují, jak zvětšit části obrazovky a jak vytvořit odrazy, najdete v [ukázce VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049).  
  
<a name="tilebrush"></a>   
## <a name="tilebrush-features"></a>Funkce TileBrush  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, a <xref:System.Windows.Media.VisualBrush> jsou typy <xref:System.Windows.Media.TileBrush> objektů. <xref:System.Windows.Media.TileBrush>objekty poskytují skvělou kontrolu nad tím, jak se oblast vykresluje s použitím obrázku, kresby nebo vizuálu. Například místo pouhého Malování oblasti s jediným roztaženým obrázkem můžete vykreslit oblast s řadou dlaždic obrázku, které tvoří vzorek.  
  
 <xref:System.Windows.Media.TileBrush> Má tři primární komponenty: obsah, dlaždice a výstupní oblast.  
  
 ![Komponenty TileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Komponenty TileBrush s jednou dlaždicí  
  
 ![Komponenty v dlaždici TileBrush](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Komponenty TileBrush s více dlaždicemi  
  
 Další informace o funkcích <xref:System.Windows.Media.TileBrush> dlaždic objektů naleznete v [přehledu TileBrush](tilebrush-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [TileBrush – přehled](tilebrush-overview.md)
- [Přehled štětců WPF](wpf-brushes-overview.md)
- [Přehled obrázků](imaging-overview.md)
- [Přehled nakreslených objektů](drawing-objects-overview.md)
- [Přehled masek neprůhlednosti](opacity-masks-overview.md)
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
- [Ukázka ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005)
- [Ukázka VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049)
