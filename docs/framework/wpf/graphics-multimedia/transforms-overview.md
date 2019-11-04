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
ms.openlocfilehash: ead1d114f773cba88e8b3e20f395019fbde3ee15
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458593"
---
# <a name="transforms-overview"></a>Přehled transformace
Toto téma popisuje, jak použít třídy 2D <xref:System.Windows.Media.Transform> k otočení, škálování, přesunutí (překladu) a zkosení <xref:System.Windows.FrameworkElement> objektů.  

<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>Co je transformace?  
 <xref:System.Windows.Media.Transform> definuje, jak namapovat nebo Transformovat body z jednoho souřadnicového prostoru na jiný prostor souřadnic. Toto mapování je popsáno pomocí transformačního <xref:System.Windows.Media.Matrix>, což je kolekce tří řádků se třemi sloupci hodnot <xref:System.Double>.  
  
> [!NOTE]
> Windows Presentation Foundation (WPF) používá hlavní matice řádků. Vektory jsou vyjádřeny jako vektory řádků, nikoli vektory sloupce.  
  
 Následující tabulka ukazuje strukturu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] matice.  
  
### <a name="a-2-d-transformation-matrix"></a>Matice 2D transformace  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Výchozí: 1,0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Výchozí: 0,0|0,0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Výchozí: 0,0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Výchozí: 1,0|0,0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Výchozí: 0,0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Výchozí: 0,0|1.0|  
  
 Díky manipulaci s hodnotami matice můžete otáčet, škálovat, zkosit a přesouvat (překládat) objekt. Například pokud změníte hodnotu v prvním sloupci třetího řádku (<xref:System.Windows.Media.Matrix.OffsetX%2A> hodnota) na 100, můžete ji použít k přesunutí jednotky objektu 100 na ose x. Pokud změníte hodnotu ve druhém sloupci druhého řádku na 3, můžete ji použít k roztažení objektu na trojnásobnou aktuální výšku. Změníte-li obě hodnoty, přesunete jednotky objektu 100 podél osy x a roztáhnete její výšku o faktoru 3. Vzhledem k tomu, že Windows Presentation Foundation (WPF) podporuje pouze transformace vztahů, jsou hodnoty v pravém sloupci vždy 0, 0, 1.  
  
 I když Windows Presentation Foundation (WPF) umožňuje přímo manipulovat s hodnotami matrice, poskytuje také několik <xref:System.Windows.Media.Transform> tříd, které umožňují transformovat objekt bez znalosti způsobu konfigurace základní struktury matice. Například třída <xref:System.Windows.Media.ScaleTransform> umožňuje škálovat objekt nastavením vlastností <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> místo manipulace s maticí transformace. Podobně třída <xref:System.Windows.Media.RotateTransform> umožňuje otočit objekt pouhým nastavením jeho vlastnosti <xref:System.Windows.Media.RotateTransform.Angle%2A>.  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Třídy transformace  
 Windows Presentation Foundation (WPF) poskytuje následující dvojrozměrné <xref:System.Windows.Media.Transform> třídy pro běžné operace transformace:  
  
