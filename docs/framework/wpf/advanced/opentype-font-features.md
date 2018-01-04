---
title: "Funkce písma OpenType"
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
- fonts [WPF], OpenType
- typography [WPF], OpenType font technology
- OpenType font technology [WPF]
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6344fed6cf480e3d3f91a559c99b79f438afa985
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="opentype-font-features"></a>Funkce písma OpenType
Toto téma obsahuje přehled některé klíčové funkce [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] technologie písma v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  

  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>Formát písem OpenType  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Písma formát je rozšířením [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] formátu písma, přidání podpory pro PostScript data písma. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Formát písma byla vyvinuta společně pomocí [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] a Adobe Corporation. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]písem a operační systém, které podpora služeb [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písem poskytují uživatelům jednoduchý způsob instalace a použití písem a zda písma obsahovat [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] jsou podrobněji popsány dále nebo jsou podrobněji popsány dále vývojového diagramu křížového procesu (PostScript).  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Formát písma řeší následující problémy developer:  
  
-   Širší podpora více platforem.  
  
-   Lepší podpora mezinárodních znaků.  
  
-   Lepší ochrana dat písma.  
  
-   Menší velikosti souborů, aby distribuční písma efektivnější.  
  
-   Širší podpora pro pokročilé typografických řízení.  
  
> [!NOTE]
>  Sada Windows SDK obsahuje sadu ukázka [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma, která můžete použít s [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace. Tyto písma poskytují většina funkcí zobrazené ve zbývající části tohoto tématu. Další informace najdete v tématu [ukázkové sadě písem OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
 Najdete v článku [OpenType specifikace](http://go.microsoft.com/fwlink/?LinkId=96731) podrobnosti [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] formát písma.  
  
### <a name="advanced-typographic-extensions"></a>Pokročilé typografických rozšíření  
 Rozšířené typografických tabulky ([!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] rozložení tabulky) rozšířit funkci písem pomocí [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] nebo jsou podrobněji popsány dále vývojového diagramu křížového procesu. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]Rozložení písem obsahovat další informace, které rozšiřuje možnosti písma pro podporu vysoce kvalitní mezinárodní typografie. Většina [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písem vystavit pouze podmnožinu celkového počtu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkce, které jsou k dispozici. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]písma poskytují následující funkce.  
  
-   Bohaté mapování mezi znaky a glyfy, které podporují ligatur, poziční formulářů, alternativ a jiné písmo nahrazení.  
  
-   Podpora pro dvourozměrná umístění a glyfy přílohy.  
  
-   Explicitní skriptu a jazyk informace obsažené v písma, takže text zpracování aplikace můžete změnit své chování odpovídajícím způsobem.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Rozložení tabulky jsou podrobně popsány v další ["Písma souboru tabulky"](http://www.microsoft.com/typography/otspec/otff.htm) části [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] specifikace.  
  
 Zbytek tohoto přehledu představuje spektra a flexibilitu některých vizuálně zajímavé [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkce, které jsou vystavené vlastnosti <xref:System.Windows.Documents.Typography> objektu. Další informace na tomto objektu najdete v tématu [typografii třída](#typography_class).  
  
<a name="variants"></a>   
## <a name="variants"></a>Varianty  
 Variant slouží k vykreslení různých typografické styly, jako je například horní a dolní indexy.  
  
### <a name="superscripts-and-subscripts"></a>Horní a dolní indexy  
 <xref:System.Windows.Documents.Typography.Variants%2A> Vlastnost můžete nastavit hodnoty horního a dolního indexu pro [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma.  
  
 Následující text zobrazuje horních Palatino Linotype písma.  
  
 ![Text s použitím OpenType horních](../../../../docs/framework/wpf/advanced/media/opentypefont14.gif "opentypefont14")  
Text s použitím OpenType horních  
  
 Následující příklad kódu ukazuje, jak definovat horních pro Palatino Linotype písmo, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Následující text zobrazí dolní indexy pro Palatino Linotype písmo.  
  
 ![Text s použitím dolní indexy OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont15.gif "opentypefont15")  
Text s použitím OpenType dolní indexy  
  
 Následující příklad kódu ukazuje, jak definovat dolní indexy pro Palatino Linotype písmo, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Dekorativní použití horní a dolní indexy  
 Můžete taky horní a dolní indexy vytvořit dekorativní důsledky smíšených textových případu. Následující text zobrazí text horního a dolního indexu pro Palatino Linotype písmo. Všimněte si, že kapitálek neovlivní.  
  
 ![Text s použitím OpenType horní a dolní indexy](../../../../docs/framework/wpf/advanced/media/opentypefont16.gif "opentypefont16")  
Text s použitím OpenType horní a dolní indexy  
  
 Následující příklad kódu ukazuje, jak definovat horní a dolní indexy pro písmo, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>Kapitálek  
 Kapitálek jsou sady typografických formuláře, které vykreslení textu v ve velkých glyfů. Obvykle, když text vykresleno jako všechny kapitálek, mezery mezi písmeny může vyskytovat příliš úzkou a váhu a podíl příliš velkou písmena. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]podporuje několik formáty stylů pro kapitálek, včetně kapitálek, petitových kapitálek, titulkových a mezery. Tyto formáty stylů umožňují řídit vzhled kapitálek.  
  
 Tento text se zobrazí standardní velkých písmen pro Pescadero písmo, za nímž následuje písmena ve tvaru "SmallCaps" a "AllSmallCaps". V takovém případě se používá stejnou velikost písma pro všechny tři nejčastější slova.  
  
 ![Text s použitím OpenType kapitálek](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")  
Text s použitím OpenType kapitálek  
  
 Následující příklad kódu ukazuje, jak definovat kapitálek pro Pescadero písmo, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu. Pokud se používá ve formátu "SmallCaps", se ignoruje všechny úvodní velké písmeno.  
  
 [!code-xaml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Titulkových kapitálek  
 Titulkové kapitálek jsou světlejší váhy a část, určené k více elegantní vzhled než normální kapitálek. Titulkové kapitálek jsou obvykle používány v větší velikosti písem jako záhlaví. Následující text zobrazí normální a titulkové kapitálek pro Pescadero písmo. Všimněte si užší šířek stem textu na druhém řádku.  
  
 ![Text s použitím OpenType titulkových kapitálek](../../../../docs/framework/wpf/advanced/media/opentypefont20.gif "OpenTypeFont20")  
Text s použitím OpenType titulkových kapitálek  
  
 Následující příklad kódu ukazuje, jak definovat titulkové kapitálek pro Pescadero písmo, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Kapitálové mezery  
 Kapitálové mezery je funkce, která umožňuje poskytovat další mezery při použití všechny kapitálek v textu. Velká písmena jsou obvykle navrženy a přizpůsobte s malými písmeny. Mezer, který se zobrazí mezi přitažlivé a velké písmeno, malé písmeno vypadat příliš úzkou v případě používají velkými písmeny. Následující text zobrazí normální a kapitálové mezery Pescadero písmo.  
  
 ![Text s použitím kapitálkové mezery](../../../../docs/framework/wpf/advanced/media/opentypefont21.gif "OpenTypeFont21")  
Text s použitím kapitálkové mezery  
  
 Následující příklad kódu ukazuje, jak definovat mezery pro Pescadero písmo, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>Ligatur  
 Ligatur jsou dvě nebo více glyfů, které jsou do jedné glyf vytvořen. Chcete-li vytvořit z něj číst nebo atraktivní text. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]podporuje čtyři typy ligatur:  
  
-   **Standardní ligatur**. Navržené pro zlepšení čitelnosti. Standardní ligatur zahrnují "fi", "fl" a "vypnuto".  
  
-   **Kontextová ligatur**. Navržené pro zlepšení čitelnosti tím, že poskytuje lepší spojování chování mezi znaky, které tvoří Zadaná vazba.  
  
-   **Volitelné ligatury**. Navržené jako dekorativní a není speciálně navrženého čitelnější.  
  
-   **Historických ligatur**. Navržený s ohledem na historické a není speciálně navrženého čitelnější.  
  
 Tento text se zobrazí standardní ligatury glyfů v písmu Pericles.  
  
 ![Text s použitím standardní ligatury OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont04.gif "opentypefont04")  
Text s použitím standardní ligatury OpenType  
  
 Následující příklad kódu ukazuje, jak definovat standardní ligatury glyfů v písmu Pericles pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 Následující text zobrazí volitelného ligatura glyfů v písmu Pericles.  
  
 ![Text s použitím volitelné ligatury OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont05.gif "opentypefont05")  
Text s použitím volitelné ligatury OpenType  
  
 Následující příklad kódu ukazuje, jak definovat volitelného ligatura glyfů v písmu Pericles pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Ve výchozím nastavení [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písem v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] povolit standardní ligatur. Například pokud použijete Palatino Linotype písmo, standardní ligatur "fi", "vypnuto" a "fl" zobrazí jako glyf kombinované znak. Všimněte si, že pár znaků pro každou standardní ligatury touch navzájem.  
  
 ![Text s použitím standardní ligatury OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont06.gif "opentypefont06")  
Text s použitím standardní ligatury OpenType  
  
 Funkce standardní ligatury však můžete zakázat tak, aby standardní ligatury, jako je například "vypnuto" zobrazí jako dva samostatné glyfů, nikoli jako glyf kombinované znak.  
  
 ![Text používající zakázané standardní ligatury OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont07.gif "opentypefont07")  
Text s použitím zakázané standardní ligatury OpenType  
  
 Následující příklad kódu ukazuje, jak zakázat standardní ligatury glyfů v písmu Palatino Linotype pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>Ozdobná písmena  
 Ozdobná písmena jsou dekorativní glyfů, které používají vypracovala dekoru často přidružené Kaligrafie. Následující text zobrazí standard a protažených glyfů v písmu Pescadero.  
  
 ![Text s použitím OpenType standard a protažených glyfů](../../../../docs/framework/wpf/advanced/media/opentypefont08.gif "opentypefont08")  
Text s použitím OpenType standard a protažených glyfů  
  
 Ozdobná písmena se často používají jako dekorativní prvky v krátké fráze například oznámení o události. Následující text používá ozdobná písmena zdůraznit velkých písmen názvu události.  
  
 ![Text s použitím ozdobná písmena OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont09.gif "opentypefont09")  
Text používající ozdobné OpenType znaky  
  
 Následující příklad kódu ukazuje, jak definovat ozdobná písmena pro písmo, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Kontextové ozdobné znaky  
 Zkuste vzhled, jako je například překrývající se dolní dotahy na sousedících písmena může způsobit určitých kombinací protažených glyfů. Použití kontextových protažených umožňuje používat substitute protažených glyf, který produkuje lepší vzhled. Následující text uvádí stejné slovo před a po použití kontextových protažených.  
  
 ![Text s použitím kontextové ozdobné znaky OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont19.gif "OpenTypeFont19")  
Text s použitím OpenType kontextové ozdobné znaky  
  
 Následující příklad kódu ukazuje, jak definovat kontextové protažených pro Pescadero písmo, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>Alternativ  
 Alternativy jsou glyfů, které pro standardní glyf se můžou nahradit. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]písma, jako je například Pericles písmo použité v následujících příkladech, může obsahovat alternativních glyfů, které můžete použít k vytvoření různých vzhled textu. Tento text se zobrazí standardní glyfů v písmu Pericles.  
  
 ![Text s použitím standardní glyfů OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont01.gif "opentypefont01")  
Text s použitím standardní glyfů OpenType  
  
 Pericles [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma obsahuje další glyfů, které poskytují stylových alternativ standardní sadu glyfů. Následující text zobrazí stylových alternativních glyfů.  
  
 ![Text s použitím stylových alternativních glyfů OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont02.gif "opentypefont02")  
Text s použitím stylových alternativních glyfů OpenType  
  
 Následující příklad kódu ukazuje, jak definovat stylových alternativních glyfů v písmu Pericles pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Tento text se zobrazí několik dalších stylových alternativních glyfů v písmu Pericles.  
  
 ![Text s použitím stylových alternativních glyfů OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont03.gif "opentypefont03")  
Text s použitím stylových alternativních glyfů OpenType  
  
 Následující příklad kódu ukazuje, jak definovat tyto další stylových alternativních glyfů.  
  
 [!code-xaml[OpenTypeFontSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Náhodné kontextových alternativ  
 Náhodné kontextových alternativ obsahují více substitute glyfů pro jeden znak. Když je implementovaná pomocí písem typ skriptu, tuto funkci můžete simulovat rukopisu pomocí sady náhodně vybrané glyfů s drobné rozdíly v vzhled. Následující text používá písmo Lindsey náhodných kontextových alternativ. Všimněte si, že písmenem "a" se mírně liší v vzhledu  
  
 ![Text s použitím náhodných kontextových alternativ OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont23.gif "OpenTypeFont23")  
Text s použitím OpenType náhodných kontextových alternativ.  
  
 Následující příklad kódu ukazuje, jak definovat náhodných kontextových alternativ pro Lindsey písmo, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Historických tvarů  
 Historických tvarů jsou typografických zásad, které byly v minulosti běžné. Následující text zobrazí fráze "Boston, Massachusetts", pomocí formuláře aplikace historických glyfů v písmu Palatino Linotype.  
  
 ![Text s použitím historických tvarů OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont10.gif "opentypefont10")  
Text s použitím OpenType historických tvarů  
  
 Následující příklad kódu ukazuje, jak definovat historických tvarů pro Palatino Linotype písmo, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>Číselné styly  
 Písem OpenType podporovat velký počet funkcí, které lze použít s číselných hodnot v textu.  
  
### <a name="fractions"></a>Zlomků  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]písem podpora styly zlomků, včetně proškrtnutých a skládaný.  
  
 Následující text zobrazí zlomek styly písma Palatino Linotype.  
  
 ![Text s použitím OpenType zkosené a standardní zlomky](../../../../docs/framework/wpf/advanced/media/opentypefont12.gif "opentypefont12")  
Text s použitím OpenType zkosené a standardní zlomky  
  
 Následující příklad kódu ukazuje, jak definovat zlomek styly písma Palatino Linotype, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Zasahují  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]písem podporují starý formát číslic stylu. Tento formát je vhodný pro zobrazení číslic v stylů, které již nejsou standardní. Následující text zobrazí datum 18 v standardní i starém stylu číslic formátech pro Palatino Linotype písmo.  
  
 ![Text s použitím OpenType zasahují](../../../../docs/framework/wpf/advanced/media/opentypefont24.gif "OpenTypeFont24")  
Text s použitím OpenType zasahují  
  
 Tento text se zobrazí standardní číslic pro Palatino Linotype písmo, za nímž následuje zasahují.  
  
 ![Text s použitím OpenType starého stylu sady číslic](../../../../docs/framework/wpf/advanced/media/opentypefont13.gif "opentypefont13")  
Text s použitím OpenType starého stylu sady číslic  
  
 Následující příklad kódu ukazuje, jak definovat zasahují pro Palatino Linotype písmo, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Proporční a tabulkové obrázků  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]písem podporují obrázek přímo úměrná a tabulkové funkce, která řídí zarovnání šířky při použití číslic. Přímo úměrná obrázky s každý číslic zacházeno jako s jinou šířku – "1" je užší než "5". Tabulkové údaje jsou považovány za rovná width číslic, aby ve svislém směru, což zvyšuje čitelnost informace o finanční typu.  
  
 Následující text zobrazí dva následující obrázky přímo úměrná prvního sloupce pomocí Miramonte písma. Poznámka: šířka rozdíl mezi číslic "5" a "1". Druhý sloupec zobrazuje dvou číselných hodnot s šířek upravit pomocí funkce tabulkové obrázek.  
  
 ![Text s použitím OpenType přímo úměrná & tabulkové obrázky](../../../../docs/framework/wpf/advanced/media/opentypefont22.gif "OpenTypeFont22")  
Text s použitím OpenType přímo úměrná a tabulkové obrázků  
  
 Následující příklad kódu ukazuje, jak definovat přímo úměrná a tabulkové obrázky pro Miramonte písmo, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Proškrtnutých nula.  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]Podpora písem proškrtnutých nulový počet číslic formátu zdůraznit rozdíl mezi písmenem "O" a "0" číslic. Proškrtnutých nulový počet číslic se často používá pro identifikátory v finanční a obchodních informací.  
  
 Následující text zobrazuje identifikátor ukázka pořadí pomocí Miramonte písma. První řádek používá standardní číslic. Druhý řádek používá zkosené nulový počet číslic zajistit lepší kontrast s velkým písmenem "O".  
  
 ![Text s použitím OpenType zkosené nulový počet číslic](../../../../docs/framework/wpf/advanced/media/opentypefont17.gif "OpenTypeFont17")  
Text s použitím OpenType zkosené nulový počet číslic  
  
 Následující příklad kódu ukazuje, jak definovat zkosené nulový počet číslic pro Miramonte písmo, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>Typografie – třída  
 <xref:System.Windows.Documents.Typography> Objekt poskytuje sada funkcí, které [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písmo podporuje. Nastavením vlastnosti <xref:System.Windows.Documents.Typography> v značek, můžete snadno vytvářet dokumenty, které využívají [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkce.  
  
 Tento text se zobrazí standardní velkých písmen pro Pescadero písmo, za nímž následuje písmena ve tvaru "SmallCaps" a "AllSmallCaps". V takovém případě se používá stejnou velikost písma pro všechny tři nejčastější slova.  
  
 ![Text s použitím OpenType kapitálek](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")  
Text s použitím OpenType kapitálek  
  
 Následující příklad kódu ukazuje, jak definovat kapitálek pro Pescadero písmo, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu. Pokud se používá ve formátu "SmallCaps", se ignoruje všechny úvodní velké písmeno.  
  
 [!code-xaml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 Následující příklad kódu provede úlohu stejný jako předchozí příklad značek.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Vlastnosti typografii – třída  
 Následující tabulka uvádí vlastnosti, hodnoty a výchozí nastavení <xref:System.Windows.Documents.Typography> objektu.  
  
|Vlastnost|Hodnoty|Výchozí hodnota|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|Číselná hodnota - bajtů|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|Číselná hodnota - bajtů|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> &#124; <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; <xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full> &#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; <xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|Číselná hodnota – bajtů|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|Číselná hodnota – bajtů|0|  
|<xref:System.Windows.Documents.Typography.StylisticSet1%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet2%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet3%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet4%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet5%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet6%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet7%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet8%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet9%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet10%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet11%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet12%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet13%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet14%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet15%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet16%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet17%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet18%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet19%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet20%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior> &#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; <xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Documents.Typography>  
 [Specifikace OpenType](http://go.microsoft.com/fwlink/?LinkId=96731)  
 [Typografie v rozhraní WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Ukázková sada písem OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)  
 [Balení písem s aplikacemi](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
