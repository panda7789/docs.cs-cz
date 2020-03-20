---
title: Úvod do objektu GlyphRun a elementu Glyph
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], Glyphs element
- Glyphs elements [WPF]
- GlyphRun object [WPF]
- text [WPF], glyphs
- glyphs [WPF]
- typography [WPF], GlyphRun object
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
ms.openlocfilehash: 32e8ab7104b8ea2f985395065868ed154ca1e378
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181954"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>Úvod do objektu GlyphRun a elementu Glyph
Toto téma <xref:System.Windows.Media.GlyphRun> popisuje objekt <xref:System.Windows.Documents.Glyphs> a prvek.  

<a name="text_glyphrunovw_intro"></a>
## <a name="introduction-to-glyphrun"></a>Úvod do Glydu  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Poskytuje pokročilou textovou podporu včetně značek na <xref:System.Windows.Documents.Glyphs> úrovni glyfů s přímým přístupem pro zákazníky, kteří chtějí zachytit a zachovat text po formátování. Tyto funkce poskytují kritickou podporu pro různé požadavky na vykreslování textu v každém z následujících scénářů.  
  
1. Zobrazení dokumentů v pevném formátu.  
  
2. Vytisknout scénáře.  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]jako jazyk tiskárny zařízení.  
  
    - Zapisovač dokumentů systému Microsoft XPS.  
  
    - Předchozí ovladače tiskárny, výstup z aplikací Win32 do pevného formátu.  
  
    - Formát zařazovací liby tisku.  
  
3. Reprezentace dokumentu s pevným formátem, včetně klientů pro předchozí verze systému Windows a dalších výpočetních zařízení.  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>a <xref:System.Windows.Media.GlyphRun> jsou určeny pro prezentační a tiskové scénáře s pevným formátem. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]obsahuje několik prvků pro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] obecné <xref:System.Windows.Controls.Label> rozložení <xref:System.Windows.Controls.TextBlock>a scénáře, jako je například a . Další informace o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] rozložení a scénářích naleznete [v tématu Typografie v WPF](typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>
## <a name="the-glyphrun-object"></a>Objekt Glyphrun  
 Objekt <xref:System.Windows.Media.GlyphRun> představuje posloupnost glyfů z jedné plochy jednoho písma v jedné velikosti a s jedním stylem vykreslování.  
  
 <xref:System.Windows.Media.GlyphRun>obsahuje jak podrobnosti <xref:System.Windows.Documents.Glyphs.Indices%2A> písma, jako je glyf, tak jednotlivé polohy glyfů. Obsahuje také původní body kódu Unicode, ze kterých bylo spuštění generováno, informace o odsazení vyrovnávací paměti znak-gly a příznaky pro znaky a glyfy.  
  
 <xref:System.Windows.Media.GlyphRun>má odpovídající vysokou <xref:System.Windows.FrameworkElement>úroveň <xref:System.Windows.Documents.Glyphs>. <xref:System.Windows.Documents.Glyphs>lze použít ve stromu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prvků a <xref:System.Windows.Media.GlyphRun> ve značkách k reprezentaci výstupu.  
  
<a name="text_glyphrunovw_glyphselement"></a>
## <a name="the-glyphs-element"></a>Element glyfů  
 Prvek <xref:System.Windows.Documents.Glyphs> představuje výstup in <xref:System.Windows.Media.GlyphRun> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Následující syntaxe značek se používá <xref:System.Windows.Documents.Glyphs> k popisu prvku.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Následující definice vlastností odpovídají prvním čtyřem atributům ve značce vzorku.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Určuje identifikátor prostředku: název souboru, identifikátor identifikátor identifikátoru URI (Web uniform) nebo odkaz na prostředek v aplikaci EXE nebo kontejneru.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Určuje velikost písma v jednotkách výkresového povrchu (výchozí hodnota je 0,96 palce).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Určuje příznaky pro tučné písmo a kurzívu.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Určuje obousměrnou úroveň rozložení. Sudé a nulové hodnoty implikují rozložení zleva doprava; liché hodnoty implikují rozložení zprava doleva.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>
### <a name="indices-property"></a>Vlastnost Indexy  
 Vlastnost <xref:System.Windows.Documents.Glyphs.Indices%2A> je řetězec specifikace glyfů. Pokud posloupnost glyfů tvoří jeden cluster, specifikaci prvního glyfu v clusteru předchází specifikace počtu glyfů a počtu bodů kódu, které se spojí a vytvoří cluster. Vlastnost <xref:System.Windows.Documents.Glyphs.Indices%2A> shromažďuje v jednom řetězci následující vlastnosti.  
  
- Indexy glyfů  
  
- Šířky glyfu  
  
- Kombinování vektorů příloh glyfu  
  
- Mapování clusteru z bodů kódu na glyfy  
  
- Příznaky glyfů  
  
 Každá specifikace glyfu má následující tvar.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>
## <a name="glyph-metrics"></a>Metriky glyfu  
 Každý glyf definuje metriky, které <xref:System.Windows.Documents.Glyphs>určují, jak bude zarovnán s ostatními . Následující obrázek definuje různé typografické kvality dvou různých znaků glyfu.  
  
 ![Diagraf měření glyfů](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>
## <a name="glyphs-markup"></a>Značky glyfů  
 Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Documents.Glyphs> různé [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]vlastnosti prvku v .  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Viz také

- [Typografie v rozhraní WPF](typography-in-wpf.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Text](optimizing-performance-text.md)