|Třída|Popis|Příklad|Obrázek|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Otočí element podle zadaného <xref:System.Windows.Media.RotateTransform.Angle%2A>.|[Otočení objektu](how-to-rotate-an-object.md)|![Otočit obrázek](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Škáluje prvek podle zadaného <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>ch částek.|[Změna velikosti elementu](how-to-scale-an-element.md)|![Měřítko – ilustrace](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Zkosí prvek podle zadaného <xref:System.Windows.Media.SkewTransform.AngleX%2A> a <xref:System.Windows.Media.SkewTransform.AngleY%2A>ch částek.|[Zkosení elementu](how-to-skew-an-element.md)|![Ilustrace zkosení](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Přesune (přenáší) prvek podle zadaného <xref:System.Windows.Media.TranslateTransform.X%2A> a <xref:System.Windows.Media.TranslateTransform.Y%2A>ch částek.|[Překlad elementu](how-to-translate-an-element.md)|![Přeložit obrázek](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Pro vytváření složitějších transformací Windows Presentation Foundation (WPF) poskytuje následující dvě třídy:  
  
|Třída|Popis|Příklad|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Seskupí více <xref:System.Windows.Media.TransformGroup> objektů do jednoho <xref:System.Windows.Media.Transform>, které pak můžete použít na transformaci vlastností.|[Použití několika transformací na objekt](how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Vytvoří vlastní transformace, které nejsou poskytovány jinými třídami <xref:System.Windows.Media.Transform>. Při použití <xref:System.Windows.Media.MatrixTransform>pracujete s maticí přímo.|[Vytvoření vlastních transformací pomocí MatrixTransform](how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) poskytuje také 3D transformace. Další informace naleznete v tématu Třída <xref:System.Windows.Media.Media3D.Transform3D>.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Běžné vlastnosti transformace  
 Jedním ze způsobů, jak transformovat objekt, je deklarovat příslušný typ <xref:System.Windows.Media.Transform> a použít ho na vlastnost Transform objektu. Různé typy objektů mají různé typy transformačních vlastností. Následující tabulka uvádí několik běžně používaných typů Windows Presentation Foundation (WPF) a jejich vlastnosti transformace.  
  
|Typ|Vlastnosti transformace|  
|----------|-------------------------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A><xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A><xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## <a name="transformations-and-coordinate-systems"></a>Transformace a systémy souřadnic  
 Při transformaci objektu neprovedete pouze transformaci objektu, transformujte místo, ve kterém objekt existuje. Ve výchozím nastavení je transformace na střed počátku souřadnicového systému cílového objektu: (0, 0). Jedinou výjimkou je <xref:System.Windows.Media.TranslateTransform>; <xref:System.Windows.Media.TranslateTransform> nemá žádné vlastnosti centra, které by bylo možné nastavit, protože účinek překladu je stejný bez ohledu na to, kde je na střed.  
  
 Následující příklad používá <xref:System.Windows.Media.RotateTransform> k otočení elementu <xref:System.Windows.Shapes.Rectangle>, typu <xref:System.Windows.FrameworkElement>, o výchozí střed (0, 0), od 45 stupňů. Následující ilustrace znázorňuje efekt otočení.  
  
 ![Objekt FrameworkElement otočený 45 stupňů o &#40;0, 0&#41;](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Prvek obdélníku otočený o 45 stupňů od bodu (0, 0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Ve výchozím nastavení se element otáčí o jeho levém horním rohu (0, 0). Třídy <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform>a <xref:System.Windows.Media.SkewTransform> poskytují vlastnosti CenterX a CenterY, které umožňují určit bod, ve kterém se transformace aplikuje.  
  
 Následující příklad také používá <xref:System.Windows.Media.RotateTransform> k otočení elementu <xref:System.Windows.Shapes.Rectangle> o 45 stupňů; Tentokrát se ale vlastnosti <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> nastavují tak, že <xref:System.Windows.Media.RotateTransform> má střed (25, 25). Následující ilustrace znázorňuje efekt otočení.  
  
 ![Geometrie otočená o 45 stupňů přibližně &#40;25, 25&#41;](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Prvek obdélníku otočený o 45 stupňů od bodu (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>Transformace prvku FrameworkElement  
 Chcete-li použít transformace na <xref:System.Windows.FrameworkElement>, vytvořte <xref:System.Windows.Media.Transform> a použijte ji na jednu ze dvou vlastností, které poskytuje třída <xref:System.Windows.FrameworkElement>:  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A> – transformace, která se aplikuje před Pass-layout. Po použití transformace systém rozložení zpracuje transformované velikosti a polohu prvku.  
  
- <xref:System.Windows.UIElement.RenderTransform%2A> – transformace, která upravuje vzhled prvku, ale je použita po dokončení úspěšnosti rozložení. Pomocí vlastnosti <xref:System.Windows.UIElement.RenderTransform%2A> místo vlastnosti <xref:System.Windows.FrameworkElement.LayoutTransform%2A> můžete získat výhody výkonu.  
  
 Kterou vlastnost byste měli použít? Z důvodu výhod výkonu, které poskytuje, použijte vlastnost <xref:System.Windows.UIElement.RenderTransform%2A>, kdykoli je to možné, zejména při použití animovaných <xref:System.Windows.Media.Transform> objektů. Použijte vlastnost <xref:System.Windows.FrameworkElement.LayoutTransform%2A> při škálování, otočení nebo zkosení a potřebujete, aby byl nadřízený prvek upraven na transformované velikosti elementu. Všimněte si, že při použití s vlastností <xref:System.Windows.FrameworkElement.LayoutTransform%2A> se nezobrazují <xref:System.Windows.Media.TranslateTransform> objektů, které by měly mít žádný vliv na prvky. Důvodem je, že systém rozložení vrátí přeložený prvek do původní pozice jako součást jeho zpracování.  
  
 Další informace o rozložení v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]najdete v tématu Přehled [rozložení](../advanced/layout.md) .  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Příklad: otočení stupně 45.  
 Následující příklad používá <xref:System.Windows.Media.RotateTransform> k otočení tlačítka po směru hodinových ručiček o 45 stupňů. Tlačítko je obsaženo v <xref:System.Windows.Controls.StackPanel>, která má dvě další tlačítka.  
  
 Ve výchozím nastavení se <xref:System.Windows.Media.RotateTransform> otočí o bod (0, 0). Vzhledem k tomu, že příklad neurčuje hodnotu středu, tlačítko se otočí o bod (0, 0), který je v levém horním rohu. <xref:System.Windows.Media.RotateTransform> se aplikuje na vlastnost <xref:System.Windows.UIElement.RenderTransform%2A>. Následující ilustrace znázorňuje výsledek transformace.  
  
 ![Tlačítko transformované pomocí RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Otočení po směru hodinových ručiček 45 stupňů z levého horního rohu  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 Následující příklad také používá <xref:System.Windows.Media.RotateTransform> k otočení tlačítka 45 stupňů doprava, ale také nastaví <xref:System.Windows.UIElement.RenderTransformOrigin%2A> tlačítka na (0,5, 0,5). Hodnota vlastnosti <xref:System.Windows.UIElement.RenderTransformOrigin%2A> je relativní vzhledem k velikosti tlačítka. V důsledku toho se rotace aplikuje na střed tlačítka místo v levém horním rohu. Následující ilustrace znázorňuje výsledek transformace.  
  
 ![Tlačítko, které se transformuje na střed](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Otáčení po směru hodinových ručiček 45 stupňů kolem středu  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Následující příklad používá vlastnost <xref:System.Windows.FrameworkElement.LayoutTransform%2A> namísto vlastnosti <xref:System.Windows.UIElement.RenderTransform%2A> k otočení tlačítka.  To způsobí, že transformace ovlivní rozložení tlačítka, které spustí úplný průchod systémem rozložení. V důsledku toho se tlačítko otočí a pak se přemístí, protože se změnila jeho velikost. Následující ilustrace znázorňuje výsledek transformace.  
  
 ![Tlačítko transformované pomocí LayoutTransform](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
LayoutTransform použitý k otočení tlačítka  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Animace transformací  
 Vzhledem k tomu, že dědí z třídy <xref:System.Windows.Media.Animation.Animatable>, mohou být <xref:System.Windows.Media.Transform> třídy animovány. Chcete-li animovat <xref:System.Windows.Media.Transform>, použijte animaci kompatibilního typu na vlastnost, kterou chcete animovat.  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.Storyboard> a <xref:System.Windows.Media.Animation.DoubleAnimation> s <xref:System.Windows.Media.RotateTransform> k tomu, aby se při kliknutí na místo na <xref:System.Windows.Controls.Button> číselník.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Úplnou ukázku najdete v tématu [Ukázka transformací 2D](https://go.microsoft.com/fwlink/?LinkID=158252). Další informace o animacích najdete v [přehledu animace](animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Funkce Freezable  
 Vzhledem k tomu, že dědí z třídy <xref:System.Windows.Freezable>, poskytuje <xref:System.Windows.Media.Transform> třídy několik speciálních funkcí: <xref:System.Windows.Media.Transform> objektů lze deklarovat jako [prostředky](../../../desktop-wpf/fundamentals/xaml-resources-define.md), sdílet mezi více objekty, které jsou určeny jen pro čtení, aby bylo možné zvýšit výkon, klonovat a vytvořit bezpečný přístup z více vláken. Další informace o různých funkcích, které poskytuje <xref:System.Windows.Freezable> objekty, najdete v tématu [Přehled objektů Freezable](../advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [Témata s postupy](transformations-how-to-topics.md)
- [Ukázka dvou D transformací](https://go.microsoft.com/fwlink/?LinkID=158252)
