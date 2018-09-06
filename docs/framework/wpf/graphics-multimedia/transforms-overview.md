---
title: Přehled transformace
ms.date: 03/30/2017
helpviewer_keywords:
- transformations [WPF], about transformations
- classes [WPF], 2-D transform
- transform classes [WPF], 2-D
- 2-D transform classes
- FrameworkElement objects [WPF], rotating
- FrameworkElement objects [WPF], skewing
- FrameworkElement objects [WPF], translating
- Transforms [WPF], about Transforms
- FrameworkElement objects [WPF], scaling
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
ms.openlocfilehash: 4fd846502fd348222bc1da1c8746f037e9f237fe
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864573"
---
# <a name="transforms-overview"></a>Přehled transformace
Toto téma popisuje způsob použití [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> třídy otočit, škálování, přesuňte (přeložit) a zkosení <xref:System.Windows.FrameworkElement> objekty.  
  
  
<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>Co je transformace?  
 A <xref:System.Windows.Media.Transform> definuje, jak mapovat nebo transformace, body z jedné souřadnicového prostoru do jiného souřadnicového prostoru. Toto mapování je popsán transformace <xref:System.Windows.Media.Matrix>, což je kolekce tři řádky se třemi sloupci <xref:System.Double> hodnoty.  
  
> [!NOTE]
>  Windows Presentation Foundation (WPF) používá maticemi. Vektory jsou vyjádřeny jako řádek vektorů, není sloupec vektorů.  
  
 V následující tabulce jsou uvedeny strukturu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] matice.  
  
