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
ms.openlocfilehash: 764e7e802ccaff50b76229b9441380bfe77fefb5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933352"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Optimalizace výkonu: 2D grafika a obrázky
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje široké spektrum 2D grafických a zobrazovacích funkcí, které je možné optimalizovat pro požadavky vaší aplikace. Toto téma poskytuje informace o optimalizaci výkonu v těchto oblastech.  

<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>Kreslení a tvary  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Media.Drawing> poskytujeobjektyiproreprezentaci<xref:System.Windows.Shapes.Shape> obsahu grafického vykreslování. Nicméně objekty jsou jednodušší konstrukce než <xref:System.Windows.Shapes.Shape> objekty a poskytují lepší výkonnostní charakteristiky. <xref:System.Windows.Media.Drawing>  
  
 <xref:System.Windows.Shapes.Shape> Umožňuje nakreslit grafický tvar na obrazovku. Vzhledem k <xref:System.Windows.FrameworkElement> tomu, že jsou odvozeny <xref:System.Windows.Shapes.Shape> z třídy, lze objekty použít uvnitř panelů a většiny ovládacích prvků.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nabízí několik vrstev přístupu ke grafikám a vykreslovacím službám. V horní vrstvě <xref:System.Windows.Shapes.Shape> se objekty snadno používají a poskytují mnoho užitečných funkcí, jako je například rozložení a zpracování událostí. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje několik objektů tvarů připravených k použití. Všechny objekty obrazce dědí z <xref:System.Windows.Shapes.Shape> třídy. Dostupné objekty obrazce zahrnují <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>a .<xref:System.Windows.Shapes.Rectangle>  
  
 <xref:System.Windows.Media.Drawing>objekty na druhé straně neodvozují z <xref:System.Windows.FrameworkElement> třídy a poskytují světlejší implementaci pro vykreslování tvarů, obrázků a textu.  
  
 Existují čtyři typy <xref:System.Windows.Media.Drawing> objektů:  
  
- <xref:System.Windows.Media.GeometryDrawing>Nakreslí obrazec.  
  
- <xref:System.Windows.Media.ImageDrawing>Nakreslí obrázek.  
  
- <xref:System.Windows.Media.GlyphRunDrawing>Nakreslí text.  
  
- <xref:System.Windows.Media.DrawingGroup>Kreslí další výkresy. K kombinování dalších kreseb do jednoho složené kresby použijte skupinu pro kreslení.  
  
 <xref:System.Windows.Media.GeometryDrawing> Objekt se používá k vykreslení geometrie obsahu. Třída a konkrétní třídy, které jsou z něj odvozeny, <xref:System.Windows.Media.CombinedGeometry>jako například <xref:System.Windows.Media.EllipseGeometry>, a <xref:System.Windows.Media.PathGeometry>, poskytují prostředky pro vykreslování 2D grafiky a také poskytují podporu testování a vystřihování. <xref:System.Windows.Media.Geometry> Objekty geometrie lze použít k definování oblasti ovládacího prvku, například nebo k definování oblasti klipu, která má být použita pro obrázek. Geometrické objekty mohou být jednoduché oblasti, například obdélníky a kružnice nebo složené oblasti vytvořené ze dvou nebo více objektů geometrie. Složitější <xref:System.Windows.Media.PathSegment>geometrické oblasti lze vytvořit kombinováním odvozených objektů, <xref:System.Windows.Media.ArcSegment>například, <xref:System.Windows.Media.BezierSegment>a <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 Na povrchu <xref:System.Windows.Media.Geometry> jsou třídy <xref:System.Windows.Shapes.Shape> a třídy velmi podobné. Obě jsou používány při vykreslování 2D grafiky a obě mají podobné konkrétní třídy, které jsou z nich odvozeny, například <xref:System.Windows.Media.EllipseGeometry> a. <xref:System.Windows.Shapes.Ellipse> Existují však důležité rozdíly mezi těmito dvěma sadami tříd. Pro jednu <xref:System.Windows.Media.Geometry> třídu chybí některé funkce <xref:System.Windows.Shapes.Shape> třídy, jako je například schopnost nakreslit sama sebe. Chcete-li nakreslit geometrický objekt, další třídu, jako je například DrawingContext, Drawing nebo Path (je třeba poznamenat, že cesta je tvar), musí být použita k provedení operace kreslení. Vykreslení vlastností, jako je výplň, tah a tloušťka tahu, jsou na třídě, která vykresluje objekt geometrie, zatímco objekt Shape obsahuje tyto vlastnosti. Jedním ze způsobů, jak si tento rozdíl představit, je, že objekt geometrie definuje oblast, kruh například, zatímco objekt Shape definuje oblast, definuje způsob, jakým je tato oblast vyplněna a doplněna, a účastní se v systému rozložení.  
  
 Vzhledem <xref:System.Windows.Shapes.Shape> k<xref:System.Windows.FrameworkElement> tomu, že objekty jsou odvozeny z třídy, jejich použití může do aplikace přidat podstatně větší spotřebu paměti. Pokud opravdu nepotřebujete <xref:System.Windows.FrameworkElement> funkce pro váš grafický obsah, zvažte použití objektů s světlejší váhou <xref:System.Windows.Media.Drawing> .  
  
 Další informace o <xref:System.Windows.Media.Drawing> objektech naleznete v tématu [Přehled nakreslených objektů](../graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>Objekty StreamGeometry  
 Objekt je zjednodušenou <xref:System.Windows.Media.PathGeometry> alternativou pro vytváření geometrických tvarů. <xref:System.Windows.Media.StreamGeometry> Použijte, <xref:System.Windows.Media.StreamGeometry> Pokud potřebujete popsat složitou geometrii. <xref:System.Windows.Media.StreamGeometry>je optimalizován pro zpracování mnoha <xref:System.Windows.Media.PathGeometry> objektů a je lepší při porovnání s použitím mnoha jednotlivých <xref:System.Windows.Media.PathGeometry> objektů.  
  
 Následující příklad používá syntaxi atributu k vytvoření trojúhelníku <xref:System.Windows.Media.StreamGeometry> v. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Další informace o <xref:System.Windows.Media.StreamGeometry> objektech naleznete v tématu [Vytvoření obrazce pomocí StreamGeometry](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>Objekty DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> Objekt je odlehčená třída pro kreslení, která se používá k vykreslování tvarů, obrázků nebo textu. Tato třída je považována za odlehčenou, protože neposkytuje rozložení nebo zpracování událostí, což zvyšuje výkon. Z tohoto důvodu jsou kresby ideální pro pozadí a kliparty. Další informace najdete v tématu [použití objektů DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>   
## <a name="images"></a>Obrázky  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]v předchozích verzích Windows poskytuje program Imaging významné vylepšení funkcí imagí. Funkce pro vytváření imagí, jako je například zobrazení rastrového obrázku nebo použití obrázku na běžném ovládacím prvku, byly primárně zpracovávány rozhraním Microsoft Windows GDI (GDI) nebo rozhraním API (Microsoft Windows GDI+ Application Programming Interface). Toto rozhraní API poskytovalo základní funkce pro vytváření bitových kopií, ale chybí funkce, jako je podpora rozšiřitelnosti kodeku a podpora obrázků s vysokou kvalitou. Rozhraní API pro zpracování obrazu WPF bylo přepracováno, aby přeznamenalo nedostatky rozhraní GDI a GDI+ a poskytovalo novou sadu rozhraní API pro zobrazení a používání imagí v rámci aplikací.  
  
 Při použití imagí zvažte následující doporučení, abyste získali lepší výkon:  
  
- Pokud vaše aplikace vyžaduje, abyste zobrazili miniatury, zvažte vytvoření bitové kopie s omezenou velikostí. Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] načte vaši image a dekóduje ji do její plné velikosti. Pokud chcete pouze miniaturní verzi obrázku, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] není nutné dekódovat obraz na jeho plnou velikost a pak ho zmenší dolů na velikost miniatury. Aby nedošlo k této zbytečné režii, můžete [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] buď požádat o dekódování obrázku na miniaturu, nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] požádat o načtení obrázku velikosti miniatur.  
  
