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
ms.openlocfilehash: e0e5e386b32425c87502d18a24e758193c14a5b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186925"
---
# <a name="painting-with-images-drawings-and-visuals"></a>Kreslení pomocí obrázků, kreseb a vizuálních objektů
Toto téma popisuje <xref:System.Windows.Media.ImageBrush>použití <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.VisualBrush> a objekty k malování <xref:System.Windows.Media.Drawing>oblasti s <xref:System.Windows.Media.Visual>obrázkem, a nebo .  

<a name="prereqs"></a>
## <a name="prerequisites"></a>Požadavky  
 Chcete-li porozumět tomuto tématu, měli byste [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] být obeznámeni s různými typy stop a jejich základními funkcemi. Úvod naleznete v přehledu [štětců WPF](wpf-brushes-overview.md).  
  
<a name="image"></a>
## <a name="paint-an-area-with-an-image"></a>Vykreslení obrázku v oblasti  
 Vymaluje <xref:System.Windows.Media.ImageBrush> oblast <xref:System.Windows.Media.ImageSource>s . Nejběžnějším <xref:System.Windows.Media.ImageSource> typem <xref:System.Windows.Media.ImageBrush> pro použití s <xref:System.Windows.Media.Imaging.BitmapImage>je , který popisuje bitmapovou grafiku. Můžete použít <xref:System.Windows.Media.DrawingImage> k malování <xref:System.Windows.Media.Drawing> pomocí objektu, ale je <xref:System.Windows.Media.DrawingBrush> jednodušší použít místo. Další informace <xref:System.Windows.Media.ImageSource> o objektech naleznete v tématu [Přehled zpracování obrázků](imaging-overview.md).  
  
 Chcete-li <xref:System.Windows.Media.ImageBrush>malovat pomocí <xref:System.Windows.Media.Imaging.BitmapImage> , vytvořte a použijte jej k načtení bitmapového obsahu. Potom použijte <xref:System.Windows.Media.Imaging.BitmapImage> k nastavení <xref:System.Windows.Media.ImageBrush.ImageSource%2A> vlastnosti <xref:System.Windows.Media.ImageBrush>. Nakonec naneste <xref:System.Windows.Media.ImageBrush> objekt, který chcete malovat.  V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]oblasti můžete také <xref:System.Windows.Media.ImageBrush.ImageSource%2A> nastavit vlastnost <xref:System.Windows.Media.ImageBrush> s cestou obrazu, který se má načíst.  
  
 Stejně <xref:System.Windows.Media.Brush> jako <xref:System.Windows.Media.ImageBrush> všechny objekty lze i k malování objektů, jako jsou tvary, panely, ovládací prvky a text, použít. Následující obrázek znázorňuje některé efekty, kterých lze dosáhnout pomocí <xref:System.Windows.Media.ImageBrush>aplikace .  
  
 ![Příklady výstupu ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Objekty vybarvené imagebrush  
  
 Ve výchozím <xref:System.Windows.Media.ImageBrush> nastavení roztáhne obraz tak, aby zcela vyplnil vybarvenou oblast, což může obraz zkreslit, pokud má malovaná oblast jiný poměr stran než obraz. Toto chování můžete změnit <xref:System.Windows.Media.TileBrush.Stretch%2A> změnou vlastnosti <xref:System.Windows.Media.Stretch.Fill> <xref:System.Windows.Media.Stretch.None>z <xref:System.Windows.Media.Stretch.Uniform>výchozí <xref:System.Windows.Media.Stretch.UniformToFill>hodnoty na , nebo . Protože <xref:System.Windows.Media.ImageBrush> se jedná <xref:System.Windows.Media.TileBrush>o typ aplikace , můžete přesně určit, jak obrazová stopa vyplní výstupní oblast, a dokonce vytvořit vzorky. Další informace o <xref:System.Windows.Media.TileBrush> pokročilých funkcích naleznete v [tématu Přehled tilebrush](tilebrush-overview.md).  
  
<a name="fillingpanelwithimage"></a>
## <a name="example-paint-an-object-with-a-bitmap-image"></a>Příklad: Malování objektu bitmapovým obrazem  
 Následující příklad používá <xref:System.Windows.Media.ImageBrush> k <xref:System.Windows.Controls.Panel.Background%2A> malování <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/ImageBrushExample.xaml#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/ImageBrushExample.cs#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMImageBrushAsCanvasBackgroundExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/imagebrushexample.vb#graphicsmmimagebrushascanvasbackgroundexamplewholepage)]  
  
<a name="drawingbrushintro"></a>
## <a name="paint-an-area-with-a-drawing"></a>Vyplnění oblasti kresbou  
 A <xref:System.Windows.Media.DrawingBrush> umožňuje malovat oblast s tvary, text, obrázky a video. Tvary uvnitř kreslicí stopy mohou být samy o <xref:System.Windows.Media.DrawingBrush>sobě vymalovány plnou barvou, přechodem, obrazem nebo dokonce jiným . Následující obrázek znázorňuje <xref:System.Windows.Media.DrawingBrush>některá použití .  
  
 ![Příklady výstupů DrawingBrush](./media/wcpsdk-mmgraphics-drawingbrushexamples.png "wcpsdk_mmgraphics_drawingbrushexamples")  
Objekty namalované drawingbrush  
  
 A <xref:System.Windows.Media.DrawingBrush> maluje oblast <xref:System.Windows.Media.Drawing> s objektem. Objekt <xref:System.Windows.Media.Drawing> popisuje viditelný obsah, například tvar, bitmapu, video nebo řádek textu. Různé typy výkresů popisují různé typy obsahu. Následuje seznam různých typů nakreslených objektů.  
  
- <xref:System.Windows.Media.GeometryDrawing>– Nakreslí tvar.  
  
- <xref:System.Windows.Media.ImageDrawing>– Nakreslí obrázek.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>– Nakreslí text.  
  
- <xref:System.Windows.Media.VideoDrawing>– Přehraje zvukový soubor nebo video soubor.  
  
- <xref:System.Windows.Media.DrawingGroup>– Kreslí jiné výkresy. Pomocí skupiny výkresů můžete kombinovat další výkresy do jednoho složeného výkresu.  
  
 Další informace <xref:System.Windows.Media.Drawing> o objektech naleznete v tématu [Přehled objektů kreslení](drawing-objects-overview.md).  
  
 Stejně <xref:System.Windows.Media.ImageBrush>jako <xref:System.Windows.Media.DrawingBrush> , <xref:System.Windows.Media.DrawingBrush.Drawing%2A> se táhne jeho vyplnit jeho výstupní oblasti. Toto chování můžete přepsat <xref:System.Windows.Media.TileBrush.Stretch%2A> změnou vlastnosti <xref:System.Windows.Media.Stretch.Fill>z výchozího nastavení aplikace . Další informace naleznete <xref:System.Windows.Media.TileBrush.Stretch%2A> v ubytovacím zařízení.  
  
<a name="fillingareawithdrawingbrushexample"></a>
## <a name="example-paint-an-object-with-a-drawing"></a>Příklad: Malování objektu výkresem  
 Následující příklad ukazuje, jak malovat objekt s výkresem tří elips. A <xref:System.Windows.Media.GeometryDrawing> se používá k popisu elipsy.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/DrawingBrushExample.xaml#graphicsmmdrawingbrushasbuttonbackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/DrawingBrushExample.cs#graphicsmmdrawingbrushasbuttonbackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMDrawingBrushAsButtonBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/drawingbrushexample.vb#graphicsmmdrawingbrushasbuttonbackgroundexample1)]  
  
<a name="visualbrushsection"></a>
## <a name="paint-an-area-with-a-visual"></a>Vykreslení vizuálního objektu v oblasti  
 Nejuniverzálnější a nejsilnější ze <xref:System.Windows.Media.VisualBrush> všech kartáčů, <xref:System.Windows.Media.Visual>barvy oblast s . A <xref:System.Windows.Media.Visual> je nízkoúrovňový grafický typ, který slouží jako předchůdce mnoha užitečných grafických komponent. Například <xref:System.Windows.Window>, <xref:System.Windows.FrameworkElement>a <xref:System.Windows.Controls.Control> třídy jsou <xref:System.Windows.Media.Visual> všechny typy objektů. Pomocí <xref:System.Windows.Media.VisualBrush>aplikace můžete malovat oblasti [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] téměř libovolným grafickým objektem.  
  
> [!NOTE]
> Přestože <xref:System.Windows.Media.VisualBrush> je <xref:System.Windows.Freezable> typ objektu, nelze jej zmrazit (jen <xref:System.Windows.Media.VisualBrush.Visual%2A> pro čtení), pokud `null`je jeho vlastnost nastavena na jinou hodnotu než .  
  
 Obsah souboru <xref:System.Windows.Media.VisualBrush.Visual%2A> lze zadat dvěma <xref:System.Windows.Media.VisualBrush>způsoby.  
  
- Vytvořte <xref:System.Windows.Media.Visual> nový a použijte <xref:System.Windows.Media.VisualBrush.Visual%2A> jej k <xref:System.Windows.Media.VisualBrush>nastavení vlastnosti . Příklad například viz [Příklad: Malování objektu s visual](#examplevisualbrush1) oddíl, který následuje.  
  
- Použijte existující <xref:System.Windows.Media.Visual>, který vytvoří duplicitní <xref:System.Windows.Media.Visual>obraz cíle . Pak můžete použít <xref:System.Windows.Media.VisualBrush> k vytvoření zajímavých efektů, jako je odraz a zvětšení. Příklad najdete v [příkladu: Vytvoření oddílu Reflexe.](#examplevisualbrush2)  
  
 Když definujete <xref:System.Windows.Media.VisualBrush.Visual%2A> nové <xref:System.Windows.Media.VisualBrush> pro <xref:System.Windows.Media.Visual> a, <xref:System.Windows.UIElement> které je (například panel nebo ovládací <xref:System.Windows.UIElement> prvek), systém <xref:System.Windows.Media.VisualBrush.AutoLayoutContent%2A> rozložení běží `true`na a jeho podřízené prvky, když je vlastnost nastavena na . Kořen <xref:System.Windows.UIElement> je však v podstatě izolován od zbytku systému: styly a externí rozložení nemůže pronikat do této hranice. Proto byste měli explicitně určit <xref:System.Windows.UIElement>velikost kořenového adresáře <xref:System.Windows.Media.VisualBrush> , protože jeho jediný nadřazený je a proto nemůže automaticky velikost sám na oblast, která je malované. Další informace o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]rozložení v tématu naleznete v [tématu Rozložení](../advanced/layout.md).  
  
 Like <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>a <xref:System.Windows.Media.VisualBrush> , roztáhne jeho obsah vyplnit jeho výstupní oblasti. Toto chování můžete přepsat <xref:System.Windows.Media.TileBrush.Stretch%2A> změnou vlastnosti <xref:System.Windows.Media.Stretch.Fill>z výchozího nastavení aplikace . Další informace naleznete <xref:System.Windows.Media.TileBrush.Stretch%2A> v ubytovacím zařízení.  
  
<a name="examplevisualbrush1"></a>
## <a name="example-paint-an-object-with-a-visual"></a>Příklad: Malování objektu vizuálním  
 V následujícím příkladu několik ovládacích prvků a panel se používají k malování obdélníku.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/VisualBrushExample.xaml#graphicsmmvisualbrushasrectanglebackgroundexample)]  
  
 [!code-csharp[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/CSharp/VisualBrushExample.cs#graphicsmmvisualbrushasrectanglebackgroundexample1)]
 [!code-vb[BrushOverviewExamples_procedural_snip#GraphicsMMVisualBrushAsRectangleBackgroundExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_procedural_snip/visualbasic/visualbrushexample.vb#graphicsmmvisualbrushasrectanglebackgroundexample1)]  
  
<a name="examplevisualbrush2"></a>
## <a name="example-create-a-reflection"></a>Příklad: Vytvoření odrazu  
 Předchozí příklad ukázal, jak vytvořit <xref:System.Windows.Media.Visual> nový pro použití jako pozadí. Můžete také použít <xref:System.Windows.Media.VisualBrush> k zobrazení existujícího vizuálu; Tato funkce umožňuje vytvářet zajímavé vizuální efekty, jako jsou odrazy a zvětšení. Následující příklad používá <xref:System.Windows.Media.VisualBrush> a k vytvoření <xref:System.Windows.Controls.Border> odrazu, který obsahuje několik prvků. Následující obrázek znázorňuje výstup, který tento příklad vytváří.  
  
 ![Odražený vizuální objekt](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Odražený vizuální objekt  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Další příklady, které ukazují, jak zvětšit části obrazovky a jak vytvořit odrazy, naleznete [visualbrush ukázku](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).  
  
<a name="tilebrush"></a>
## <a name="tilebrush-features"></a>Funkce tilebrush  
 <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>a <xref:System.Windows.Media.VisualBrush> jsou <xref:System.Windows.Media.TileBrush> typy objektů. <xref:System.Windows.Media.TileBrush>objekty poskytují velkou kontrolu nad tím, jak je oblast namalována obrazem, výkresem nebo vizuálem. Například místo pouhého malování oblasti jedním roztaženým obrazem můžete malovat oblast řadou dlaždic obrazu, které vytvářejí vzorek.  
  
 A <xref:System.Windows.Media.TileBrush> má tři primární součásti: obsah, dlaždice a výstupní oblast.  
  
 ![Komponenty TileBrush](./media/wcpsdk-mmgraphics-defaultcontentprojection2.png "wcpsdk_mmgraphics_defaultcontentprojection2")  
Součásti TileBrush s jednou dlaždicí  
  
 ![Součásti dlaždicové dlaždiceBrush](./media/graphicsmm-tiledprojection.png "graphicsmm_tiledprojection")  
Součásti tilebrush s více dlaždicemi  
  
 Další informace o funkcích <xref:System.Windows.Media.TileBrush> dlaždic objektů naleznete v [tématu Přehled tilebrush](tilebrush-overview.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.VisualBrush>
- <xref:System.Windows.Media.TileBrush>
- [TileBrush – přehled](tilebrush-overview.md)
- [Přehled štětců WPF](wpf-brushes-overview.md)
- [Přehled obrázků](imaging-overview.md)
- [Přehled vykreslovaných objektů](drawing-objects-overview.md)
- [Přehled masek neprůhlednosti](opacity-masks-overview.md)
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
- [Ukázka imagebrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [Ukázka visualbrushu](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
