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
ms.openlocfilehash: 52fe73bccd625c9508b398874fd6b075af2445e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186810"
---
# <a name="opentype-font-features"></a>Funkce písma OpenType

Toto téma obsahuje přehled některých klíčových funkcí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]technologie písma OpenType v aplikaci .  
  
<a name="overview"></a>
## <a name="opentype-font-format"></a>Formát písma OpenType  
 Formát písma OpenType je příponou formátu písma TrueType®, který přidává podporu pro postscriptová data písem. Formát písma OpenType byl vyvinut společně společnostmi Microsoft a Adobe Corporation. Písma OpenType a služby operačního systému, které podporují písma OpenType, poskytují uživatelům jednoduchý způsob instalace a používání písem bez ohledu na to, zda písma obsahují obrysy TrueType nebo Obrysy CFF (PostScript).  
  
 Formát písma OpenType řeší následující výzvy pro vývojáře:  
  
- Širší podpora více platforem.  
  
- Lepší podpora mezinárodních znakových sad.  
  
- Lepší ochrana dat písem.  
  
- Menší velikosti souborů, aby distribuce písem efektivnější.  
  
- Širší podpora pro pokročilé typografické ovládání.  
  
> [!NOTE]
> Sada Windows SDK obsahuje sadu ukázkových písem OpenType, které lze použít s [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacemi. Tato písma poskytují většinu funkcí ilustrovaných ve zbývající části tohoto tématu. Další informace naleznete [v tématu Ukázka sady OpenType Font Pack](sample-opentype-font-pack.md).  
  
Podrobnosti o formátu písma OpenType naleznete ve [specifikaci OpenType](https://docs.microsoft.com/typography/opentype/spec/).  
  
### <a name="advanced-typographic-extensions"></a>Pokročilá typografická rozšíření  
 Rozšířené typografické tabulky (tabulky rozložení OpenType) rozšiřují funkce písem pomocí obrysů TrueType nebo CFF. Písma rozložení OpenType obsahují další informace, které rozšiřují možnosti písem tak, aby podporovaly vysoce kvalitní mezinárodní typografii. Většina písem OpenType zveřejňuje pouze podmnožinu celkových dostupných funkcí OpenType. Písma OpenType poskytují následující funkce.  
  
- Rozšířené mapování mezi znaky a glyfy, které podporují ligatury, poziční formuláře, alternativy a další náhrady písem.  
  
- Podpora dvojrozměrného polohování a připojení glyfů.  
  
- Explicitní skript a informace o jazyce obsažené v písmu, takže aplikace pro zpracování textu můžete upravit své chování odpovídajícím způsobem.  
  
 Tabulky rozložení OpenType jsou podrobněji popsány v části ["Tabulky souborů písem"](https://www.microsoft.com/typography/otspec/otff.htm) ve specifikaci OpenType.  
  
 Zbývající část tohoto přehledu představuje šíři a flexibilitu některých vizuálně zajímavé funkce OpenType, <xref:System.Windows.Documents.Typography> které jsou vystaveny vlastnosti objektu. Další informace o tomto objektu naleznete [v tématu Typography Class](#typography_class).  
  
<a name="variants"></a>
## <a name="variants"></a>Varianty  
 Varianty se používají k vykreslení různých typografických stylů, jako jsou horní indexy a dolní indexy.  
  
### <a name="superscripts-and-subscripts"></a>Horní indexy a dolní indexy  
 Vlastnost <xref:System.Windows.Documents.Typography.Variants%2A> umožňuje nastavit hodnoty horního a dolního indexu pro písmo OpenType.  
  
 Následující text zobrazuje horní indexy písma Palatino Linotype.  
  
 ![Text pomocí horních indexů OpenType](./media/opentype-font-features/opentype-superscripts.gif "Text pomocí horních indexů OpenType")  
  
 Následující příklad značek ukazuje, jak definovat horní indexy pro písmo Palatino <xref:System.Windows.Documents.Typography> Linotype pomocí vlastností objektu.  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Následující text zobrazuje dolní indexy písma Palatino Linotype.  
  
 ![Text pomocí dolních indexů OpenType](./media/opentype-font-features/opentype-subscripts.gif "Text pomocí dolních indexů OpenType")  
  
 Následující příklad značek ukazuje, jak definovat dolní indexy písma Palatino Linotype pomocí vlastností objektu. <xref:System.Windows.Documents.Typography>  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Dekorativní použití horních indexů a dolních indexů  
 Pomocí horních a dolních indexů můžete také vytvořit dekorativní efekty smíšeného textu případu. Následující text zobrazuje text horního a dolního indexu písma Palatino Linotype. Všimněte si, že hlavní města nejsou ovlivněny.  
  
 ![Text pomocí horních a dolních indexů OpenType](./media/opentype-font-features/opentype-superscripts-subscripts.gif "Text pomocí horních a dolních indexů OpenType")  

 Následující příklad značek ukazuje, jak definovat horní a dolní indexy pro <xref:System.Windows.Documents.Typography> písmo pomocí vlastností objektu.  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>
## <a name="capitals"></a>Hlavních městech  
 Velká písmena jsou sada typografických formulářů, které vykreslují text v glyfech velkých stylu. Obvykle, když je text vykreslen jako všechna velká písmena, mezery mezi písmeny se mohou zdát příliš těsné a tloušťka a poměr písmen příliš těžké. OpenType podporuje řadu formátů stylů pro velká písmena, včetně malých velkých písmen, drobných velkých písmen, titrování a mezer velkých písmen. Tyto stylové formáty umožňují ovládat vzhled velkých písmen.  
  
 Následující text zobrazuje standardní velká písmena pro písmo Pescadero, následované písmeny stylizovanými jako "SmallCaps" a "AllSmallCaps". V tomto případě se pro všechna tři slova používá stejná velikost písma.  
  
 ![Text pomocí velkých písmen OpenType](./media/opentype-font-features/opentype-capitals.gif "Text pomocí velkých písmen OpenType")  
  
 Následující příklad značek ukazuje, jak definovat velká písmena pro písmo <xref:System.Windows.Documents.Typography> Pescadero pomocí vlastností objektu. Při použití formátu "SmallCaps" je ignorováno jakékoli hlavní velké písmeno.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Vítací hlavní města  
 Vířící kapitálky jsou lehčí v hmotnosti a poměru a jsou navrženy tak, aby poskytly elegantnější vzhled než normální velká písmena. Velká písmena pro přeslování se obvykle používají ve větších velikostech písma jako nadpisy. Následující text zobrazuje normální a titrující velká písmena pro písmo Pescadero. Všimněte si užší šířky stonku textu na druhém řádku.  
  
 ![Text pomocí velkých písmen s titlingem OpenType](./media/opentype-font-features/opentype-titling-capitals.gif "Text pomocí velkých písmen s titlingem OpenType")  
  
 Následující příklad značek ukazuje, jak definovat titling velká písmena pro písmo Pescadero pomocí vlastností objektu. <xref:System.Windows.Documents.Typography>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Velké mezery  
 Velké mezery je funkce, která umožňuje poskytnout větší mezery při použití všech velkých písmen v textu. Velká písmena jsou obvykle navržena tak, aby se prolnula s malá písmena. Mezery, které se jeví jako atraktivní mezi velkým písmenem a písmenem s malou písmeno, mohou při použití všech velkých písmen vypadat příliš těsně. Následující text zobrazuje normální a velké mezery pro písmo Pescadero.  
  
 ![Text pomocí velkých mezer OpenType](./media/opentype-font-features/opentype-capital-spacing.gif "Text pomocí velkých mezer OpenType")  

 Následující příklad značek ukazuje, jak definovat velké mezery pro písmo Pescadero pomocí vlastností objektu. <xref:System.Windows.Documents.Typography>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>
## <a name="ligatures"></a>Ligatury  
 Ligatury jsou dva nebo více glyfů, které jsou vytvořeny do jednoho glyfu, aby se vytvořil čitelnější nebo atraktivnější text. Písma OpenType podporují čtyři typy ligatur:  
  
- **Standardní ligatury**. Navrženo pro zvýšení čitelnosti. Standardní ligatury zahrnují "fi", "fl" a "ff".  
  
- **Kontextové ligatury**. Navrženo pro zlepšení čitelnosti tím, že poskytuje lepší spojení chování mezi znaky, které tvoří ligaturu.  
  
- **Diskreční ligatury**. Navržentak, aby byl okrasný a není speciálně navržen pro čitelnost.  
  
- **Historické ligatury**. Navržentak, aby byl historický a nebyl speciálně navržen pro čitelnost.  
  
 Následující text zobrazuje standardní glyfy ligatury pro písmo Pericles.  
  
 ![Text pomocí standardních ligatur OpenType](./media/opentype-font-features/opentype-standard-ligatures.gif "Text pomocí standardních ligatur OpenType")  
  
 Následující příklad značek ukazuje, jak definovat standardní glyfy ligatury pro <xref:System.Windows.Documents.Typography> písmo Pericles pomocí vlastností objektu.  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 Následující text zobrazuje volitelné glyfy ligatury pro písmo Pericles.  
  
 ![Text pomocí volitelných ligatur OpenType](./media/opentype-font-features/opentype-discretionary-ligatures.gif "Text pomocí volitelných ligatur OpenType")  
  
 Následující příklad značek ukazuje, jak definovat volitelné glyfy ligatury pro <xref:System.Windows.Documents.Typography> písmo Pericles pomocí vlastností objektu.  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Ve výchozím nastavení umožňují [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] písma OpenType standardní ligatury. Pokud například použijete písmo Palatino Linotype, standardní ligatury "fi", "ff" a "fl" se zobrazí jako glyf z kombinovaného znaku. Všimněte si, že dvojice znaků pro každou standardní ligaturu se vzájemně dotýká.  
  
 ![Text pomocí standardních ligatur OpenType s Palatino Linotypem](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "Text pomocí standardních ligatur OpenType s Palatino Linotypem")

 Můžete však zakázat standardní prvky ligatury tak, aby se standardní ligatura, například "ff", zobrazovala jako dva samostatné glyfy, nikoli jako kombinovaný znakový glyf.  
  
 ![Text pomocí zakázaných standardních ligatur OpenType](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "Text pomocí zakázaných standardních ligatur OpenType")  

 Následující příklad značek ukazuje, jak zakázat standardní glyfy ligatury pro <xref:System.Windows.Documents.Typography> písmo Palatino Linotype pomocí vlastností objektu.  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>
## <a name="swashes"></a>Swashes  
 Ozdobné výmysly jsou ozdobné glyfy, které používají propracované ornamenty často spojené s kaligrafií. Následující text zobrazuje standardní a vymývací glyfy pro písmo Pescadero.  
  
 ![Text pomocí standardu OpenType a glyfů s mycími barvami](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "Text pomocí standardu OpenType a glyfů s mycími barvami")  

 Ozdobná písmena se často používají jako dekorativní prvky v krátkých frázích, jako jsou oznámení událostí. Následující text používá swashes zdůraznit velká písmena názvu události.  
  
 ![Text using OpenType swashes](./media/opentype-font-features/opentype-swashes.gif "Text using OpenType swashes")  
  
 Následující příklad značek ukazuje, jak definovat velká amalá písmena <xref:System.Windows.Documents.Typography> pro písmo pomocí vlastností objektu.  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Kontextové swashes  
 Některé kombinace glyfů vlnitého měchu mohou způsobit neatraktivní vzhled, například překrývající se dotahy na sousedních písmenech. Použití kontextové topí umožňuje použít náhradní kývat glyf, který vytváří lepší vzhled. Následující text ukazuje stejné slovo před a po použití kontextové swash.  
  
 ![Text pomocí kontextových semincovních sematovětch OpenType](./media/opentype-font-features/opentype-contextual-swashes.gif "Text pomocí kontextových semincovních sematovětch OpenType")  
  
 Následující příklad značek ukazuje, jak definovat kontextové swash pro písmo Pescadero pomocí vlastností objektu. <xref:System.Windows.Documents.Typography>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>
## <a name="alternates"></a>Náhradníky  
 Alternativy jsou glyfy, které mohou být nahrazeny standardním glyfem. Písma OpenType, například písmo Pericles použité v následujících příkladech, mohou obsahovat alternativní glyfy, které můžete použít k vytvoření různých vzhledů pro text. Následující text zobrazuje standardní glyfy pro písmo Pericles.  
  
 ![Text pomocí standardních glyfů OpenType](./media/opentype-font-features/opentype-standard-glyphs.gif "Text pomocí standardních glyfů OpenType")  

 Písmo Pericles OpenType obsahuje další glyfy, které poskytují stylistické alternativy ke standardní sadě glyfů. Následující text zobrazuje stylistické alternativní glyfy.  
  
 ![Text pomocí alternativních glyfů stylistické opentype](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "Text pomocí alternativních glyfů stylistické opentype")  
  
 Následující příklad značek ukazuje, jak definovat stylistické alternativní glyfy pro <xref:System.Windows.Documents.Typography> písmo Pericles pomocí vlastností objektu.  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Následující text zobrazuje několik dalších stylistických alternativních glyfů pro písmo Pericles.  
  
 ![Text pomocí alternativních glyfů stylistické opentype pro písmo Pericles](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "Text pomocí alternativních glyfů stylistické opentype pro písmo Pericles")

 Následující příklad značek ukazuje, jak definovat tyto další stylistické alternativní glyfy.  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Náhodné kontextové alternativy  
 Náhodné kontextové alternativy poskytují více náhradních glyfů pro jeden znak. Při implementaci pomocí písem typu skriptu může tato funkce simulovat rukopis pomocí sady náhodně vybraných glyfů s mírnými rozdíly ve vzhledu. Následující text používá náhodné kontextové alternativy pro písmo Lindsey. Všimněte si, že písmeno "a" se mírně liší ve vzhledu  
  
 ![Text pomocí náhodných kontextových alternativ OpenType](./media/opentype-font-features/opentype-random-contextual-alternates.gif "Text pomocí náhodných kontextových alternativ OpenType")  
  
 Následující příklad značek ukazuje, jak definovat náhodné kontextové alternativy pro písmo Lindsey pomocí vlastností objektu. <xref:System.Windows.Documents.Typography>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Historické formy  
 Historické formy jsou typografické konvence, které byly běžné v minulosti. Následující text zobrazuje frázi "Boston, Massachusetts" pomocí historické formy glyfů pro písmo Palatino Linotype.  
  
 ![Text pomocí historických formulářů OpenType](./media/opentype-font-features/opentype-historical-forms.gif "Text pomocí historických formulářů OpenType")  

 Následující příklad značek ukazuje, jak definovat historické formuláře pro písmo Palatino <xref:System.Windows.Documents.Typography> Linotype pomocí vlastností objektu.  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>
## <a name="numerical-styles"></a>Numerické styly  
 Písma OpenType podporují velké množství funkcí, které lze použít s číselnými hodnotami v textu.  
  
### <a name="fractions"></a>Frakce  
 Písma OpenType podporují styly zlomků, včetně sekl a skládaný.  
  
 Následující text zobrazuje styly zlomků pro písmo Palatino Linotype.  
  
 ![Text pomocí OpenType osekané a skládaný zlomky](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "Text pomocí OpenType osekané a skládaný zlomky")  

 Následující příklad značek ukazuje, jak definovat styly zlomků pro písmo <xref:System.Windows.Documents.Typography> Palatino Linotype pomocí vlastností objektu.  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Číslice starého stylu  
 Písma OpenType podporují formát číslic starého stylu. Tento formát je užitečný pro zobrazení číslic ve stylech, které již nejsou standardní. Následující text zobrazuje datum 18th století ve standardních a starých formátech číslic stylu pro písmo Palatino Linotype.  
  
 ![Text pomocí číslic starého stylu OpenType](./media/opentype-font-features/opentype-old-style-numerals.gif "Text pomocí číslic starého stylu OpenType")  

 Následující text zobrazuje standardní číslice písma Palatino Linotype, následované číslicemi starého stylu.  
  
 ![Text pomocí sad starých stylů OpenType](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "Text pomocí sad starých stylů OpenType")  
  
 Následující příklad značek ukazuje, jak definovat číslice starého stylu pro písmo Palatino Linotype pomocí vlastností objektu. <xref:System.Windows.Documents.Typography>  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Proporcionální a tabulkové obrázky  
 Písma OpenType podporují proporcionální a tabulkový obrázek, který řídí zarovnání šířek při použití číslic. Proporcionální hodnoty považují každou číslici za číslici s jinou šířkou – "1" je užší než "5". Tabulkové hodnoty jsou považovány za číslice se stejnou šířkou, takže jsou zarovnány svisle, což zvyšuje čitelnost informací o finančním typu.  
  
 Následující text zobrazí dvě proporcionální číslice v prvním sloupci pomocí písma Miramonte. Všimněte si rozdílu v šířce mezi číslicemi "5" a "1". Druhý sloupec zobrazuje stejné dvě číselné hodnoty s šířkami upravenými pomocí funkce tabulkového obrázku.  
  
 ![Text pomocí proporcionálních & tabulkových obrázků OpenType](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "Text pomocí proporcionálních a tabulkových obrázků OpenType")  

 Následující příklad značek ukazuje, jak definovat proporcionální a tabulkové <xref:System.Windows.Documents.Typography> obrázky pro písmo Miramonte pomocí vlastností objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Rozseknutá nula  
 Písma OpenType podporují přeškrtnutý formát nulových číslic, který zdůrazňuje rozdíl mezi písmenem "O" a číslicí "0". Přeškrtnutá nulová číslice se často používá pro identifikátory ve finančních a obchodních informacích.  
  
 Následující text zobrazuje ukázkový identifikátor objednávky pomocí písma Miramonte. První řádek používá standardní číslice. Druhý řádek používá sekl nula číslic poskytnout lepší kontrast s velkými písmeny "O".  
  
 ![Text pomocí OpenType přeřízl nula číslic](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "Text pomocí OpenType přeřízl nula číslic")  

 Následující příklad značek ukazuje, jak definovat přeříznuté nulové číslice pro <xref:System.Windows.Documents.Typography> písmo Miramonte pomocí vlastností objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>
## <a name="typography-class"></a>Typografie třída  
 Objekt <xref:System.Windows.Documents.Typography> zpřístupňuje sadu funkcí, které podporuje písmo OpenType. Nastavením vlastností <xref:System.Windows.Documents.Typography> v značkách můžete snadno vytvářet dokumenty, které využívají funkce OpenType.  
  
 Následující text zobrazuje standardní velká písmena pro písmo Pescadero, následované písmeny stylizovanými jako "SmallCaps" a "AllSmallCaps". V tomto případě se pro všechna tři slova používá stejná velikost písma.  
  
 ![Text pomocí velkých písmen OpenType](./media/opentype-font-features/opentype-capitals.gif "Text pomocí velkých písmen OpenType")  

 Následující příklad značek ukazuje, jak definovat velká písmena pro písmo <xref:System.Windows.Documents.Typography> Pescadero pomocí vlastností objektu. Při použití formátu "SmallCaps" je ignorováno jakékoli hlavní velké písmeno.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 Následující příklad kódu provádí stejný úkol jako předchozí příklad značky.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Vlastnosti třídy typografie  
 V následující tabulce jsou uvedeny vlastnosti, <xref:System.Windows.Documents.Typography> hodnoty a výchozí nastavení objektu.  
  
|Vlastnost|Hodnoty|Výchozí hodnota|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|Číselná hodnota - bajt|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps>&#124; <xref:System.Windows.FontCapitals.AllSmallCaps> <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; &#124; &#124; &#124; &#124; &#124; &#124;<xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|Číselná hodnota - bajt|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji>&#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; &#124; &#124; &#124; &#124; &#124; &#124; &#124; &#124; &#124;.<xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full>&#124; <xref:System.Windows.FontEastAsianWidths.Half> <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; &#124; &#124; &#124; &#124;<xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction.Normal>&#124; <xref:System.Windows.FontFraction.Slashed> &#124;<xref:System.Windows.FontFraction.Stacked>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment.Normal>&#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124;<xref:System.Windows.FontNumeralAlignment.Tabular>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|číselná hodnota – bajt|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|číselná hodnota – bajt|0|  
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
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior>&#124; <xref:System.Windows.FontVariants.Normal> <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> <xref:System.Windows.FontVariants.Subscript> &#124; &#124; &#124; &#124; &#124;<xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Documents.Typography>
- [Specifikace OpenType](https://docs.microsoft.com/typography/opentype/spec/)
- [Typografie v rozhraní WPF](typography-in-wpf.md)
- [Ukázková sada písem OpenType](sample-opentype-font-pack.md)
- [Balení písem s aplikacemi](packaging-fonts-with-applications.md)
