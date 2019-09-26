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
ms.openlocfilehash: 3f1f0698afce6e64711e37ac60d0662d65bbee6b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "70016143"
---
# <a name="opentype-font-features"></a>Funkce písma OpenType

Toto téma obsahuje přehled některých klíčových funkcí technologie písma OpenType v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>Formát písma OpenType  
 Formát písma OpenType je rozšířením [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] formátu písma a přidává podporu pro PostScriptová data písma. Formát písma OpenType vyvinuly společnosti Microsoft a společnost Adobe Corporation společně. Písma OpenType a služby operačního systému, které podporují písma OpenType, poskytují uživatelům jednoduchý způsob, jak nainstalovat a používat písma, ať už písma obsahují [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] obrysy nebo CFF (PostScript).  
  
 Formát písma OpenType řeší následující výzvy pro vývojáře:  
  
- Širší podpora více platforem.  
  
- Lepší podpora pro mezinárodní znakové sady.  
  
- Lepší ochrana pro data písma.  
  
- Menší velikosti souborů, aby se distribuce písem zajistila efektivněji.  
  
- Širší podpora pro pokročilou typografickou kontrolu.  
  
> [!NOTE]
> Windows SDK obsahuje sadu ukázkových písem OpenType, která můžete použít s [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacemi. Tato písma poskytují většinu funkcí, které jsou znázorněné ve zbývající části tohoto tématu. Další informace najdete v tématu [Ukázková sada písem OpenType](sample-opentype-font-pack.md).  
  
 Podrobnosti o formátu písma OpenType najdete v tématu [specifikace OpenType](https://go.microsoft.com/fwlink/?LinkId=96731) .  
  
### <a name="advanced-typographic-extensions"></a>Pokročilá typografická rozšíření  
 Pokročilé typografické tabulky (tabulky rozložení OpenType) zvyšují funkčnost písem pomocí [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] CFF nebo osnovy. Písma rozložení OpenType obsahují další informace, které rozšiřují možnosti písem, aby podporovaly vysoce kvalitní mezinárodní typografie. Většina písem OpenType zveřejňuje pouze podmnožinu celkových dostupných funkcí OpenType. Písma OpenType poskytují následující funkce.  
  
- Obsáhlé mapování mezi znaky a glyfy, které podporují ligatury, poziční formuláře, alternativy a další náhrady písma.  
  
- Podpora dvojrozměrného umístění a přílohy glyfů.  
  
- Explicitní informace o skriptech a jazycích obsažené v písmu, takže aplikace pro zpracování textu může odpovídajícím způsobem upravit její chování.  
  
 Tabulky rozložení OpenType jsou podrobněji popsané v oddílu [tabulky souborů písem](https://www.microsoft.com/typography/otspec/otff.htm) specifikace OpenType.  
  
 Zbývající část tohoto přehledu zavádí širokou škálu a flexibilitu některých vizuálně zajímavých funkcí OpenType, které jsou vystaveny vlastnostmi <xref:System.Windows.Documents.Typography> objektu. Další informace o tomto objektu naleznete v tématu [Typografie třídy](#typography_class).  
  
<a name="variants"></a>   
## <a name="variants"></a>Varianty  
 Varianty se používají k vykreslení různých typografických stylů, jako jsou například horní indexy a dolní indexy.  
  
### <a name="superscripts-and-subscripts"></a>Horní indexy a dolní indexy  
 <xref:System.Windows.Documents.Typography.Variants%2A> Vlastnost umožňuje nastavit horní index a hodnoty dolního indexu pro písmo OpenType.  
  
 Následující text zobrazuje horní indexy pro písmo Palatino Linotype.  
  
 ![Text používající horní indexy OpenType](./media/opentype-font-features/opentype-superscripts.gif "Text používající horní indexy OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat horní indexy pro písmo Palatino Linotype s použitím vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Následující text zobrazuje dolní indexy pro písmo Palatino Linotype.  
  
 ![Text s použitím dolních indexů OpenType](./media/opentype-font-features/opentype-subscripts.gif "Text s použitím dolních indexů OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat dolní indexy pro písmo Palatino Linotype s použitím vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Ozdobné použití horních a dolních indexů  
 Pomocí horních a dolních indexů můžete také vytvořit ozdobné efekty smíšeného textu případu. Následující text zobrazuje horní a dolní indexový text pro písmo Palatino Linotype. Všimněte si, že velká písmena nejsou ovlivněna.  
  
 ![Text používající horní indexy a dolní indexy písma OpenType](./media/opentype-font-features/opentype-superscripts-subscripts.gif "Text používající horní indexy a dolní indexy písma OpenType")  

 Následující příklad kódu ukazuje, jak definovat horní indexy a dolní indexy pro písmo pomocí vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>Kapitálek  
 Velká písmena představují sadu typografických tvarů, které vykreslují text v glyfech ve stylu velkými písmeny. Když se text vykreslí jako velká písmena, mezery mezi písmeny se můžou zobrazovat příliš těsné a váha a podíl písmen je moc velký. OpenType podporuje mnoho formátů stylů pro velká písmena, včetně malých písmen, petitových velkých písmen, titulků a velkých mezer. Tyto formáty stylů umožňují ovládat vzhled velkých písmen.  
  
 Následující text zobrazuje standardní velká písmena pro písmo Pescadero a potom písmena se stylem "SmallCaps" a "AllSmallCaps". V takovém případě se pro všechna tři slova použije stejná velikost písma.  
  
 ![Text používající velká písmena písma OpenType](./media/opentype-font-features/opentype-capitals.gif "Text používající velká písmena písma OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat velká písmena pro písmo Pescadero pomocí vlastností <xref:System.Windows.Documents.Typography> objektu. Když se použije formát "SmallCaps", bude se ignorovat počáteční velké písmeno.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Titulková velká písmena  
 Titulková velká písmena jsou světlejší v poměru a rozsahu a jsou navržena tak, aby lépe vypadala jako běžná velká písmena. Titulková velká písmena se obvykle používají v širší velikosti písem jako záhlaví. Následující text zobrazuje normální a titulkové kapitálky pro písmo Pescadero. Všimněte si zúžené šířky textu na druhém řádku.  
  
 ![Text používající Titulková velká písmena písma OpenType](./media/opentype-font-features/opentype-titling-capitals.gif "Text používající Titulková velká písmena písma OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat Titulková velká písmena pro písmo Pescadero pomocí vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Velké mezery  
 Základní řádkování je funkce, která umožňuje zadat další mezery při použití všech velkých písmen v textu. Velká písmena jsou obvykle navržena pro míchání s malými písmeny. Mezery, které se zdají být atraktivní a velké písmeno a malé písmeno, může při použití všech velkých písmen zobrazit příliš těsné. Následující text zobrazuje normální a velké mezery pro písmo Pescadero.  
  
 ![Text s využitím velkých mezer písma OpenType](./media/opentype-font-features/opentype-capital-spacing.gif "Text s využitím velkých mezer písma OpenType")  
 
 Následující příklad kódu ukazuje, jak definovat velké mezery pro písmo Pescadero pomocí vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>Vybraný  
 Ligatury jsou dva nebo více glyfů, které jsou tvořeny jedním glyfem, aby bylo možné vytvořit čitelnější nebo atraktivní text. Písma OpenType podporují čtyři typy ligatur:  
  
- **Standardní ligatury**. Navrženo pro zlepšení čitelnosti. Standardní ligatury zahrnují "Fi", "FL" a "FF".  
  
- **Kontextové ligatury**. Navrženo pro zlepšení čitelnosti tím, že poskytuje lepší spojení mezi znaky, které tvoří ligaturu.  
  
- **Volitelné ligatury**. Navrženo tak, aby bylo ozdobné a neurčené pro čitelnost.  
  
- **Historické ligatury**. Navrženo tak, aby bylo historické a nebylo určeno konkrétně pro čitelnost.  
  
 Následující text zobrazuje standardní glyfy ligatur pro písmo Pericles.  
  
 ![Text používající standardní ligatury OpenType](./media/opentype-font-features/opentype-standard-ligatures.gif "Text používající standardní ligatury OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat standardní glyfy ligatur pro písmo Pericles pomocí vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 Následující text zobrazuje volitelné glyfy ligatur pro písmo Pericles.  
  
 ![Text používající volitelné ligatury OpenType](./media/opentype-font-features/opentype-discretionary-ligatures.gif "Text používající volitelné ligatury OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat glyfy nezávazných ligatur pro písmo Pericles pomocí vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Ve výchozím nastavení jsou písma OpenType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] v nástroji povolit standardní ligatury. Pokud například použijete písmo Palatino Linotype, standardní ligatury "Fi", "FF" a "FL" se zobrazí jako piktogramy kombinovaného znaku. Všimněte si, že dvojice znaků pro každou standardní ligaturu je vzájemně dotykem.  
  
 ![Text používající standardní ligatury OpenType s Palatino Linotype](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "Text používající standardní ligatury OpenType s Palatino Linotype")    
   
 Funkce standardního odložení ale můžete zakázat, aby se standardní ligatura jako "FF" zobrazoval jako dvě samostatné glyfy, nikoli jako piktogramy kombinovaného znaku.  
  
 ![Text používající zakázané standardní ligatury OpenType](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "Text používající zakázané standardní ligatury OpenType")  
    
 Následující příklad kódu ukazuje, jak zakázat standardní glyfy ligatur pro písmo Palatino Linotype s použitím vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>Ozdobná písmena  
 Ozdobné znaky jsou ozdobné glyfy, které používají výtvarné ozdoby, které jsou často spojeny s kaligraficky. Následující text zobrazuje standardní a ozdobné glyfy pro písmo Pescadero.  
  
 ![Text používající standardní a ozdobné glyfy OpenType](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "Text používající standardní a ozdobné glyfy OpenType")  

 Ozdobné znaky se často používají jako ozdobné elementy v krátkých slovnících, jako je například oznamování událostí. Následující text používá ozdobná písmena k zdůraznění velkých písmen názvu události.  
  
 ![Text používající ozdobné znaky písma OpenType](./media/opentype-font-features/opentype-swashes.gif "Text používající ozdobné znaky písma OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat ozdobné znaky písma pomocí vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Kontextová ozdobná písmena  
 Některé kombinace ozdobných glyfů mohou způsobit neatraktivní vzhled, například překrývající se dotahy na sousedících písmenech. Použití kontextového ozdobu v kontextu umožňuje použít náhradní ozdobný glyf, který vytváří lepší vzhled. Následující text zobrazuje stejné slovo před a po použití kontextového ozdobu.  
  
 ![Text používající kontextová ozdobná písma OpenType](./media/opentype-font-features/opentype-contextual-swashes.gif "Text používající kontextová ozdobná písma OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat kontextové ozdobné znaky pro písmo Pescadero pomocí vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>Alternativy  
 Alternativy jsou glyfy, které je možné nahradit standardním glyfem. Písma OpenType, jako je písmo Pericles použité v následujících příkladech, mohou obsahovat alternativní glyfy, které můžete použít k vytvoření různých vzhledů pro text. Následující text zobrazuje standardní glyfy pro písmo Pericles.  
  
 ![Text používající glyfy standardu OpenType](./media/opentype-font-features/opentype-standard-glyphs.gif "Text používající glyfy standardu OpenType")  

 Písmo OpenType Pericles obsahuje další glyfy, které představují stylistické alternativy standardní sady glyfů. Následující text zobrazuje stylistické alternativní glyfy.  
  
 ![Text používající stylistické alternativní glyfy písma OpenType](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "Text používající stylistické alternativní glyfy písma OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat stylistické alternativní glyfy pro písmo Pericles pomocí vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Následující text zobrazuje několik dalších stylistických alternativních glyfů pro písmo Pericles.  
  
 ![Text používající stylistické alternativní glyfy písma OpenType pro písmo Pericles](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "Text používající stylistické alternativní glyfy písma OpenType pro písmo Pericles")

 Následující příklad kódu ukazuje, jak definovat tyto další stylistické alternativní glyfy.  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Náhodné kontextové alternativy  
 Náhodné kontextové alternativy poskytují více náhradních glyfů pro jeden znak. Při implementaci pomocí písma typu skriptu může tato funkce simulovat rukopis pomocí sady náhodně vybraných glyfů s drobnými rozdíly v zobrazení. Následující text používá náhodná kontextová alternativa pro písmo Lindsey. Všimněte si, že se písmeno "a" mírně liší vzhledem  
  
 ![Text s použitím náhodných kontextových alternativ písma OpenType](./media/opentype-font-features/opentype-random-contextual-alternates.gif "Text s použitím náhodných kontextových alternativ písma OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat náhodné kontextové alternativy pro písmo Lindsey pomocí vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Historické formuláře  
 Historické formuláře jsou typografické konvence, které byly v minulosti běžné. Následující text zobrazí frázi "Boston, Massachusetts" s použitím historické formy glyfů pro písmo Palatino Linotype.  
  
 ![Text pomocí historických formulářů OpenType](./media/opentype-font-features/opentype-historical-forms.gif "Text pomocí historických formulářů OpenType")  
   
 Následující příklad kódu ukazuje, jak definovat historické formuláře pro písmo Palatino Linotype s použitím vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>Číselné styly  
 Písma OpenType podporují velký počet funkcí, které lze použít s numerickými hodnotami v textu.  
  
### <a name="fractions"></a>Zlomky  
 Písma OpenType podporují styly pro zlomky, včetně lomítka a skládaného.  
  
 Následující text zobrazuje styly zlomku pro písmo Palatino Linotype.  
  
 ![Text používající lomítka a skládané zlomky písma OpenType](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "Text používající lomítka a skládané zlomky písma OpenType")  
   
 Následující příklad kódu ukazuje, jak definovat styly zlomků pro písmo Palatino Linotype s použitím vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Stará čísla stylu  
 Písma OpenType podporují starý formát čísla stylu. Tento formát je vhodný pro zobrazení číslic v stylech, které už nejsou standardně standardní. Následující text zobrazuje datum 18 století ve formátech Standard a Star Style pro písmo Linotype Palatino.  
  
 ![Text používající čísla stylu písma OpenType stará](./media/opentype-font-features/opentype-old-style-numerals.gif "Text používající čísla stylu písma OpenType stará")  
    
 Následující text zobrazuje standardní číslice pro písmo Palatino Linotype, za kterými následuje původní číslice stylu.  
  
 ![Text s použitím sad číslic ve starém stylu OpenType](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "Text s použitím sad číslic ve starém stylu OpenType")  
  
 Následující příklad kódu ukazuje, jak definovat stará čísla stylu pro písmo Palatino Linotype s použitím vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Proporcionální a tabulkové hodnoty  
 Písma OpenType podporují proporcionální a tabelární obrázek pro řízení zarovnání šířky při použití číslic. Proporcionální hodnoty považují každé číslo za jinou šířku – "1" je užší než "5". Tabulkové hodnoty jsou považovány za číslice se stejnou šířkou, aby byly zarovnány svisle, což zvyšuje čitelnost informací o finančních typech.  
  
 Následující text zobrazí dvě proporcionální hodnoty v prvním sloupci pomocí písma Miramonte. Všimněte si rozdílové šířky mezi číslicemi "5" a "1". Druhý sloupec zobrazuje stejné dvě číselné hodnoty se šířkou, které jsou upraveny pomocí funkce tabulkového obrázku.  
  
 ![Text používající proporcionální & tabulkových obrázků písma OpenType](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "Text s použitím proporcionálních a tabelárních číslic písma OpenType")  
    
 Následující příklad kódu ukazuje, jak definovat proporcionální a tabulkové hodnoty pro písmo Miramonte pomocí vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Nula s lomítkem  
 Písma OpenType podporují lomítko s nulou pro zdůraznění rozdílu mezi písmenem "O" a číslicí "0". Číslice nula se často používá pro identifikátory ve finančních a podnikových informacích.  
  
 Následující text zobrazuje identifikátor pořadí vzorku pomocí písma Miramonte. První řádek používá standardní číslice. Druhý řádek použil lomítka nula, aby poskytoval větší kontrast s velkým písmenem "O".  
  
 ![Text používající číslice písma OpenType s lomítkem (0] ) (./media/opentype-font-features/opentype-slashed-zero-numerals.gif "Text používající číslice písma OpenType s lomítkem (0") )  
    
 Následující příklad kódu ukazuje, jak definovat čísla s lomítkem (0) pro písmo Miramonte pomocí vlastností <xref:System.Windows.Documents.Typography> objektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>Typografie – třída  
 <xref:System.Windows.Documents.Typography> Objekt zpřístupňuje sadu funkcí, které písmo OpenType podporuje. Nastavením vlastností <xref:System.Windows.Documents.Typography> v kódu můžete snadno vytvářet dokumenty, které využívají funkce OpenType.  
  
 Následující text zobrazuje standardní velká písmena pro písmo Pescadero a potom písmena se stylem "SmallCaps" a "AllSmallCaps". V takovém případě se pro všechna tři slova použije stejná velikost písma.  
  
 ![Text používající velká písmena písma OpenType](./media/opentype-font-features/opentype-capitals.gif "Text používající velká písmena písma OpenType")  
    
 Následující příklad kódu ukazuje, jak definovat velká písmena pro písmo Pescadero pomocí vlastností <xref:System.Windows.Documents.Typography> objektu. Když se použije formát "SmallCaps", bude se ignorovat počáteční velké písmeno.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 Následující příklad kódu provede stejnou úlohu jako předchozí příklad označení.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Typografické vlastnosti třídy  
 V následující tabulce jsou uvedeny vlastnosti, hodnoty a výchozí nastavení <xref:System.Windows.Documents.Typography> objektu.  
  
|Vlastnost|Hodnota (y)|Výchozí hodnota|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|Číselná hodnota – Byte|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|Číselná hodnota – Byte|0|  
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
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|Číselná hodnota – Byte|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|Číselná hodnota – Byte|0|  
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
