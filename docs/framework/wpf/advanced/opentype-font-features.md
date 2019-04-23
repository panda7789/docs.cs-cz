---
title: Funkce písma OpenType
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], OpenType
- typography [WPF], OpenType font technology
- OpenType font technology [WPF]
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
ms.openlocfilehash: 86921b610b4b42cfc0393af2966b70870bc650f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104478"
---
# <a name="opentype-font-features"></a>Funkce písma OpenType

Toto téma obsahuje základní informace o některé klíčové funkce [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] technologie písem v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>OpenType Font Format  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Formát písma je rozšířením [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] formát písma, přidání podpory pro technologii PostScript data písma. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Formát písma byla vyvinuta společně za [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] a Adobe Corporation. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma a operačního systému služby které podporují [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma poskytují uživatelům jednoduchý způsob instalace a používání písem, jestli obsahují písma [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] jsou podrobněji popsány dále nebo vývojového diagramu křížového procesu (PostScript) jsou podrobněji popsány dále.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Formát písma řeší následující problémy pro vývojáře:  
  
-   Širší podporu pro víc platforem.  
  
-   Lepší podpora mezinárodních znakových sad.  
  
-   Lepší ochrana pro data písma.  
  
-   Menší velikosti souborů zefektivnit distribuci písma.  
  
-   Širší podporu pro pokročilé typografické kontrolu.  
  
> [!NOTE]
>  Sada Windows SDK obsahuje sadu ukázkových [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písem, které můžete použít s [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací. Těchto písmo poskytuje většinu funkcí znázorněn ve zbývající části tohoto tématu. Další informace najdete v tématu [Ukázková sada písem OpenType](sample-opentype-font-pack.md).  
  
 Najdete v článku [OpenType specifikace](https://go.microsoft.com/fwlink/?LinkId=96731) podrobnosti o [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] formát písma.  
  
### <a name="advanced-typographic-extensions"></a>Pokročilé typografickém rozšíření  
 Pokročilé typografickém tabulky ([!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] rozložení tabulky) rozšiřují funkce nástroje písma s oběma [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] nebo vývojového diagramu křížového procesu jsou podrobněji popsány dále. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Rozložení písma obsahují další informace, které rozšiřuje možnosti písma pro podporu mezinárodní Typografie vysoké kvalitě. Většina [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma vystavit pouze podmnožinu celkové [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkce, které jsou k dispozici. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma poskytují následující funkce.  
  
-   Bohaté mapování mezi znaky a glyfy, které podporují ligatur, poziční formulářů, alternativní úložiště a dalších náhrady písma.  
  
-   Podpora dvojrozměrné umístění a piktogram přílohy.  
  
-   Explicitní skriptu a jazyk informace obsažené v písma, tak text zpracování aplikace můžete upravit jeho chování odpovídajícím způsobem.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Rozložení tabulky jsou popsány podrobněji ["Písmo soubor tabulky"](https://www.microsoft.com/typography/otspec/otff.htm) část [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] specifikace.  
  
 Zbývající část tohoto přehledu představuje šířku a flexibilitu některých vizuálně vytváří [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkce, které jsou vystavené vlastnosti <xref:System.Windows.Documents.Typography> objektu. Další informace v tomto objektu najdete v tématu [Typografie třídy](#typography_class).  
  
<a name="variants"></a>   
## <a name="variants"></a>Varianty  
 Varianty slouží pro vykreslení různé styly typografickém, jako je například horní a dolní indexy.  
  
### <a name="superscripts-and-subscripts"></a>Horní a dolní indexy  
 <xref:System.Windows.Documents.Typography.Variants%2A> Vlastnost umožňuje nastavit hodnoty horního a dolního indexu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma.  
  
 Následující text zobrazuje horních Palatino Linotype písma.  
  
 ![Textu s použitím OpenType horních](./media/opentype-font-features/opentype-superscripts.gif "textu s použitím horních OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat horních Palatino Linotype písma, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Zobrazí se následující text dolních indexů pro písmo Palatino Linotype.  
  
 ![Textu s použitím dolní indexy OpenType](./media/opentype-font-features/opentype-subscripts.gif "textu s použitím dolní indexy OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat dolních indexů pro písmo Palatino Linotype pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Dekorativní použití horní a dolní indexy  
 Také vám pomůže horní a dolní indexy vytvořit dekorativní efekty smíšených textových případu. Následující text zobrazí text horního a dolního indexu Palatino Linotype písma. Všimněte si, že to nebude mít vliv velká písmena.  
  
 ![Textu s použitím OpenType horní a dolní indexy](./media/opentype-font-features/opentype-superscripts-subscripts.gif "textu s použitím OpenType horní a dolní indexy")  

 Následující příklad kódu ukazuje, jak definovat horní a dolní indexy pro písmo, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>Velká písmena  
 Kapitálek představují sadu zkrácené typografické formuláře, které vykreslení textu ve stylu velké glyphs. Obvykle, když text je vykreslen jako všechna velká písmena, mezery mezi písmeny může objevit příliš vysoké a váhy a podíl příliš velkým písmenům. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] podporuje řadu formátů pro používání stylů pro písmeny, včetně kapitálek petitových kapitálek, titulkové a mezery. Tyto formáty stylů umožňují řídit vzhled kapitálek.  
  
 Zobrazí se následující text standardní písmeny Pescadero písma, za nímž následuje písmena tvaru "SmallCaps" a "AllSmallCaps". V takovém případě se používá stejnou velikost písma pro všechny tři slova.  
  
 ![Textu s použitím OpenType kapitálek](./media/opentype-font-features/opentype-capitals.gif "textu s použitím kapitálek OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat kapitálek pro Pescadero písmo, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu. Při použití formátu "SmallCaps" se ignoruje všechny úvodní velké písmeno.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Titulkových kapitálek  
 Titulkové kapitálek jsou světlejší v hmotnosti a poměr a navržená tak, aby více elegantní vzhled než normálním písmem. Titulkové písmeny se obvykle používají ve větší velikosti písma jako záhlaví. Zobrazí se následující text normální a titulkové kapitálek pro písmo Pescadero. Všimněte si, že užší stem šířku textu na druhém řádku.  
  
 ![Textu s použitím OpenType titulkových kapitálek](./media/opentype-font-features/opentype-titling-capitals.gif "textu s použitím titulkových kapitálek OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat titulkové kapitálek pro Pescadero písmo, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Mezery  
 Mezery je funkce, která umožňuje poskytnout více mezer při použití všechna velká písmena v textu. Velká písmena jsou obvykle navrženy s malými písmeny a přizpůsobte. Mezery, který se zobrazí mezi atraktivní a písmeno velké a malé písmeno může vypadat moc vysoké zadáním velkými písmeny. Následující text zobrazí normální a velké mezery Pescadero písma.  
  
 ![Textu s použitím kapitálkové mezery](./media/opentype-font-features/opentype-capital-spacing.gif "textu s použitím kapitálkové mezery ")  
 
 Následující příklad kódu ukazuje, jak definovat mezery pro Pescadero písmo, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>Ligatur  
 Ligatur jsou dvě nebo více glyfy, které jsou uspořádané do jednoho piktogram Chcete-li vytvořit z něj číst nebo atraktivní text. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] podporuje čtyři typy ligatur:  
  
-   **Standardní ligatury**. Účelem je zlepšit čitelnost. Standardní ligatury zahrnují "fi", "USA" a "ff".  
  
-   **Kontextové ligatur**. Účelem je zlepšit čitelnost tím, že poskytuje lepší spojování chování mezi znaky, které tvoří Zadaná vazba.  
  
-   **Volitelné ligatury**. Navržena jako dekorativní a ne specificky navržených pro lepší čitelnost.  
  
-   **Historických ligatur**. Navržena jako historická data a ne specificky navržených pro lepší čitelnost.  
  
 Následující text zobrazí standardní ligatury glyfy Pericles písma.  
  
 ![Textu s použitím standardní ligatury OpenType](./media/opentype-font-features/opentype-standard-ligatures.gif "textu s použitím standardní ligatury OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat standardní ligatury glyfy Pericles písma, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 Následující text zobrazí volitelný ligatura glyfy Pericles písma.  
  
 ![Textu s použitím volitelné ligatury OpenType](./media/opentype-font-features/opentype-discretionary-ligatures.gif "textu s použitím volitelné ligatury OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat volitelné ligatura glyfy Pericles písma, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Ve výchozím nastavení [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] povolit standardní ligatur. Například pokud používáte Palatino Linotype písma, standardní ligatury "fi", "ff" a "USA" zobrazí jako piktogram kombinovaných znaků. Všimněte si, že pár znaků pro každé standardní ligatury touch mezi sebou.  
  
 ![Text pomocí standardní ligatury OpenType Palatino Linotype](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "Text pomocí Palatino Linotype standardní ligatury OpenType")    
   
 Standardní ligatury funkce však můžete zakázat tak, aby standardní ligatury, jako je například "ff" zobrazí jako dva samostatné glyfy, nikoli jako piktogram kombinovaných znaků.  
  
 ![Textu s využitím zakázané OpenType standardní ligatury](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "textu s využitím zakázané standardní ligatury OpenType")  
    
 Následující příklad kódu ukazuje, jak zakázat standardní ligatury glyfy Palatino Linotype písma, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>Ozdobná písmena  
 Ozdobná písmena jsou dekorativní glyfy, které používají propracované dekoru často přidružený Kaligrafie. Následující text zobrazí standardní a swash glyfy Pescadero písma.  
  
 ![Textu použitím piktogramů standard a swash OpenType](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "textu použitím piktogramů standard a swash OpenType")  

 Ozdobná písmena jsou často používá jako dekorativní prvků v krátkých frází například oznámení události. Následující text používá ozdobná písmena zdůraznit písmeny názvu události.  
  
 ![Textu s použitím ozdobná OpenType písmena](./media/opentype-font-features/opentype-swashes.gif "textu s použitím ozdobná písmena OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat ozdobná písmena pro písmo, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Kontextové ozdobné znaky  
 Zkuste vzhled, jako je například překrývající se dolní dotahy na sousední písmena může způsobit určité kombinace protažených glyfů. Použití kontextových swash umožňuje použít náhradní swash glyf, který vytváří lepší vzhled. Následující text zobrazuje téhož slova před a po použití kontextových swash.  
  
 ![Textu s použitím kontextové ozdobné znaky OpenType](./media/opentype-font-features/opentype-contextual-swashes.gif "textu s použitím kontextové ozdobné znaky OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat kontextové swash Pescadero písma, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>Alternativní úložiště  
 Alternativy jsou glyfy, které mohou být nahrazeny pro standardní glyf. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma, jako je například Pericles písmo použité v následujících příkladech, může obsahovat alternativních glyfů, které můžete použít k vytvoření rozdílný vzhled dosažený textu. Následující text zobrazí standardní glyfy Pericles písma.  
  
 ![Textu použitím piktogramů standardní OpenType](./media/opentype-font-features/opentype-standard-glyphs.gif "textu použitím piktogramů standardní OpenType")  

 Pericles [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písmo obsahuje další glyfy, které poskytují stylových alternativ na standardní sadu glyphs. Zobrazí se následující text stylistické alternativních glyfů.  
  
 ![Textu s použitím stylových alternativních glyfů OpenType](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "textu s použitím stylových alternativních glyfů OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat stylistické alternativních glyfů v písmu Pericles pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Následující text zobrazí několik dalších stylistické alternativních glyfů pro Pericles písma.  
  
 ![Textu s použitím OpenType stylistické alternativních glyfů v písmu Pericles](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "textu s použitím stylových alternativních glyfů OpenType Pericles písma")

 Následující příklad kódu ukazuje, jak definovat tyto další stylistické alternativních glyfů.  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Náhodné kontextových alternativ.  
 Náhodné kontextových alternativ obsahují více náhradní glyfů pro jeden znak. Při implementaci s písmy typ skriptu, tuto funkci můžete simulovat rukopisu pomocí sady náhodně vybrané glyfů s mírné rozdíly v vzhled. Následující text pro písmo Lindsey používá náhodný kontextových alternativ. Všimněte si, že písmeno "a" se mírně liší v vzhled  
  
 ![Textu s použitím náhodného kontextových alternativ OpenType](./media/opentype-font-features/opentype-random-contextual-alternates.gif "textu s použitím náhodného kontextových alternativ OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat náhodné kontextových alternativ Lindsey písma, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Historických tvarů  
 Typografické konvence, které byly v minulosti běžné jsou historických formuláře. Frázi "Boston, Massachusetts", zobrazí se následující text pomocí historických formuláře glyfů pro Palatino Linotype písma.  
  
 ![Textu s použitím historických tvarů OpenType](./media/opentype-font-features/opentype-historical-forms.gif "textu s použitím historických tvarů OpenType")  
   
 Následující příklad kódu ukazuje, jak definovat historických tvarů Palatino Linotype písma, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>Číselné styly  
 Písem OpenType podporovat velký počet funkcí, které lze použít s číselných hodnot v textu.  
  
### <a name="fractions"></a>Podíly  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma podporu zlomky, včetně proškrtnutých a skládaný styly.  
  
 Následující text zobrazí styly zlomek Palatino Linotype písma.  
  
 ![Textu s použitím OpenType zkosené a standardní zlomky](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "textu s použitím OpenType zkosené a standardní podíly")  
   
 Následující příklad kódu ukazuje, jak definovat zlomek styly písma Palatino Linotype, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Starý styl číslice  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma podporují starý formát číslic style. Tento formát je užitečný při zobrazování číslice v stylů, které už nejsou standard. Číselné formáty standardní i starém stylu písma Palatino Linotype zobrazí datem 18 století následující text.  
  
 ![Textu s použitím OpenType zasahují](./media/opentype-font-features/opentype-old-style-numerals.gif "textu s použitím OpenType zasahují")  
    
 Zobrazí se následující text standardní číslice Palatino Linotype písmo, za nímž následuje zasahují.  
  
 ![Textu s použitím OpenType starý styl sady číslic](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "textu s použitím OpenType starý styl sady číslic")  
  
 Následující příklad kódu ukazuje, jak definovat zasahují Palatino Linotype písma, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Proporcionální a tabulkové obrázků  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma podporují obrázek proporcionální a tabulkové funkce řízení zarovnání šířky při použití číslic. Proporcionální obrázky považovat s jinou šířku každé číslo: "1" je menší než "5". Tabulkové obrázky jsou považovány za rovná width číslice tak, aby jejich zarovnání bylo svisle, které zvyšují čitelnost informace o finanční typu.  
  
 Následující text zobrazí dva proporcionální obrázky v prvním sloupci pomocí Miramonte písma. Všimněte si rozdílu číslice "5" a "1" na šířku. Druhý sloupec zobrazuje stejné dvou číselných hodnot pomocí šířky upravit tak, že použití funkce tabulkových obrázek.  
  
 ![Textu s použitím OpenType proporcionální & tabulkové obrázky](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "textu s použitím OpenType proporcionální a tabulkové obrázky")  
    
 Následující příklad kódu ukazuje, jak definovat proporcionální a tabulkové údaje o Miramonte písma, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Nula s lomítkem  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma podporují s lomítkem nula číslice formátu zdůraznit rozdíl mezi "O" písmena a číslice "0". Přeškrtnutý žádnou odečtete se často používá pro identifikátory v finančních a obchodních informací.  
  
 Následující text zobrazí identifikátor objednávky vzorku pomocí Miramonte písma. První řádek používá standardní číslice. Druhý řádek používá zkosené nula číslice zajistit lepší kontrastu s velkým písmenem "O".  
  
 ![Textu s použitím OpenType zkosené nula číslice](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "textu s použitím OpenType zkosené nula číslice")  
    
 Následující příklad kódu ukazuje, jak definovat zkosené nula číslice Miramonte písma, pomocí vlastnosti <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>Typografie třídy  
 <xref:System.Windows.Documents.Typography> Objekt poskytuje sadu funkcí, které [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písmo podporuje. Nastavením vlastnosti <xref:System.Windows.Documents.Typography> v kódu, můžete snadno vytvářet dokumenty, které budou využívat [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkce.  
  
 Zobrazí se následující text standardní písmeny Pescadero písma, za nímž následuje písmena tvaru "SmallCaps" a "AllSmallCaps". V takovém případě se používá stejnou velikost písma pro všechny tři slova.  
  
 ![Textu s použitím OpenType kapitálek](./media/opentype-font-features/opentype-capitals.gif "textu s použitím kapitálek OpenType")  
    
 Následující příklad kódu ukazuje, jak definovat kapitálek pro Pescadero písmo, použití vlastnosti <xref:System.Windows.Documents.Typography> objektu. Při použití formátu "SmallCaps" se ignoruje všechny úvodní velké písmeno.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 Následující příklad kódu provede stejné úkoly, jako předchozí příklad kódu.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Typografické vlastnosti třídy  
 V následující tabulce jsou uvedeny vlastnosti, hodnoty a výchozí nastavení pro položky <xref:System.Windows.Documents.Typography> objektu.  
  
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
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|Číselná hodnota – bajty|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|Číselná hodnota – bajty|0|  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Documents.Typography>
- [Specifikace OpenType](https://go.microsoft.com/fwlink/?LinkId=96731)
- [Typografie v rozhraní WPF](typography-in-wpf.md)
- [Ukázková sada písem OpenType](sample-opentype-font-pack.md)
- [Balení písem s aplikacemi](packaging-fonts-with-applications.md)