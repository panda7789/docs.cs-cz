---
title: Syntaxe značek cesty
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: d681cd15fa3daa3698edc5e0ad3d3c2669c1dfdf
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591929"
---
# <a name="path-markup-syntax"></a>Syntaxe značek cesty
Cesty jsou popsány v [tvary a základní kresby v přehledu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md) a [přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md), ale toto téma popisuje podrobně výkonná a komplexní zkrácené jazyk, slouží k určení cesty geometrie více kompaktně pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu informace o tom, měli byste se seznámit se základními funkcemi <xref:System.Windows.Media.Geometry> objekty. Další informace najdete v tématu [přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>Streamgeometry – a PathFigureCollection Mini – jazyky  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje dvě třídy, které poskytují mini jazyky pro popis geometrické cesty: <xref:System.Windows.Media.StreamGeometry> a <xref:System.Windows.Media.PathFigureCollection>.  
  
-   Použijete <xref:System.Windows.Media.StreamGeometry> zkrácené jazyce, pokud je nastavení vlastnosti typu <xref:System.Windows.Media.Geometry>, jako <xref:System.Windows.UIElement.Clip%2A> vlastnost <xref:System.Windows.UIElement> nebo <xref:System.Windows.Shapes.Path.Data%2A> vlastnost <xref:System.Windows.Shapes.Path> element. Následující příklad používá syntaxi atributů k vytvoření <xref:System.Windows.Media.StreamGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   Použijete <xref:System.Windows.Media.PathFigureCollection> zkrácené jazyk při nastavení <xref:System.Windows.Media.PathGeometry.Figures%2A> vlastnost <xref:System.Windows.Media.PathGeometry>. Následující příklad používá syntaxi atributů k vytvoření <xref:System.Windows.Media.PathFigureCollection> pro <xref:System.Windows.Media.PathGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 Jak je vidět z předchozích příkladů dva jazyků mini jsou velmi podobné. Vždy je možné použít <xref:System.Windows.Media.PathGeometry> v každé situaci, kde můžete použít <xref:System.Windows.Media.StreamGeometry>; Ano která byste měli použít? Použít <xref:System.Windows.Media.StreamGeometry> při není nutné změnit cesty po vytvoření; použijte <xref:System.Windows.Media.PathGeometry> Pokud potřebujete změnit cesty.  
  
 Další informace o rozdílech mezi <xref:System.Windows.Media.PathGeometry> a <xref:System.Windows.Media.StreamGeometry> objekty, najdete [přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
### <a name="a-note-about-white-space"></a>Poznámka k prázdné znaky  
 Pro zkrácení se zobrazí jedna mezera v oddílech syntaxe, které následují, ale více prostorů jsou přijatelné také všude, kde se zobrazí jedna mezera.  
  
 Dvě čísla nemusí ve skutečnosti být odděleny čárkami nebo mezerami, ale to jde jenom když je výsledný řetězec je jednoznačný. Například `2..3` je ve skutečnosti dvě čísla: "2". A ". 3". Obdobně `2-3` je "2" a "-3". Mezery nejsou vyžadovány před nebo po příkazech, buď.  
  
### <a name="syntax"></a>Syntaxe  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Použití syntaxe pro atribut <xref:System.Windows.Media.StreamGeometry> se skládá z volitelné <xref:System.Windows.Media.FillRule> hodnotu a jeden nebo více obrázek popisy.  
  
|Použití atributu XAML StreamGeometry|  
|-----------------------------------------|  
|`<` *objekt* *vlastnost* `="`[ `fillRule`] `figureDescription`[ `figureDescription`] * `" ... />`|  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Použití syntaxe pro atribut <xref:System.Windows.Media.PathFigureCollection> se skládá z jednoho nebo více popisy obrázek.  
  
|Použití atributu XAML PathFigureCollection|  
|-----------------------------------------------|  
|`<` *objekt* *vlastnost* `="` `figureDescription`[ `figureDescription`] * `" ... />`|  
  
|Termín|Popis|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> Určuje, zda <xref:System.Windows.Media.StreamGeometry> používá <xref:System.Windows.Media.FillRule.EvenOdd> nebo <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A>.<br /><br /> -   `F0` Určuje, <xref:System.Windows.Media.FillRule.EvenOdd> výplně pravidlo.<br />-   `F1` Určuje, <xref:System.Windows.Media.FillRule.Nonzero> výplně pravidlo.<br /><br /> Vynecháte-li tento příkaz, podřízená cesta v použije výchozí chování, což je <xref:System.Windows.Media.FillRule.EvenOdd>. Pokud zadáte tento příkaz, musíte ji nejprve umístit.|  
|*figureDescription*|Obrázek skládá move příkazu, nakreslete příkazy a volitelný příkaz Zavřít.<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|Přesunout příkaz, který určuje počáteční bod na obrázku. Zobrazit [příkaz přesunout](#themovecommand) části.|  
|*drawCommands*|Jeden nebo více výkresu příkazů, které popisují obsah na obrázku. Najdete v článku [vykreslení příkazů](#drawcommands) oddílu.|  
|*closeCommand*|Volitelný zavřít příkaz, který obrázek se zavře. Zobrazit [příkaz Zavřít](#closecommand) části.|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a>Příkaz přesunout  
 Určuje počáteční bod nový obrázek.  
  
|Syntaxe|  
|------------|  
|`M` *startPoint*<br /><br /> - nebo -<br /><br /> `m` *startPoint*|  
  
|Termín|Popis|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Počáteční bod nový obrázek.|  
  
 Velké `M` znamená, že `startPoint` je absolutní hodnota; malé `m` znamená, že `startPoint` je posun oproti dřívějšímu bodu, nebo (0,0), pokud žádný neexistuje. Pokud uvedete více bodů po příkazu přesunout, linie vychází do těchto bodů v případě, že jste zadali příkazového řádku.  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a>Příkazy vystavení  
 Příkaz vystavení se může skládat z několika příkazů tvaru. Nejsou k dispozici následující příkazy obrazce: řádek, vodorovnou horizontální čáru, svislá čára, kubické Bézierovy křivky, kvadratické Bézierovy křivky, smooth kubické Bézierovy křivky, smooth kvadratické Bézierovy křivky a oblouku elipsy.  
  
 Zadejte jednotlivé příkazy pomocí velkým nebo malým písmenem: velká písmena označení hodnoty absolutní a relativní hodnoty označení malá písmena: kontrolní body pro tento segment jsou relativní vzhledem k koncový bod v předchozím příkladu. Při zadávání postupně více než jednoho příkazu stejného typu, můžete vynechat příkaz duplicitní položky. například `L 100,200 300,400` je ekvivalentní `L 100,200 L 300,400`. V následující tabulce jsou popsány **přesunout** a **nakreslit** příkazy.  
  
### <a name="line-command"></a>Příkazový řádek  
 Vytvoří rovné čáry mezi aktuálním bodem a zadaným koncový bod. `l 20 30` a `L 20,30` jsou příklady platných **řádku** příkazy.  
  
|Syntaxe|  
|------------|  
|`L` *koncový bod*<br /><br /> - nebo -<br /><br /> `l` *koncový bod*|  
  
|Termín|Popis|  
|----------|-----------------|  
|*koncový bod*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Koncový bod čáry.|  

Velké `L` znamená, že `endPoint` je absolutní hodnota; malé `l` znamená, že `endPoint` je posun oproti dřívějšímu bodu, nebo (0,0), pokud žádný neexistuje.

### <a name="horizontal-line-command"></a>Příkaz Vodorovná čára  
 Vytvoří vodorovnou horizontální čáru mezi aktuálním bodem a zadaným souřadnici x. `H 90` je příklad příkazu platná vodorovnou horizontální čáru.

  
|Syntaxe|  
|------------|  
|`H`  *x*<br /><br /> - nebo -<br /><br /> `h`  *x*|  
  
|Termín|Popis|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice x koncového bodu čáry.|  
  
Velké `H` znamená, že `x` je absolutní hodnota; malé `h` znamená, že `x` je posun oproti dřívějšímu bodu, nebo (0,0), pokud žádný neexistuje.
  
### <a name="vertical-line-command"></a>Příkaz svislá čára  
 Vytvoří svislé čáry mezi aktuálním bodem a zadaným souřadnice na ose y. `v 90` je příklad příkazu platná svislé čáry.

  
|Syntaxe|  
|------------|  
|`V`  *y*<br /><br /> - nebo -<br /><br /> `v`  *y*|  
  
|Termín|Popis|  
|----------|-----------------|  
|*y*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice y koncového bodu čáry.|  

Velké `V` znamená, že `y` je absolutní hodnota; malé `v` znamená, že `y` je posun oproti dřívějšímu bodu, nebo (0,0), pokud žádný neexistuje.  
    
### <a name="cubic-bezier-curve-command"></a>Příkaz kubické Bézierovy křivky  
 Vytvoří kubické Bézierovy křivky mezi aktuálním bodem a zadaným koncový bod s použitím dva body zadaný ovládací prvek (`controlPoint`1 a `controlPoint`2). `C 100,200 200,400 300,200` je příklad příkazu platná křivky.  
  
|Syntaxe|  
|------------|  
|`C` `controlPoint`1`controlPoint`2`endPoint`<br /><br /> - nebo -<br /><br /> `c` `controlPoint`1`controlPoint`2`endPoint`|  
  
|Termín|Popis|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> První řídicí bod křivky, která určuje počáteční tangens křivky.|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Druhý řídicí bod křivky, který určuje koncové tangens křivky.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod křivky je vykreslit.|  
  
### <a name="quadratic-bezier-curve-command"></a>Příkaz kvadratické Bézierovy křivky  
 Vytvoří kvadratické Bézierovy křivky mezi aktuálním bodem a zadaným koncový bod pomocí bodu zadaný ovládací prvek (`controlPoint`). `q 100,200 300,200` je příkladem platný příkaz kvadratické Bézierovy křivky.  
  
|Syntaxe|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> - nebo -<br /><br /> `q` `controlPoint` `endPoint`|  
  
|Termín|Popis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Řídicí bod křivky, která určuje počáteční a koncovou tečny křivky.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod křivky je vykreslit.|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>Příkaz kubické Bézierovy křivky vyhlazení  
 Vytvoří kubické Bézierovy křivky mezi aktuálním bodem a zadaným koncový bod. První řídicí bod je považován za reflexe druhý řídicí bod předchozího příkazu, vzhledem k aktuálnímu bodu. Pokud neexistuje žádný předchozí příkaz nebo pokud předchozí příkaz nebyl kubické Bézierovy křivky příkazu nebo příkazu smooth křivky kubické Bézierovy křivky, Předpokládejme, že první řídicí bod je totožná se do aktuálního místa. Druhý ovládací prvek bod, bod ovládacího prvku na konci křivku, je určená `controlPoint`2. Například `S 100,200 200,300` je platný smooth kubické Bézierovy křivky příkaz.  
  
|Syntaxe|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> - nebo -<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|Termín|Popis|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Řídicí bod křivky, který určuje koncové tangens křivky.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod křivky je vykreslit.|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>Příkaz kvadratické Bézierovy křivky vyhlazení  
 Vytvoří kvadratické Bézierovy křivky mezi aktuálním bodem a zadaným koncový bod. Řídicí bod je považován za reflexe řídicí bod předchozího příkazu, vzhledem k aktuálnímu bodu. Pokud není žádná předchozí příkaz nebo pokud předchozí příkaz nebyl kvadratické Bézierovy křivky příkazu nebo příkazu smooth křivky kvadratické Bézierovy křivky řídicí bod je totožná se do aktuálního místa.  
  
|Syntaxe|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> - nebo -<br /><br /> `t` `controlPoint` `endPoint`|  
  
|Termín|Popis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Řídicí bod křivky, která určuje počáteční a tečný křivky.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod křivky je vykreslit.|  
  
### <a name="elliptical-arc-command"></a>Příkaz oblouku elipsy  
 Vytvoří oblouku elipsy mezi aktuálním bodem a zadaným koncový bod.  
  
|Syntaxe|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> - nebo -<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|Termín|Popis|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> X - a y úhlu oblouku.|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Otočení elipsy ve stupních.|  
|`isLargeArcFlag`|Nastavíte úhel oblouku by měl být 180stupňový rozsah s orientací na 1 nebo novější; v opačném případě nastavte na hodnotu 0.|  
|`sweepDirectionFlag`|Nastavte na 1, pokud oblouku vykreslením ve směru pozitivní úhel; v opačném případě nastavte na hodnotu 0.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod na oblouk vykreslením.|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a>Příkaz Zavřít  
 Ukončí aktuální obrázek a vytvoří řádek, který spojuje bod aktuální výchozí bod na obrázku. Tento příkaz vytvoří řádku spojení (rohu). poslední segment a první segment na obrázku.  
  
|Syntaxe|  
|------------|  
|`Z`<br /><br /> - nebo -<br /><br /> `z`|  

<a name="pointsyntax"></a>   
## <a name="point-syntax"></a>Syntaxe bodu  
 Popisuje x - a souřadnice y bodu, kde (0; 0) je levého horního rohu.
  
|Syntaxe|  
|------------|  
|`x` `,` `y`<br /><br /> - nebo -<br /><br /> `x``y`|  
  
|Termín|Popis|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice x bodu.|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice y bodu.|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a>Speciální hodnoty  
 Místo standardní číselnou hodnotu můžete také použít následující speciální hodnoty. Tyto hodnoty jsou malá a velká písmena.  
  
 Infinity  
 Představuje <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.  
  
 -Nekonečno  
 Představuje <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.  
  
 NaN  
 Představuje <xref:System.Double.NaN?displayProperty=nameWithType>.  
  
 Můžete také použít vědecký zápis. Například `+1.e17` platná hodnota.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.PathFigureCollection>  
 [Přehled objektů Shape a základního kreslení ve WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)
