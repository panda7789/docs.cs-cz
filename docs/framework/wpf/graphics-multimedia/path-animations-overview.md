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
ms.openlocfilehash: 07628d26c8222c7c01f58826a36a15e13dc31ff4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181870"
---
# <a name="path-animations-overview"></a>Přehled animací cesty
<a name="introduction"></a>Toto téma představuje animace cest, které umožňují použít geometrickou cestu ke generování výstupních hodnot. Animace cest jsou užitečné pro přesouvání a otáčení objektů podél složitých cest.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Chcete-li porozumět tomuto tématu, měli byste být obeznámeni s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcemi animací. Úvod k funkcím animace najdete v tématu [Přehled animací](animation-overview.md).  
  
 Vzhledem <xref:System.Windows.Media.PathGeometry> k tomu, že používáte objekt k <xref:System.Windows.Media.PathGeometry> definování animace cesty, měli byste být také obeznámeni s různými typy <xref:System.Windows.Media.PathSegment> objektů. Další informace naleznete v tématu [Přehled geometrie](geometry-overview.md).  
  
<a name="what_is_a_path_animation"></a>
## <a name="what-is-a-path-animation"></a>Co je animace cesty?  
 Animace cesty je <xref:System.Windows.Media.Animation.AnimationTimeline> typ, který <xref:System.Windows.Media.PathGeometry> používá jako jeho vstup. Namísto nastavení vlastnosti Od, Do nebo Podle (stejně jako u animace Od/Do/Podle) nebo použití klíčových snímků (při použití animace `PathGeometry` klíčových snímků) definujete geometrickou cestu a použijte ji k nastavení vlastnosti animace cesty. Jak animace cesty postupuje, přečte informace x, y a úhel z cesty a použije tyto informace ke generování výstupu.  
  
 Animace cesty jsou velmi užitečné pro animaci objektu podél složité cesty. Jedním ze způsobů přesunutí objektu podél <xref:System.Windows.Media.MatrixTransform> cesty <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> je použití a a transformace objektu podél složité cesty. Následující příklad ukazuje tuto techniku <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> pomocí objektu <xref:System.Windows.Media.MatrixTransform.Matrix%2A> animovat vlastnost <xref:System.Windows.Media.MatrixTransform>. Použije <xref:System.Windows.Media.MatrixTransform> se na tlačítko a způsobí, že se pohybuje po zakřivené cestě. Vzhledem <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> k tomu, že vlastnost je nastavena na `true`, obdélník se otáčí podél tečny cesty.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Další informace o syntaxi cesty, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] která se používá v příkladu, naleznete v přehledu [syntaxe značek cesty.](path-markup-syntax.md) Kompletní ukázku naleznete v tématu [Cesta animace Ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 Animaci cesty můžete použít na <xref:System.Windows.Media.Animation.Storyboard> vlastnost [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pomocí in a <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> code nebo pomocí metody v kódu. Animaci cesty můžete také <xref:System.Windows.Media.Animation.AnimationClock> použít k vytvoření a použití na jednu nebo více vlastností. Další informace o různých metodách použití animací naleznete v [tématu Property Animation Techniques Overview](property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>
## <a name="path-animation-types"></a>Typy animací cesty  
 Vzhledem k tomu, že animace generují hodnoty vlastností, existují různé typy animací pro různé typy vlastností. Chcete-li animovat <xref:System.Double> vlastnost, která <xref:System.Windows.Media.TranslateTransform.X%2A> trvá <xref:System.Windows.Media.TranslateTransform>(například vlastnost ), <xref:System.Double> použijte animaci, která vytváří hodnoty. Chcete-li animovat <xref:System.Windows.Point>vlastnost, která trvá , <xref:System.Windows.Point> použijte animaci, která vytváří hodnoty a tak dále.  
  
 Cesty animace třídy <xref:System.Windows.Media.Animation> patří do oboru názvů a použít následující konvence pojmenování:  
  
 * \<Typ>*`AnimationUsingPath`  
  
 Kde * \<Type>* je typ hodnoty, kterou třída animuje.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje následující cesty animační třídy.  
  
|Typ vlastnosti|Odpovídající třída animace cesty|Příklad|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[Animace objektu podél cesty (dvojitá animace)](how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[Animace objektu podél cesty (animace matice)](how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[Animace objektu podél cesty (bodová animace)](how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> generuje <xref:System.Windows.Media.Matrix> hodnoty <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>z jeho . Při použití <xref:System.Windows.Media.MatrixTransform>s <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> , může objekt přesunout podél cesty. Pokud nastavíte <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> vlastnost <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> `true`do , otočí také objekt podél křivek cesty.  
  
 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> generuje <xref:System.Windows.Point> hodnoty z souřadnic x <xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>a y jeho . Pomocí <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animovat vlastnost, která <xref:System.Windows.Point> přijímá hodnoty, můžete přesunout objekt podél cesty. A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> nelze otáčet objekty.  
  
 A <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> generuje <xref:System.Double> hodnoty <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>z jeho . Nastavením <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A> vlastnosti můžete určit, <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> zda použije souřadnice x, souřadnice y nebo úhel cesty jako výstup. Objekt můžete <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> použít k otočení objektu nebo k jeho přesunutí podél osy x nebo y.  
  
<a name="pathanimationinput"></a>
## <a name="path-animation-input"></a>Vstup animace cesty  
 Každá třída animace <xref:System.Windows.Media.PathGeometry> cesty poskytuje vlastnost pro určení jeho vstupu. Animace cesty používá <xref:System.Windows.Media.PathGeometry> ke generování jeho výstupní hodnoty. Třída <xref:System.Windows.Media.PathGeometry> umožňuje popsat více složitých obrázků, které se skládají z oblouků, křivek a čar.  
  
 V srdci <xref:System.Windows.Media.PathGeometry> je sbírka <xref:System.Windows.Media.PathFigure> objektů; Tyto objekty jsou pojmenovány tak, že každá <xref:System.Windows.Media.PathGeometry>postava popisuje samostatný tvar v . Každý <xref:System.Windows.Media.PathFigure> se skládá z <xref:System.Windows.Media.PathSegment> jednoho nebo více objektů, z nichž každý popisuje segment obrázku.  
  
 Existuje mnoho typů segmentů.  
  
|Typ segmentu|Popis|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|Vytvoří eliptický oblouk mezi dvěma body.|  
|<xref:System.Windows.Media.BezierSegment>|Vytvoří kubickou Bezierovu křivku mezi dvěma body.|  
|<xref:System.Windows.Media.LineSegment>|Vytvoří čáru mezi dvěma body.|  
|<xref:System.Windows.Media.PolyBezierSegment>|Vytvoří řadu kubických Bezierových křivek.|  
|<xref:System.Windows.Media.PolyLineSegment>|Vytvoří řadu řádků.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Vytvoří řadu kvadratické Bezierovy křivky.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Vytvoří kvadratickou Bezierovu křivku.|  
  
 Segmenty v <xref:System.Windows.Media.PathFigure> a jsou sloučeny do jednoho geometrického tvaru, který používá koncový bod segmentu jako počáteční bod dalšího segmentu. Vlastnost <xref:System.Windows.Media.PathFigure.StartPoint%2A> <xref:System.Windows.Media.PathFigure> určuje bod, ze kterého je vykreslen první segment. Každý následující segment začíná v koncovém bodě předchozího segmentu. Například svislou `10,50` `10,150` čáru od do <xref:System.Windows.Media.PathFigure.StartPoint%2A> lze `10,50` definovat nastavením <xref:System.Windows.Media.LineSegment.Point%2A> vlastnosti `10,150`a vytvořením <xref:System.Windows.Media.LineSegment> s nastavením vlastnosti .  
  
 Další informace <xref:System.Windows.Media.PathGeometry> o objektech naleznete v přehledu [geometrie](geometry-overview.md).  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]oblasti můžete také použít speciální zkrácenou syntaxi <xref:System.Windows.Media.PathGeometry.Figures%2A> k <xref:System.Windows.Media.PathGeometry>nastavení vlastnosti . Další informace naleznete v tématu Přehled [syntaxe značek cesty.](path-markup-syntax.md)  
  
 Další informace o syntaxi cesty, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] která se používá v příkladu, naleznete v přehledu [syntaxe značek cesty.](path-markup-syntax.md)  
  
## <a name="see-also"></a>Viz také

- [Ukázka animace cesty](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Syntaxe značek cesty](path-markup-syntax.md)
- [Postupy: Témata animace cesty](path-animation-how-to-topics.md)
- [Přehled animace](animation-overview.md)
- [Přehled způsobů animace vlastností](property-animation-techniques-overview.md)
