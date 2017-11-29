---
title: "Přehled transformace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd4e0f65d404e70f441cf2918fd6c50e08ebec79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="transforms-overview"></a>Přehled transformace
Toto téma popisuje postup použití [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> třídy otočit, škálování, přejděte (přeložit) a zkosení <xref:System.Windows.FrameworkElement> objekty.  
  
  
<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>Co je transformace?  
 A <xref:System.Windows.Media.Transform> definuje, jak mapování a transformace bodů z jednoho souřadnicového prostoru pro jiný souřadnicového prostoru. Toto mapování je popsán transformace <xref:System.Windows.Media.Matrix>, což je kolekce tři řádky s tři sloupce <xref:System.Double> hodnoty.  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]používá řádek hlavní matice. Vektory jsou vyjádřené jako řádek vektory, není sloupec vektory.  
  
 V následující tabulce jsou uvedeny strukturu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] matice.  
  
### <a name="a-2-d-transformation-matrix"></a>2D transformační matice  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Výchozí: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Výchozí: 0,0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Výchozí: 0,0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Výchozí: 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Výchozí: 0,0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Výchozí: 0,0|1.0|  
  
 Manipulací hodnoty matice může otočit, škálovat, zkreslit a přesunutí (převede) objekt. Například, pokud změníte hodnotu prvního sloupce třetím řádku ( <xref:System.Windows.Media.Matrix.OffsetX%2A> hodnotu) do 100, můžete ho přesunout objektu 100 jednotky podél osy x. Je-li změnit hodnotu v druhém sloupci druhého řádku na 3, můžete k roztahování třikrát aktuální výšku objektu. Pokud změníte obě hodnoty, přesunout objekt 100 jednotky podél osy x a roztažení výšku faktorem 3. Protože [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] jen podporuje afinní transformace, hodnoty v pravém sloupci jsou vždy 0, 0, 1.  
  
 I když [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] umožňuje přímo upravit hodnoty matice také nabízí několik <xref:System.Windows.Media.Transform> třídy, které vám umožní transformace objektu bez znalosti konfigurace podkladová struktura matice. Například <xref:System.Windows.Media.ScaleTransform> třída umožňuje škálovat objekt nastavením jeho <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> vlastnosti místo manipulace s transformační matice. Podobně <xref:System.Windows.Media.RotateTransform> třída umožňuje otočení objektu pouze pomocí nastavení jeho <xref:System.Windows.Media.RotateTransform.Angle%2A> vlastnost.  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Transformace třídy  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]poskytuje následující [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] <xref:System.Windows.Media.Transform> třídy pro běžné operace transformace:  
  
