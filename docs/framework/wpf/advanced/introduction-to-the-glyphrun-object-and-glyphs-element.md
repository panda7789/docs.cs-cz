---
title: "Úvod do objektu GlyphRun a elementu Glyph"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], Glyphs element
- Glyphs elements [WPF]
- GlyphRun object [WPF]
- text [WPF], glyphs
- glyphs [WPF]
- typography [WPF], GlyphRun object
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa868b520224b27b3cd2b3dc99431728ad8ea527
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>Úvod do objektu GlyphRun a elementu Glyph
Toto téma popisuje <xref:System.Windows.Media.GlyphRun> objektu a <xref:System.Windows.Documents.Glyphs> elementu.  
  
  
<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>Úvod do GlyphRun  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje podporu rozšířené textové včetně značek glyfy úrovni s přímým přístupem k <xref:System.Windows.Documents.Glyphs> pro zákazníky, kteří chtějí zachytávat a zachovat po formátování textu. Tyto funkce podporují kritické jiným textovým vykreslování požadavky v každé z následujících scénářů.  
  
1.  Zobrazování dokumentů pevného formátu.  
  
2.  Tisk scénáře.  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]jako jazyk tiskárny zařízení.  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   Předchozí ovladače tiskárny, výstup z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikace do pevné formátu.  
  
    -   Formát zařazování tisku.  
  
3.  Reprezentace-formátovat dokument, včetně klientů pro předchozí verze [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a dalších výpočetních zařízení.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs>a <xref:System.Windows.Media.GlyphRun> jsou navrženy pro tiskové scénáře a prezentace-formátovat dokument. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje několik elementy pro obecné rozložení a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénáře, jako <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.TextBlock>. Další informace o rozložení a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénáře, najdete v článku [typografii v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>Objekt GlyphRun  
 <xref:System.Windows.Media.GlyphRun> Objekt představuje pořadí glyfů z jednoho řez jediného písma v jednom velikosti a s styl vykreslování jedné.  
  
 <xref:System.Windows.Media.GlyphRun>zahrnuje obě podrobnosti písma, například glyfy <xref:System.Windows.Documents.Glyphs.Indices%2A> a umístění jednotlivých glyfů. Zahrnuje také původní [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] code body spustit byla vygenerována z informace o posunu mapování znak glyfy vyrovnávací paměti a příznaky za znak a za glyfů.  
  
 <xref:System.Windows.Media.GlyphRun>má odpovídající vysoké úrovně <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>. <xref:System.Windows.Documents.Glyphs>je možné ve stromové struktuře elementu a v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek k reprezentaci <xref:System.Windows.Media.GlyphRun> výstup.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Element glyfů  
 <xref:System.Windows.Documents.Glyphs> Element reprezentuje výstup <xref:System.Windows.Media.GlyphRun> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Následující syntaxe značek se používá k popisu <xref:System.Windows.Documents.Glyphs> elementu.  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Následující definice vlastností odpovídají první čtyři atributy v ukázkový kód.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Určuje identifikátor zdroje: název souboru, webové [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], nebo odkaz prostředků ve aplikace .exe nebo kontejneru.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Určuje velikost písma v kreslení prostor jednotky (výchozí hodnota je.96 palce).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Určuje příznaky pro tučné písmo a kurzíva stylů.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Určuje úroveň obousměrného rozložení. Číslované a nulové hodnoty implikují rozložení zleva doprava; hodnoty lichých implikují rozložení zprava doleva.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Vlastnost indexů  
 <xref:System.Windows.Documents.Glyphs.Indices%2A> Vlastnost je řetězec ve specifikacích glyfů. Kde pořadí glyfů forms jednoho clusteru, je specifikace prvním glyfem clusteru před specifikaci kolik glyfů a kolik bodů kódu kombinace a vytvoří cluster. <xref:System.Windows.Documents.Glyphs.Indices%2A> Vlastnost shromažďuje v jednom řetězci následující vlastnosti.  
  
-   Glyfy indexů  
  
-   Glyfy zálohy šířek  
  
-   Kombinování vektory glyfy přílohy  
  
-   Mapování clusteru z kódu ukazuje na glyfů  
  
-   Příznaky glyfy  
  
 Každý glyfy specifikace má následující formulář.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Glyfy metriky  
 Každý glyfy definuje metriky, které zadejte, jak zarovnaná s jinými <xref:System.Windows.Documents.Glyphs>. Na následujícím obrázku definuje různé typografických kvality dva různé glyfy znaky.  
  
 ![Diagram měření piktogramu](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Glyfů značek  
 Následující příklad kódu ukazuje, jak používat různé vlastnosti <xref:System.Windows.Documents.Glyphs> element v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Viz také  
 [Typografie v rozhraní WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
