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
ms.openlocfilehash: 89b781d3e5b88a66598a301a1d08cf7dfedd57a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962901"
---
# <a name="transforms-overview"></a>Přehled transformace
Toto téma popisuje, jak použít <xref:System.Windows.Media.Transform> třídy 2D k otočení, škálování, přesunutí (posunutí) a zkosení <xref:System.Windows.FrameworkElement> objektů.  

<a name="whatIsATransformSection"></a>   
## <a name="what-is-a-transform"></a>Co je transformace?  
 <xref:System.Windows.Media.Transform> Definuje, jak namapovat nebo Transformovat body z jednoho souřadnicového prostoru na jiný prostor souřadnic. Toto mapování je popsáno transformací <xref:System.Windows.Media.Matrix>, což je kolekce tří řádků se třemi <xref:System.Double> sloupci hodnot.  
  
> [!NOTE]
> Windows Presentation Foundation (WPF) používá hlavní matice řádků. Vektory jsou vyjádřeny jako vektory řádků, nikoli vektory sloupce.  
  
 V následující tabulce je uvedena struktura [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] matice.  
  
### <a name="a-2-d-transformation-matrix"></a>Matice 2D transformace  
  
||||  
|-|-|-|  
|<xref:System.Windows.Media.Matrix.M11%2A><br /><br /> Výchozí 1.0|<xref:System.Windows.Media.Matrix.M12%2A><br /><br /> Výchozí 0.0|0.0|  
|<xref:System.Windows.Media.Matrix.M21%2A><br /><br /> Výchozí 0.0|<xref:System.Windows.Media.Matrix.M22%2A><br /><br /> Výchozí 1.0|0.0|  
|<xref:System.Windows.Media.Matrix.OffsetX%2A><br /><br /> Výchozí 0.0|<xref:System.Windows.Media.Matrix.OffsetY%2A><br /><br /> Výchozí 0.0|1.0|  
  
 Díky manipulaci s hodnotami matice můžete otáčet, škálovat, zkosit a přesouvat (překládat) objekt. Například pokud změníte hodnotu v prvním sloupci třetího řádku ( <xref:System.Windows.Media.Matrix.OffsetX%2A> hodnota) na 100, můžete ji použít k přesunutí jednotky objektu 100 na ose x. Pokud změníte hodnotu ve druhém sloupci druhého řádku na 3, můžete ji použít k roztažení objektu na trojnásobnou aktuální výšku. Změníte-li obě hodnoty, přesunete jednotky objektu 100 podél osy x a roztáhnete její výšku o faktoru 3. Vzhledem k tomu, že Windows Presentation Foundation (WPF) podporuje pouze transformace vztahů, jsou hodnoty v pravém sloupci vždy 0, 0, 1.  
  
 I když Windows Presentation Foundation (WPF) umožňuje přímo manipulovat s hodnotami matice, poskytuje také několik <xref:System.Windows.Media.Transform> tříd, které umožňují transformovat objekt bez znalosti způsobu konfigurace základní struktury matice. Například <xref:System.Windows.Media.ScaleTransform> třída umožňuje škálovat objekt <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> nastavením vlastností a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> namísto manipulace s transformační maticí. Podobně třída umožňuje otočit objekt pouhým nastavením jeho <xref:System.Windows.Media.RotateTransform.Angle%2A> vlastnosti. <xref:System.Windows.Media.RotateTransform>  
  
<a name="transformClassesSection"></a>   
## <a name="transform-classes"></a>Třídy transformace  
 Windows Presentation Foundation (WPF) poskytuje následující dvojrozměrné <xref:System.Windows.Media.Transform> třídy pro běžné operace transformace:  
  
