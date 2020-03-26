---
title: Přehled transformace
ms.date: 03/30/2017
helpviewer_keywords:
- transformations [WPF], about transformations
- classes [WPF], 2D transform
- transform classes [WPF], 2D
- 2D transform classes
- FrameworkElement objects [WPF], rotating
- FrameworkElement objects [WPF], skewing
- FrameworkElement objects [WPF], translating
- Transforms [WPF], about Transforms
- FrameworkElement objects [WPF], scaling
ms.assetid: 8f153d5e-ed61-4aa5-a7cd-286f0c427a13
ms.openlocfilehash: c5f29404a301eb023ff24b2890531dede6440ec4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111956"
---
# <a name="transforms-overview"></a>Přehled transformace
Toto téma popisuje, jak <xref:System.Windows.Media.Transform> používat 2D třídy k otáčení, <xref:System.Windows.FrameworkElement> škálování, přesouvání (překládání) a zkosení objektů.  

<a name="whatIsATransformSection"></a>
## <a name="what-is-a-transform"></a>Co je transformace?  
 Definuje, <xref:System.Windows.Media.Transform> jak mapovat nebo transformovat body z jednoho souřadnicového prostoru do jiného souřadnicového prostoru. Toto mapování je popsáno transformací <xref:System.Windows.Media.Matrix>, což je <xref:System.Double> kolekce tří řádků se třemi sloupci hodnot.  
  
> [!NOTE]
> Windows Presentation Foundation (WPF) používá řádek hlavní matice. Vektory jsou vyjádřeny jako vektory řádků, nikoli jako vektory sloupců.  
  
 V následující tabulce je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uvedena struktura matice.  
  
### <a name="a-2d-transformation-matrix"></a>2D transformační matice  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Výchozí hodnota: 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Výchozí: 0,0|0,0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Výchozí: 0,0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Výchozí hodnota: 1.0|0,0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Výchozí: 0,0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Výchozí: 0,0|1.0|  
  
 Manipulací s hodnotami matice můžete objekt otáčet, měnit jejich velikost, zkosit a přesouvat (překládat). Pokud například změníte hodnotu v prvním sloupci <xref:System.Windows.Media.Matrix.OffsetX%2A> třetího řádku (hodnota) na 100, můžete ji použít k přesunutí objektu o 100 jednotek podél osy x. Pokud změníte hodnotu ve druhém sloupci druhého řádku na 3, můžete ji použít k roztažení objektu na trojnásobek jeho aktuální výšky. Pokud změníte obě hodnoty, přesunete objekt o 100 jednotek podél osy x a protáhnete jeho výšku koeficientem 3. Vzhledem k tomu, že Windows Presentation Foundation (WPF) podporuje pouze podobné transformace, hodnoty v pravém sloupci jsou vždy 0, 0, 1.  
  
 Přestože Windows Presentation Foundation (WPF) umožňuje přímo manipulovat s <xref:System.Windows.Media.Transform> hodnotami matice, poskytuje také několik tříd, které umožňují transformovat objekt bez znalosti, jak je nakonfigurována základní maticová struktura. <xref:System.Windows.Media.ScaleTransform> Například třída umožňuje škálovat objekt nastavením <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> jeho a vlastností namísto manipulace s transformační maticí. Podobně <xref:System.Windows.Media.RotateTransform> třída umožňuje otočit objekt pouhým nastavením <xref:System.Windows.Media.RotateTransform.Angle%2A> jeho vlastnosti.  
  
<a name="transformClassesSection"></a>
## <a name="transform-classes"></a>Transformovat třídy  
 Windows Presentation Foundation (WPF) poskytuje <xref:System.Windows.Media.Transform> následující 2D třídy pro běžné operace transformace:  
  
