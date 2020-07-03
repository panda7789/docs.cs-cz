---
title: Syntaxe značek cesty
description: Přečtěte si o výkonném a komplexním minimu jazyku, který můžete použít k zadání cesty Compact geometrií v Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: 6d2778522b622f0b0dcb59673e793a6d772a4b4f
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853651"
---
# <a name="path-markup-syntax"></a>Syntaxe značek cesty
Cesty jsou popsány v tématu [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md) a [Geometry Overview](geometry-overview.md), ale toto téma podrobně popisuje výkonný a složitý miniický jazyk, který můžete použít k určení cesty geometrií kompaktnější pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Pro pochopení tohoto tématu byste měli být obeznámeni se základními funkcemi <xref:System.Windows.Media.Geometry> objektů. Další informace najdete v [přehledu geometrie](geometry-overview.md).  
  
<a name="abouthisdocument"></a>
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry a PathFigureCollection zkrácené jazyky  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje dvě třídy, které poskytují zkrácené jazyky pro popis geometrických cest: <xref:System.Windows.Media.StreamGeometry> a <xref:System.Windows.Media.PathFigureCollection> .  
  
- <xref:System.Windows.Media.StreamGeometry>Při nastavování vlastnosti typu <xref:System.Windows.Media.Geometry> , jako je například <xref:System.Windows.UIElement.Clip%2A> vlastnost <xref:System.Windows.UIElement> nebo <xref:System.Windows.Shapes.Path.Data%2A> vlastnost prvku, používáte zkrácený jazyk <xref:System.Windows.Shapes.Path> . Následující příklad používá syntaxi atributu k vytvoření <xref:System.Windows.Media.StreamGeometry> .  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
- <xref:System.Windows.Media.PathFigureCollection>Při nastavování vlastnosti pro je použit zkrácený jazyk <xref:System.Windows.Media.PathGeometry.Figures%2A> <xref:System.Windows.Media.PathGeometry> . Následující příklad používá syntaxi atributu pro vytvoření <xref:System.Windows.Media.PathFigureCollection> pro <xref:System.Windows.Media.PathGeometry> .  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 Jak vidíte v předchozích příkladech, dva malé jazyky jsou velmi podobné. V jakékoli situaci je vždycky možné použít <xref:System.Windows.Media.PathGeometry> , pokud byste mohli použít <xref:System.Windows.Media.StreamGeometry> , takže byste měli použít? Použijte, <xref:System.Windows.Media.StreamGeometry> když po jeho vytvoření nemusíte cestu upravovat <xref:System.Windows.Media.PathGeometry> . Pokud budete chtít cestu změnit, použijte.  
  
 Další informace o rozdílech mezi <xref:System.Windows.Media.PathGeometry> objekty a <xref:System.Windows.Media.StreamGeometry> naleznete v [přehledu geometrie](geometry-overview.md).  
  
### <a name="a-note-about-white-space"></a>Poznámka o mezerách  
 V případě zkrácení se v následujících oddílech syntaxe zobrazí jedno místo, ale více mezer je současně přijatelné všude, kde je zobrazeno jedno místo.  
  
 Dvě čísla ve skutečnosti nemusí být oddělena čárkou nebo prázdným znakem, ale lze ji provést pouze v případě, že výsledný řetězec je nejednoznačný. Například `2..3` je ve skutečnosti dvě čísla: "2". A ". 3". Podobně `2-3` je to "2" a "-3". Mezery nejsou požadovány před nebo za příkazy, buď.  
  
### <a name="syntax"></a>Syntax  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]Syntaxe použití atributu pro <xref:System.Windows.Media.StreamGeometry> se skládá z volitelné <xref:System.Windows.Media.FillRule> hodnoty a jednoho nebo více popisů obrázku.  
  
|Použití atributu StreamGeometry XAML|  
|-----------------------------------------|  
|`<`*Object* – *vlastnost* `="` [ `fillRule` ] `figureDescription` [ `figureDescription` ] *`" ... />`|  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]Syntaxe použití atributu pro <xref:System.Windows.Media.PathFigureCollection> se skládá z jednoho nebo více popisů obrázku.  
  
|Použití atributu PathFigureCollection XAML|  
|-----------------------------------------------|  
|`<`*Object* – *vlastnost* `="` `figureDescription` [ `figureDescription` ] *`" ... />`|  
  
