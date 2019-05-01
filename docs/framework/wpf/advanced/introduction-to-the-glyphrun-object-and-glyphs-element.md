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
ms.openlocfilehash: 0e5ec2b89f015c7e061b59fea755eb368f1ac7a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031301"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="ccb51-102">Úvod do objektu GlyphRun a elementu Glyph</span><span class="sxs-lookup"><span data-stu-id="ccb51-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="ccb51-103">Toto téma popisuje <xref:System.Windows.Media.GlyphRun> objektu a <xref:System.Windows.Documents.Glyphs> elementu.</span><span class="sxs-lookup"><span data-stu-id="ccb51-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="ccb51-104">Úvod do GlyphRun</span><span class="sxs-lookup"><span data-stu-id="ccb51-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="ccb51-105">podporuje rozšířené textové včetně úrovni piktogramu značky s přímým přístupem k <xref:System.Windows.Documents.Glyphs> pro zákazníky, kteří chtějí zachytit a zachovat po formátování textu.</span><span class="sxs-lookup"><span data-stu-id="ccb51-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="ccb51-106">Tyto funkce umožňují podpory se zásadním jiným textovým požadavky na vykreslování v každém z těchto scénářů.</span><span class="sxs-lookup"><span data-stu-id="ccb51-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1. <span data-ttu-id="ccb51-107">Zobrazování dokumentů pevného formátu.</span><span class="sxs-lookup"><span data-stu-id="ccb51-107">Screen display of fixed-format documents.</span></span>  
  
2. <span data-ttu-id="ccb51-108">Tisk scénáře.</span><span class="sxs-lookup"><span data-stu-id="ccb51-108">Print scenarios.</span></span>  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <span data-ttu-id="ccb51-109">jako jazyk tiskárny zařízení.</span><span class="sxs-lookup"><span data-stu-id="ccb51-109">as a device printer language.</span></span>  
  
    - [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)]<span data-ttu-id="ccb51-110">.</span><span class="sxs-lookup"><span data-stu-id="ccb51-110">.</span></span>  
  
    - <span data-ttu-id="ccb51-111">Předchozí ovladače tiskárny, výstup z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikací na pevném formátu.</span><span class="sxs-lookup"><span data-stu-id="ccb51-111">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>  
  
    - <span data-ttu-id="ccb51-112">Formát zařazování tisku.</span><span class="sxs-lookup"><span data-stu-id="ccb51-112">Print spool format.</span></span>  
  
