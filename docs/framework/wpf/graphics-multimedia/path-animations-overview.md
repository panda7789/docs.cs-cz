---
title: "Přehled animací cesty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], paths
- path animations [WPF]
ms.assetid: 979c732c-df74-47a6-be96-8e07b3707d53
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10f2e27a2f68dd784c6fce66ae63873436923d63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="path-animations-overview"></a>Přehled animací cesty
<a name="introduction"></a>Toto téma představuje animací cesty, které vám umožní používat geometrickou cestu ke generování hodnot výstup. Cesta animací jsou užitečné pro přesunutí a otáčení objektů podél komplexní cesty.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Zjistit, v tomto tématu, měli byste se seznámit s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce animace. Úvod do animace funkce, najdete v článku [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Vzhledem k tomu, že používáte <xref:System.Windows.Media.PathGeometry> objekt, který chcete definovat animace cestu, měli byste také se seznámit s <xref:System.Windows.Media.PathGeometry> a různé typy <xref:System.Windows.Media.PathSegment> objekty. Další informace najdete v tématu [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="what_is_a_path_animation"></a>   
## <a name="what-is-a-path-animation"></a>Co je cesta animace?  
 Animace cesta je typ <xref:System.Windows.Media.Animation.AnimationTimeline> používající <xref:System.Windows.Media.PathGeometry> jako vstup. Místo k nastavení From, nebo vlastností (jako u From/k/podle animace) nebo pomocí klíčových snímků (jak je můžete použít pro klíč rámce animace), zadejte cestu k geometrickou a použít ho k nastavení `PathGeometry` vlastnost animace cestu. V průběhu animace cesta přečte x, y a úhel informace z cesty a používá tyto informace k vygenerování její výstup.  
  
 Cesta animace jsou užitečné pro animace objekt podél komplexní cesty. Jeden ze způsobů, jak přesunout objekt podél cesty se má používat <xref:System.Windows.Media.MatrixTransform> a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> k transformaci objekt podél komplexní cesty. Následující příklad ukazuje tento postup pomocí <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objekt, který má animace <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform>. <xref:System.Windows.Media.MatrixTransform> Se použije pro tlačítko a způsobí, že ho přesunout společně zakřivené cesty. Protože <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> je nastavena na `true`, rámeček otáčí společně tangens cestu.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Další informace o syntaxi cestu, která se používá v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příkladu najdete v článku [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) Přehled. Kompletní příklad, najdete v části [cesta animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Můžete použít cestu animace do vlastnosti s využitím <xref:System.Windows.Media.Animation.Storyboard> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a kód, nebo pomocí <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda v kódu. Cesta animace můžete také použít k vytvoření <xref:System.Windows.Media.Animation.AnimationClock> a použít ji na jeden nebo více vlastností. Další informace o různých způsobech použití animace najdete v tématu [vlastnost animace techniky přehled](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## <a name="path-animation-types"></a>Cesta animace typy  
 Protože animací generovat hodnoty vlastností, existují různé animace typy pro typy jinou vlastnost. Pro animaci vlastnost, která přebírá <xref:System.Double> (například <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform>), používáte animace, která vytváří <xref:System.Double> hodnoty. Pro vlastnost, která přebírá animaci <xref:System.Windows.Point>, použijte animace, která vytváří <xref:System.Windows.Point> hodnoty a tak dále.  
  
 Cesta animace třídy patří do <xref:System.Windows.Media.Animation> obor názvů a použijte následující konvence:  
  
 *\<Typ >*`AnimationUsingPath`  
  
 Kde  *\<typ >* je typ hodnoty, které animuje třídy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje následující cestě třídy animace.  
  
|Typ vlastnosti|Třída animace odpovídající cesta|Příklad|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[Animace objektu podél cesty (dvojitá animace)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[Animace objektu podél cesty (animace matice)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[Animace objektu podél cesty (bodová animace)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> generuje <xref:System.Windows.Media.Matrix> hodnoty z jeho <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>. Při použití s <xref:System.Windows.Media.MatrixTransform>, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> můžete přesunout objekt podél cesty. Pokud nastavíte <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> vlastnost <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> k `true`, je také otočí objekt podél křivek cesty.  
  
 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> generuje <xref:System.Windows.Point> hodnoty z x-y souřadnice a jeho <xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>. Pomocí <xref:System.Windows.Media.Animation.PointAnimationUsingPath> pro animaci vlastnost, která přebírá <xref:System.Windows.Point> hodnoty, můžete přesunout objekt podél cesty. A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> nelze otočit objekty.  
  
 A <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> generuje <xref:System.Double> hodnoty z jeho <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>. Nastavením <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A> vlastnost, můžete určit zda <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> používá souřadnice x, souřadnici y nebo úhel cesty jako výstup. Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> otočení objektu nebo přesunout podél osy x nebo osy y.  
  
<a name="pathanimationinput"></a>   
## <a name="path-animation-input"></a>Cesta animace vstup  
 Každá cesta animace třída poskytuje <xref:System.Windows.Media.PathGeometry> vlastnost pro zadání vstupem. Cesta animace používá <xref:System.Windows.Media.PathGeometry> ke generování hodnot její výstup. <xref:System.Windows.Media.PathGeometry> Třída umožňuje popisují více komplexní obrázky, které se skládají z oblouky, křivek a řádky.  
  
 Jádrem <xref:System.Windows.Media.PathGeometry> je kolekce <xref:System.Windows.Media.PathFigure> objekty; tyto objekty jsou pojmenované, protože každý obrázek popisuje diskrétní obrazce v <xref:System.Windows.Media.PathGeometry>. Každý <xref:System.Windows.Media.PathFigure> se skládá z jednoho nebo více <xref:System.Windows.Media.PathSegment> objektů, z nichž každý popisuje segment na obrázku.  
  
 Existuje mnoho typů segmentů.  
  
|Typ segmentu|Popis|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|Vytvoří oblouk eliptické mezi dva body.|  
|<xref:System.Windows.Media.BezierSegment>|Vytvoří krychlový Bézierovu křivku mezi dva body.|  
|<xref:System.Windows.Media.LineSegment>|Vytvoří řádek mezi dva body.|  
|<xref:System.Windows.Media.PolyBezierSegment>|Vytvoří řadu krychlový Bézierových křivek.|  
|<xref:System.Windows.Media.PolyLineSegment>|Vytvoří řadu řádky.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Vytvoří řadu kvadratické Bézierovy křivky.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Vytvoří kvadratické Bézierovy křivky.|  
  
 Segmentů v <xref:System.Windows.Media.PathFigure> slučují do jediného geometrické obrazce, který používá koncový bod segment jako počáteční bod další segmentu. <xref:System.Windows.Media.PathFigure.StartPoint%2A> Vlastnost <xref:System.Windows.Media.PathFigure> Určuje bod, ze kterého se nevykreslí první segment. Každý další segment začíná na koncový bod předchozího segmentu. Například svislá čára z `10,50` k `10,150` můžete definovat nastavením <xref:System.Windows.Media.PathFigure.StartPoint%2A> vlastnost `10,50` a vytváření <xref:System.Windows.Media.LineSegment> s <xref:System.Windows.Media.LineSegment.Point%2A> vlastnost na hodnotu `10,150`.  
  
 Další informace o <xref:System.Windows.Media.PathGeometry> objekty, najdete [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete také použít speciální zkrácené syntaxe nastavit <xref:System.Windows.Media.PathGeometry.Figures%2A> vlastnost <xref:System.Windows.Media.PathGeometry>. Další informace najdete v tématu [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) Přehled.  
  
 Další informace o syntaxi cestu, která se používá v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příkladu najdete v článku [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) Přehled.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka animace cesta](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [Syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)  
 [Postupy: Témata animace cesty](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled způsobů animace vlastností](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
