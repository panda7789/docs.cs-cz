---
title: Syntaxe značek cesty
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9cd8f9b14f114060ebec8e336c1212d61fa19c83
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="path-markup-syntax"></a>Syntaxe značek cesty
Cesty, které jsou popsané v [tvarů a základní kreslení v přehledu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md) a [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md), ale toto téma popisuje podrobně výkonná a komplexní jazyk malý můžete zadat cestu geometrie více kompaktně pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Zjistit, v tomto tématu, měli byste se seznámit s základní funkce <xref:System.Windows.Media.Geometry> objekty. Další informace najdete v tématu [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry a PathFigureCollection malé – jazyky  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje dvě třídy, které poskytují malé jazyky pro geometrickou cesty popisující: <xref:System.Windows.Media.StreamGeometry> a <xref:System.Windows.Media.PathFigureCollection>.  
  
-   Používáte <xref:System.Windows.Media.StreamGeometry> jazyk malý při nastavování vlastnosti typu <xref:System.Windows.Media.Geometry>, například <xref:System.Windows.UIElement.Clip%2A> vlastnost <xref:System.Windows.UIElement> nebo <xref:System.Windows.Shapes.Path.Data%2A> vlastnost <xref:System.Windows.Shapes.Path> element. Následující příklad používá syntaxi atributů k vytvoření <xref:System.Windows.Media.StreamGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   Můžete použít <xref:System.Windows.Media.PathFigureCollection> jazyk malý při nastavení <xref:System.Windows.Media.PathGeometry.Figures%2A> vlastnost <xref:System.Windows.Media.PathGeometry>. Následující příklad používá syntaxi atributů k vytvoření <xref:System.Windows.Media.PathFigureCollection> pro <xref:System.Windows.Media.PathGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 Jak je vidět v předchozích příkladech jsou velmi podobné dvou malé jazyků. Vždy je možné použít <xref:System.Windows.Media.PathGeometry> v každé situaci, kde můžete použít <xref:System.Windows.Media.StreamGeometry>; Ano která mám použít? Použít <xref:System.Windows.Media.StreamGeometry> použít při nemusíte po vytvoření změňte cestu <xref:System.Windows.Media.PathGeometry> Pokud potřebujete změnit cestu.  
  
 Další informace o rozdílech mezi <xref:System.Windows.Media.PathGeometry> a <xref:System.Windows.Media.StreamGeometry> objekty, najdete [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
### <a name="a-note-about-white-space"></a>Poznámka o mezer  
 Jako stručný výtah a jedna mezera se zobrazí v části syntaxe, které následují, ale více prostory jsou přijatelné taky všude, kde se zobrazí a jedna mezera.  
  
 Dvou čísel nemusí ve skutečnosti oddělených čárkou nebo prázdný znak, ale to provést pouze po jednoznačným výsledný řetězec. Například `2..3` je ve skutečnosti dvě čísla: "2". A ". 3". Podobně `2-3` je "2" a "-3". Mezery nejsou vyžadovány před nebo po příkazy, buď.  
  
### <a name="syntax"></a>Syntaxe  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Atribut použití syntaxe <xref:System.Windows.Media.StreamGeometry> se skládá z volitelný <xref:System.Windows.Media.FillRule> hodnotu a jednu nebo více obrázek popisy.  
  
|Použití atributu StreamGeometry XAML|  
|-----------------------------------------|  
|`<` *object* *property* `="`[ `fillRule`] `figureDescription`[ `figureDescription`]* `" ... />`|  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Atribut použití syntaxe <xref:System.Windows.Media.PathFigureCollection> se skládá z jednoho nebo více popisy obrázek.  
  
|Použití atributu PathFigureCollection XAML|  
|-----------------------------------------------|  
|`<` *object* *property* `="` `figureDescription`[ `figureDescription`]* `" ... />`|  
  
|Termín|Popis|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> Určuje, zda <xref:System.Windows.Media.StreamGeometry> používá <xref:System.Windows.Media.FillRule.EvenOdd> nebo <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A>.<br /><br /> -   `F0` Určuje, <xref:System.Windows.Media.FillRule.EvenOdd> výplně pravidlo.<br />-   `F1` Určuje, <xref:System.Windows.Media.FillRule.Nonzero> výplně pravidlo.<br /><br /> Pokud není tento příkaz, na dílčí cestu použije výchozí chování, což je <xref:System.Windows.Media.FillRule.EvenOdd>. Pokud zadáte tento příkaz, musíte ji nejprve umístit.|  
|*figureDescription*|Obrázek, tvořený move příkazu kreslení příkazy a volitelný příkaz Zavřít.<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|Přesunutí příkaz, který určuje počáteční bod na obrázku. Najdete v článku [příkaz přesunout](#themovecommand) části.|  
|*drawCommands*|Jeden nebo více kreslení příkazy, které popisují obsah na obrázku. Najdete v článku [kreslení příkazy](#drawcommands) části.|  
|*closeCommand*|Volitelné zavřít příkaz, který zavře obrázek. Najdete v článku [zavřít příkaz](#closecommand) části.|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a>Příkaz přesunout  
 Určuje počáteční bod nový obrázek.  
  
|Syntaxe|  
|------------|  
|`M` *startPoint*<br /><br /> - nebo -<br /><br /> `m` *startPoint*|  
  
|Termín|Popis|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Počáteční bod nový obrázek.|  
  
 Velká `M` znamená, že `startPoint` jako absolutní hodnota; jedno malé písmeno `m` znamená, že `startPoint` je posun předchozího bodu nebo (0,0), pokud žádný neexistuje. Pokud uvedete více bodů po příkaz přesunutí, řádek vykreslením do těchto bodů, když jste zadali příkazového řádku.  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a>Kreslení příkazy  
 Příkaz kreslení se může skládat z několika příkazy tvaru. Jsou k dispozici následující příkazy tvar: řádku, vodorovném řádku, svislá čára, krychlový Bézierovu křivku, kvadratické Bézierovy křivky, technologie smooth krychlový Bézierovu křivku, technologie smooth kvadratické Bézierovy křivky a eliptické oblouk.  
  
 Zadejte každý příkaz pomocí velké nebo malé písmeno: velká písmena označují absolutní hodnoty a malá písmena označují relativní hodnoty: kontrolní body pro tento segment jsou relativní vzhledem k koncového bodu v předchozím příkladu. Při zadávání postupně víc než jednoho příkazu stejného typu, můžete vynechat příkaz duplicitní položky. například `L 100,200 300,400` je ekvivalentní `L 100,200 L 300,400`. V následující tabulce jsou popsány **přesunout** a **kreslení** příkazy.  
  
### <a name="line-command"></a>Příkazový řádek  
 Vytvoří přímku mezi bodem aktuální a zadaný koncový bod. `l 20 30` a `L 20,30` jsou příklady platný **řádku** příkazy.  
  
|Syntaxe|  
|------------|  
|`L` *endPoint*<br /><br /> - nebo -<br /><br /> `l` *endPoint*|  
  
|Termín|Popis|  
|----------|-----------------|  
|*endPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Koncový bod řádku.|  

Velká `L` znamená, že `endPoint` jako absolutní hodnota; jedno malé písmeno `l` znamená, že `endPoint` je posun předchozího bodu nebo (0,0), pokud žádný neexistuje.

### <a name="horizontal-line-command"></a>Příkaz Vodorovná čára  
 Vytvoří na vodorovném řádku mezi bodem aktuální a zadaný souřadnice x. `H 90` je příklad příkazu platný vodorovném řádku.

  
|Syntaxe|  
|------------|  
|`H`  *x*<br /><br /> - nebo -<br /><br /> `h`  *x*|  
  
|Termín|Popis|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice x koncového bodu čáry.|  
  
Velká `H` znamená, že `x` jako absolutní hodnota; jedno malé písmeno `h` znamená, že `x` je posun předchozího bodu nebo (0,0), pokud žádný neexistuje.
  
### <a name="vertical-line-command"></a>Příkaz svislá čára  
 Vytvoří svislice mezi bodem aktuální a zadaný souřadnici y. `v 90` je příklad příkazu platný svislá čára.

  
|Syntaxe|  
|------------|  
|`V`  *y*<br /><br /> - nebo -<br /><br /> `v`  *y*|  
  
|Termín|Popis|  
|----------|-----------------|  
|*y*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice y koncového bodu čáry.|  

Velká `V` znamená, že `y` jako absolutní hodnota; jedno malé písmeno `v` znamená, že `y` je posun předchozího bodu nebo (0,0), pokud žádný neexistuje.  
    
### <a name="cubic-bezier-curve-command"></a>Příkaz krychlový Bézierovu křivku  
 Vytvoří krychlový Bézierovu křivku mezi bodem aktuální a zadaný koncový bod pomocí dva body ovládací prvek (`controlPoint`1 a `controlPoint`2). `C 100,200 200,400 300,200` je příkladem křivky platný příkaz.  
  
|Syntaxe|  
|------------|  
|`C` `controlPoint`1`controlPoint`2`endPoint`<br /><br /> - nebo -<br /><br /> `c` `controlPoint`1`controlPoint`2`endPoint`|  
  
|Termín|Popis|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> První řídicí bod křivky, která určuje počáteční tangens křivku.|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Druhý řídicí bod křivky, která určuje koncovou tangens křivku.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod na křivku vykreslením.|  
  
### <a name="quadratic-bezier-curve-command"></a>Příkaz kvadratické Bézierovy křivky  
 Vytvoří kvadratické Bézierovy křivky mezi bodem aktuální a zadaný koncový bod pomocí zadané řídicí bod (`controlPoint`). `q 100,200 300,200` je příkladem platný příkaz kvadratické Bézierovy křivky.  
  
|Syntaxe|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> - nebo -<br /><br /> `q` `controlPoint` `endPoint`|  
  
|Termín|Popis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Řídicí bod křivky, která určuje počáteční a koncovou tangent křivky.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod na křivku vykreslením.|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>Funkce Smooth krychlový Bézierovu křivku příkaz  
 Vytvoří krychlový Bézierovu křivku mezi bodem aktuální a zadaný koncový bod. První řídicí bod se považuje za odraz druhý řídicí bod předchozí příkaz relativně k aktuálnímu bodu. Pokud není žádná předchozí příkaz nebo pokud nebyla předchozí příkaz krychlový příkaz Bézierovy křivky nebo smooth krychlový příkaz Bézierovy křivky, předpokládají, že první řídicí bod je totožná se aktuálnímu bodu. Druhý řídicí bod, kontrolního bodu pro element end křivky, je zadána `controlPoint`2. Například `S 100,200 200,300` je platný smooth krychlový Bézierovy křivky příkaz.  
  
|Syntaxe|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> - nebo -<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|Termín|Popis|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Řídicí bod křivky, která určuje koncovou tangens křivku.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod na křivku vykreslením.|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>Funkce Smooth kvadratické Bézierovy křivky příkaz  
 Vytvoří kvadratické Bézierovy křivky mezi bodem aktuální a zadaný koncový bod. Řídicí bod se považuje za odraz řídicího bodu pro předchozí příkaz relativně k aktuálnímu bodu. Pokud není žádná předchozí příkaz nebo pokud nebyla předchozí příkaz kvadratické Bézierovy křivky příkaz nebo smooth kvadratické Bézierovy křivky příkaz, je totožnou s bodem aktuální řídicí bod.  
  
|Syntaxe|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> - nebo -<br /><br /> `t` `controlPoint` `endPoint`|  
  
|Termín|Popis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Řídicí bod křivky, která určuje počáteční a tečný křivky.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod na křivku vykreslením.|  
  
### <a name="elliptical-arc-command"></a>Příkaz eliptické oblouk  
 Vytvoří oblouk eliptické mezi bodem aktuální a zadaný koncový bod.  
  
|Syntaxe|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> - nebo -<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|Termín|Popis|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> Hodnota x - a y úhlu oblouk.|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Otočení se třemi tečkami ve stupních.|  
|`isLargeArcFlag`|Pokud úhel oblouku by měla být 180 stupňů nastavena na hodnotu 1 nebo novější; jinak hodnota nastavena na hodnotu 0.|  
|`sweepDirectionFlag`|Nastavena na hodnotu 1, pokud oblouk vykreslením kladnou úhel směrem; jinak hodnota nastavena na hodnotu 0.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod na oblouk vykreslením.|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a>Příkaz Zavřít  
 Končí na aktuální obrázku a vytvoří řádek, který spojuje bod aktuální výchozí bod na obrázku. Tento příkaz vytvoří řádku spojení (rohu) mezi poslední segment a první segment na obrázku.  
  
|Syntaxe|  
|------------|  
|`Z`<br /><br /> - nebo -<br /><br /> `z`|  

<a name="pointsyntax"></a>   
## <a name="point-syntax"></a>Syntaxe bodu  
 Popisuje a y souřadnice x bodu, kde (0,0) je levého horního rohu.
  
|Syntaxe|  
|------------|  
|`x` `,` `y`<br /><br /> - nebo -<br /><br /> `x``y`|  
  
|Termín|Popis|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice x bodu.|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice y bodu.|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a>Speciální hodnoty  
 Místo standardní číselnou hodnotu můžete také použít následující zvláštní hodnoty. Tyto hodnoty jsou malá a velká písmena.  
  
 Infinity  
 Představuje <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.  
  
 -Infinity  
 Představuje <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.  
  
 NaN  
 Představuje <xref:System.Double.NaN?displayProperty=nameWithType>.  
  
 Můžete také používat exponenciální notace. Například `+1.e17` platná hodnota.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.PathFigureCollection>  
 [Přehled objektů Shape a základního kreslení ve WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)
