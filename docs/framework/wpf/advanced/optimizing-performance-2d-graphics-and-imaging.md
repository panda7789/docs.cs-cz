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
ms.openlocfilehash: 25803bd772832cd22e855f530d10a3f3639c180c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348447"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Optimalizace výkonu: 2D grafika a obrázky
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje širokou škálu 2D grafika a funkce pro zpracování obrázků lze optimalizovat pro potřeby vaší aplikace. Toto téma obsahuje informace o optimalizaci výkonu v těchto oblastech.  

<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>Kreslení a obrazce  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje <xref:System.Windows.Media.Drawing> a <xref:System.Windows.Shapes.Shape> objekty k reprezentaci grafické vykreslování obsahu. Ale <xref:System.Windows.Media.Drawing> objekty jsou jednodušší konstrukce než <xref:System.Windows.Shapes.Shape> objekty a poskytuje lepší výkonové charakteristiky.  
  
 A <xref:System.Windows.Shapes.Shape> je možné kreslit grafické obrazce na obrazovku. Protože jsou odvozeny z <xref:System.Windows.FrameworkElement> třídy, <xref:System.Windows.Shapes.Shape> objekty mohou být použity uvnitř panelů a většina ovládacích prvků.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nabízí několik úrovní přístupu k grafické a vykreslovací služby. V horní vrstvě <xref:System.Windows.Shapes.Shape> objekty jsou snadné použití a poskytují mnoho užitečných funkcí, jako je rozložení a zpracování událostí. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje řadu připravených k použití shape – objekty obrazce. Dědí všechny objekty obrazce <xref:System.Windows.Shapes.Shape> třídy. K dispozici shape – objekty zahrnují <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, a <xref:System.Windows.Shapes.Rectangle>.  
  
 <xref:System.Windows.Media.Drawing> objekty, na druhé straně není odvozen od <xref:System.Windows.FrameworkElement> třídy a poskytnout implementaci nenáročný pro vykreslování tvarů, obrázky a text.  
  
 Existují čtyři druhy <xref:System.Windows.Media.Drawing> objekty:  
  
- <xref:System.Windows.Media.GeometryDrawing> Nakreslí obrazec.  
  
- <xref:System.Windows.Media.ImageDrawing> Nakreslí obrázek.  
  
- <xref:System.Windows.Media.GlyphRunDrawing> Kreslení textu.  
  
