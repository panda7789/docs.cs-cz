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
ms.openlocfilehash: 9e40a9656bd1d89203b167860ef6951d5e30377c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918401"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>Úvod do objektu GlyphRun a elementu Glyph
Toto téma popisuje <xref:System.Windows.Media.GlyphRun> objekt <xref:System.Windows.Documents.Glyphs> a element.  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>Úvod do GlyphRun  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje rozšířenou podporu textu včetně značek na úrovni glyfů s přímým přístupem <xref:System.Windows.Documents.Glyphs> pro zákazníky, kteří chtějí zachytit a uchovat text po formátování. Tyto funkce poskytují kritickou podporu pro různé požadavky na vykreslování textu v každém z následujících scénářů.  
  
1. Zobrazení dokumentů s pevným formátem  
  
2. Scénáře tisku.  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]jako jazyk tiskárny zařízení.  
  
    - Zapisovač dokumentů Microsoft XPS.  
  
    - Předchozí ovladače tiskárny, výstup z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikací do pevného formátu.  
  
    - Formát zařazování tisku.  
  
3. Reprezentace dokumentu s pevným formátem, včetně klientů pro předchozí verze Windows a dalších výpočetních zařízení.  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>a <xref:System.Windows.Media.GlyphRun> jsou navržené pro scénáře s pevným formátem a prezentace a tisku. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje několik prvků pro obecné rozložení a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénáře <xref:System.Windows.Controls.Label> , jako například <xref:System.Windows.Controls.TextBlock>a. Další informace o rozložení a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénářích najdete v tématu [Typografie v](typography-in-wpf.md)subsystému WPF.  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>Objekt GlyphRun  
 <xref:System.Windows.Media.GlyphRun> Objekt představuje sekvenci glyfů z jedné plošky jednoho písma v jedné velikosti a s jedním vykreslovacím stylem.  
  
 <xref:System.Windows.Media.GlyphRun>zahrnuje podrobnosti o písmu, jako <xref:System.Windows.Documents.Glyphs.Indices%2A> jsou glyfy a jednotlivé pozice glyfů. Zahrnuje také původní [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] body kódu, ve kterých byl vygenerován běh, informace o mapování vyrovnávací paměti znaků na glyf a příznaky pro jednotlivé znaky a pro piktogramy.  
  
 <xref:System.Windows.Media.GlyphRun>má odpovídající nejvyšší úroveň <xref:System.Windows.FrameworkElement>. <xref:System.Windows.Documents.Glyphs> <xref:System.Windows.Documents.Glyphs>lze použít ve stromové struktuře elementu a v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] označení pro reprezentaci <xref:System.Windows.Media.GlyphRun> výstupu.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Piktograms – element  
 Element představuje výstup <xref:System.Windows.Media.GlyphRun> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. <xref:System.Windows.Documents.Glyphs> Následující syntaxe kódu se používá k popisu <xref:System.Windows.Documents.Glyphs> prvku.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Následující definice vlastností odpovídají prvních čtyř atributů v ukázkovém kódu.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Určuje identifikátor prostředku: název souboru, web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]nebo odkaz na prostředek v souboru Application. exe nebo Container.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Určuje velikost písma v jednotkách kresby (výchozí hodnota je. 96 palců).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Určuje příznaky pro styly tučného písma a kurzívy.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Určuje obousměrnou úroveň rozložení. Sudé a nulové hodnoty implikují rozložení zleva doprava; hodnoty s lichými čísly naznačují rozložení zprava doleva.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Vlastnost Indexes  
 <xref:System.Windows.Documents.Glyphs.Indices%2A> Vlastnost je řetězec specifikace glyfů. Pokud sekvence glyfů tvoří jeden cluster, předá specifikace prvního glyfu v clusteru specifikace toho, kolik glyfů a kolik bodů kódu se kombinuje s vytvořením clusteru. <xref:System.Windows.Documents.Glyphs.Indices%2A> Vlastnost shromažďuje v jednom řetězci následující vlastnosti.  
  
- Indexy glyfů  
  
- Šířka pro zálohy glyfů  
  
- Kombinování vektorů příloh glyfů  
  
- Mapování clusteru z bodů kódu na glyfy  
  
- Příznaky glyfů  
  
 Každá specifikace glyfu má následující formu.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Metriky glyfů  
 Každý glyf definuje metriky, které určují, jak se má zarovnat <xref:System.Windows.Documents.Glyphs>s jiným. Následující obrázek definuje různé typografické kvality dvou různých znaků glyfů.  
  
 ![Diagraph měření glyfů](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Piktogramy – značky  
 Následující příklad kódu ukazuje, jak použít různé vlastnosti <xref:System.Windows.Documents.Glyphs> prvku v. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Viz také:

- [Typografie v rozhraní WPF](typography-in-wpf.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Text](optimizing-performance-text.md)
