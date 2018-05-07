---
title: 'Optimalizace výkonu: 2D grafika a obrázky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2-D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: 4e6b72dae863e89d70ec70c2cb99a5874581e9ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Optimalizace výkonu: 2D grafika a obrázky
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje širokou škálu 2D grafika a vytváření bitové kopie funkce, které lze optimalizovat pro požadavky vaší aplikace. Toto téma obsahuje informace o optimalizaci výkonu v těchto oblastech.  
  
  
<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>Kreslení a obrazců  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nabízí <xref:System.Windows.Media.Drawing> a <xref:System.Windows.Shapes.Shape> objekty představují grafické kreslení obsah. Ale <xref:System.Windows.Media.Drawing> objekty jsou jednodušší konstrukce než <xref:System.Windows.Shapes.Shape> objekty a lepší výkonové charakteristiky.  
  
 A <xref:System.Windows.Shapes.Shape> umožňuje kreslení obrazce grafické na obrazovku. Protože jsou odvozeny od <xref:System.Windows.FrameworkElement> třídy, <xref:System.Windows.Shapes.Shape> objekty mohou být použity uvnitř panelů a většina ovládacích prvků.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nabízí několik vrstev přístupu k grafika a vykreslování služby. V horní vrstvě <xref:System.Windows.Shapes.Shape> objekty jsou snadno použitelné a poskytují řady užitečných funkcí, jako je například rozložení a zpracování událostí. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje několik objektů tvar připravené k použití. Všechny objekty tvar dědí <xref:System.Windows.Shapes.Shape> třídy. K dispozici tvar objekty zahrnují <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, a <xref:System.Windows.Shapes.Rectangle>.  
  
 <xref:System.Windows.Media.Drawing> objekty, na druhé straně není odvozena od <xref:System.Windows.FrameworkElement> třídy a zajištění světlejšího váhy implementace pro vykreslování tvarů, obrázky a text.  
  
 Existují čtyři typy <xref:System.Windows.Media.Drawing> objekty:  
  
-   <xref:System.Windows.Media.GeometryDrawing> Kreslení obrazce.  
  
-   <xref:System.Windows.Media.ImageDrawing> Nakreslí obrázek.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> Kreslení textu.  
  
-   <xref:System.Windows.Media.DrawingGroup> Nakreslí kresby na další. Použijte skupinu kreslení kombinovat jiné kresby do jedné složené kreslení.  
  
 <xref:System.Windows.Media.GeometryDrawing> Objektu slouží k vykreslení geometrie obsahu. <xref:System.Windows.Media.Geometry> Třídy a konkrétní třídy, které jsou odvozeny od, jako například <xref:System.Windows.Media.CombinedGeometry>, <xref:System.Windows.Media.EllipseGeometry>, a <xref:System.Windows.Media.PathGeometry>, umožňují pro vykreslování 2D grafiky, jakož i poskytnutí vstupů do testování a výstřižek podpory. Objekty geometrie lze použít k definování oblast ovládacího prvku, například nebo k definování klip oblasti, kterou chcete použít na bitovou kopii. Jednoduché oblastech, jako je obdélníků a kroužky nebo složený oblasti vytvořit ze dvou nebo více objektů geometrie mohou být geometrie objekty. Složitější geometrickou oblasti lze vytvořit tím, že zkombinujete <xref:System.Windows.Media.PathSegment>-odvozené objekty, jako například <xref:System.Windows.Media.ArcSegment>, <xref:System.Windows.Media.BezierSegment>, a <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 Na ploše <xref:System.Windows.Media.Geometry> třídy a <xref:System.Windows.Shapes.Shape> třídy jsou velmi podobné. Jak se používají při vykreslování grafiky 2D a mají podobné konkrétní třídy odvozené z nich, například <xref:System.Windows.Media.EllipseGeometry> a <xref:System.Windows.Shapes.Ellipse>. Existují však rozdíly mezi těmito dvěma sadami třídy. Pro jeden <xref:System.Windows.Media.Geometry> třída chybí některé funkce <xref:System.Windows.Shapes.Shape> třídy, například možnost kreslení sám sebe. Kreslení geometrický objekt, musí být jiné třídy, jako je například DrawingContext, kreslení nebo cestu (je vhodné poznamenat, že se cesta ke obrazce) použít k provedení kreslení operaci. Pro třídu, která získává geometrický objekt, zatímco objektu obrazce obsahuje tyto vlastnosti jsou vlastnosti vykreslování například výplň, tahy a sílu tahu. Jedním ze způsobů zamyslet nad tento rozdíl je, že geometrický objekt definuje oblast, kruh například při objektu obrazce definuje oblast, definují způsob je danou oblast vyplněna a uvedených a účastní rozložení systému.  
  
 Vzhledem k tomu <xref:System.Windows.Shapes.Shape> objekty jsou odvozeny od <xref:System.Windows.FrameworkElement> třídy, pomocí nich můžete přidat podstatně víc využití paměti v aplikaci. Pokud skutečně není nutné <xref:System.Windows.FrameworkElement> funkce pro grafické obsah, zvažte použití světlejšího weight <xref:System.Windows.Media.Drawing> objekty.  
  
 Další informace o <xref:System.Windows.Media.Drawing> objekty, najdete v části [kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>StreamGeometry objekty  
 <xref:System.Windows.Media.StreamGeometry> Objekt je šedé – alternativa k <xref:System.Windows.Media.PathGeometry> pro vytvoření geometrické obrazce. Použití <xref:System.Windows.Media.StreamGeometry> když potřebujete popisují komplexní geometrie. <xref:System.Windows.Media.StreamGeometry> je optimalizovaná pro zpracování mnoho <xref:System.Windows.Media.PathGeometry> objekty a provede lépe ve srovnání s použitím mnoho jednotlivé <xref:System.Windows.Media.PathGeometry> objekty.  
  
 Následující příklad používá syntaxi atributů k vytvoření trojúhelníkovou <xref:System.Windows.Media.StreamGeometry> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Další informace o <xref:System.Windows.Media.StreamGeometry> objekty, najdete v části [vytvoření obrazce pomocí StreamGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>DrawingVisual objekty  
 <xref:System.Windows.Media.DrawingVisual> Objekt je lehké kreslení třídu, která se použije k vykreslení tvarů, Image nebo text. Tato třída se považuje za lightweight, protože neposkytuje rozložení nebo událostí zpracování, což zvyšuje jeho výkon. Z toho důvodu jsou ideální pro pozadí a vytvoříte čára. Další informace najdete v tématu [pomocí objekty DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>   
## <a name="images"></a>Obrázky  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vytvoření bitové kopie poskytuje výrazným vylepšením oproti možnosti vytváření bitové kopie v předchozích verzích [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Imaging možnosti, například zobrazení rastrový obrázek nebo pomocí bitovou kopii na běžného ovládacího prvku se primárně zpracovávaných Microsoft Windows zařízení rozhraní GDI (Graphics) nebo Microsoft Windows GDI + rozhraní (API). Těmto rozhraním API poskytuje základní funkce pro zpracování obrázků, ale chybějící funkce, například podporu rozšiřitelnosti kodeků a podporu HD bitové kopie. Rozhraní API Imaging WPF mít upravený tak, aby překonat nedostatků GDI a GDI + a zadejte novou sadu rozhraní API pro zobrazení a použití bitové kopie v rámci vaší aplikace.  
  
 Při použití bitové kopie, zvažte následující doporučení pro získání lepší výkon:  
  
-   Pokud vaše aplikace vyžaduje, abyste k zobrazení miniatur, zvažte vytvoření snížit velikost verzi image. Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] načte bitové kopie a dekóduje na jeho plnou velikost. Pokud chcete pouze miniatur verze bitové kopie, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nepotřebné dekóduje bitovou kopii do jeho plné velikosti a potom ho škáluje dolů velikost miniatur. Nechcete tuto nárokům, můžete buď požadavek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] k dekódování obrázek, který má velikost miniatur, nebo požádejte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] načíst obrázek velikosti miniatury.  
  
