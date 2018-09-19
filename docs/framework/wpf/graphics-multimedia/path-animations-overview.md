---
title: Přehled animací cesty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], paths
- path animations [WPF]
ms.assetid: 979c732c-df74-47a6-be96-8e07b3707d53
ms.openlocfilehash: 0f795ad00823e7b1c37221f7417b09d3982c4c18
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006753"
---
# <a name="path-animations-overview"></a>Přehled animací cesty
<a name="introduction"></a> Toto téma představuje animace cesty, které vám umožní používat geometrické cesty k vygenerování výstupní hodnoty. Animace cesty jsou užitečné pro přesun a otočení objekty podél cest složité.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu informace o tom, měli byste se seznámit s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce animace. Úvod do funkce animace, najdete v článku [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Vzhledem k tomu, že používáte <xref:System.Windows.Media.PathGeometry> objektu k definování animace cesty, byste měli také znáte <xref:System.Windows.Media.PathGeometry> a různých typech <xref:System.Windows.Media.PathSegment> objekty. Další informace najdete v tématu [přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="what_is_a_path_animation"></a>   
## <a name="what-is-a-path-animation"></a>Co je animace cesty?  
 Animace cesty je typ <xref:System.Windows.Media.Animation.AnimationTimeline> , která používá <xref:System.Windows.Media.PathGeometry> jako vstup. Místo na nastavení From, nebo podle vlastnosti (jako u od/Komu/kým animace) nebo pomocí klíčových snímků (jak je můžete použít pro animace klíčových snímků), definovat geometrické cesty a použít ji nastavit `PathGeometry` vlastnost animace cesty. Animace průběhu cestu přečte x, y a informace o úhel z cesty a použije tyto informace ke generování jeho výstup.  
  
 Animace cesty jsou velmi užitečné pro animace objektu podél cesty složité. Jeden ze způsobů, jak přesunout, je použití objektu podél cesty <xref:System.Windows.Media.MatrixTransform> a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> transformace objektu podél cesty složité. Následující příklad ukazuje tento postup pomocí <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objektu animace <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.MatrixTransform> Se použije k tlačítku a způsobí, že chcete přesunout podél zakřivené cesty. Vzhledem k tomu, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> je nastavena na `true`, obdélník se otočí spolu tangens cestu.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Další informace o syntaxi cestu, která se používá v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příkladu najdete v článku [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) Přehled. Úplnou ukázku najdete v tématu [ukázkové animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Animace cesty můžete použít na vlastnost s použitím <xref:System.Windows.Media.Animation.Storyboard> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a kód, nebo pomocí <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody v kódu. Animace cesty můžete také použít k vytvoření <xref:System.Windows.Media.Animation.AnimationClock> a použít ji pro jednu nebo více vlastností. Další informace o různých způsobech použití animací, naleznete v tématu [přehled způsobů animace vlastností](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## <a name="path-animation-types"></a>Typy animace cesty  
 Protože animace hodnoty vlastností, existují jiné typy jiné vlastnosti. Animovat vlastnost, která přebírá <xref:System.Double> (například <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform>), používat animaci, která vytváří <xref:System.Double> hodnoty. Animovat vlastnost, která přijímá <xref:System.Windows.Point>, použijte animaci, která vytváří <xref:System.Windows.Point> hodnoty a tak dále.  
  
 Cesta animace třídy patřit do <xref:System.Windows.Media.Animation> obor názvů a použít následujícími zásadami vytváření názvů:  
  
 *\<Typ >* `AnimationUsingPath`  
  
 Kde  *\<typ >* je typ hodnoty, který animuje třídy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje následující cesta třídy animace.  
  
|Typ vlastnosti|Odpovídající třída animace cesty|Příklad|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[Animace objektu podél cesty (dvojitá animace)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[Animace objektu podél cesty (animace matice)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[Animace objektu podél cesty (bodová animace)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> generuje <xref:System.Windows.Media.Matrix> hodnoty z jeho <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>. Při použití s <xref:System.Windows.Media.MatrixTransform>, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> můžete přesunout objektu podél cesty. Pokud jste nastavili <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> vlastnost <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> k `true`, také otočí objektu podél křivky cesty.  
  
 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> generuje <xref:System.Windows.Point> hodnoty z x-y souřadnice a jeho <xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>. Pomocí <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animovat vlastnost, která přebírá <xref:System.Windows.Point> hodnoty, můžete přesunout objektu podél cesty. A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> nelze otočit objekty.  
  
 A <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> generuje <xref:System.Double> hodnoty z jeho <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>. Nastavením <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A> vlastností, můžete určit, zda <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> souřadnice x, souřadnice y nebo úhel cesty používá jako výstup. Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> otočení objektu nebo přesunout společně osu x nebo osu y.  
  
<a name="pathanimationinput"></a>   
## <a name="path-animation-input"></a>Vstup animace cesty  
 Každá třída animace cesty poskytuje <xref:System.Windows.Media.PathGeometry> vlastnosti pro určení vstup. Animace cesty používá <xref:System.Windows.Media.PathGeometry> ke generování jeho výstupní hodnoty. <xref:System.Windows.Media.PathGeometry> Třída umožňuje popisují několik komplexní hodnoty, které se skládají z elipsy, křivky a řádků.  
  
 V srdci <xref:System.Windows.Media.PathGeometry> je kolekce <xref:System.Windows.Media.PathFigure> objektů; tyto objekty se proto s názvem, protože každý obrázek popisuje diskrétní tvar v <xref:System.Windows.Media.PathGeometry>. Každý <xref:System.Windows.Media.PathFigure> obsahuje jeden nebo více <xref:System.Windows.Media.PathSegment> objektů, z nichž každý popisuje segment na obrázku.  
  
 Existuje mnoho typů segmentů.  
  
|Typ segmentu|Popis|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|Vytvoří oblouku elipsy mezi dvěma body.|  
|<xref:System.Windows.Media.BezierSegment>|Vytvoří kubické Bézierovy křivky mezi dvěma body.|  
|<xref:System.Windows.Media.LineSegment>|Vytvoří čáry mezi dvěma body.|  
|<xref:System.Windows.Media.PolyBezierSegment>|Vytvoří řadu kubické Bézierovy křivky.|  
|<xref:System.Windows.Media.PolyLineSegment>|Vytvoří řadu řádky.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Vytvoří řadu kvadratické Bézierovy křivky.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Vytvoří kvadratické Bézierovy křivky.|  
  
 Segmenty v <xref:System.Windows.Media.PathFigure> jsou zkombinované do jediného geometrické obrazce, která používá koncový bod segment, který jako počáteční bod dalšího segmentu. <xref:System.Windows.Media.PathFigure.StartPoint%2A> Vlastnost <xref:System.Windows.Media.PathFigure> Určuje bod, ze které je vykresleno první segment. Každý další segment začíná na koncový bod předchozího segmentu. Například zobrazuje svislá čára z `10,50` k `10,150` lze definovat tak, že nastavíte <xref:System.Windows.Media.PathFigure.StartPoint%2A> vlastnost `10,50` a vytváření <xref:System.Windows.Media.LineSegment> s <xref:System.Windows.Media.LineSegment.Point%2A> nastavení vlastnosti `10,150`.  
  
 Další informace o <xref:System.Windows.Media.PathGeometry> objekty, najdete [přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete nastavit speciální syntaxe zkrácený <xref:System.Windows.Media.PathGeometry.Figures%2A> vlastnost <xref:System.Windows.Media.PathGeometry>. Další informace najdete v tématu [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) Přehled.  
  
 Další informace o syntaxi cestu, která se používá v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příkladu najdete v článku [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) Přehled.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka animace cesty](https://go.microsoft.com/fwlink/?LinkID=160028)  
 [Syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)  
 [Postupy: Témata animace cesty](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled způsobů animace vlastností](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