- <xref:System.Windows.Media.DrawingGroup> Nakreslí jiných kreslení. Pomocí vykreslení skupiny můžete kombinovat další drawings do jednoho kompozitní kresby.  
  
 <xref:System.Windows.Media.GeometryDrawing> Objektu se použije k vykreslení obsahu geometry. <xref:System.Windows.Media.Geometry> Třídy a konkrétními třídami, které jsou odvozeny z něj, jako například <xref:System.Windows.Media.CombinedGeometry>, <xref:System.Windows.Media.EllipseGeometry>, a <xref:System.Windows.Media.PathGeometry>, poskytují prostředky pro vykreslování 2D grafika, stejně jako spuštění testu a podporu oříznutí. Geometrické objekty je možné definovat oblasti ovládacího prvku, například nebo k definování oblast ústřižku použít na bitovou kopii. Geometrické objekty mohou být jednoduché oblastech, třeba obdélníky a kruhy nebo složený oblastech vytvořené ze dvou nebo více geometrické objekty. Je možné vytvořit složitější geometrické oblasti tím, že zkombinujete <xref:System.Windows.Media.PathSegment>-odvozené objekty, jako například <xref:System.Windows.Media.ArcSegment>, <xref:System.Windows.Media.BezierSegment>, a <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 Na ploše <xref:System.Windows.Media.Geometry> třídy a <xref:System.Windows.Shapes.Shape> třídy jsou velmi podobné. Jak se používají při vykreslování 2D grafika a mají podobné konkrétních tříd, které jsou odvozeny z nich, například <xref:System.Windows.Media.EllipseGeometry> a <xref:System.Windows.Shapes.Ellipse>. Nicméně existují důležité rozdíly mezi těmito dvěma sadami třídy. Za prvé <xref:System.Windows.Media.Geometry> třída nemá některé funkce <xref:System.Windows.Shapes.Shape> třídy, jako je například schopnost vykreslit. Chcete-li nakreslit objektu geometry, musí využívat jiné třídy, jako je například DrawingContext, kreslení nebo cesta (je vhodné poznamenat, že cesta je tvar) k provedení této operace kreslení. Na třídu, která získává objektu geometry, zatímco objekt shape obsahuje tyto vlastnosti jsou vlastnosti vykreslování, jako je výplň, tahy a tloušťka tahu. Jedním ze způsobů Zamyslete se nad tento rozdíl je, že geometrický objekt definuje oblast, kruh například při tvar objektu definuje oblast, definují způsob této oblasti je vyplněný a uvedených a účastní se systém rozložení.  
  
 Protože <xref:System.Windows.Shapes.Shape> objekty jsou odvozeny z <xref:System.Windows.FrameworkElement> třídy, jejich používání lze přidat mnohem větší spotřebu paměti v aplikaci. Pokud se ve skutečnosti není nutné <xref:System.Windows.FrameworkElement> funkce pro grafického obsahu, zvažte použití míň náročné <xref:System.Windows.Media.Drawing> objekty.  
  
 Další informace o <xref:System.Windows.Media.Drawing> objekty, najdete [kreslení objekty – přehled](../graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>Streamgeometry – objekty  
 <xref:System.Windows.Media.StreamGeometry> Objektu je zjednodušené alternativou k <xref:System.Windows.Media.PathGeometry> pro vytvoření geometrické tvary. Použití <xref:System.Windows.Media.StreamGeometry> když potřebujete komplexní geometrie popisují. <xref:System.Windows.Media.StreamGeometry> je optimalizovaný pro zpracování mnoho <xref:System.Windows.Media.PathGeometry> objektů a vrací lepší výsledky při ve srovnání s použitím mnoho jednotlivých <xref:System.Windows.Media.PathGeometry> objekty.  
  
 Následující příklad používá syntaxi atributů k vytvoření trojúhelníkové <xref:System.Windows.Media.StreamGeometry> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Další informace o <xref:System.Windows.Media.StreamGeometry> objekty, najdete [vytvoření tvaru použitím StreamGeometry](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>Objekty DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> Objekt je zjednodušenou kreslení třídu, která se použije k vykreslení obrazce, Image nebo text. Tato třída se považuje za jednoduché, protože neposkytuje rozložení nebo událostí zpracování, což zvyšuje výkon. Z tohoto důvodu jsou ideální pro pozadí a klipart kreslení. Další informace najdete v tématu [použití objektů DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>   
## <a name="images"></a>Obrázky  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vytvoření bitové kopie nabízí přináší značné vylepšení v porovnání s funkce pro zpracování obrázků v předchozích verzích [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Imaging možnosti, jako například zobrazení rastrový obrázek nebo pomocí image na běžný ovládací prvek se primárně stará samotná Microsoft Windows rozhraní GDI (Graphics Device) nebo Microsoft Windows GDI + rozhraní (API). Tato rozhraní API poskytuje základní funkce pro zpracování obrázků, ale chybějící funkce, jako je například podporu podle kodeku rozšíření a věrného image. Rozhraní API pro zpracování obrázků WPF mají upravený tak, aby překonat nedostatky GDI a rozhraní GDI + a zadejte novou sadu rozhraní API pro zobrazení a použití imagí v rámci vašich aplikací.  
  
 Při použití bitové kopie, vezměte v úvahu následující doporučení pro získání lepší výkon:  
  
- Pokud vaše aplikace vyžaduje, abyste k zobrazení obrázků miniatur, zvažte vytvoření snížení velikosti verzi image. Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] načte bitové kopie a dekóduje na jeho plnou velikost. Pokud chcete pouze miniatury verzi image, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zbytečné dekóduje obrázek, který se jeho reklamy a škáluje ho na velikost miniatur. Abyste předešli této zbytečnou režii, můžete buď vyžádat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] k dekódování obrázku na velikost miniatur, nebo požádat o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] načíst obrázek miniatury.  
  