-   Vždy dekódovat bitovou kopii do požadované velikosti a ne do výchozí velikost. Jak je uvedeno nahoře, žádosti o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dekódování bitové kopie do požadované velikosti a výchozí plnou velikost. Se sníží pouze aplikace pracovní sadu, ale také rychlost provádění.  
  
-   Pokud je to možné kombinovat bitové kopie do jedné image, jako je film pruhu skládá z více bitových kopií.  
  
-   Další informace najdete v tématu [Imaging přehled](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 Při animaci škále všechny bitové mapy, výchozí vysoce kvalitní bitovou kopii znovu vzorkování algoritmus spotřebovat někdy dostatek systémových prostředků na způsobit snížení míry rámečku, účinně způsobující animace do trhaně. Nastavením <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> vlastnost <xref:System.Windows.Media.RenderOptions> do objektu <xref:System.Windows.Media.BitmapScalingMode.LowQuality> hladší animaci lze vytvořit při škálování rastrový obrázek. <xref:System.Windows.Media.BitmapScalingMode.LowQuality> režim informuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modul vykreslování přepnutí z algoritmu optimalizované kvality se optimalizované rychlost algoritmem při zpracování obrázků.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Media.BitmapScalingMode> pro objekt bitové kopie.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] neukládá do mezipaměti vykreslené obsah <xref:System.Windows.Media.TileBrush> objekty, jako například <xref:System.Windows.Media.DrawingBrush> a <xref:System.Windows.Media.VisualBrush>. Ve scénářích statické kde obsah ani použití <xref:System.Windows.Media.TileBrush> v scény mění, dává smysl, protože ho šetří grafické paměti. Neprovede jako mnohem smysl při <xref:System.Windows.Media.TileBrush> s statickým obsahem používá nestatické způsobem – například když statického <xref:System.Windows.Media.DrawingBrush> nebo <xref:System.Windows.Media.VisualBrush> je namapovaný na povrch rotační 3D objektu. Výchozí chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je znovu zpracovat celý obsah <xref:System.Windows.Media.DrawingBrush> nebo <xref:System.Windows.Media.VisualBrush> pro každý snímek, i když je obsah neměnné.  
  
 Nastavením <xref:System.Windows.Media.RenderOptions.CachingHint%2A> vlastnost <xref:System.Windows.Media.RenderOptions> do objektu <xref:System.Windows.Media.CachingHint.Cache> můžete zvýšit výkon pomocí verze uložené v mezipaměti objektů štětce vedle sebe.  
  
 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> a <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> hodnoty vlastností jsou relativní velikost hodnoty, které určují při zpracování <xref:System.Windows.Media.TileBrush> objekt by měl znovu vygenerovat z důvodu změn v škálování. Například podle nastavení <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> vlastnost 2.0, mezipaměti <xref:System.Windows.Media.TileBrush> pouze musí být znovu vygenerována při jeho velikost překračuje dvojnásobku velikosti aktuální mezipaměť.  
  
 Následující příklad ukazuje, jak použít možnost ukládání do mezipaměti nápovědu pro <xref:System.Windows.Media.DrawingBrush>.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Viz také  
 [Optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Plánování výkonu aplikace](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Využití výhod hardwaru](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Rozložení a návrh](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Chování objektu](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Prostředky aplikace](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Další výkonnostní doporučení](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [Tipy a triky animace](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