|Třída|Popis|Příklad|Obrázek|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Otočí element k zadanému <xref:System.Windows.Media.RotateTransform.Angle%2A>.|[Otočení objektu](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object.md)|![Otočit obrázek](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Škáluje element k zadanému <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> objemy.|[Změnit velikost elementu](../../../../docs/framework/wpf/graphics-multimedia/how-to-scale-an-element.md)|![Škálování obrázku](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Zkosí element o zadaný <xref:System.Windows.Media.SkewTransform.AngleX%2A> a <xref:System.Windows.Media.SkewTransform.AngleY%2A> objemy.|[Zkreslit Element](../../../../docs/framework/wpf/graphics-multimedia/how-to-skew-an-element.md)|![Obrázek zkreslit](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Přesune (překládá) elementu k zadanému <xref:System.Windows.Media.TranslateTransform.X%2A> a <xref:System.Windows.Media.TranslateTransform.Y%2A> objemy.|[Převede Element](../../../../docs/framework/wpf/graphics-multimedia/how-to-translate-an-element.md)|![Převede obrázek](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Pro vytvoření složitější transformace [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] poskytuje následující dvě třídy:  
  
|Třída|Popis|Příklad|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Skupiny více <xref:System.Windows.Media.TransformGroup> objekty do jednoho <xref:System.Windows.Media.Transform> , lze následně použít k transformaci vlastnosti.|[Použití více transformací k objektu](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Vytvoří vlastní transformace, které nejsou k dispozici jinými <xref:System.Windows.Media.Transform> třídy. Při použití <xref:System.Windows.Media.MatrixTransform>, zpracovávají matice přímo.|[Použít MatrixTransform k vytvoření vlastních transformací](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]také poskytuje [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] transformace. Další informace najdete v tématu <xref:System.Windows.Media.Media3D.Transform3D> třídy.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Běžné vlastnosti transformace  
 Je možné transformovat objekt deklarovat odpovídající <xref:System.Windows.Media.Transform> typ a použijte ho k transformaci vlastnosti objektu. Různé typy objektů, které mají různé typy vlastností transformace. Následující tabulka uvádí některé nejčastěji používané [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] typy a jejich vlastnosti transformace.  
  
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
## <a name="transformations-and-coordinate-systems"></a>Systémy souřadnic a transformace  
 Při transformaci objektu není právě transformujete objekt, transformovat souřadnicového prostoru, ve které tento objekt existuje. Ve výchozím nastavení, transformace je umístěn na střed v původu cílový objekt souřadnicový systém: (0,0). Jedinou výjimkou je <xref:System.Windows.Media.TranslateTransform>; <xref:System.Windows.Media.TranslateTransform> nemá žádné vlastnosti center nastavit, protože výsledek překlad je stejný bez ohledu na to, kde je na střed.  
  
 Následující příklad používá <xref:System.Windows.Media.RotateTransform> otočení <xref:System.Windows.Shapes.Rectangle> element, typ <xref:System.Windows.FrameworkElement>, o 45 stupňů o jeho výchozí centrum (0, 0). Následující obrázek znázorňuje efekt natočení.  
  
 ![Objekt FrameworkElement otočený o 45 stupňů o &#40; 0,0 &#41; ] (../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Elementu obdélníku otočený o 45 stupňů o bodu (0,0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Ve výchozím nastavení, otočí element o jeho levého horního rohu (0, 0). <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform>, A <xref:System.Windows.Media.SkewTransform> třídy zadejte CenterX a CenterY vlastnosti, které vám umožní zadat bod, ve kterém je použita transformace.  
  
 Další příklad také používá <xref:System.Windows.Media.RotateTransform> otočení <xref:System.Windows.Shapes.Rectangle> element o 45 stupňů; však této doby <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti jsou nastaveny tak, aby <xref:System.Windows.Media.RotateTransform> má Centrum z (25, 25). Následující obrázek znázorňuje efekt natočení.  
  
 ![Objekt Geometry otočený 45 stupňů o &#40; 25, 25 &#41; ] (../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Elementu obdélníku otočený o 45 stupňů o bodu (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>Převod FrameworkElement  
 Použití transformací pro <xref:System.Windows.FrameworkElement>, vytvoření <xref:System.Windows.Media.Transform> a použijte ho pro jednu ze dvou vlastností, <xref:System.Windows.FrameworkElement> třída poskytuje:  
  
-   <xref:System.Windows.FrameworkElement.LayoutTransform%2A>– Transformace, který je použit před průchodu rozložení. Pokud je použita pro transformaci, systém rozložení zpracovává transformovaných velikost a umístění elementu.  
  
-   <xref:System.Windows.UIElement.RenderTransform%2A>– Transformace, která upraví vzhled elementu, ale platí po dokončení průchodu rozložení. Pomocí <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost místo <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost, můžete získat výhody výkonu.  
  
 Vlastností, které budete používat? Kvůli výkonu výhody, které poskytuje, použijte <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost vždy, když je možné, zejména v případě, že používáte animovaný <xref:System.Windows.Media.Transform> objekty. Použití <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost při škálování, otáčení nebo zkosení a je nutné nadřazeného elementu upravit velikosti transformovaného elementu. Všimněte si, že, pokud se používá s <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> objekty pravděpodobně žádný vliv na elementy. Je to způsobeno rozložení systém vrátí přeložený element na původní pozici v rámci jeho zpracování.  
  
 Další informace o rozložení v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], najdete v části [rozložení](../../../../docs/framework/wpf/advanced/layout.md) Přehled.  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Příklad: Otočit FrameworkElement 45 stupňů  
 Následující příklad používá <xref:System.Windows.Media.RotateTransform> otočení tlačítko po směru hodinových ručiček o 45 stupňů. Tlačítko je součástí <xref:System.Windows.Controls.StackPanel> , má dva další tlačítka.  
  
 Ve výchozím nastavení <xref:System.Windows.Media.RotateTransform> otočí o bodu (0, 0). Vzhledem k tomu, že v příkladu neurčuje center hodnota, otočí tlačítko o bodu (0, 0), což je jeho levého horního rohu. <xref:System.Windows.Media.RotateTransform> Se použijí na <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost. Následující obrázek znázorňuje výsledek transformace.  
  
 ![Tlačítko transformované pomocí RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Po směru hodinových ručiček kolem od levého horního rohu 45 stupňů.  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 Další příklad také používá <xref:System.Windows.Media.RotateTransform> otočení tlačítko 45 stupňů doprava, ale také nastaví <xref:System.Windows.UIElement.RenderTransformOrigin%2A> u tlačítka (0,5, 0,5). Hodnota <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost je relativní vzhledem k velikosti tlačítko. V důsledku toho je oběh se použije k centru tlačítko místo jeho levého horního rohu. Následující obrázek znázorňuje výsledek transformace.  
  
 ![Tlačítko transformované o jeho center](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Po směru hodinových ručiček kolem 45 stupňů kolem center  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Následující příklad používá <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost místo <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost otočení tlačítko.  To způsobí, že transformace ovlivňují rozložení tlačítka, která aktivuje úplné průchodu systémem rozložení. V důsledku toho je tlačítko otáčet a potom změnit jejich umístění protože došlo ke změně jeho velikost. Následující obrázek znázorňuje výsledek transformace.  
  
 ![Tlačítko transformované pomocí LayoutTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
LayoutTransform umožňuje otočit tlačítko  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Animace transformace  
 Protože dědí z <xref:System.Windows.Media.Animation.Animatable> třídy, <xref:System.Windows.Media.Transform> třídy mohou být animace. Pro animaci <xref:System.Windows.Media.Transform>, použijte vlastnost, kterou chcete animace animaci kompatibilní.  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.Storyboard> a <xref:System.Windows.Media.Animation.DoubleAnimation> s <xref:System.Windows.Media.RotateTransform> aby <xref:System.Windows.Controls.Button> typu číselník zavedené po klepnutí.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Kompletní příklad, najdete v části [2-D transformací ukázka](http://go.microsoft.com/fwlink/?LinkID=158252). Další informace o animací najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Zmrazitelné funkce  
 Protože dědí z <xref:System.Windows.Freezable> třídy, <xref:System.Windows.Media.Transform> třídy poskytují několik speciální funkce: <xref:System.Windows.Media.Transform> objekty lze deklarovat jako [prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md), sdílené mezi více objektů, jen pro čtení ke zlepšení výkon, klonovat a provedené bezpečné pro přístup z více vláken. Další informace o různých funkcích, které jsou poskytovány <xref:System.Windows.Freezable> objekty, najdete [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Matrix>  
 [Postupy: témata](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Ukázka 2-D transformací](http://go.microsoft.com/fwlink/?LinkID=158252)