- Vždy dekódování obrázku požadovaná velikost a ne výchozí velikost. Jak je uvedeno výše, požádat o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] k dekódování svou image do požadované velikosti a výchozí plnou velikost. Sníží jenom vaše aplikace pracovní sadu, ale i rychlostí provádění.  
  
- Pokud je to možné sloučit bitové kopie do jedné image, jako proužek film skládá z více bitových kopií.  
  
- Další informace najdete v tématu [Imaging přehled](../graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 Při animaci škálování jakékoli rastrový obrázek, výchozí vysoce kvalitní bitovou kopii znovu algoritmus vzorkování spotřebovat někdy způsobit snížení frekvence snímků, účinně způsobující animace zadrhávají dostatečné systémové prostředky. Tím, že nastavíte <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> vlastnost <xref:System.Windows.Media.RenderOptions> objektu <xref:System.Windows.Media.BitmapScalingMode.LowQuality> vytvoříte hladší animace při změně velikosti rastrový obrázek. <xref:System.Windows.Media.BitmapScalingMode.LowQuality> Určuje režim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslovací modul přepnutí z algoritmu optimalizované kvality algoritmu optimalizované rychlost při zpracování obrázků.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Media.BitmapScalingMode> objektu image.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] neukládá do mezipaměti vykreslený obsah <xref:System.Windows.Media.TileBrush> objekty, jako například <xref:System.Windows.Media.DrawingBrush> a <xref:System.Windows.Media.VisualBrush>. Ve scénářích statické kde obsah ani použití <xref:System.Windows.Media.TileBrush> v změnu scény, to dává smysl, protože šetří grafické paměti. Nepoužívá jako mnohem smysl při <xref:System.Windows.Media.TileBrush> s statického obsahu se používá jako nestatická – například když statickou <xref:System.Windows.Media.DrawingBrush> nebo <xref:System.Windows.Media.VisualBrush> je namapována na povrchu objektu otáčení 3D. Výchozí chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je znovu zpracovat celý obsah <xref:System.Windows.Media.DrawingBrush> nebo <xref:System.Windows.Media.VisualBrush> pro každý snímek, i když je obsah neměnné.  
  
 Tím, že nastavíte <xref:System.Windows.Media.RenderOptions.CachingHint%2A> vlastnost <xref:System.Windows.Media.RenderOptions> objektu <xref:System.Windows.Media.CachingHint.Cache> může zvýšit výkon s použitím verze uložené v mezipaměti objektů vedle sebe štětce.  
  
 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> a <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> hodnoty vlastností jsou relativní velikosti hodnoty, které určují, kdy <xref:System.Windows.Media.TileBrush> objekt by měl být znovu vygenerován z důvodu změn v měřítku. Například tak, že nastavíte <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> vlastnost 2.0, je mezipaměť <xref:System.Windows.Media.TileBrush> pouze musí být znovu vygenerován při její velikost přesahuje dvojnásobku velikosti aktuální mezipaměť.  
  
 Následující příklad ukazuje, jak použít možnost ukládání do mezipaměti pomocný parametr pro <xref:System.Windows.Media.DrawingBrush>.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Viz také:

- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Plánování výkonu aplikace](planning-for-application-performance.md)
- [Využití výhod hardwaru](optimizing-performance-taking-advantage-of-hardware.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [Chování objektu](optimizing-performance-object-behavior.md)
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Další výkonnostní doporučení](optimizing-performance-other-recommendations.md)
- [Tipy a triky animace](../graphics-multimedia/animation-tips-and-tricks.md)
