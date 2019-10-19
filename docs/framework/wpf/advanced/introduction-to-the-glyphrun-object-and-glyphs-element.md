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
ms.openlocfilehash: 2f7bb3fb4f28b063c78dde9f9f354b38a5e707f3
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581893"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="5d670-102">Úvod do objektu GlyphRun a elementu Glyph</span><span class="sxs-lookup"><span data-stu-id="5d670-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="5d670-103">Toto téma popisuje objekt <xref:System.Windows.Media.GlyphRun> a prvek <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="5d670-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="5d670-104">Úvod do GlyphRun</span><span class="sxs-lookup"><span data-stu-id="5d670-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="5d670-105">poskytuje rozšířenou podporu textu včetně značek na úrovni glyfů s přímým přístupem k <xref:System.Windows.Documents.Glyphs> pro zákazníky, kteří chtějí zachytit a uchovat text po formátování.</span><span class="sxs-lookup"><span data-stu-id="5d670-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="5d670-106">Tyto funkce poskytují kritickou podporu pro různé požadavky na vykreslování textu v každém z následujících scénářů.</span><span class="sxs-lookup"><span data-stu-id="5d670-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1. <span data-ttu-id="5d670-107">Zobrazení dokumentů s pevným formátem</span><span class="sxs-lookup"><span data-stu-id="5d670-107">Screen display of fixed-format documents.</span></span>  
  
2. <span data-ttu-id="5d670-108">Scénáře tisku.</span><span class="sxs-lookup"><span data-stu-id="5d670-108">Print scenarios.</span></span>  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <span data-ttu-id="5d670-109">jako jazyk tiskárny zařízení.</span><span class="sxs-lookup"><span data-stu-id="5d670-109">as a device printer language.</span></span>  
  
    - <span data-ttu-id="5d670-110">Zapisovač dokumentů Microsoft XPS.</span><span class="sxs-lookup"><span data-stu-id="5d670-110">Microsoft XPS Document Writer.</span></span>  
  
    - <span data-ttu-id="5d670-111">Předchozí ovladače tiskárny, výstup z aplikací [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] do pevného formátu.</span><span class="sxs-lookup"><span data-stu-id="5d670-111">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>  
  
    - <span data-ttu-id="5d670-112">Formát zařazování tisku.</span><span class="sxs-lookup"><span data-stu-id="5d670-112">Print spool format.</span></span>  
  
3. <span data-ttu-id="5d670-113">Reprezentace dokumentu s pevným formátem, včetně klientů pro předchozí verze Windows a dalších výpočetních zařízení.</span><span class="sxs-lookup"><span data-stu-id="5d670-113">Fixed-format document representation, including clients for previous versions of Windows and other computing devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d670-114"><xref:System.Windows.Documents.Glyphs> a <xref:System.Windows.Media.GlyphRun> jsou navržené pro scénáře pro prezentaci a tisk v dokumentu s pevným formátováním.</span><span class="sxs-lookup"><span data-stu-id="5d670-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="5d670-115">poskytuje několik prvků pro obecné rozložení a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénáře, jako je například <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="5d670-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="5d670-116">Další informace o scénářích rozložení a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] najdete v tématu [Typografie v](typography-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="5d670-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a><span data-ttu-id="5d670-117">Objekt GlyphRun</span><span class="sxs-lookup"><span data-stu-id="5d670-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="5d670-118">Objekt <xref:System.Windows.Media.GlyphRun> představuje sekvenci glyfů z jedné plošky jednoho písma v jedné velikosti a s jedním stylem vykreslování.</span><span class="sxs-lookup"><span data-stu-id="5d670-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="5d670-119"><xref:System.Windows.Media.GlyphRun> obsahuje jak podrobnosti o písmu, například glyf <xref:System.Windows.Documents.Glyphs.Indices%2A> a jednotlivé pozice glyfů.</span><span class="sxs-lookup"><span data-stu-id="5d670-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="5d670-120">Zahrnuje také původní body kódování Unicode, ke kterým byl vygenerován běh, informace o mapování vyrovnávací paměti znaků na glyfy a příznaky pro jednotlivé znaky a pro piktogramy.</span><span class="sxs-lookup"><span data-stu-id="5d670-120">It also includes the original Unicode code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="5d670-121"><xref:System.Windows.Media.GlyphRun> má odpovídající <xref:System.Windows.FrameworkElement> na nejvyšší úrovni <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="5d670-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="5d670-122"><xref:System.Windows.Documents.Glyphs> lze použít ve stromové struktuře elementů a v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek pro reprezentaci <xref:System.Windows.Media.GlyphRun>ho výstupu.</span><span class="sxs-lookup"><span data-stu-id="5d670-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a><span data-ttu-id="5d670-123">Piktograms – element</span><span class="sxs-lookup"><span data-stu-id="5d670-123">The Glyphs Element</span></span>  
 <span data-ttu-id="5d670-124">Element <xref:System.Windows.Documents.Glyphs> představuje výstup <xref:System.Windows.Media.GlyphRun> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5d670-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="5d670-125">Následující syntaxe kódu se používá k popisu prvku <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="5d670-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="5d670-126">Následující definice vlastností odpovídají prvních čtyř atributů v ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="5d670-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="5d670-127">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="5d670-127">Property</span></span>|<span data-ttu-id="5d670-128">Popis</span><span class="sxs-lookup"><span data-stu-id="5d670-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="5d670-129">Určuje identifikátor prostředku: název souboru, identifikátor URI (Web Uniform Resource Identifier) nebo odkaz na prostředek v souboru Application. exe nebo Container.</span><span class="sxs-lookup"><span data-stu-id="5d670-129">Specifies a resource identifier: file name, Web uniform resource identifier (URI), or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="5d670-130">Určuje velikost písma v jednotkách kresby (výchozí hodnota je. 96 palců).</span><span class="sxs-lookup"><span data-stu-id="5d670-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="5d670-131">Určuje příznaky pro styly tučného písma a kurzívy.</span><span class="sxs-lookup"><span data-stu-id="5d670-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="5d670-132">Určuje obousměrnou úroveň rozložení.</span><span class="sxs-lookup"><span data-stu-id="5d670-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="5d670-133">Sudé a nulové hodnoty implikují rozložení zleva doprava; hodnoty s lichými čísly naznačují rozložení zprava doleva.</span><span class="sxs-lookup"><span data-stu-id="5d670-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a><span data-ttu-id="5d670-134">Vlastnost Indexes</span><span class="sxs-lookup"><span data-stu-id="5d670-134">Indices property</span></span>  
 <span data-ttu-id="5d670-135">Vlastnost <xref:System.Windows.Documents.Glyphs.Indices%2A> je řetězec specifikace glyfů.</span><span class="sxs-lookup"><span data-stu-id="5d670-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="5d670-136">Pokud sekvence glyfů tvoří jeden cluster, předá specifikace prvního glyfu v clusteru specifikace toho, kolik glyfů a kolik bodů kódu se kombinuje s vytvořením clusteru.</span><span class="sxs-lookup"><span data-stu-id="5d670-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="5d670-137">Vlastnost <xref:System.Windows.Documents.Glyphs.Indices%2A> shromažďuje v jednom řetězci následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5d670-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
