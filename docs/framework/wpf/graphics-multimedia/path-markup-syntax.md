---
title: Syntaxe značek cesty
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: adcedcea6c8d6d988021cbbccf87bd25a042fd16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181851"
---
# <a name="path-markup-syntax"></a>Syntaxe značek cesty
Cesty jsou popsány v [obrazcích a základní výkres v WPF Přehled](shapes-and-basic-drawing-in-wpf-overview.md) a [Přehled geometrie](geometry-overview.md), ale toto téma podrobně popisuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]výkonný a složitý mini-jazyk, který můžete použít k určení geometrie cesty kompaktněji pomocí .  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Chcete-li pochopit toto téma, měli <xref:System.Windows.Media.Geometry> byste být obeznámeni se základními funkcemi objektů. Další informace naleznete v tématu [Přehled geometrie](geometry-overview.md).  
  
<a name="abouthisdocument"></a>
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>Minijazyky StreamGeometry a PathFigureCollection  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje dvě třídy, které poskytují mini-jazyky pro popis geometrické cesty: <xref:System.Windows.Media.StreamGeometry> a <xref:System.Windows.Media.PathFigureCollection>.  
  
- <xref:System.Windows.Media.StreamGeometry> Mini-jazyk se používá při nastavování vlastnosti <xref:System.Windows.Media.Geometry>typu <xref:System.Windows.UIElement> , například <xref:System.Windows.Shapes.Path> <xref:System.Windows.UIElement.Clip%2A> vlastnost nebo <xref:System.Windows.Shapes.Path.Data%2A> vlastnost prvku. Následující příklad používá syntaxi <xref:System.Windows.Media.StreamGeometry>atributu k vytvoření .  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
- Minijazyk <xref:System.Windows.Media.PathFigureCollection> se používá při <xref:System.Windows.Media.PathGeometry.Figures%2A> nastavování <xref:System.Windows.Media.PathGeometry>vlastnosti rozhraní . Následující příklad používá syntaxi atributu k vytvoření <xref:System.Windows.Media.PathFigureCollection> a <xref:System.Windows.Media.PathGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 Jak můžete vidět z předchozích příkladů, dva mini-jazyky jsou velmi podobné. Je vždy možné použít <xref:System.Windows.Media.PathGeometry> v každé situaci, kdy <xref:System.Windows.Media.StreamGeometry>byste mohli použít ; takže který z nich byste měli použít? Použijte, <xref:System.Windows.Media.StreamGeometry> když není nutné upravit cestu po jejím vytvoření; použijte, <xref:System.Windows.Media.PathGeometry> pokud potřebujete upravit cestu.  
  
 Další informace o rozdílech <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.StreamGeometry> mezi objekty a objekty naleznete v přehledu [geometrie](geometry-overview.md).  
  
### <a name="a-note-about-white-space"></a>Poznámka o prázdnéploše  
 Pro stručnost je v následujících částech syntaxe zobrazena jedna mezera, ale více mezer je také přijatelné všude tam, kde je zobrazena jedna mezera.  
  
 Dvě čísla ve skutečnosti nemusí být oddělena čárkou nebo mezerami, ale to lze provést pouze v případě, že výsledný řetězec je jednoznačný. Například, `2..3` je vlastně dvě čísla: "2." A ".3". Podobně `2-3` je "2" a "-3". Mezery nejsou vyžadovány před nebo po příkazy, a to buď.  
  
### <a name="syntax"></a>Syntaxe  
 Syntaxe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] použití atributu pro <xref:System.Windows.Media.StreamGeometry> a <xref:System.Windows.Media.FillRule> se skládá z volitelné hodnoty a jednoho nebo více popisů obrázku.  
  
|Využití atributu XAML StreamGeometry|  
|-----------------------------------------|  
|`<`*vlastnost objektu* *property* `="`[ `fillRule`] `figureDescription`[ `figureDescription`]*`" ... />`|  
  
 Syntaxe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] použití atributu pro a <xref:System.Windows.Media.PathFigureCollection> se skládá z jednoho nebo více popisů obrázku.  
  
|Využití atributu PathFigureCollection XAML|  
|-----------------------------------------------|  
|`<`*vlastnost* *objektu* `="` `figureDescription`[ `figureDescription`]*`" ... />`|  
  