|Třída|Popis|Příklad|Obrázek|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Otočí prvek o zadaný <xref:System.Windows.Media.RotateTransform.Angle%2A>prvek .|[Otočení objektu](how-to-rotate-an-object.md)|![Otočit ilustrace](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Změní velikost prvku podle <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> zadaných a částek.|[Změna velikosti elementu](how-to-scale-an-element.md)|![Ilustrace měřítka](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Zkosí prvek o <xref:System.Windows.Media.SkewTransform.AngleX%2A> <xref:System.Windows.Media.SkewTransform.AngleY%2A> zadané částky a částky.|[Zkreslení elementu](how-to-skew-an-element.md)|![Zkosení, ilustrace](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Přesune (přeloží) prvek <xref:System.Windows.Media.TranslateTransform.X%2A> podle <xref:System.Windows.Media.TranslateTransform.Y%2A> zadaného a částek.|[Překlad elementu](how-to-translate-an-element.md)|![Přeložit ilustraci](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Pro vytváření složitější transformace, Windows Presentation Foundation (WPF) poskytuje následující dvě třídy:  
  
|Třída|Popis|Příklad|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Seskupí <xref:System.Windows.Media.TransformGroup> <xref:System.Windows.Media.Transform> více objektů do jednoho, který pak můžete použít na transformační vlastnosti.|[Použití několika transformací na objekt](how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Vytvoří vlastní transformace, které nejsou poskytovány jinými <xref:System.Windows.Media.Transform> třídami. Při použití <xref:System.Windows.Media.MatrixTransform>, můžete manipulovat Matrix přímo.|[Vytvoření vlastních transformací pomocí MatrixTransform](how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) také poskytuje 3D transformace. Další informace naleznete <xref:System.Windows.Media.Media3D.Transform3D> ve třídě.  
  
<a name="transformationproperties"></a>
## <a name="common-transformation-properties"></a>Běžné vlastnosti transformace  
 Jedním ze způsobů transformace objektu <xref:System.Windows.Media.Transform> je deklarovat příslušný typ a použít jej na vlastnost transformace objektu. Různé typy objektů mají různé typy vlastností transformace. V následující tabulce je uvedeno několik běžně používaných typů Windows Presentation Foundation (WPF) a jejich vlastnosti transformace.  
  
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
## <a name="transformations-and-coordinate-systems"></a>Transformace a souřadné systémy  
 Při transformaci objektu netransformujete pouze objekt, ale transformujete souřadnicový prostor, ve kterém tento objekt existuje. Ve výchozím nastavení je transformace vystředěna na počátek souřadnicového systému cílového objektu: (0,0). Jedinou výjimkou <xref:System.Windows.Media.TranslateTransform>je ; <xref:System.Windows.Media.TranslateTransform> a nemá žádné vlastnosti centra, které by bylo možné nastavit, protože efekt překladu je stejný bez ohledu na to, kde je vystředěn.  
  
 Následující příklad používá <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Shapes.Rectangle> otočit prvek, <xref:System.Windows.FrameworkElement>typ , o 45 stupňů kolem jeho výchozí ho středu (0, 0). Následující obrázek znázorňuje účinek otočení.  
  
 ![A FrameworkElement otočený o 45 stupňů o &#40;0,0&#41;](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Element Obdélník otočený o 45 stupňů kolem bodu (0,0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Ve výchozím nastavení se prvek otáčí kolem levého horního rohu (0, 0). <xref:System.Windows.Media.RotateTransform>Vlastnosti <xref:System.Windows.Media.ScaleTransform>, <xref:System.Windows.Media.SkewTransform> a , a centerx poskytují vlastnosti, které umožňují určit bod, ve kterém je transformace použita.  
  
 Další příklad také <xref:System.Windows.Media.RotateTransform> používá k <xref:System.Windows.Shapes.Rectangle> otočení prvku o 45 stupňů; však tentokrát <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti jsou <xref:System.Windows.Media.RotateTransform> nastaveny tak, aby má střed (25, 25). Následující obrázek znázorňuje účinek otočení.  
  
 ![Geometrie otočená o 45 stupňů kolem 25 &#40;, 25&#41;](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Obdélník ový prvek otočený o 45 stupňů kolem bodu (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>
## <a name="transforming-a-frameworkelement"></a>Transformace frameworkelement  
 Chcete-li použít <xref:System.Windows.FrameworkElement>transformace na <xref:System.Windows.Media.Transform> , vytvořte a aplikujte <xref:System.Windows.FrameworkElement> na jednu ze dvou vlastností, které třída poskytuje:  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A>– Transformace, která je použita před průchodrozložení. Po použití transformace systém rozložení zpracuje transformovanou velikost a umístění prvku.  
  
- <xref:System.Windows.UIElement.RenderTransform%2A>– Transformace, která upravuje vzhled prvku, ale je použita po dokončení průchodu rozložení. Pomocí vlastnosti <xref:System.Windows.UIElement.RenderTransform%2A> namísto <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnosti můžete získat výhody výkonu.  
  
 Kterou vlastnost byste měli použít? Z důvodu výhody výkonu, které <xref:System.Windows.UIElement.RenderTransform%2A> poskytuje, použijte vlastnost, kdykoli <xref:System.Windows.Media.Transform> je to možné, zejména při použití animovaných objektů. <xref:System.Windows.FrameworkElement.LayoutTransform%2A> Vlastnost použijte při změně měřítka, otočení nebo zkosení a potřebujete, aby se nadřazený prvek přizpůsobil transformované velikosti prvku. Všimněte si, že při <xref:System.Windows.FrameworkElement.LayoutTransform%2A> použití <xref:System.Windows.Media.TranslateTransform> s vlastností, objekty se zdají mít žádný vliv na prvky. Důvodem je, že systém rozložení vrátí přeložený prvek do původní polohy jako součást jeho zpracování.  
  
 Další informace o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]rozložení v tématu přehled [rozložení.](../advanced/layout.md)  
  
<a name="exampleRotateAnElement45degSection"></a>
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Příklad: Otočení prvku FrameworkElement o 45 stupňů  
 Následující příklad používá <xref:System.Windows.Media.RotateTransform> tlačítko ve směru hodinových ručiček o 45 stupňů. Tlačítko je obsaženo <xref:System.Windows.Controls.StackPanel> v a, která má další dvě tlačítka.  
  
 Ve výchozím <xref:System.Windows.Media.RotateTransform> nastavení se otáčí kolem bodu (0, 0). Vzhledem k tomu, že příklad neurčuje středovou hodnotu, tlačítko se otáčí kolem bodu (0, 0), což je jeho levý horní roh. Použije <xref:System.Windows.Media.RotateTransform> se na <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost. Následující obrázek znázorňuje výsledek transformace.  
  
 ![Tlačítko transformované pomocí RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Otáčení ve směru hodinových ručiček o 45 stupňů od levého horního rohu  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 Další příklad také <xref:System.Windows.Media.RotateTransform> používá tlačítko otočit o 45 stupňů ve <xref:System.Windows.UIElement.RenderTransformOrigin%2A> směru hodinových ručiček, ale také nastaví tlačítko na (0,5, 0,5). Hodnota vlastnosti <xref:System.Windows.UIElement.RenderTransformOrigin%2A> je relativní vzhledem k velikosti tlačítka. V důsledku toho je otočení aplikováno na střed tlačítka namísto levého horního rohu. Následující obrázek znázorňuje výsledek transformace.  
  
 ![Tlačítko transformované kolem jeho středu](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Otáčení ve směru hodinových ručiček o 45 stupňů kolem středu  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Následující příklad používá <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost namísto vlastnosti <xref:System.Windows.UIElement.RenderTransform%2A> otočit tlačítko.  To způsobí, že transformace ovlivnit rozložení tlačítka, který aktivuje úplný průchod systémem rozložení. V důsledku toho je tlačítko otočeno a poté přemístěno, protože se změnila jeho velikost. Následující obrázek znázorňuje výsledek transformace.  
  
 ![Tlačítko transformované pomocí LayoutTransform](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
LayoutTransform slouží k otočení tlačítka  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>
## <a name="animating-transformations"></a>Animace transformací  
 Protože dědí <xref:System.Windows.Media.Animation.Animatable> z třídy, <xref:System.Windows.Media.Transform> třídy mohou být animovány. Chcete-li <xref:System.Windows.Media.Transform>animovat , použijte animaci kompatibilního typu na vlastnost, kterou chcete animovat.  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.Storyboard> a <xref:System.Windows.Media.Animation.DoubleAnimation> a <xref:System.Windows.Media.RotateTransform> s, <xref:System.Windows.Controls.Button> aby se po klepnutí na místo zavrtalo.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Kompletní ukázku naleznete v tématu [2D transformace Ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms). Další informace o animacích naleznete v přehledu [animací](animation-overview.md).  
  
<a name="freezable_features"></a>
## <a name="freezable-features"></a>Zmrazitelné funkce  
 Vzhledem k tomu, že dědí z <xref:System.Windows.Freezable> třídy, <xref:System.Windows.Media.Transform> třída poskytuje několik speciálních funkcí: <xref:System.Windows.Media.Transform> objekty mohou být deklarovány jako [prostředky](../../../desktop-wpf/fundamentals/xaml-resources-define.md), sdílené mezi více objektů, jen pro čtení ke zlepšení výkonu, klonované a z přístupu k vláknu. Další informace o různých funkcích poskytovaných objekty <xref:System.Windows.Freezable> naleznete v tématu Přehled [mrazivých objektů](../advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [Témata s postupy](transformations-how-to-topics.md)
- [Ukázka 2D transformací](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
