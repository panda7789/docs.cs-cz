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
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="1df2e-102">Úvod do objektu GlyphRun a elementu Glyph</span><span class="sxs-lookup"><span data-stu-id="1df2e-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="1df2e-103">Toto téma <xref:System.Windows.Media.GlyphRun> popisuje objekt <xref:System.Windows.Documents.Glyphs> a prvek.</span><span class="sxs-lookup"><span data-stu-id="1df2e-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="1df2e-104">Úvod do Glydu</span><span class="sxs-lookup"><span data-stu-id="1df2e-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="1df2e-105">Poskytuje pokročilou textovou podporu včetně značek na <xref:System.Windows.Documents.Glyphs> úrovni glyfů s přímým přístupem pro zákazníky, kteří chtějí zachytit a zachovat text po formátování.</span><span class="sxs-lookup"><span data-stu-id="1df2e-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="1df2e-106">Tyto funkce poskytují kritickou podporu pro různé požadavky na vykreslování textu v každém z následujících scénářů.</span><span class="sxs-lookup"><span data-stu-id="1df2e-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1. <span data-ttu-id="1df2e-107">Zobrazení dokumentů v pevném formátu.</span><span class="sxs-lookup"><span data-stu-id="1df2e-107">Screen display of fixed-format documents.</span></span>  
  
2. <span data-ttu-id="1df2e-108">Vytisknout scénáře.</span><span class="sxs-lookup"><span data-stu-id="1df2e-108">Print scenarios.</span></span>  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<span data-ttu-id="1df2e-109">jako jazyk tiskárny zařízení.</span><span class="sxs-lookup"><span data-stu-id="1df2e-109">as a device printer language.</span></span>  
  
    - <span data-ttu-id="1df2e-110">Zapisovač dokumentů systému Microsoft XPS.</span><span class="sxs-lookup"><span data-stu-id="1df2e-110">Microsoft XPS Document Writer.</span></span>  
  
    - <span data-ttu-id="1df2e-111">Předchozí ovladače tiskárny, výstup z aplikací Win32 do pevného formátu.</span><span class="sxs-lookup"><span data-stu-id="1df2e-111">Previous printer drivers, output from Win32 applications to the fixed format.</span></span>  
  
    - <span data-ttu-id="1df2e-112">Formát zařazovací liby tisku.</span><span class="sxs-lookup"><span data-stu-id="1df2e-112">Print spool format.</span></span>  
  
3. <span data-ttu-id="1df2e-113">Reprezentace dokumentu s pevným formátem, včetně klientů pro předchozí verze systému Windows a dalších výpočetních zařízení.</span><span class="sxs-lookup"><span data-stu-id="1df2e-113">Fixed-format document representation, including clients for previous versions of Windows and other computing devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1df2e-114"><xref:System.Windows.Documents.Glyphs>a <xref:System.Windows.Media.GlyphRun> jsou určeny pro prezentační a tiskové scénáře s pevným formátem.</span><span class="sxs-lookup"><span data-stu-id="1df2e-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="1df2e-115">obsahuje několik prvků pro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] obecné <xref:System.Windows.Controls.Label> rozložení <xref:System.Windows.Controls.TextBlock>a scénáře, jako je například a .</span><span class="sxs-lookup"><span data-stu-id="1df2e-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="1df2e-116">Další informace o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] rozložení a scénářích naleznete [v tématu Typografie v WPF](typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="1df2e-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>
## <a name="the-glyphrun-object"></a><span data-ttu-id="1df2e-117">Objekt Glyphrun</span><span class="sxs-lookup"><span data-stu-id="1df2e-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="1df2e-118">Objekt <xref:System.Windows.Media.GlyphRun> představuje posloupnost glyfů z jedné plochy jednoho písma v jedné velikosti a s jedním stylem vykreslování.</span><span class="sxs-lookup"><span data-stu-id="1df2e-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="1df2e-119"><xref:System.Windows.Media.GlyphRun>obsahuje jak podrobnosti <xref:System.Windows.Documents.Glyphs.Indices%2A> písma, jako je glyf, tak jednotlivé polohy glyfů.</span><span class="sxs-lookup"><span data-stu-id="1df2e-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="1df2e-120">Obsahuje také původní body kódu Unicode, ze kterých bylo spuštění generováno, informace o odsazení vyrovnávací paměti znak-gly a příznaky pro znaky a glyfy.</span><span class="sxs-lookup"><span data-stu-id="1df2e-120">It also includes the original Unicode code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="1df2e-121"><xref:System.Windows.Media.GlyphRun>má odpovídající vysokou <xref:System.Windows.FrameworkElement>úroveň <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="1df2e-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="1df2e-122"><xref:System.Windows.Documents.Glyphs>lze použít ve stromu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prvků a <xref:System.Windows.Media.GlyphRun> ve značkách k reprezentaci výstupu.</span><span class="sxs-lookup"><span data-stu-id="1df2e-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>
## <a name="the-glyphs-element"></a><span data-ttu-id="1df2e-123">Element glyfů</span><span class="sxs-lookup"><span data-stu-id="1df2e-123">The Glyphs Element</span></span>  
 <span data-ttu-id="1df2e-124">Prvek <xref:System.Windows.Documents.Glyphs> představuje výstup in <xref:System.Windows.Media.GlyphRun> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1df2e-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="1df2e-125">Následující syntaxe značek se používá <xref:System.Windows.Documents.Glyphs> k popisu prvku.</span><span class="sxs-lookup"><span data-stu-id="1df2e-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="1df2e-126">Následující definice vlastností odpovídají prvním čtyřem atributům ve značce vzorku.</span><span class="sxs-lookup"><span data-stu-id="1df2e-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="1df2e-127">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="1df2e-127">Property</span></span>|<span data-ttu-id="1df2e-128">Popis</span><span class="sxs-lookup"><span data-stu-id="1df2e-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="1df2e-129">Určuje identifikátor prostředku: název souboru, identifikátor identifikátor identifikátoru URI (Web uniform) nebo odkaz na prostředek v aplikaci EXE nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="1df2e-129">Specifies a resource identifier: file name, Web uniform resource identifier (URI), or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="1df2e-130">Určuje velikost písma v jednotkách výkresového povrchu (výchozí hodnota je 0,96 palce).</span><span class="sxs-lookup"><span data-stu-id="1df2e-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="1df2e-131">Určuje příznaky pro tučné písmo a kurzívu.</span><span class="sxs-lookup"><span data-stu-id="1df2e-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="1df2e-132">Určuje obousměrnou úroveň rozložení.</span><span class="sxs-lookup"><span data-stu-id="1df2e-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="1df2e-133">Sudé a nulové hodnoty implikují rozložení zleva doprava; liché hodnoty implikují rozložení zprava doleva.</span><span class="sxs-lookup"><span data-stu-id="1df2e-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>