|Třída|Popis|Příklad|Obrázek|  
|-----------|-----------------|-------------|------------------|  
|<xref:System.Windows.Media.RotateTransform>|Otočí element o zadanou <xref:System.Windows.Media.RotateTransform.Angle%2A>.|[Otočení objektu](how-to-rotate-an-object.md)|![Otočit obrázek](./media/graphicsmm-thumbnails-rotate.png "graphicsmm_thumbnails_rotate")|  
|<xref:System.Windows.Media.ScaleTransform>|Škáluje prvek podle zadané <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> hodnoty a. <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>|[Změna velikosti elementu](how-to-scale-an-element.md)|![Měřítko – ilustrace](./media/graphicsmm-thumbnails-scale.png "graphicsmm_thumbnails_scale")|  
|<xref:System.Windows.Media.SkewTransform>|Zkosí prvek podle zadaného <xref:System.Windows.Media.SkewTransform.AngleX%2A> a <xref:System.Windows.Media.SkewTransform.AngleY%2A> množství.|[Zkosení elementu](how-to-skew-an-element.md)|![Ilustrace zkosení](./media/graphicsmm-thumbnails-skew.png "graphicsmm_thumbnails_skew")|  
|<xref:System.Windows.Media.TranslateTransform>|Přesune (převede) prvek o zadaný <xref:System.Windows.Media.TranslateTransform.X%2A> a <xref:System.Windows.Media.TranslateTransform.Y%2A> množství.|[Překlad elementu](how-to-translate-an-element.md)|![Přeložit obrázek](./media/graphicsmm-thumbnails-translate.png "graphicsmm_thumbnails_translate")|  
  
 Pro vytváření složitějších transformací Windows Presentation Foundation (WPF) poskytuje následující dvě třídy:  
  
|Třída|Popis|Příklad|  
|-----------|-----------------|-------------|  
|<xref:System.Windows.Media.TransformGroup>|Seskupí <xref:System.Windows.Media.TransformGroup> více objektů do jediného <xref:System.Windows.Media.Transform> , které pak můžete použít na transformaci vlastností.|[Použití několika transformací na objekt](how-to-apply-multiple-transforms-to-an-object.md)|  
|<xref:System.Windows.Media.MatrixTransform>|Vytvoří vlastní transformace, které nejsou poskytovány jinými <xref:System.Windows.Media.Transform> třídami. Když použijete <xref:System.Windows.Media.MatrixTransform>, budete pracovat s maticí přímo.|[Vytvoření vlastních transformací pomocí MatrixTransform](how-to-use-a-matrixtransform-to-create-custom-transforms.md)|  
  
 Windows Presentation Foundation (WPF) poskytuje také 3D transformace. Další informace naleznete v tématu <xref:System.Windows.Media.Media3D.Transform3D> třída.  
  
<a name="transformationproperties"></a>   
## <a name="common-transformation-properties"></a>Běžné vlastnosti transformace  
 Jedním ze způsobů, jak transformovat objekt, je deklarovat <xref:System.Windows.Media.Transform> příslušný typ a použít ho na vlastnost Transform objektu. Různé typy objektů mají různé typy transformačních vlastností. Následující tabulka uvádí několik běžně používaných typů Windows Presentation Foundation (WPF) a jejich vlastnosti transformace.  
  
|type|Vlastnosti transformace|  
|----------|-------------------------------|  
|<xref:System.Windows.Media.Brush>|<xref:System.Windows.Media.Brush.Transform%2A>, <xref:System.Windows.Media.Brush.RelativeTransform%2A>|  
|<xref:System.Windows.Media.ContainerVisual>|<xref:System.Windows.Media.ContainerVisual.Transform%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.Transform%2A>|  
|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.UIElement.RenderTransform%2A>, <xref:System.Windows.FrameworkElement.LayoutTransform%2A>|  
|<xref:System.Windows.Media.Geometry>|<xref:System.Windows.Media.Geometry.Transform%2A>|  
|<xref:System.Windows.Media.TextEffect>|<xref:System.Windows.Media.TextEffect.Transform%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.RenderTransform%2A>|  
  
