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
- 2D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: eb3686367873276587572addda436471cd1abf27
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291805"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Optimalizace výkonu: 2D grafika a obrázky
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje širokou škálu funkcí 2D grafiky a zobrazování, které lze optimalizovat pro vaše požadavky na aplikaci. Toto téma obsahuje informace o optimalizaci výkonu v těchto oblastech.  

<a name="Drawing_and_Shapes"></a>
## <a name="drawing-and-shapes"></a>Kreslení a obrazce  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje <xref:System.Windows.Media.Drawing> oba <xref:System.Windows.Shapes.Shape> a objekty představují grafický obsah výkresu. Objekty <xref:System.Windows.Media.Drawing> jsou však <xref:System.Windows.Shapes.Shape> jednodušší konstrukce než objekty a poskytují lepší charakteristiky výkonu.  
  
 A <xref:System.Windows.Shapes.Shape> umožňuje nakreslit grafický tvar na obrazovku. Vzhledem k tomu, <xref:System.Windows.FrameworkElement> že <xref:System.Windows.Shapes.Shape> jsou odvozeny z třídy, objekty lze použít uvnitř panelů a většina ovládacích prvků.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nabízí několik vrstev přístupu ke grafickým a vykreslovací službám. V horní vrstvě <xref:System.Windows.Shapes.Shape> jsou objekty snadno použitelné a poskytují mnoho užitečných funkcí, jako je rozložení a zpracování událostí. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje řadu objektů obrazců připravených k použití. Všechny objekty obrazce dědí z <xref:System.Windows.Shapes.Shape> třídy. Mezi dostupné <xref:System.Windows.Shapes.Ellipse>objekty tvarů patří <xref:System.Windows.Shapes.Line>, , <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, a <xref:System.Windows.Shapes.Rectangle>.  
  
 <xref:System.Windows.Media.Drawing>objekty, na druhé straně nepocházejí <xref:System.Windows.FrameworkElement> z třídy a poskytují lehčí implementace pro vykreslování tvarů, obrázků a textu.  
  
 Existují čtyři typy <xref:System.Windows.Media.Drawing> objektů:  
  
- <xref:System.Windows.Media.GeometryDrawing>Nakreslí tvar.  
  
- <xref:System.Windows.Media.ImageDrawing>Nakreslí obrázek.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>Nakreslí text.  
  
