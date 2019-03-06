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
ms.openlocfilehash: 24ffffc959891b6dab45350c6cda02adcc4f619a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362887"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>Úvod do objektu GlyphRun a elementu Glyph
Toto téma popisuje <xref:System.Windows.Media.GlyphRun> objektu a <xref:System.Windows.Documents.Glyphs> elementu.  
  
  
<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>Úvod do GlyphRun  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] podporuje rozšířené textové včetně úrovni piktogramu značky s přímým přístupem k <xref:System.Windows.Documents.Glyphs> pro zákazníky, kteří chtějí zachytit a zachovat po formátování textu. Tyto funkce umožňují podpory se zásadním jiným textovým požadavky na vykreslování v každém z těchto scénářů.  
  
1.  Zobrazování dokumentů pevného formátu.  
  
2.  Tisk scénáře.  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jako jazyk tiskárny zařízení.  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   Předchozí ovladače tiskárny, výstup z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikací na pevném formátu.  
  
    -   Formát zařazování tisku.  
  
3.  Reprezentace pevného formátu dokumentu, včetně klientů k předchozím verzím sady [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a další výpočetní zařízení.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs> a <xref:System.Windows.Media.GlyphRun> jsou navrženy pro prezentaci pevného formátu dokumentu a tisku scénáře. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje několik elementů pro obecné rozložení a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénáře, jako <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.TextBlock>. Další informace o rozložení a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénáře, naleznete v tématu [Typografie v rozhraní WPF](typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>Objektu GlyphRun  
 <xref:System.Windows.Media.GlyphRun> Objekt představuje posloupnost glyfy z jednoho rozpoznávání tváře jediného písma v jedné velikosti a stylem jeden vykreslování.  
  
 <xref:System.Windows.Media.GlyphRun> obsahuje podrobnosti o obou písmo jako je například piktogram <xref:System.Windows.Documents.Glyphs.Indices%2A> a umístění jednotlivých glyfů. Obsahuje také původní [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kódu bodů spuštění bylo vygenerováno, informace o posunu mapování znaků piktogram vyrovnávací paměti a příznaky za znak a za glyfů.  
  
 <xref:System.Windows.Media.GlyphRun> má odpovídající vysoké úrovně <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>. <xref:System.Windows.Documents.Glyphs> je možné na strom prvku a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky, které představují <xref:System.Windows.Media.GlyphRun> výstup.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Glyph – Element  
 <xref:System.Windows.Documents.Glyphs> Element představuje výstup <xref:System.Windows.Media.GlyphRun> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Následující syntaxe značek se používá k popisu <xref:System.Windows.Documents.Glyphs> elementu.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Následující definice vlastnosti odpovídají první čtyři atributy ve značce vzorku.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Určuje identifikátor prostředku: název souboru, webové [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], nebo odkaz na prostředek aplikace .exe nebo kontejneru.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Určuje velikost písma v kreslení surface jednotek (výchozí hodnota je.96 palců).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Určuje příznaky pro tučný i kurzívu styly.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Určuje úroveň obousměrného rozložení. Sudým číslem a nulové hodnoty znamenají rozložení zleva doprava; lichých hodnoty znamenají rozložení zprava doleva.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Vlastnost indexů  
 <xref:System.Windows.Documents.Glyphs.Indices%2A> Vlastnost představuje řetězec piktogram specifikací. Pokud pořadí glyfů tvoří jeden cluster, předchází specifikace prvním glyfem clusteru specifikace kolik glyfů a kolik bodů kódu kombinovat a vytvoří cluster. <xref:System.Windows.Documents.Glyphs.Indices%2A> Vlastnost shromažďuje v jednom řetězci následující vlastnosti.  
  
-   Glyphs indexy  
  
-   Piktogram zálohy šířky  
  
-   Kombinování piktogram přílohy vektorů  
  
-   Cluster mapování z bodů kódu na piktogramy  
  
-   Piktogram příznaky  
  
 Každá specifikace piktogram má následující formát.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Piktogram metriky  
 Každý piktogram definuje metriky, určit zarovnání s jinými <xref:System.Windows.Documents.Glyphs>. Na následujícím obrázku definuje různé typografickém kvality dva znaky jiné glyfů.  
  
 ![Diagram měření piktogramu](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Glyfy značek  
 Následující příklad kódu ukazuje, jak používat různé vlastnosti objektu <xref:System.Windows.Documents.Glyphs> prvek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Viz také:
- [Typografie v rozhraní WPF](typography-in-wpf.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Text](optimizing-performance-text.md)