- Vždy dekódovat obrázek na požadovanou velikost, nikoli na výchozí velikost. Jak je uvedeno výše, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vyžádejte si požadavek na dekódování obrázku na požadovanou velikost, nikoli na výchozí plnou velikost. Omezíte nejen pracovní sadu vaší aplikace, ale i rychlost provádění.  
  
- Pokud je to možné, zkombinujte obrázky do jedné image, jako je například filmový pruh tvořený více obrázky.  
  
- Další informace najdete v tématu [Přehled imagí](../graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 Při animování měřítka rastrového obrázku může výchozí algoritmus opakovaného vzorkování obrázků někdy spotřebovat dostatečné systémové prostředky, aby mohla způsobit snížení četnosti snímků, což efektivně vede k Stutter animací. <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> Nastavením vlastnosti <xref:System.Windows.Media.RenderOptions> objektu na<xref:System.Windows.Media.BitmapScalingMode.LowQuality> můžete vytvořit hladší animaci při škálování rastrového obrázku. <xref:System.Windows.Media.BitmapScalingMode.LowQuality>režim oznamuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modulu vykreslování, aby při zpracování imagí přepnul z algoritmu optimalizovaného pro rychlost do algoritmu optimalizovaného pro rychlost.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Media.BitmapScalingMode> objekt obrázku.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] neukládá do mezipaměti vykreslený <xref:System.Windows.Media.TileBrush> obsah objektů, jako jsou <xref:System.Windows.Media.DrawingBrush> a <xref:System.Windows.Media.VisualBrush>. Ve statických scénářích, kdy se nemění obsah <xref:System.Windows.Media.TileBrush> ani použití v rámci scény, je to smysl, protože zachovává paměť pro video. Nemá smysl, pokud <xref:System.Windows.Media.TileBrush> se statický obsah používá nestatickým způsobem – například když je statický <xref:System.Windows.Media.DrawingBrush> nebo <xref:System.Windows.Media.VisualBrush> mapován na povrch rotujícího 3D objektu. Výchozím chováním [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je opětovné vykreslení celého obsahu <xref:System.Windows.Media.DrawingBrush> nebo <xref:System.Windows.Media.VisualBrush> pro každý rámec, i když se obsah nemění.  
  
 <xref:System.Windows.Media.RenderOptions.CachingHint%2A> Nastavením vlastnosti <xref:System.Windows.Media.RenderOptions> objektu na<xref:System.Windows.Media.CachingHint.Cache> můžete zvýšit výkon pomocí verzí uložených v mezipaměti vedle objektů štětce.  
  
 Hodnoty vlastností <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>ajsou relativní velikosti, které určují, kdy <xref:System.Windows.Media.TileBrush> by měl být objekt znovu vygenerován z důvodu změn ve stupnici. <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> Například <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> nastavením vlastnosti na 2,0 je nutné znovu vygenerovat mezipaměť <xref:System.Windows.Media.TileBrush> pouze v případě, že velikost přesáhne dvojnásobnou velikost aktuální mezipaměti.  
  
 Následující příklad ukazuje, jak použít možnost pomocný parametr pro ukládání do mezipaměti <xref:System.Windows.Media.DrawingBrush>pro.  
  
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