<a name="transformcenter"></a>   
## <a name="transformations-and-coordinate-systems"></a>Transformace a systémy souřadnic  
 Při transformaci objektu neprovedete pouze transformaci objektu, transformujte místo, ve kterém objekt existuje. Ve výchozím nastavení je transformace na střed počátku souřadnicového systému cílového objektu: (0,0). Jedinou výjimkou je <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.Media.TranslateTransform> ; neobsahuje žádné vlastnosti centra, které by bylo možné nastavit, protože účinek překladu je stejný bez ohledu na to, kde je na střed.  
  
 Následující příklad používá <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Shapes.Rectangle> otočení elementu, typu o <xref:System.Windows.FrameworkElement>výchozí střed (0, 0) od 45 stupňů. Následující ilustrace znázorňuje efekt otočení.  
  
 ![Objekt FrameworkElement otočený 45 stupňů o &#40;0, 0&#41; ](./media/graphicsmm-fe-rotated-about-upperleft-corner.png "graphicsmm_FE_rotated_about_upperleft_corner")  
Prvek obdélníku otočený o 45 stupňů od bodu (0, 0)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedabouttopleft)]  
  
 Ve výchozím nastavení se element otáčí o jeho levém horním rohu (0, 0). Třídy <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.ScaleTransform> a<xref:System.Windows.Media.SkewTransform> poskytují vlastnosti CenterX a CenterY, které umožňují určit bod, ve kterém se transformace aplikuje.  
  
 Následující příklad také používá <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Shapes.Rectangle> otočení prvku o 45 stupňů; tentokrát <xref:System.Windows.Media.RotateTransform.CenterX%2A> však jsou vlastnosti a <xref:System.Windows.Media.RotateTransform.CenterY%2A> nastaveny tak, že <xref:System.Windows.Media.RotateTransform> má střed (25, 25). Následující ilustrace znázorňuje efekt otočení.  
  
 ![Geometrie otočená o 45 stupňů přibližně &#40;25, 25&#41; ](./media/graphicsmm-fe-rotated-about-center.png "graphicsmm_FE_rotated_about_center")  
Prvek obdélníku otočený o 45 stupňů od bodu (25, 25)  
  
 [!code-xaml[Transforms_snip#TransformsFERotatedAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/CoordinateSystemExample.xaml#transformsferotatedaboutcenter)]  
  
<a name="layoutTransformsAndRenderTransformsSection"></a>   
## <a name="transforming-a-frameworkelement"></a>Transformace prvku FrameworkElement  
 Chcete-li použít transformace <xref:System.Windows.FrameworkElement>na, <xref:System.Windows.Media.Transform> vytvořte a použijte ho pro jednu ze dvou vlastností, které <xref:System.Windows.FrameworkElement> poskytuje třída:  
  
- <xref:System.Windows.FrameworkElement.LayoutTransform%2A>– Transformace, která se aplikuje před Pass-layout. Po použití transformace systém rozložení zpracuje transformované velikosti a polohu prvku.  
  
- <xref:System.Windows.UIElement.RenderTransform%2A>– Transformace, která upravuje vzhled prvku, ale je použita po dokončení úspěšnosti rozložení. Pomocí <xref:System.Windows.UIElement.RenderTransform%2A> vlastnosti namísto <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnosti můžete získat výhody výkonu.  
  
 Kterou vlastnost byste měli použít? Z důvodu výhod výkonu, které poskytuje, použijte <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost, kdykoli je to možné, zejména při použití animovaných <xref:System.Windows.Media.Transform> objektů. <xref:System.Windows.FrameworkElement.LayoutTransform%2A> Použijte vlastnost při škálování, otočení nebo zkosení a potřebujete, aby byl nadřazený prvek prvku upraven na transformované velikosti elementu. Všimněte si, že při použití s <xref:System.Windows.FrameworkElement.LayoutTransform%2A> <xref:System.Windows.Media.TranslateTransform> vlastností se objekty jeví jako nemusejí mít žádný vliv na prvky. Důvodem je, že systém rozložení vrátí přeložený prvek do původní pozice jako součást jeho zpracování.  
  
 Další informace o rozložení v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]nástroji najdete v tématu Přehled [rozložení](../advanced/layout.md) .  
  
<a name="exampleRotateAnElement45degSection"></a>   
## <a name="example-rotate-a-frameworkelement-45-degrees"></a>Příklad: Otočení stupně FrameworkElement 45  
 Následující příklad používá <xref:System.Windows.Media.RotateTransform> k otočení tlačítka po směru hodinových ručiček o 45 stupňů. Tlačítko je obsaženo v <xref:System.Windows.Controls.StackPanel> , které má dvě další tlačítka.  
  
 Ve výchozím nastavení <xref:System.Windows.Media.RotateTransform> se otáčí kolem bodu (0, 0). Vzhledem k tomu, že příklad neurčuje hodnotu středu, tlačítko se otočí o bod (0, 0), který je v levém horním rohu. <xref:System.Windows.Media.RotateTransform> Je použita<xref:System.Windows.UIElement.RenderTransform%2A> na vlastnost. Následující ilustrace znázorňuje výsledek transformace.  
  
 ![Tlačítko transformované pomocí RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Otočení po směru hodinových ručiček 45 stupňů z levého horního rohu  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 Následující příklad také používá <xref:System.Windows.Media.RotateTransform> k otočení tlačítka 45 stupňů doprava, ale také <xref:System.Windows.UIElement.RenderTransformOrigin%2A> nastaví tlačítko na (0,5, 0,5). Hodnota <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnosti je relativní vzhledem k velikosti tlačítka. V důsledku toho se rotace aplikuje na střed tlačítka místo v levém horním rohu. Následující ilustrace znázorňuje výsledek transformace.  
  
 ![Tlačítko, které se transformuje na střed](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Otáčení po směru hodinových ručiček 45 stupňů kolem středu  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Následující příklad používá <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost namísto <xref:System.Windows.UIElement.RenderTransform%2A> vlastnosti k otočení tlačítka.  To způsobí, že transformace ovlivní rozložení tlačítka, které spustí úplný průchod systémem rozložení. V důsledku toho se tlačítko otočí a pak se přemístí, protože se změnila jeho velikost. Následující ilustrace znázorňuje výsledek transformace.  
  
 ![Tlačítko transformované pomocí LayoutTransform](./media/graphicsmm-layouttransform.png "graphicsmm_LayoutTransform")  
LayoutTransform použitý k otočení tlačítka  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample3](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample3)]  
  
<a name="animate_transforms"></a>   
## <a name="animating-transformations"></a>Animace transformací  
 Vzhledem k <xref:System.Windows.Media.Animation.Animatable> tomu <xref:System.Windows.Media.Transform> , že dědí z třídy, třídy mohou být animovány. Chcete-li <xref:System.Windows.Media.Transform>animovat, použijte animaci kompatibilního typu na vlastnost, kterou chcete animovat.  
  
 V následujícím příkladu je použita <xref:System.Windows.Media.Animation.Storyboard> značka <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Controls.Button> a s <xref:System.Windows.Media.RotateTransform> a, která při kliknutí umístí na místo.  
  
 [!code-xaml[Transforms_snip#GraphicsMMAnimatedRotateButtonExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonAnimatedRotateTransformExample.xaml#graphicsmmanimatedrotatebuttonexamplewholepage)]  
  
 Úplnou ukázku najdete v tématu [Ukázka transformací 2D](https://go.microsoft.com/fwlink/?LinkID=158252). Další informace o animacích najdete v [přehledu animace](animation-overview.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Funkce Freezable  
 Vzhledem k tomu <xref:System.Windows.Media.Transform> , že <xref:System.Windows.Freezable> dědí z třídy, poskytuje třída několik speciálních funkcí <xref:System.Windows.Media.Transform> : objekty mohou být deklarovány jako [prostředky](../advanced/xaml-resources.md), sdílené mezi více objekty, pro zlepšení výkonu, klonování a bylo zabezpečeno pro přístup z více vláken. Další informace o různých funkcích, které jsou poskytovány <xref:System.Windows.Freezable> objekty, naleznete v tématu [Freezable Objects Overview](../advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Matrix>
- [Témata s postupy](transformations-how-to-topics.md)
- [Ukázka dvou D transformací](https://go.microsoft.com/fwlink/?LinkID=158252)