### <a name="a-2-d-transformation-matrix"></a>Matice 2D transformace  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Výchozí: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Výchozí: 0,0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Výchozí: 0,0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Výchozí: 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Výchozí: 0,0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Výchozí: 0,0|1.0|  
  
 Manipulací matice hodnoty můžete otočit, škálování, zkosení a přesunout (přeložit) objektu. Například, pokud změníte hodnotu v prvním sloupci třetího řádku ( <xref:System.Windows.Media.Matrix.OffsetX%2A> hodnota) do 100, můžete ho přesunout objekt 100 jednotek podél osy x. Pokud změníte hodnotu v druhém sloupci druhého řádku na 3, můžete ji roztáhnout třikrát aktuální výšku objektu. Pokud změníte obě hodnoty, přesunout objekt 100 jednotek podél osy x a roztažení výšku faktorem 3. Protože Windows Presentation Foundation (WPF) podporuje pouze afinní transformace, hodnoty v pravém sloupci je vždy 0, 0, 1.  
  
 I když Windows Presentation Foundation (WPF) umožňuje přímo manipulaci s hodnotami matice, poskytuje také několik <xref:System.Windows.Media.Transform> třídy, které vám umožní transformovat objektu bez znalosti konfigurace podkladová struktura matice. Například <xref:System.Windows.Media.ScaleTransform> třída umožňuje škálovat objektu nastavením jeho <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> vlastnosti namísto manipulace s transformační matice. Podobně <xref:System.Windows.Media.RotateTransform> třída umožňuje otočení objektu právě nastavením jeho <xref:System.Windows.Media.RotateTransform.Angle%2A> vlastnost.  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Třídy transformace  
 Windows Presentation Foundation (WPF) poskytuje následující [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> třídy pro běžné operace transformace:  
  
|Třída|Popis|Příklad|Obrázek|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Otočí element zadanou <xref:System.Windows.Media.RotateTransform.Angle%2A>.|[Otočení objektu](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object.md)|![Otočení obrázku](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Element se škáluje podle zadaného <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> částky.|[Změna velikosti elementu](../../../../docs/framework/wpf/graphics-multimedia/how-to-scale-an-element.md)|![Změnit měřítko obrázku](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Zkosí prvek k zadanému <xref:System.Windows.Media.SkewTransform.AngleX%2A> a <xref:System.Windows.Media.SkewTransform.AngleY%2A> částky.|[Zkosení elementu](../../../../docs/framework/wpf/graphics-multimedia/how-to-skew-an-element.md)|![Zkosení obrázek](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Přesune (přeloží) elementu podle zadaného <xref:System.Windows.Media.TranslateTransform.X%2A> a <xref:System.Windows.Media.TranslateTransform.Y%2A> částky.|[Překlad elementu](../../../../docs/framework/wpf/graphics-multimedia/how-to-translate-an-element.md)|![Převede obrázek](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Pro vytvoření složitější transformace Windows Presentation Foundation (WPF) obsahuje následující třídy, dvě:  
  
|Třída|Popis|Příklad|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Skupiny více <xref:System.Windows.Media.TransformGroup> objekty do jednoho <xref:System.Windows.Media.Transform> , lze následně použít k transformaci vlastnosti.|[Použití několika transformací na objekt](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Vytvoří vlastní transformace, které nejsou součástí druhé <xref:System.Windows.Media.Transform> třídy. Při použití <xref:System.Windows.Media.MatrixTransform>, pracovat s matice přímo.|[Vytvoření vlastních transformací pomocí MatrixTransform](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) poskytuje také [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] transformace. Další informace najdete v tématu <xref:System.Windows.Media.Media3D.Transform3D> třídy.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Společné vlastnosti transformace  
 Jedním ze způsobů transformace objektu je deklarovat odpovídající <xref:System.Windows.Media.Transform> typ a použijte ji pro vlastnost transformace objektu. Různé typy objektů mají různé typy vlastnosti transformace. Následující tabulka uvádí několik běžně používané typy Windows Presentation Foundation (WPF) a jejich vlastnosti transformace.  
  
|Typ|Vlastnosti transformace|  
|----------|-------------------------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>, <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## <a name="transformations-and-coordinate-systems"></a>Transformace a souřadnicových systémů  
 Při transformaci objekt je právě netransformují objektu, transformovali souřadnicového prostoru, ve které tento objekt existuje. Ve výchozím nastavení, transformace je zarovnaný na střed v původní cílový objekt souřadnicový systém: (0; 0). Jedinou výjimkou je <xref:System.Windows.Media.TranslateTransform>; <xref:System.Windows.Media.TranslateTransform> nemá žádné vlastnosti center nastavit, protože výsledek překladu je stejný bez ohledu na to, kde je na střed.  
  
 V následujícím příkladu <xref:System.Windows.Media.RotateTransform> otočíte <xref:System.Windows.Shapes.Rectangle> elementu, typu <xref:System.Windows.FrameworkElement>, o 45 stupňů o jeho výchozí centrum (0, 0). Následující obrázek znázorňuje vliv otočení.  
  
 ![Objekt FrameworkElement otáčet 45 stupňů o &#40;0,0&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Element obdélník otáčet 45 stupňů o bodu (0; 0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Ve výchozím nastavení, otočí element o jeho levého horního rohu (0, 0). <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform>, A <xref:System.Windows.Media.SkewTransform> třídy poskytují CenterX a CenterY vlastnosti, které vám umožní určit bod, ve kterém je použita transformace.  
  
 Následující příklad používá také <xref:System.Windows.Media.RotateTransform> otočíte <xref:System.Windows.Shapes.Rectangle> element o 45 stupňů; však tentokrát <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> jsou nastaveny vlastnosti tak, aby <xref:System.Windows.Media.RotateTransform> má střed (25, 25). Následující obrázek znázorňuje vliv otočení.  
  
 ![Geometrii otáčet 45 stupňů o &#40;25, 25&#41;](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Element obdélník otáčet 45 stupňů o bodu (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>Transformace FrameworkElement  
 Použití transformací pro <xref:System.Windows.FrameworkElement>, vytvořit <xref:System.Windows.Media.Transform> a použít ho na jednu ze dvou vlastností, které <xref:System.Windows.FrameworkElement> třída poskytuje:  
  
-   <xref:System.Windows.FrameworkElement.LayoutTransform%2A> – Transformace, který je použit před předání rozložení. Po je použita transformace, zpracuje systém rozložení transformovaný velikost a umístění elementu.  
  
-   <xref:System.Windows.UIElement.RenderTransform%2A> – Transformace změní vzhled elementu, který se použije po předání rozložení je dokončena. S použitím <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost místo <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost, získáte výhody výkonu.  
  
 Vlastností, které byste měli použít? Protože výkony těží, které poskytuje, použijte <xref:System.Windows.UIElement.RenderTransform%2A> pokaždé, když se nejvíce, zejména v případě, že používáte animovat vlastnost <xref:System.Windows.Media.Transform> objekty. Použití <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost při škálování, otáčení nebo zkosení a potřebujete nadřazeného elementu upravit transformovaný velikosti prvku. Všimněte si, že při použití s <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> objekty se nemají žádný vliv na elementy. Důvodem je, systém rozložení vrátí přeložené prvek na jeho původní pozice v rámci jeho zpracování.  
  
 Další informace o rozložení v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], naleznete v tématu [rozložení](../../../../docs/framework/wpf/advanced/layout.md) Přehled.  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Příklad: Otočit objekt FrameworkElement 45 stupňů  
 Následující příklad používá <xref:System.Windows.Media.RotateTransform> obměna tlačítka po směru hodinových ručiček o 45 stupňů. Tlačítko je součástí <xref:System.Windows.Controls.StackPanel> , který má dva další tlačítka.  
  
 Ve výchozím nastavení <xref:System.Windows.Media.RotateTransform> otočí o bodu (0, 0). Protože příklad neurčuje středovou hodnotou, tlačítko otočí o bod (0, 0), který je jeho levého horního rohu. <xref:System.Windows.Media.RotateTransform> Aplikován <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost. Následující obrázek ukazuje výsledek transformace.  
  
 ![Tlačítko transformovat pomocí RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Otočení po směru hodinových ručiček od levého horního rohu 45 stupňů  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 Následující příklad používá také <xref:System.Windows.Media.RotateTransform> obměna tlačítko 45 stupňů po směru hodinových ručiček, ale také nastaví <xref:System.Windows.UIElement.RenderTransformOrigin%2A> tlačítka (0,5, 0,5). Hodnota <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost je relativní vzhledem k velikosti panelu. Otočení v důsledku toho se použije k centru pro tlačítka, namísto jeho levého horního rohu. Následující obrázek ukazuje výsledek transformace.  
  
 ![Tlačítko transformované o jeho střed](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Rotaci kolem 45 stupňů kolem středu  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 V následujícím příkladu <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost místo <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost otočíte na tlačítko.  To způsobí, že transformace ovlivnit rozložení tlačítko, které aktivuje úplné předáván systém rozložení. V důsledku toho je tlačítko otočen a potom přesunout, protože došlo ke změně jeho velikosti. Následující obrázek ukazuje výsledek transformace.  
  
 ![Tlačítko transformovat pomocí LayoutTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
LayoutTransform – používá k otočení tlačítka  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Animace transformace  
 Protože dědí z <xref:System.Windows.Media.Animation.Animatable> třídy, <xref:System.Windows.Media.Transform> třídy lze animovat. Animování <xref:System.Windows.Media.Transform>, použijte animaci kompatibilní typ. vlastnost má být animován.  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.Storyboard> a <xref:System.Windows.Media.Animation.DoubleAnimation> s <xref:System.Windows.Media.RotateTransform> aby <xref:System.Windows.Controls.Button> typu číselník na místě, když dojde ke kliknutí na.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Úplnou ukázku najdete v tématu [2D transformace ukázka](https://go.microsoft.com/fwlink/?LinkID=158252). Další informace o animacích naleznete v tématu [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable – funkce  
 Protože dědí sám od <xref:System.Windows.Freezable> třídy, <xref:System.Windows.Media.Transform> třídy poskytují několik speciálních funkcí: <xref:System.Windows.Media.Transform> objekty mohou být deklarovány jako [prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md), sdíleny mezi více objektů, jen pro čtení ke zlepšení výkon, klonování a provedli bezpečné pro vlákna. Další informace o různých funkcí, které jsou poskytovány <xref:System.Windows.Freezable> objekty, najdete [přehled Zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Matrix>  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Ukázka 2D transformace](https://go.microsoft.com/fwlink/?LinkID=158252)