|Označení|Popis|  
|----------|-----------------|  
|*Fillrule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Media.StreamGeometry> Určuje, zda se <xref:System.Windows.Media.FillRule.EvenOdd> <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A>použije písmeno nebo .<br /><br /> -   `F0`určuje pravidlo <xref:System.Windows.Media.FillRule.EvenOdd> výplně.<br />-   `F1`určuje pravidlo <xref:System.Windows.Media.FillRule.Nonzero> výplně.<br /><br /> Pokud tento příkaz vynechete, podcesta použije <xref:System.Windows.Media.FillRule.EvenOdd>výchozí chování, které je . Pokud zadáte tento příkaz, musíte jej nejprve umístit.|  
|*obrázekPopis*|Obrázek složený z příkazu move, příkazů kreslení a volitelného příkazu zavřít.<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|Příkaz move, který určuje počáteční bod obrázku. Viz část [Příkaz k přesunutí.](#themovecommand)|  
|*drawPříkazy*|Jeden nebo více příkazů kreslení, které popisují obsah obrázku. Viz část [Nakreslit příkazy.](#drawcommands)|  
|*closeCommand*|Volitelný příkaz zavřít, který zavře obrázek. Viz část [Zavřít příkaz.](#closecommand)|  
  
<a name="themovecommand"></a>
## <a name="move-command"></a>Přesunout, příkaz  
 Určuje počáteční bod nového obrázku.  
  
|Syntaxe|  
|------------|  
|`M`*startpoint*<br /><br /> - nebo -<br /><br /> `m`*startpoint*|  
  
|Označení|Popis|  
|----------|-----------------|  
|*startpoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Počáteční bod nové holce.|  
  
 Velká písmena `M` `startPoint` označují, že je absolutní hodnota; malá písmena `m` `startPoint` označují, že je posun k předchozímu bodu, nebo (0,0), pokud neexistuje. Pokud za příkazem move uvádíte více bodů, bude k těmto bodům nakreslena čára, i když jste zadali příkaz čáry.  
  
<a name="drawcommands"></a>
## <a name="draw-commands"></a>Kreslit příkazy  
 Příkaz kreslení se může skládat z několika příkazů tvaru. K dispozici jsou následující příkazy tvaru: čára, vodorovná čára, svislá čára, krychlová Bezierova křivka, kvadratická Bezierova křivka, hladká kubická Bezierova křivka, hladká kvadratická Bezierova křivka a eliptický oblouk.  
  
 Každý příkaz zadáte pomocí velkých nebo malých písmen: velká písmena označují absolutní hodnoty a malá písmena označují relativní hodnoty: řídicí body pro tento segment jsou relativní vzhledem ke koncovému bodu předchozího příkladu. Při postupném zadávání více než jednoho příkazu stejného typu můžete vynechat duplicitní položku příkazu; například `L 100,200 300,400` je ekvivalentní `L 100,200 L 300,400`. Následující tabulka popisuje **příkazy pro přesun** a **kreslení.**  
  
### <a name="line-command"></a>Příkaz řádek  
 Vytvoří přímku mezi aktuálním a zadaným koncovým bodem. `l 20 30`a `L 20,30` jsou příklady platných **řádkových** příkazů.  
  
|Syntaxe|  
|------------|  
|`L`*koncový bod*<br /><br /> - nebo -<br /><br /> `l`*koncový bod*|  
  
|Označení|Popis|  
|----------|-----------------|  
|*Koncový bod*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Koncový bod čáry.|  

Velká písmena `L` `endPoint` označují, že je absolutní hodnota; malá písmena `l` `endPoint` označují, že je posun k předchozímu bodu, nebo (0,0), pokud neexistuje.

### <a name="horizontal-line-command"></a>Příkaz Vodorovná čára  
 Vytvoří vodorovnou čáru mezi aktuálním bodem a zadanou souřadnicí x. `H 90`je příkladem platného příkazu vodorovné čáry.

|Syntaxe|  
|------------|  
|`H`  *X*<br /><br /> - nebo -<br /><br /> `h`  *X*|  
  
|Označení|Popis|  
|----------|-----------------|  
|*X*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice x koncového bodu čáry.|  
  
Velká písmena `H` `x` označují, že je absolutní hodnota; malá písmena `h` `x` označují, že je posun k předchozímu bodu, nebo (0,0), pokud neexistuje.
  
### <a name="vertical-line-command"></a>Příkaz Svislé čáry  
 Vytvoří svislou čáru mezi aktuálním bodem a zadanou souřadnicí y. `v 90`je příkladem platného příkazu svislé čáry.

|Syntaxe|  
|------------|  
|`V`  *Y*<br /><br /> - nebo -<br /><br /> `v`  *Y*|  
  
|Označení|Popis|  
|----------|-----------------|  
|*Y*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice y koncového bodu čáry.|  

Velká písmena `V` `y` označují, že je absolutní hodnota; malá písmena `v` `y` označují, že je posun k předchozímu bodu, nebo (0,0), pokud neexistuje.  

### <a name="cubic-bezier-curve-command"></a>Příkaz Kubické beziierovy křivky  
 Vytvoří kubickou Bezierovu křivku mezi aktuálním bodem a zadaným koncovým bodem pomocí dvou určených řídicích bodů (`controlPoint`1 a `controlPoint`2). `C 100,200 200,400 300,200`je příkladem platného příkazu křivky.  
  
|Syntaxe|  
|------------|  
|`C``controlPoint`1`controlPoint`2.`endPoint`<br /><br /> - nebo -<br /><br /> `c``controlPoint`1`controlPoint`2.`endPoint`|  
  
|Označení|Popis|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> První řídicí bod křivky, který určuje počáteční tečnu křivky.|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Druhý řídicí bod křivky, který určuje koncovou tečnu křivky.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod, ke kterému je křivka nakreslena.|  
  
### <a name="quadratic-bezier-curve-command"></a>Kvadratická Bezierova křivka, příkaz  
 Vytvoří kvadratickou Bezierovu křivku mezi aktuálním a zadaným`controlPoint`koncovým bodem pomocí určeného řídicího bodu ( ). `q 100,200 300,200`je příkladem platného příkazu kvadratické Bezierovy křivky.  
  
|Syntaxe|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> - nebo -<br /><br /> `q` `controlPoint` `endPoint`|  
  
|Označení|Popis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Řídicí bod křivky, který určuje počáteční a koncové tečny křivky.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod, ke kterému je křivka nakreslena.|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>Příkaz Hladká kubická Bezierova křivka  
 Vytvoří kubickou Bezierovu křivku mezi aktuálním a zadaným koncovým bodem. Předpokládá se, že první řídicí bod je odrazem druhého řídicího bodu předchozího příkazu vzhledem k aktuálnímu bodu. Pokud neexistuje žádný předchozí příkaz nebo pokud předchozí příkaz nebyl příkazem kubické Bezierovy křivky nebo příkazem hladké kubické Bezierovy křivky, předpokládejme, že první řídicí bod je totožný s aktuálním bodem. Druhý řídicí bod, řídicí bod pro konec křivky, `controlPoint`je určen 2. Je například `S 100,200 200,300` platný příkaz hladké kubické Bezierovy křivky.  
  
|Syntaxe|  
|------------|  
|`S``controlPoint`2.`endPoint`<br /><br /> - nebo -<br /><br /> `s``controlPoint`2.`endPoint`|  
  
|Označení|Popis|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Řídicí bod křivky, který určuje koncovou tečnu křivky.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod, ke kterému je křivka nakreslena.|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>Příkaz Kvadratické Bezierovy křivky  
 Vytvoří kvadratickou Bezierovu křivku mezi aktuálním a zadaným koncovým bodem. Řídicí bod je považován za odraz řídicího bodu předchozího příkazu vzhledem k aktuálnímu bodu. Pokud neexistuje žádný předchozí příkaz nebo pokud předchozí příkaz nebyl kvadratický příkaz Bezierovy křivky nebo příkaz hladké kvadratické Bezierovy křivky, řídicí bod je totožný s aktuálním bodem.  
  
|Syntaxe|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> - nebo -<br /><br /> `t` `controlPoint` `endPoint`|  
  
|Označení|Popis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Řídicí bod křivky, který určuje počáteční a tečnou křivky.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod, ke kterému je křivka nakreslena.|  
  
### <a name="elliptical-arc-command"></a>Příkaz eliptický oblouk  
 Vytvoří eliptický oblouk mezi aktuálním a určeným koncovým bodem.  
  
|Syntaxe|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> - nebo -<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|Označení|Popis|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> Poloměr x a y oblouku.|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Rotace elipsy, ve stupních.|  
|`isLargeArcFlag`|Nastavte na 1, pokud by měl být úhel oblouku 180 stupňů nebo větší; v opačném případě nastavte 0.|  
|`sweepDirectionFlag`|Nastavte na 1, pokud je oblouk nakreslen ve směru kladného úhlu; v opačném případě nastavte 0.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod, ke kterému je nakreslena oblouku.|  
  
<a name="closecommand"></a>
## <a name="the-close-command"></a>Příkaz Zavřít  
 Ukončí aktuální obrázek a vytvoří čáru, která spojuje aktuální bod s počátečním bodem obrázku. Tento příkaz vytvoří spoj(roh) mezi posledním segmentem a prvním segmentem obrázku.  
  
|Syntaxe|  
|------------|  
|`Z`<br /><br /> - nebo -<br /><br /> `z`|  

<a name="pointsyntax"></a>
## <a name="point-syntax"></a>Syntaxe bodu  
 Popisuje souřadnice x a y bodu, kde (0,0) je levý horní roh.
  
|Syntaxe|  
|------------|  
|`x` `,` `y`<br /><br /> - nebo -<br /><br /> `x` `y`|  
  
|Označení|Popis|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice x bodu.|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice bodu.|  
  
<a name="specialvalues"></a>
## <a name="special-values"></a>Speciální hodnoty  
 Namísto standardní číselné hodnoty můžete také použít následující speciální hodnoty. Tyto hodnoty rozlišují malá a velká písmena.  
  
 Nekonečno  
 Představuje <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.  
  
 -Nekonečno  
 Představuje <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.  
  
 Není číslo  
 Představuje <xref:System.Double.NaN?displayProperty=nameWithType>.  
  
 Můžete také použít vědecký zápis. Například `+1.e17` je platná hodnota.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.PathFigureCollection>
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Přehled geometrie](geometry-overview.md)
- [Témata s postupy](geometries-how-to-topics.md)