- <xref:System.Windows.Media.DrawingGroup>Nakreslí další výkresy. Pomocí skupiny výkresů můžete kombinovat další výkresy do jednoho složeného výkresu.  
  
 Objekt <xref:System.Windows.Media.GeometryDrawing> se používá k vykreslení obsahu geometrie. Třída <xref:System.Windows.Media.Geometry> a konkrétní třídy, které jsou <xref:System.Windows.Media.CombinedGeometry> <xref:System.Windows.Media.EllipseGeometry>z <xref:System.Windows.Media.PathGeometry>ní odvozeny, například , , a , poskytují prostředky pro vykreslování 2D grafiky a poskytuje podporu testování přístupů a oříznutí. Objekty geometrie lze použít například k definování oblasti ovládacího prvku nebo k definování oblasti klipu, která se má aplikovat na obraz. Objekty geometrie mohou být jednoduché oblasti, například obdélníky a kružnice, nebo složené oblasti vytvořené ze dvou nebo více objektů geometrie. Složitější geometrické oblasti lze vytvořit <xref:System.Windows.Media.PathSegment>kombinací odvozených objektů, například <xref:System.Windows.Media.ArcSegment>, <xref:System.Windows.Media.BezierSegment>a <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 Na povrchu <xref:System.Windows.Media.Geometry> jsou třídy a třídy <xref:System.Windows.Shapes.Shape> podobné. Obě se používají při vykreslování 2D grafiky a <xref:System.Windows.Media.EllipseGeometry> obě <xref:System.Windows.Shapes.Ellipse>mají podobné konkrétní třídy, které z nich pocházejí, například a . Existují však důležité rozdíly mezi těmito dvěma sadami tříd. Pro jednoho <xref:System.Windows.Media.Geometry> třídy postrádá některé funkce <xref:System.Windows.Shapes.Shape> třídy, jako je například schopnost kreslit sám. Chcete-li nakreslit objekt geometrie, musí být k provedení operace kreslení použita jiná třída, například DrawingContext, Drawing nebo Path (stojí za zmínku, že Cesta je tvar). Vlastnosti vykreslování, jako je výplň, tah a tloušťka tahu, jsou na třídě, která kreslí objekt geometrie, zatímco objekt tvaru obsahuje tyto vlastnosti. Jedním ze způsobů, jak si tento rozdíl uvažovat, je, že objekt geometrie definuje oblast, například kruh, zatímco objekt tvaru definuje oblast, definuje, jak je tato oblast vyplněna a obrysována, a účastní se systému rozvržení.  
  
 Vzhledem k tomu, že <xref:System.Windows.Shapes.Shape> objekty jsou odvozeny <xref:System.Windows.FrameworkElement> z třídy, jejich použití může přidat výrazně vyšší spotřebu paměti ve vaší aplikaci. Pokud opravdu nepotřebujete <xref:System.Windows.FrameworkElement> funkce grafického obsahu, zvažte použití <xref:System.Windows.Media.Drawing> objektů s nižší hmotností.  
  
 Další informace <xref:System.Windows.Media.Drawing> o objektech naleznete v [tématu Přehled objektů kreslení](../graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>
## <a name="streamgeometry-objects"></a>Objekty StreamGeometry  
 Objekt <xref:System.Windows.Media.StreamGeometry> je zjednodušenou <xref:System.Windows.Media.PathGeometry> alternativou k vytváření geometrických tvarů. Použijte, <xref:System.Windows.Media.StreamGeometry> když potřebujete popsat složitou geometrii. <xref:System.Windows.Media.StreamGeometry>je optimalizován pro <xref:System.Windows.Media.PathGeometry> zpracování mnoha objektů a funguje <xref:System.Windows.Media.PathGeometry> lépe ve srovnání s použitím mnoha jednotlivých objektů.  
  
 Následující příklad používá syntaxi atributu <xref:System.Windows.Media.StreamGeometry> k [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]vytvoření trojúhelníku v .  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Další informace <xref:System.Windows.Media.StreamGeometry> o objektech naleznete v [tématu Vytvoření obrazce pomocí StreamGeometry](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>
## <a name="drawingvisual-objects"></a>KresleníVizuální objekty  
 Objekt <xref:System.Windows.Media.DrawingVisual> je zjednodušená třída kreslení, která slouží k vykreslení tvarů, obrázků nebo textu. Tato třída je považována za zjednodušenou, protože neposkytuje rozložení nebo zpracování událostí, což zlepšuje jeho výkon. Z tohoto důvodu jsou kresby ideální pro pozadí a kliparty. Další informace naleznete [v tématu Použití objektů DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>
## <a name="images"></a>Image  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zobrazování poskytuje významné zlepšení oproti možnostem zpracování obrázků v předchozích verzích systému Windows. Funkce zpracování obrázků, jako je například zobrazení bitmapy nebo použití bitmapy na společném ovládacím prvku, byly primárně zpracovány rozhraním GDI (Microsoft Windows Graphics Device Interface) nebo Microsoft Windows GDI+ (API). Tato api poskytovala základní funkce zobrazování, ale postrádala funkce, jako je podpora rozšiřitelnosti kodeku a podpora obrazu s vysokou věrností. WPF Imaging API byly přepracovány tak, aby překonaly nedostatky GDI a GDI+ a poskytly novou sadu api pro zobrazení a použití obrázků ve vašich aplikacích.  
  
 Při použití obrázků zvažte následující doporučení pro získání lepšího výkonu:  
  
- Pokud vaše aplikace vyžaduje zobrazení miniatur, zvažte vytvoření verze obrázku se sníženou velikostí. Ve výchozím [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavení načte obrázek a dekóduje jej na plnou velikost. Pokud chcete pouze miniaturu obrázku, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zbytečné dekóduje obrázek na jeho plnou velikost a pak se zmenší na velikost miniatury. Chcete-li se vyhnout této [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zbytečné režii, můžete buď [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] požádat o dekódování obrázku na velikost miniatury, nebo požádat o načtení obrázku velikosti miniatury.  
  
- Obraz vždy dekódujte na požadovanou velikost a ne na výchozí velikost. Jak bylo uvedeno [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] výše, požádejte o dekódování obrázku na požadovanou velikost a ne výchozí plnou velikost. Snížíte nejen pracovní sadu vaší aplikace, ale také rychlost provádění.  
  
- Pokud je to možné, zkombinujte obrazy do jednoho obrazu, například do filmového proužku složeného z více obrazů.  
  
- Další informace naleznete v [tématu Přehled zpracování obrázků](../graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>Režim bitmapy měřítka  
 Při animaci škálování libovolné bitmapy může výchozí algoritmus převzorkování obrazu ve vysoké kvalitě někdy spotřebovat dostatek systémových prostředků, aby způsobil zhoršení kmitočet snímků, což může způsobit zadrhávání animací. Nastavením <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> vlastnosti <xref:System.Windows.Media.RenderOptions> objektu <xref:System.Windows.Media.BitmapScalingMode.LowQuality>na , můžete vytvořit hladší animaci při změně velikosti bitmapy. <xref:System.Windows.Media.BitmapScalingMode.LowQuality>režim říká [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslovacímu modulu, aby při zpracování obrazů přepnul z algoritmu optimalizovaného pro kvalitu na algoritmus optimalizovaný pro rychlost.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Media.BitmapScalingMode> nastavit objekt obrázku pro.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>Tip do mezipaměti  
 Ve výchozím [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavení neukládá do <xref:System.Windows.Media.TileBrush> mezipaměti vykreslený obsah objektů, například <xref:System.Windows.Media.DrawingBrush> a <xref:System.Windows.Media.VisualBrush>. Ve statických scénářích, kde <xref:System.Windows.Media.TileBrush> se obsah nebo použití ve scéně nemění, to dává smysl, protože šetří video paměť. Nemá takový smysl, když <xref:System.Windows.Media.TileBrush> se statický obsah se statickým způsobem používá nestatickým <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush> způsobem – například když je statický objekt nebo je mapován na povrch rotujícího 3D objektu. Výchozí chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je re-render celý obsah <xref:System.Windows.Media.DrawingBrush> nebo <xref:System.Windows.Media.VisualBrush> pro každý snímek, i když obsah je neměnný.  
  
 Nastavením <xref:System.Windows.Media.RenderOptions.CachingHint%2A> vlastnosti <xref:System.Windows.Media.RenderOptions> objektu <xref:System.Windows.Media.CachingHint.Cache>na , můžete zvýšit výkon pomocí verzí objektů kachlová stopy v mezipaměti.  
  
 A <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> hodnoty vlastností jsou relativní hodnoty <xref:System.Windows.Media.TileBrush> velikosti, které určují, kdy má být objekt znovu vygenerován z důvodu změn v měřítku. Například nastavením <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> vlastnosti 2.0, mezipaměti <xref:System.Windows.Media.TileBrush> pro pouze je třeba obnovit, pokud jeho velikost překročí dvojnásobek velikosti aktuální mezipaměti.  
  
 Následující příklad ukazuje, jak používat možnost nápovědy <xref:System.Windows.Media.DrawingBrush>pro ukládání do mezipaměti pro .  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Viz také

- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Plánování výkonu aplikace](planning-for-application-performance.md)
- [Využití výhod hardwaru](optimizing-performance-taking-advantage-of-hardware.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [Chování objektu](optimizing-performance-object-behavior.md)
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Další doporučení k optimalizaci výkonu](optimizing-performance-other-recommendations.md)
- [Tipy a triky animace](../graphics-multimedia/animation-tips-and-tricks.md)