- <span data-ttu-id="5d670-138">Indexy glyfů</span><span class="sxs-lookup"><span data-stu-id="5d670-138">Glyph indices</span></span>  
  
- <span data-ttu-id="5d670-139">Šířka pro zálohy glyfů</span><span class="sxs-lookup"><span data-stu-id="5d670-139">Glyph advance widths</span></span>  
  
- <span data-ttu-id="5d670-140">Kombinování vektorů příloh glyfů</span><span class="sxs-lookup"><span data-stu-id="5d670-140">Combining glyph attachment vectors</span></span>  
  
- <span data-ttu-id="5d670-141">Mapování clusteru z bodů kódu na glyfy</span><span class="sxs-lookup"><span data-stu-id="5d670-141">Cluster mapping from code points to glyphs</span></span>  
  
- <span data-ttu-id="5d670-142">Příznaky glyfů</span><span class="sxs-lookup"><span data-stu-id="5d670-142">Glyph flags</span></span>  
  
 <span data-ttu-id="5d670-143">Každá specifikace glyfu má následující formu.</span><span class="sxs-lookup"><span data-stu-id="5d670-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a><span data-ttu-id="5d670-144">Metriky glyfů</span><span class="sxs-lookup"><span data-stu-id="5d670-144">Glyph Metrics</span></span>  
 <span data-ttu-id="5d670-145">Každý glyf definuje metriky, které určují, jak se zarovnává s ostatními <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="5d670-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="5d670-146">Následující obrázek definuje různé typografické kvality dvou různých znaků glyfů.</span><span class="sxs-lookup"><span data-stu-id="5d670-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="5d670-147">![Diagraph měření glyfů](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="5d670-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a><span data-ttu-id="5d670-148">Piktogramy – značky</span><span class="sxs-lookup"><span data-stu-id="5d670-148">Glyphs Markup</span></span>  
 <span data-ttu-id="5d670-149">Následující příklad kódu ukazuje, jak použít různé vlastnosti prvku <xref:System.Windows.Documents.Glyphs> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5d670-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5d670-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d670-150">See also</span></span>

- [<span data-ttu-id="5d670-151">Typografie v rozhraní WPF</span><span class="sxs-lookup"><span data-stu-id="5d670-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="5d670-152">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="5d670-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="5d670-153">Text</span><span class="sxs-lookup"><span data-stu-id="5d670-153">Text</span></span>](optimizing-performance-text.md)