3. <span data-ttu-id="ccb51-113">Reprezentace pevného formátu dokumentu, včetně klientů k předchozím verzím sady [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a další výpočetní zařízení.</span><span class="sxs-lookup"><span data-stu-id="ccb51-113">Fixed-format document representation, including clients for previous versions of [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] and other computing devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ccb51-114"><xref:System.Windows.Documents.Glyphs> a <xref:System.Windows.Media.GlyphRun> jsou navrženy pro prezentaci pevného formátu dokumentu a tisku scénáře.</span><span class="sxs-lookup"><span data-stu-id="ccb51-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="ccb51-115">poskytuje několik elementů pro obecné rozložení a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénáře, jako <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="ccb51-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="ccb51-116">Další informace o rozložení a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénáře, naleznete v tématu [Typografie v rozhraní WPF](typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="ccb51-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a><span data-ttu-id="ccb51-117">Objektu GlyphRun</span><span class="sxs-lookup"><span data-stu-id="ccb51-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="ccb51-118"><xref:System.Windows.Media.GlyphRun> Objekt představuje posloupnost glyfy z jednoho rozpoznávání tváře jediného písma v jedné velikosti a stylem jeden vykreslování.</span><span class="sxs-lookup"><span data-stu-id="ccb51-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="ccb51-119"><xref:System.Windows.Media.GlyphRun> obsahuje podrobnosti o obou písmo jako je například piktogram <xref:System.Windows.Documents.Glyphs.Indices%2A> a umístění jednotlivých glyfů.</span><span class="sxs-lookup"><span data-stu-id="ccb51-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="ccb51-120">Obsahuje také původní [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kódu bodů spuštění bylo vygenerováno, informace o posunu mapování znaků piktogram vyrovnávací paměti a příznaky za znak a za glyfů.</span><span class="sxs-lookup"><span data-stu-id="ccb51-120">It also includes the original [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="ccb51-121"><xref:System.Windows.Media.GlyphRun> má odpovídající vysoké úrovně <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="ccb51-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="ccb51-122"><xref:System.Windows.Documents.Glyphs> je možné na strom prvku a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky, které představují <xref:System.Windows.Media.GlyphRun> výstup.</span><span class="sxs-lookup"><span data-stu-id="ccb51-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a><span data-ttu-id="ccb51-123">Glyph – Element</span><span class="sxs-lookup"><span data-stu-id="ccb51-123">The Glyphs Element</span></span>  
 <span data-ttu-id="ccb51-124"><xref:System.Windows.Documents.Glyphs> Element představuje výstup <xref:System.Windows.Media.GlyphRun> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ccb51-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="ccb51-125">Následující syntaxe značek se používá k popisu <xref:System.Windows.Documents.Glyphs> elementu.</span><span class="sxs-lookup"><span data-stu-id="ccb51-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="ccb51-126">Následující definice vlastnosti odpovídají první čtyři atributy ve značce vzorku.</span><span class="sxs-lookup"><span data-stu-id="ccb51-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="ccb51-127">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ccb51-127">Property</span></span>|<span data-ttu-id="ccb51-128">Popis</span><span class="sxs-lookup"><span data-stu-id="ccb51-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="ccb51-129">Určuje identifikátor prostředku: název souboru, webové [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], nebo odkaz na prostředek aplikace .exe nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ccb51-129">Specifies a resource identifier: file name, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="ccb51-130">Určuje velikost písma v kreslení surface jednotek (výchozí hodnota je.96 palců).</span><span class="sxs-lookup"><span data-stu-id="ccb51-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="ccb51-131">Určuje příznaky pro tučný i kurzívu styly.</span><span class="sxs-lookup"><span data-stu-id="ccb51-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="ccb51-132">Určuje úroveň obousměrného rozložení.</span><span class="sxs-lookup"><span data-stu-id="ccb51-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="ccb51-133">Sudým číslem a nulové hodnoty znamenají rozložení zleva doprava; lichých hodnoty znamenají rozložení zprava doleva.</span><span class="sxs-lookup"><span data-stu-id="ccb51-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a><span data-ttu-id="ccb51-134">Vlastnost indexů</span><span class="sxs-lookup"><span data-stu-id="ccb51-134">Indices property</span></span>  
 <span data-ttu-id="ccb51-135"><xref:System.Windows.Documents.Glyphs.Indices%2A> Vlastnost představuje řetězec piktogram specifikací.</span><span class="sxs-lookup"><span data-stu-id="ccb51-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="ccb51-136">Pokud pořadí glyfů tvoří jeden cluster, předchází specifikace prvním glyfem clusteru specifikace kolik glyfů a kolik bodů kódu kombinovat a vytvoří cluster.</span><span class="sxs-lookup"><span data-stu-id="ccb51-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="ccb51-137"><xref:System.Windows.Documents.Glyphs.Indices%2A> Vlastnost shromažďuje v jednom řetězci následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ccb51-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
- <span data-ttu-id="ccb51-138">Glyphs indexy</span><span class="sxs-lookup"><span data-stu-id="ccb51-138">Glyph indices</span></span>  
  
- <span data-ttu-id="ccb51-139">Piktogram zálohy šířky</span><span class="sxs-lookup"><span data-stu-id="ccb51-139">Glyph advance widths</span></span>  
  
- <span data-ttu-id="ccb51-140">Kombinování piktogram přílohy vektorů</span><span class="sxs-lookup"><span data-stu-id="ccb51-140">Combining glyph attachment vectors</span></span>  
  
- <span data-ttu-id="ccb51-141">Cluster mapování z bodů kódu na piktogramy</span><span class="sxs-lookup"><span data-stu-id="ccb51-141">Cluster mapping from code points to glyphs</span></span>  
  
- <span data-ttu-id="ccb51-142">Piktogram příznaky</span><span class="sxs-lookup"><span data-stu-id="ccb51-142">Glyph flags</span></span>  
  
 <span data-ttu-id="ccb51-143">Každá specifikace piktogram má následující formát.</span><span class="sxs-lookup"><span data-stu-id="ccb51-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a><span data-ttu-id="ccb51-144">Piktogram metriky</span><span class="sxs-lookup"><span data-stu-id="ccb51-144">Glyph Metrics</span></span>  
 <span data-ttu-id="ccb51-145">Každý piktogram definuje metriky, určit zarovnání s jinými <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="ccb51-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="ccb51-146">Na následujícím obrázku definuje různé typografickém kvality dva znaky jiné glyfů.</span><span class="sxs-lookup"><span data-stu-id="ccb51-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="ccb51-147">![Diagram měření piktogramu](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="ccb51-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a><span data-ttu-id="ccb51-148">Glyfy značek</span><span class="sxs-lookup"><span data-stu-id="ccb51-148">Glyphs Markup</span></span>  
 <span data-ttu-id="ccb51-149">Následující příklad kódu ukazuje, jak používat různé vlastnosti objektu <xref:System.Windows.Documents.Glyphs> prvek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ccb51-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ccb51-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccb51-150">See also</span></span>

- [<span data-ttu-id="ccb51-151">Typografie v rozhraní WPF</span><span class="sxs-lookup"><span data-stu-id="ccb51-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="ccb51-152">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="ccb51-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="ccb51-153">Text</span><span class="sxs-lookup"><span data-stu-id="ccb51-153">Text</span></span>](optimizing-performance-text.md)