|Pojem|Popis|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> Určuje, zda <xref:System.Windows.Media.StreamGeometry> používá <xref:System.Windows.Media.FillRule.EvenOdd> <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A> .<br /><br /> -   `F0`Určuje <xref:System.Windows.Media.FillRule.EvenOdd> pravidlo výplně.<br />-   `F1`Určuje <xref:System.Windows.Media.FillRule.Nonzero> pravidlo výplně.<br /><br /> Pokud tento příkaz vynecháte, použije dílčí cesta výchozí chování, což je <xref:System.Windows.Media.FillRule.EvenOdd> . Pokud zadáte tento příkaz, musíte ho nejdřív umístit.|  
|*figureDescription*|Obrázek tvořený příkazem Move, příkazy kreslení a volitelným ukončovacím příkazem.<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|Příkaz Move, který určuje počáteční bod obrázku. Viz část [přesunutí příkazu](#themovecommand) .|  
|*drawCommands*|Jeden nebo více příkazů kreslení popisujících obsah obrázku. Viz část [Draw Commands](#drawcommands) .|  
|*closeCommand*|Volitelný uzavírací příkaz, který zavírá obrázek. Viz část [příkazu Zavřít](#closecommand) .|  
  
<a name="themovecommand"></a>
## <a name="move-command"></a>Přesunout příkaz  
 Určuje počáteční bod nového obrázku.  
  
|Syntax|  
|------------|  
|`M`*startPoint*<br /><br /> - nebo -<br /><br /> `m`*startPoint*|  
  
|Pojem|Popis|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Počáteční bod nového obrázku.|  
  
 Velká písmena `M` označují, že `startPoint` se jedná o absolutní hodnotu; malé písmeno `m` označuje, že `startPoint` se jedná o posun k předchozímu bodu, nebo (0, 0), pokud žádný neexistuje. Pokud vypíšete více bodů po příkazu přesunout, je čára nakreslena na tyto body, i když jste zadali příkaz line.  
  
<a name="drawcommands"></a>
## <a name="draw-commands"></a>Příkazy Draw  
 Příkaz pro kreslení se může skládat z několika příkazů Shape. K dispozici jsou následující příkazy tvaru: line, vodorovná čára, svislá čára, krychle Bézierovy křivky, kvadratická Bézierová křivka, plynulá křivka Bézierovy krychle, plynulá kvadratická křivka a eliptický oblouk  
  
 Jednotlivé příkazy zadáte pomocí velkých nebo malých písmen: velká písmena označují absolutní hodnoty a malá písmena: relativní hodnoty: řídicí body pro tento segment jsou relativní vzhledem k koncovému bodu v předchozím příkladu. Při sekvenčním zadávání více než jednoho příkazu stejného typu můžete položku duplikovat příkaz vynechat; například `L 100,200 300,400` je ekvivalentem k `L 100,200 L 300,400` . Následující tabulka popisuje příkazy **Move** a **Draw** .  
  
### <a name="line-command"></a>Příkaz line  
 Vytvoří rovnou čáru mezi aktuálním bodem a zadaným koncovým bodem. `l 20 30`a `L 20,30` jsou příklady platných příkazů **řádků** .  
  
|Syntax|  
|------------|  
|`L`*koncový bod*<br /><br /> - nebo -<br /><br /> `l`*koncový bod*|  
  
|Pojem|Popis|  
|----------|-----------------|  
|*Služba*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Koncový bod řádku|  

Velká písmena `L` označují, že `endPoint` se jedná o absolutní hodnotu; malé písmeno `l` označuje, že `endPoint` se jedná o posun k předchozímu bodu, nebo (0, 0), pokud žádný neexistuje.

### <a name="horizontal-line-command"></a>Příkaz Vodorovná čára  
 Vytvoří vodorovnou čáru mezi aktuálním bodem a zadanou souřadnicí x. `H 90`je příkladem platného příkazu vodorovné čáry.

|Syntax|  
|------------|  
|`H`  *znak*<br /><br /> - nebo -<br /><br /> `h`  *znak*|  
  
|Pojem|Popis|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice x koncového bodu řádku|  
  
Velká písmena `H` označují, že `x` se jedná o absolutní hodnotu; malé písmeno `h` označuje, že `x` se jedná o posun k předchozímu bodu, nebo (0, 0), pokud žádný neexistuje.
  
### <a name="vertical-line-command"></a>Příkaz svislá čára  
 Vytvoří svislou čáru mezi aktuálním bodem a zadanou souřadnicí y. `v 90`je příkladem platného příkazu svislé čáry.

|Syntax|  
|------------|  
|`V`  *požadované*<br /><br /> - nebo -<br /><br /> `v`  *požadované*|  
  
|Pojem|Popis|  
|----------|-----------------|  
|*požadované*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice y koncového bodu řádku|  

Velká písmena `V` označují, že `y` se jedná o absolutní hodnotu; malé písmeno `v` označuje, že `y` se jedná o posun k předchozímu bodu, nebo (0, 0), pokud žádný neexistuje.  

### <a name="cubic-bezier-curve-command"></a>Krychle Bézierovy křivky – příkaz  
 Vytvoří Bézierovu křivku krychle mezi aktuálním bodem a zadaným koncovým bodem pomocí dvou určených řídicích bodů ( `controlPoint` 1 a `controlPoint` 2). `C 100,200 200,400 300,200`je příkladem platného příkazu křivky.  
  
|Syntax|  
|------------|  
|`C``controlPoint`1 `controlPoint` 2`endPoint`<br /><br /> - nebo -<br /><br /> `c``controlPoint`1 `controlPoint` 2`endPoint`|  
  
|Pojem|Popis|  
|----------|-----------------|  
|`controlPoint`první|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> První řídicí bod křivky, který určuje počáteční tangens křivky.|  
|`controlPoint`odst|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Druhý řídicí bod křivky, který určuje koncovou tečnu křivky.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod, do kterého se má křivka vykreslovat|  
  
### <a name="quadratic-bezier-curve-command"></a>Příkaz kvadratické Bézierovy křivky  
 Vytvoří kvadratickou Bézierovu křivku mezi aktuálním bodem a zadaným koncovým bodem pomocí zadaného řídicího bodu ( `controlPoint` ). `q 100,200 300,200`je příkladem platného příkazu kvadratické Bézierovy křivky.  
  
|Syntax|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> - nebo -<br /><br /> `q` `controlPoint` `endPoint`|  
  
|Pojem|Popis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Řídicí bod křivky, který určuje počáteční a koncové tečny křivky.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod, do kterého se má křivka vykreslovat|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>Příkaz plynulé Bézierovy křivky krychle  
 Vytvoří Bézierovu křivku krychle mezi aktuálním bodem a zadaným koncovým bodem. První řídicí bod se předpokládá jako odraz druhého řídicího bodu předchozího příkazu vzhledem k aktuálnímu bodu. Pokud není k dispozici žádný předchozí příkaz, nebo pokud předchozí příkaz nebyl příkazem Bézierovy křivky krychle nebo hladkým příkazem Bézierovy křivky, Předpokládejme, že první řídicí bod je koincident s aktuálním bodem. Druhý řídicí bod, řídicí bod pro konec křivky, je určen `controlPoint` 2. Například `S 100,200 200,300` je platný příkaz plynule Bézierovy křivky krychle.  
  
|Syntax|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> - nebo -<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|Pojem|Popis|  
|----------|-----------------|  
|`controlPoint`odst|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Řídicí bod křivky, který určuje koncovou tečnu křivky.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod, do kterého se má křivka vykreslovat|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>Příkaz plynule kvadratické Bézierovy křivky  
 Vytvoří kvadratickou Bézierovu křivku mezi aktuálním bodem a zadaným koncovým bodem. V ovládacím bodu se předpokládá, že se jedná o odraz řídicího bodu předchozího příkazu vzhledem k aktuálnímu bodu. Pokud není k dispozici žádný předchozí příkaz nebo pokud předchozí příkaz nebyl kvadratický příkaz Bézierovy křivky nebo je-li k dispozici příkaz plynule kvadratické Bézierovy křivky, je řídicí bod koincident s aktuálním bodem.  
  
|Syntax|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> - nebo -<br /><br /> `t` `controlPoint` `endPoint`|  
  
|Pojem|Popis|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Řídicí bod křivky, který určuje počáteční a tečnu křivky.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod, do kterého se má křivka vykreslovat|  
  
### <a name="elliptical-arc-command"></a>Eliptický oblouk – příkaz  
 Vytvoří eliptický oblouk mezi aktuálním bodem a zadaným koncovým bodem.  
  
|Syntax|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> - nebo -<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|Pojem|Popis|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> X-a y-poloměr oblouku.|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Rotace elipsy ve stupních.|  
|`isLargeArcFlag`|Nastavte na hodnotu 1, pokud má úhel oblouku 180 stupňů nebo větší. v opačném případě nastavte na 0.|  
|`sweepDirectionFlag`|Nastavte na hodnotu 1, je-li oblouk vykreslen v úhlu kladného úhlu; v opačném případě nastavte na 0.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Bod, na který je vykreslován oblouk.|  
  
<a name="closecommand"></a>
## <a name="the-close-command"></a>Příkaz Zavřít  
 Ukončí aktuální obrázek a vytvoří čáru, která připojí aktuální bod k počátečnímu bodu obrázku. Tento příkaz vytvoří spojnici (roh) mezi posledním segmentem a prvním segmentem obrázku.  
  
|Syntax|  
|------------|  
|`Z`<br /><br /> - nebo -<br /><br /> `z`|  

<a name="pointsyntax"></a>
## <a name="point-syntax"></a>Syntaxe bodu  
 Popisuje souřadnice x a y bodu, kde (0, 0) je levý horní roh.
  
|Syntax|  
|------------|  
|`x` `,` `y`<br /><br /> - nebo -<br /><br /> `x` `y`|  
  
|Pojem|Popis|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice x bodu|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Souřadnice y bodu|  
  
<a name="specialvalues"></a>
## <a name="special-values"></a>Speciální hodnoty  
 Místo standardní číselné hodnoty můžete také použít následující speciální hodnoty. U těchto hodnot se rozlišují malá a velká písmena.  
  
 Nekonečno  
 Představuje <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> .  
  
 – Nekonečno  
 Představuje <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> .  
  
 Není číslo  
 Představuje <xref:System.Double.NaN?displayProperty=nameWithType> .  
  
 Můžete použít také vědecký zápis. Například `+1.e17` je platná hodnota.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.PathFigureCollection>
- [Tvary a základní kresby v přehledu WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Přehled geometrie](geometry-overview.md)
- [– postupy](geometries-how-to-topics.md)