### <a name="indices-property"></a><span data-ttu-id="1df2e-134">Vlastnost Indexy</span><span class="sxs-lookup"><span data-stu-id="1df2e-134">Indices property</span></span>  
 <span data-ttu-id="1df2e-135">Vlastnost <xref:System.Windows.Documents.Glyphs.Indices%2A> je řetězec specifikace glyfů.</span><span class="sxs-lookup"><span data-stu-id="1df2e-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="1df2e-136">Pokud posloupnost glyfů tvoří jeden cluster, specifikaci prvního glyfu v clusteru předchází specifikace počtu glyfů a počtu bodů kódu, které se spojí a vytvoří cluster.</span><span class="sxs-lookup"><span data-stu-id="1df2e-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="1df2e-137">Vlastnost <xref:System.Windows.Documents.Glyphs.Indices%2A> shromažďuje v jednom řetězci následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1df2e-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
- <span data-ttu-id="1df2e-138">Indexy glyfů</span><span class="sxs-lookup"><span data-stu-id="1df2e-138">Glyph indices</span></span>  
  
- <span data-ttu-id="1df2e-139">Šířky glyfu</span><span class="sxs-lookup"><span data-stu-id="1df2e-139">Glyph advance widths</span></span>  
  
- <span data-ttu-id="1df2e-140">Kombinování vektorů příloh glyfu</span><span class="sxs-lookup"><span data-stu-id="1df2e-140">Combining glyph attachment vectors</span></span>  
  
- <span data-ttu-id="1df2e-141">Mapování clusteru z bodů kódu na glyfy</span><span class="sxs-lookup"><span data-stu-id="1df2e-141">Cluster mapping from code points to glyphs</span></span>  
  
- <span data-ttu-id="1df2e-142">Příznaky glyfů</span><span class="sxs-lookup"><span data-stu-id="1df2e-142">Glyph flags</span></span>  
  
 <span data-ttu-id="1df2e-143">Každá specifikace glyfu má následující tvar.</span><span class="sxs-lookup"><span data-stu-id="1df2e-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>
## <a name="glyph-metrics"></a><span data-ttu-id="1df2e-144">Metriky glyfu</span><span class="sxs-lookup"><span data-stu-id="1df2e-144">Glyph Metrics</span></span>  
 <span data-ttu-id="1df2e-145">Každý glyf definuje metriky, které <xref:System.Windows.Documents.Glyphs>určují, jak bude zarovnán s ostatními .</span><span class="sxs-lookup"><span data-stu-id="1df2e-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="1df2e-146">Následující obrázek definuje různé typografické kvality dvou různých znaků glyfu.</span><span class="sxs-lookup"><span data-stu-id="1df2e-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="1df2e-147">![Diagraf měření glyfů](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="1df2e-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>
## <a name="glyphs-markup"></a><span data-ttu-id="1df2e-148">Značky glyfů</span><span class="sxs-lookup"><span data-stu-id="1df2e-148">Glyphs Markup</span></span>  
 <span data-ttu-id="1df2e-149">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Documents.Glyphs> různé [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]vlastnosti prvku v .</span><span class="sxs-lookup"><span data-stu-id="1df2e-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1df2e-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="1df2e-150">See also</span></span>

- [<span data-ttu-id="1df2e-151">Typografie v rozhraní WPF</span><span class="sxs-lookup"><span data-stu-id="1df2e-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="1df2e-152">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="1df2e-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="1df2e-153">Text</span><span class="sxs-lookup"><span data-stu-id="1df2e-153">Text</span></span>](optimizing-performance-text.md)
