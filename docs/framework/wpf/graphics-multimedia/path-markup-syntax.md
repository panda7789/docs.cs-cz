---
title: Syntaxe značek cesty
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: 32eefba26b5e04370599e4c97767b6662cfd1c13
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082487"
---
# <a name="path-markup-syntax"></a><span data-ttu-id="43aa1-102">Syntaxe značek cesty</span><span class="sxs-lookup"><span data-stu-id="43aa1-102">Path Markup Syntax</span></span>
<span data-ttu-id="43aa1-103">Cesty jsou popsány v [tvary a základní kresby v přehledu WPF](shapes-and-basic-drawing-in-wpf-overview.md) a [přehled geometrie](geometry-overview.md), ale toto téma popisuje podrobně výkonná a komplexní zkrácené jazyk, slouží k určení cesty geometrie více kompaktně pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="43aa1-103">Paths are discussed in [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md) and the [Geometry Overview](geometry-overview.md), however, this topic describes in detail the powerful and complex mini-language you can use to specify path geometries more compactly using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a><span data-ttu-id="43aa1-104">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43aa1-104">Prerequisites</span></span>  
 <span data-ttu-id="43aa1-105">V tomto tématu informace o tom, měli byste se seznámit se základními funkcemi <xref:System.Windows.Media.Geometry> objekty.</span><span class="sxs-lookup"><span data-stu-id="43aa1-105">To understand this topic, you should be familiar with the basic features of <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="43aa1-106">Další informace najdete v tématu [přehled geometrie](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="43aa1-106">For more information, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a><span data-ttu-id="43aa1-107">Streamgeometry – a PathFigureCollection Mini – jazyky</span><span class="sxs-lookup"><span data-stu-id="43aa1-107">StreamGeometry and PathFigureCollection Mini-Languages</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="43aa1-108">poskytuje dvě třídy, které poskytují mini jazyky pro popis geometrické cesty: <xref:System.Windows.Media.StreamGeometry> a <xref:System.Windows.Media.PathFigureCollection>.</span><span class="sxs-lookup"><span data-stu-id="43aa1-108">provides two classes that provide mini-languages for describing geometric paths: <xref:System.Windows.Media.StreamGeometry> and <xref:System.Windows.Media.PathFigureCollection>.</span></span>  
  
-   <span data-ttu-id="43aa1-109">Použijete <xref:System.Windows.Media.StreamGeometry> zkrácené jazyce, pokud je nastavení vlastnosti typu <xref:System.Windows.Media.Geometry>, jako <xref:System.Windows.UIElement.Clip%2A> vlastnost <xref:System.Windows.UIElement> nebo <xref:System.Windows.Shapes.Path.Data%2A> vlastnost <xref:System.Windows.Shapes.Path> element.</span><span class="sxs-lookup"><span data-stu-id="43aa1-109">You use the <xref:System.Windows.Media.StreamGeometry> mini-language when setting a property of type <xref:System.Windows.Media.Geometry>, such as the <xref:System.Windows.UIElement.Clip%2A> property of a <xref:System.Windows.UIElement> or the <xref:System.Windows.Shapes.Path.Data%2A> property of a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="43aa1-110">Následující příklad používá syntaxi atributů k vytvoření <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="43aa1-110">The following example uses attribute syntax to create a <xref:System.Windows.Media.StreamGeometry>.</span></span>  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   <span data-ttu-id="43aa1-111">Použijete <xref:System.Windows.Media.PathFigureCollection> zkrácené jazyk při nastavení <xref:System.Windows.Media.PathGeometry.Figures%2A> vlastnost <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="43aa1-111">You use the <xref:System.Windows.Media.PathFigureCollection> mini-language when setting the <xref:System.Windows.Media.PathGeometry.Figures%2A> property of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="43aa1-112">Následující příklad používá syntaxi atributů k vytvoření <xref:System.Windows.Media.PathFigureCollection> pro <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="43aa1-112">The following example uses a attribute syntax to create a <xref:System.Windows.Media.PathFigureCollection> for a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 <span data-ttu-id="43aa1-113">Jak je vidět z předchozích příkladů dva jazyků mini jsou velmi podobné.</span><span class="sxs-lookup"><span data-stu-id="43aa1-113">As you can see from the preceding examples, the two mini-languages are very similar.</span></span> <span data-ttu-id="43aa1-114">Vždy je možné použít <xref:System.Windows.Media.PathGeometry> v každé situaci, kde můžete použít <xref:System.Windows.Media.StreamGeometry>; Ano která byste měli použít?</span><span class="sxs-lookup"><span data-stu-id="43aa1-114">It's always possible to use a <xref:System.Windows.Media.PathGeometry> in any situation where you could use a <xref:System.Windows.Media.StreamGeometry>; so which one should you use?</span></span> <span data-ttu-id="43aa1-115">Použít <xref:System.Windows.Media.StreamGeometry> při není nutné změnit cesty po vytvoření; použijte <xref:System.Windows.Media.PathGeometry> Pokud potřebujete změnit cesty.</span><span class="sxs-lookup"><span data-stu-id="43aa1-115">Use a <xref:System.Windows.Media.StreamGeometry> when you don't need to modify the path after creating it; use a <xref:System.Windows.Media.PathGeometry> if you do need to modify the path.</span></span>  
  
 <span data-ttu-id="43aa1-116">Další informace o rozdílech mezi <xref:System.Windows.Media.PathGeometry> a <xref:System.Windows.Media.StreamGeometry> objekty, najdete [přehled geometrie](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="43aa1-116">For more information about the differences between <xref:System.Windows.Media.PathGeometry> and <xref:System.Windows.Media.StreamGeometry> objects, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
### <a name="a-note-about-white-space"></a><span data-ttu-id="43aa1-117">Poznámka k prázdné znaky</span><span class="sxs-lookup"><span data-stu-id="43aa1-117">A Note about White Space</span></span>  
 <span data-ttu-id="43aa1-118">Pro zkrácení se zobrazí jedna mezera v oddílech syntaxe, které následují, ale více prostorů jsou přijatelné také všude, kde se zobrazí jedna mezera.</span><span class="sxs-lookup"><span data-stu-id="43aa1-118">For brevity, a single space is shown in the syntax sections that follow, but multiple spaces are also acceptable wherever a single space is shown.</span></span>  
  
 <span data-ttu-id="43aa1-119">Dvě čísla nemusí ve skutečnosti být odděleny čárkami nebo mezerami, ale to jde jenom když je výsledný řetězec je jednoznačný.</span><span class="sxs-lookup"><span data-stu-id="43aa1-119">Two numbers don’t actually have to be separated by a comma or white space, but this can only be done when the resulting string is unambiguous.</span></span> <span data-ttu-id="43aa1-120">Například `2..3` je ve skutečnosti dvě čísla: "2."</span><span class="sxs-lookup"><span data-stu-id="43aa1-120">For instance, `2..3` is actually two numbers: "2."</span></span> <span data-ttu-id="43aa1-121">A ". 3".</span><span class="sxs-lookup"><span data-stu-id="43aa1-121">And ".3".</span></span> <span data-ttu-id="43aa1-122">Obdobně `2-3` je "2" a "-3".</span><span class="sxs-lookup"><span data-stu-id="43aa1-122">Similarly, `2-3` is "2" and "-3".</span></span> <span data-ttu-id="43aa1-123">Mezery nejsou vyžadovány před nebo po příkazech, buď.</span><span class="sxs-lookup"><span data-stu-id="43aa1-123">Spaces are not required before or after commands, either.</span></span>  
  
### <a name="syntax"></a><span data-ttu-id="43aa1-124">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43aa1-124">Syntax</span></span>  
 <span data-ttu-id="43aa1-125">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Použití syntaxe pro atribut <xref:System.Windows.Media.StreamGeometry> se skládá z volitelné <xref:System.Windows.Media.FillRule> hodnotu a jeden nebo více obrázek popisy.</span><span class="sxs-lookup"><span data-stu-id="43aa1-125">The [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] attribute usage syntax for a <xref:System.Windows.Media.StreamGeometry> is composed of an optional <xref:System.Windows.Media.FillRule> value and one or more figure descriptions.</span></span>  
  
|<span data-ttu-id="43aa1-126">Použití atributu XAML StreamGeometry</span><span class="sxs-lookup"><span data-stu-id="43aa1-126">StreamGeometry XAML Attribute Usage</span></span>|  
|-----------------------------------------|  
|`<` <span data-ttu-id="43aa1-127">*object* *property* `="`[ `fillRule`] `figureDescription`[ `figureDescription`]\*</span><span class="sxs-lookup"><span data-stu-id="43aa1-127">*object* *property* `="`[ `fillRule`] `figureDescription`[ `figureDescription`]\*</span></span> `" ... />`|  
  
 <span data-ttu-id="43aa1-128">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Použití syntaxe pro atribut <xref:System.Windows.Media.PathFigureCollection> se skládá z jednoho nebo více popisy obrázek.</span><span class="sxs-lookup"><span data-stu-id="43aa1-128">The [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] attribute usage syntax for a <xref:System.Windows.Media.PathFigureCollection> is composed of one or more figure descriptions.</span></span>  
  
|<span data-ttu-id="43aa1-129">Použití atributu XAML PathFigureCollection</span><span class="sxs-lookup"><span data-stu-id="43aa1-129">PathFigureCollection XAML Attribute Usage</span></span>|  
|-----------------------------------------------|  
|`<` <span data-ttu-id="43aa1-130">*objekt* *vlastnost* `="` `figureDescription`[ `figureDescription`] \*</span><span class="sxs-lookup"><span data-stu-id="43aa1-130">*object* *property* `="` `figureDescription`[ `figureDescription`]\*</span></span> `" ... />`|  
  
|<span data-ttu-id="43aa1-131">Termín</span><span class="sxs-lookup"><span data-stu-id="43aa1-131">Term</span></span>|<span data-ttu-id="43aa1-132">Popis</span><span class="sxs-lookup"><span data-stu-id="43aa1-132">Description</span></span>|  
|----------|-----------------|  
|*<span data-ttu-id="43aa1-133">fillRule</span><span class="sxs-lookup"><span data-stu-id="43aa1-133">fillRule</span></span>*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-134">Určuje, zda <xref:System.Windows.Media.StreamGeometry> používá <xref:System.Windows.Media.FillRule.EvenOdd> nebo <xref:System.Windows.Media.FillRule.Nonzero><xref:System.Windows.Media.PathGeometry.FillRule%2A>.</span><span class="sxs-lookup"><span data-stu-id="43aa1-134">Specifies whether the <xref:System.Windows.Media.StreamGeometry> uses the <xref:System.Windows.Media.FillRule.EvenOdd> or <xref:System.Windows.Media.FillRule.Nonzero><xref:System.Windows.Media.PathGeometry.FillRule%2A>.</span></span><br /><br /> <span data-ttu-id="43aa1-135">-   `F0` Určuje, <xref:System.Windows.Media.FillRule.EvenOdd> výplně pravidlo.</span><span class="sxs-lookup"><span data-stu-id="43aa1-135">-   `F0` specifies the <xref:System.Windows.Media.FillRule.EvenOdd> fill rule.</span></span><br /><span data-ttu-id="43aa1-136">-   `F1` Určuje, <xref:System.Windows.Media.FillRule.Nonzero> výplně pravidlo.</span><span class="sxs-lookup"><span data-stu-id="43aa1-136">-   `F1` specifies the <xref:System.Windows.Media.FillRule.Nonzero> fill rule.</span></span><br /><br /> <span data-ttu-id="43aa1-137">Vynecháte-li tento příkaz, podřízená cesta v použije výchozí chování, což je <xref:System.Windows.Media.FillRule.EvenOdd>.</span><span class="sxs-lookup"><span data-stu-id="43aa1-137">If you omit this command, the subpath uses the default behavior, which is <xref:System.Windows.Media.FillRule.EvenOdd>.</span></span> <span data-ttu-id="43aa1-138">Pokud zadáte tento příkaz, musíte ji nejprve umístit.</span><span class="sxs-lookup"><span data-stu-id="43aa1-138">If you specify this command, you must place it first.</span></span>|  
|*<span data-ttu-id="43aa1-139">figureDescription</span><span class="sxs-lookup"><span data-stu-id="43aa1-139">figureDescription</span></span>*|<span data-ttu-id="43aa1-140">Obrázek skládá move příkazu, nakreslete příkazy a volitelný příkaz Zavřít.</span><span class="sxs-lookup"><span data-stu-id="43aa1-140">A figure composed of a move command, draw commands, and an optional close command.</span></span><br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*<span data-ttu-id="43aa1-141">moveCommand</span><span class="sxs-lookup"><span data-stu-id="43aa1-141">moveCommand</span></span>*|<span data-ttu-id="43aa1-142">Přesunout příkaz, který určuje počáteční bod na obrázku.</span><span class="sxs-lookup"><span data-stu-id="43aa1-142">A move command that specifies the start point of the figure.</span></span> <span data-ttu-id="43aa1-143">Zobrazit [příkaz přesunout](#themovecommand) části.</span><span class="sxs-lookup"><span data-stu-id="43aa1-143">See the [Move Command](#themovecommand) section.</span></span>|  
|*<span data-ttu-id="43aa1-144">drawCommands</span><span class="sxs-lookup"><span data-stu-id="43aa1-144">drawCommands</span></span>*|<span data-ttu-id="43aa1-145">Jeden nebo více výkresu příkazů, které popisují obsah na obrázku.</span><span class="sxs-lookup"><span data-stu-id="43aa1-145">One or more drawing commands that describe the figure's contents.</span></span> <span data-ttu-id="43aa1-146">Najdete v článku [vykreslení příkazů](#drawcommands) oddílu.</span><span class="sxs-lookup"><span data-stu-id="43aa1-146">See the [Draw Commands](#drawcommands) section.</span></span>|  
|*<span data-ttu-id="43aa1-147">closeCommand</span><span class="sxs-lookup"><span data-stu-id="43aa1-147">closeCommand</span></span>*|<span data-ttu-id="43aa1-148">Volitelný zavřít příkaz, který obrázek se zavře.</span><span class="sxs-lookup"><span data-stu-id="43aa1-148">An optional close command that closes figure.</span></span> <span data-ttu-id="43aa1-149">Zobrazit [příkaz Zavřít](#closecommand) části.</span><span class="sxs-lookup"><span data-stu-id="43aa1-149">See the [Close Command](#closecommand) section.</span></span>|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a><span data-ttu-id="43aa1-150">Příkaz přesunout</span><span class="sxs-lookup"><span data-stu-id="43aa1-150">Move Command</span></span>  
 <span data-ttu-id="43aa1-151">Určuje počáteční bod nový obrázek.</span><span class="sxs-lookup"><span data-stu-id="43aa1-151">Specifies the start point of a new figure.</span></span>  
  
|<span data-ttu-id="43aa1-152">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43aa1-152">Syntax</span></span>|  
|------------|  
|`M` *<span data-ttu-id="43aa1-153">startPoint</span><span class="sxs-lookup"><span data-stu-id="43aa1-153">startPoint</span></span>*<br /><br /> <span data-ttu-id="43aa1-154">- nebo -</span><span class="sxs-lookup"><span data-stu-id="43aa1-154">- or -</span></span><br /><br /> `m` *<span data-ttu-id="43aa1-155">startPoint</span><span class="sxs-lookup"><span data-stu-id="43aa1-155">startPoint</span></span>*|  
  
|<span data-ttu-id="43aa1-156">Termín</span><span class="sxs-lookup"><span data-stu-id="43aa1-156">Term</span></span>|<span data-ttu-id="43aa1-157">Popis</span><span class="sxs-lookup"><span data-stu-id="43aa1-157">Description</span></span>|  
|----------|-----------------|  
|*<span data-ttu-id="43aa1-158">startPoint</span><span class="sxs-lookup"><span data-stu-id="43aa1-158">startPoint</span></span>*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-159">Počáteční bod nový obrázek.</span><span class="sxs-lookup"><span data-stu-id="43aa1-159">The start point of a new figure.</span></span>|  
  
 <span data-ttu-id="43aa1-160">Velké `M` znamená, že `startPoint` je absolutní hodnota; malé `m` znamená, že `startPoint` je posun oproti dřívějšímu bodu, nebo (0,0), pokud žádný neexistuje.</span><span class="sxs-lookup"><span data-stu-id="43aa1-160">An uppercase `M` indicates that `startPoint` is an absolute value; a lowercase `m` indicates that `startPoint` is an offset to the previous point, or (0,0) if none exists.</span></span> <span data-ttu-id="43aa1-161">Pokud uvedete více bodů po příkazu přesunout, linie vychází do těchto bodů v případě, že jste zadali příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="43aa1-161">If you list multiple points after the move command, a line is drawn to those points though you specified the line command.</span></span>  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a><span data-ttu-id="43aa1-162">Příkazy vystavení</span><span class="sxs-lookup"><span data-stu-id="43aa1-162">Draw Commands</span></span>  
 <span data-ttu-id="43aa1-163">Příkaz vystavení se může skládat z několika příkazů tvaru.</span><span class="sxs-lookup"><span data-stu-id="43aa1-163">A draw command can consist of several shape commands.</span></span> <span data-ttu-id="43aa1-164">Nejsou k dispozici následující příkazy obrazce: řádek, vodorovnou horizontální čáru, svislá čára, kubické Bézierovy křivky, kvadratické Bézierovy křivky, smooth kubické Bézierovy křivky, smooth kvadratické Bézierovy křivky a oblouku elipsy.</span><span class="sxs-lookup"><span data-stu-id="43aa1-164">The following shape commands are available: line, horizontal line, vertical line, cubic Bezier curve, quadratic Bezier curve, smooth cubic Bezier curve, smooth quadratic Bezier curve, and elliptical arc.</span></span>  
  
 <span data-ttu-id="43aa1-165">Zadejte jednotlivé příkazy pomocí velkým nebo malým písmenem: velká písmena označení hodnoty absolutní a relativní hodnoty označení malá písmena: kontrolní body pro tento segment jsou relativní vzhledem k koncový bod v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="43aa1-165">You enter each command by using either an uppercase or a lowercase letter: uppercase letters denote absolute values and lowercase letters denote relative values: the control points for that segment are relative to the end point of the preceding example.</span></span> <span data-ttu-id="43aa1-166">Při zadávání postupně více než jednoho příkazu stejného typu, můžete vynechat příkaz duplicitní položky. například `L 100,200 300,400` je ekvivalentní `L 100,200 L 300,400`.</span><span class="sxs-lookup"><span data-stu-id="43aa1-166">When sequentially entering more than one command of the same type, you can omit the duplicate command entry; for example, `L 100,200 300,400` is equivalent to `L 100,200 L 300,400`.</span></span> <span data-ttu-id="43aa1-167">V následující tabulce jsou popsány **přesunout** a **nakreslit** příkazy.</span><span class="sxs-lookup"><span data-stu-id="43aa1-167">The following table describes the **move** and **draw** commands.</span></span>  
  
### <a name="line-command"></a><span data-ttu-id="43aa1-168">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="43aa1-168">Line Command</span></span>  
 <span data-ttu-id="43aa1-169">Vytvoří rovné čáry mezi aktuálním bodem a zadaným koncový bod.</span><span class="sxs-lookup"><span data-stu-id="43aa1-169">Creates a straight line between the current point and the specified end point.</span></span> `l 20 30` <span data-ttu-id="43aa1-170">a `L 20,30` jsou příklady platných **řádku** příkazy.</span><span class="sxs-lookup"><span data-stu-id="43aa1-170">and `L 20,30` are examples of valid **line** commands.</span></span>  
  
|<span data-ttu-id="43aa1-171">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43aa1-171">Syntax</span></span>|  
|------------|  
|`L` *<span data-ttu-id="43aa1-172">endPoint</span><span class="sxs-lookup"><span data-stu-id="43aa1-172">endPoint</span></span>*<br /><br /> <span data-ttu-id="43aa1-173">- nebo -</span><span class="sxs-lookup"><span data-stu-id="43aa1-173">- or -</span></span><br /><br /> `l` *<span data-ttu-id="43aa1-174">endPoint</span><span class="sxs-lookup"><span data-stu-id="43aa1-174">endPoint</span></span>*|  
  
|<span data-ttu-id="43aa1-175">Termín</span><span class="sxs-lookup"><span data-stu-id="43aa1-175">Term</span></span>|<span data-ttu-id="43aa1-176">Popis</span><span class="sxs-lookup"><span data-stu-id="43aa1-176">Description</span></span>|  
|----------|-----------------|  
|*<span data-ttu-id="43aa1-177">endPoint</span><span class="sxs-lookup"><span data-stu-id="43aa1-177">endPoint</span></span>*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-178">Koncový bod čáry.</span><span class="sxs-lookup"><span data-stu-id="43aa1-178">The end point of the line.</span></span>|  

<span data-ttu-id="43aa1-179">Velké `L` znamená, že `endPoint` je absolutní hodnota; malé `l` znamená, že `endPoint` je posun oproti dřívějšímu bodu, nebo (0,0), pokud žádný neexistuje.</span><span class="sxs-lookup"><span data-stu-id="43aa1-179">An uppercase `L` indicates that `endPoint` is an absolute value; a lowercase `l` indicates that `endPoint` is an offset to the previous point, or (0,0) if none exists.</span></span>

### <a name="horizontal-line-command"></a><span data-ttu-id="43aa1-180">Příkaz Vodorovná čára</span><span class="sxs-lookup"><span data-stu-id="43aa1-180">Horizontal Line Command</span></span>  
 <span data-ttu-id="43aa1-181">Vytvoří vodorovnou horizontální čáru mezi aktuálním bodem a zadaným souřadnici x.</span><span class="sxs-lookup"><span data-stu-id="43aa1-181">Creates a horizontal line between the current point and the specified x-coordinate.</span></span> `H 90` <span data-ttu-id="43aa1-182">je příklad příkazu platná vodorovnou horizontální čáru.</span><span class="sxs-lookup"><span data-stu-id="43aa1-182">is an example of a valid horizontal line command.</span></span>

|<span data-ttu-id="43aa1-183">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43aa1-183">Syntax</span></span>|  
|------------|  
|`H`  *<span data-ttu-id="43aa1-184">x</span><span class="sxs-lookup"><span data-stu-id="43aa1-184">x</span></span>*<br /><br /> <span data-ttu-id="43aa1-185">- nebo -</span><span class="sxs-lookup"><span data-stu-id="43aa1-185">- or -</span></span><br /><br /> `h`  *<span data-ttu-id="43aa1-186">x</span><span class="sxs-lookup"><span data-stu-id="43aa1-186">x</span></span>*|  
  
|<span data-ttu-id="43aa1-187">Termín</span><span class="sxs-lookup"><span data-stu-id="43aa1-187">Term</span></span>|<span data-ttu-id="43aa1-188">Popis</span><span class="sxs-lookup"><span data-stu-id="43aa1-188">Description</span></span>|  
|----------|-----------------|  
|*<span data-ttu-id="43aa1-189">x</span><span class="sxs-lookup"><span data-stu-id="43aa1-189">x</span></span>*|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-190">Souřadnice x koncového bodu čáry.</span><span class="sxs-lookup"><span data-stu-id="43aa1-190">The x-coordinate of the end point of the line.</span></span>|  
  
<span data-ttu-id="43aa1-191">Velké `H` znamená, že `x` je absolutní hodnota; malé `h` znamená, že `x` je posun oproti dřívějšímu bodu, nebo (0,0), pokud žádný neexistuje.</span><span class="sxs-lookup"><span data-stu-id="43aa1-191">An uppercase `H` indicates that `x` is an absolute value; a lowercase `h` indicates that `x` is an offset to the previous point, or (0,0) if none exists.</span></span>
  
### <a name="vertical-line-command"></a><span data-ttu-id="43aa1-192">Příkaz svislá čára</span><span class="sxs-lookup"><span data-stu-id="43aa1-192">Vertical Line Command</span></span>  
 <span data-ttu-id="43aa1-193">Vytvoří svislé čáry mezi aktuálním bodem a zadaným souřadnice na ose y.</span><span class="sxs-lookup"><span data-stu-id="43aa1-193">Creates a vertical line between the current point and the specified y-coordinate.</span></span> `v 90` <span data-ttu-id="43aa1-194">je příklad příkazu platná svislé čáry.</span><span class="sxs-lookup"><span data-stu-id="43aa1-194">is an example of a valid vertical line command.</span></span>

|<span data-ttu-id="43aa1-195">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43aa1-195">Syntax</span></span>|  
|------------|  
|`V`  *<span data-ttu-id="43aa1-196">y</span><span class="sxs-lookup"><span data-stu-id="43aa1-196">y</span></span>*<br /><br /> <span data-ttu-id="43aa1-197">- nebo -</span><span class="sxs-lookup"><span data-stu-id="43aa1-197">- or -</span></span><br /><br /> `v`  *<span data-ttu-id="43aa1-198">y</span><span class="sxs-lookup"><span data-stu-id="43aa1-198">y</span></span>*|  
  
|<span data-ttu-id="43aa1-199">Termín</span><span class="sxs-lookup"><span data-stu-id="43aa1-199">Term</span></span>|<span data-ttu-id="43aa1-200">Popis</span><span class="sxs-lookup"><span data-stu-id="43aa1-200">Description</span></span>|  
|----------|-----------------|  
|*<span data-ttu-id="43aa1-201">y</span><span class="sxs-lookup"><span data-stu-id="43aa1-201">y</span></span>*|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-202">Souřadnice y koncového bodu čáry.</span><span class="sxs-lookup"><span data-stu-id="43aa1-202">The y-coordinate of the end point of the line.</span></span>|  

<span data-ttu-id="43aa1-203">Velké `V` znamená, že `y` je absolutní hodnota; malé `v` znamená, že `y` je posun oproti dřívějšímu bodu, nebo (0,0), pokud žádný neexistuje.</span><span class="sxs-lookup"><span data-stu-id="43aa1-203">An uppercase `V` indicates that `y` is an absolute value; a lowercase `v` indicates that `y` is an offset to the previous point, or (0,0) if none exists.</span></span>  
    
### <a name="cubic-bezier-curve-command"></a><span data-ttu-id="43aa1-204">Příkaz kubické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="43aa1-204">Cubic Bezier Curve Command</span></span>  
 <span data-ttu-id="43aa1-205">Vytvoří kubické Bézierovy křivky mezi aktuálním bodem a zadaným koncový bod s použitím dva body zadaný ovládací prvek (`controlPoint`1 a `controlPoint`2).</span><span class="sxs-lookup"><span data-stu-id="43aa1-205">Creates a cubic Bezier curve between the current point and the specified end point by using the two specified control points (`controlPoint`1 and `controlPoint`2).</span></span> `C 100,200 200,400 300,200` <span data-ttu-id="43aa1-206">je příklad příkazu platná křivky.</span><span class="sxs-lookup"><span data-stu-id="43aa1-206">is an example of a valid curve command.</span></span>  
  
|<span data-ttu-id="43aa1-207">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43aa1-207">Syntax</span></span>|  
|------------|  
|`C` `controlPoint`<span data-ttu-id="43aa1-208">1`controlPoint`2</span><span class="sxs-lookup"><span data-stu-id="43aa1-208">1`controlPoint`2</span></span>`endPoint`<br /><br /> <span data-ttu-id="43aa1-209">- nebo -</span><span class="sxs-lookup"><span data-stu-id="43aa1-209">- or -</span></span><br /><br /> `c` `controlPoint`<span data-ttu-id="43aa1-210">1`controlPoint`2</span><span class="sxs-lookup"><span data-stu-id="43aa1-210">1`controlPoint`2</span></span>`endPoint`|  
  
|<span data-ttu-id="43aa1-211">Termín</span><span class="sxs-lookup"><span data-stu-id="43aa1-211">Term</span></span>|<span data-ttu-id="43aa1-212">Popis</span><span class="sxs-lookup"><span data-stu-id="43aa1-212">Description</span></span>|  
|----------|-----------------|  
|`controlPoint`<span data-ttu-id="43aa1-213">1</span><span class="sxs-lookup"><span data-stu-id="43aa1-213">1</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-214">První řídicí bod křivky, která určuje počáteční tangens křivky.</span><span class="sxs-lookup"><span data-stu-id="43aa1-214">The first control point of the curve, which determines the starting tangent of the curve.</span></span>|  
|`controlPoint`<span data-ttu-id="43aa1-215">2</span><span class="sxs-lookup"><span data-stu-id="43aa1-215">2</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-216">Druhý řídicí bod křivky, který určuje koncové tangens křivky.</span><span class="sxs-lookup"><span data-stu-id="43aa1-216">The second control point of the curve, which determines the ending tangent of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-217">Bod křivky je vykreslit.</span><span class="sxs-lookup"><span data-stu-id="43aa1-217">The point to which the curve is drawn.</span></span>|  
  
### <a name="quadratic-bezier-curve-command"></a><span data-ttu-id="43aa1-218">Příkaz kvadratické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="43aa1-218">Quadratic Bezier Curve Command</span></span>  
 <span data-ttu-id="43aa1-219">Vytvoří kvadratické Bézierovy křivky mezi aktuálním bodem a zadaným koncový bod pomocí bodu zadaný ovládací prvek (`controlPoint`).</span><span class="sxs-lookup"><span data-stu-id="43aa1-219">Creates a quadratic Bezier curve between the current point and the specified end point by using the specified control point (`controlPoint`).</span></span> `q 100,200 300,200` <span data-ttu-id="43aa1-220">je příkladem platný příkaz kvadratické Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="43aa1-220">is an example of a valid quadratic Bezier curve command.</span></span>  
  
|<span data-ttu-id="43aa1-221">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43aa1-221">Syntax</span></span>|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> <span data-ttu-id="43aa1-222">- nebo -</span><span class="sxs-lookup"><span data-stu-id="43aa1-222">- or -</span></span><br /><br /> `q` `controlPoint` `endPoint`|  
  
|<span data-ttu-id="43aa1-223">Termín</span><span class="sxs-lookup"><span data-stu-id="43aa1-223">Term</span></span>|<span data-ttu-id="43aa1-224">Popis</span><span class="sxs-lookup"><span data-stu-id="43aa1-224">Description</span></span>|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-225">Řídicí bod křivky, která určuje počáteční a koncovou tečny křivky.</span><span class="sxs-lookup"><span data-stu-id="43aa1-225">The control point of the curve, which determines the starting and ending tangents of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-226">Bod křivky je vykreslit.</span><span class="sxs-lookup"><span data-stu-id="43aa1-226">The point to which the curve is drawn.</span></span>|  
  
### <a name="smooth-cubic-bezier-curve-command"></a><span data-ttu-id="43aa1-227">Příkaz kubické Bézierovy křivky vyhlazení</span><span class="sxs-lookup"><span data-stu-id="43aa1-227">Smooth cubic Bezier curve Command</span></span>  
 <span data-ttu-id="43aa1-228">Vytvoří kubické Bézierovy křivky mezi aktuálním bodem a zadaným koncový bod.</span><span class="sxs-lookup"><span data-stu-id="43aa1-228">Creates a cubic Bezier curve between the current point and the specified end point.</span></span> <span data-ttu-id="43aa1-229">První řídicí bod je považován za reflexe druhý řídicí bod předchozího příkazu, vzhledem k aktuálnímu bodu.</span><span class="sxs-lookup"><span data-stu-id="43aa1-229">The first control point is assumed to be the reflection of the second control point of the previous command relative to the current point.</span></span> <span data-ttu-id="43aa1-230">Pokud neexistuje žádný předchozí příkaz nebo pokud předchozí příkaz nebyl kubické Bézierovy křivky příkazu nebo příkazu smooth křivky kubické Bézierovy křivky, Předpokládejme, že první řídicí bod je totožná se do aktuálního místa.</span><span class="sxs-lookup"><span data-stu-id="43aa1-230">If there is no previous command or if the previous command was not a cubic Bezier curve command or a smooth cubic Bezier curve command, assume the first control point is coincident with the current point.</span></span> <span data-ttu-id="43aa1-231">Druhý ovládací prvek bod, bod ovládacího prvku na konci křivku, je určená `controlPoint`2.</span><span class="sxs-lookup"><span data-stu-id="43aa1-231">The second control point, the control point for the end of the curve, is specified by `controlPoint`2.</span></span> <span data-ttu-id="43aa1-232">Například `S 100,200 200,300` je platný smooth kubické Bézierovy křivky příkaz.</span><span class="sxs-lookup"><span data-stu-id="43aa1-232">For example, `S 100,200 200,300` is a valid smooth cubic Bezier curve command.</span></span>  
  
|<span data-ttu-id="43aa1-233">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43aa1-233">Syntax</span></span>|  
|------------|  
|`S` `controlPoint`<span data-ttu-id="43aa1-234">2</span><span class="sxs-lookup"><span data-stu-id="43aa1-234">2</span></span>`endPoint`<br /><br /> <span data-ttu-id="43aa1-235">- nebo -</span><span class="sxs-lookup"><span data-stu-id="43aa1-235">- or -</span></span><br /><br /> `s` `controlPoint`<span data-ttu-id="43aa1-236">2</span><span class="sxs-lookup"><span data-stu-id="43aa1-236">2</span></span>`endPoint`|  
  
|<span data-ttu-id="43aa1-237">Termín</span><span class="sxs-lookup"><span data-stu-id="43aa1-237">Term</span></span>|<span data-ttu-id="43aa1-238">Popis</span><span class="sxs-lookup"><span data-stu-id="43aa1-238">Description</span></span>|  
|----------|-----------------|  
|`controlPoint`<span data-ttu-id="43aa1-239">2</span><span class="sxs-lookup"><span data-stu-id="43aa1-239">2</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-240">Řídicí bod křivky, který určuje koncové tangens křivky.</span><span class="sxs-lookup"><span data-stu-id="43aa1-240">The control point of the curve, which determines the ending tangent of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-241">Bod křivky je vykreslit.</span><span class="sxs-lookup"><span data-stu-id="43aa1-241">The point to which the curve is drawn.</span></span>|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a><span data-ttu-id="43aa1-242">Příkaz kvadratické Bézierovy křivky vyhlazení</span><span class="sxs-lookup"><span data-stu-id="43aa1-242">Smooth quadratic Bezier curve Command</span></span>  
 <span data-ttu-id="43aa1-243">Vytvoří kvadratické Bézierovy křivky mezi aktuálním bodem a zadaným koncový bod.</span><span class="sxs-lookup"><span data-stu-id="43aa1-243">Creates a quadratic Bezier curve between the current point and the specified end point.</span></span> <span data-ttu-id="43aa1-244">Řídicí bod je považován za reflexe řídicí bod předchozího příkazu, vzhledem k aktuálnímu bodu.</span><span class="sxs-lookup"><span data-stu-id="43aa1-244">The control point is assumed to be the reflection of the control point of the previous command relative to the current point.</span></span> <span data-ttu-id="43aa1-245">Pokud není žádná předchozí příkaz nebo pokud předchozí příkaz nebyl kvadratické Bézierovy křivky příkazu nebo příkazu smooth křivky kvadratické Bézierovy křivky řídicí bod je totožná se do aktuálního místa.</span><span class="sxs-lookup"><span data-stu-id="43aa1-245">If there is no previous command or if the previous command was not a quadratic Bezier curve command or a smooth quadratic Bezier curve command, the control point is coincident with the current point.</span></span>  
  
|<span data-ttu-id="43aa1-246">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43aa1-246">Syntax</span></span>|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> <span data-ttu-id="43aa1-247">- nebo -</span><span class="sxs-lookup"><span data-stu-id="43aa1-247">- or -</span></span><br /><br /> `t` `controlPoint` `endPoint`|  
  
|<span data-ttu-id="43aa1-248">Termín</span><span class="sxs-lookup"><span data-stu-id="43aa1-248">Term</span></span>|<span data-ttu-id="43aa1-249">Popis</span><span class="sxs-lookup"><span data-stu-id="43aa1-249">Description</span></span>|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-250">Řídicí bod křivky, která určuje počáteční a tečný křivky.</span><span class="sxs-lookup"><span data-stu-id="43aa1-250">The control point of the curve, which determines the starting and tangent of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-251">Bod křivky je vykreslit.</span><span class="sxs-lookup"><span data-stu-id="43aa1-251">The point to which the curve is drawn.</span></span>|  
  
### <a name="elliptical-arc-command"></a><span data-ttu-id="43aa1-252">Příkaz oblouku elipsy</span><span class="sxs-lookup"><span data-stu-id="43aa1-252">Elliptical Arc Command</span></span>  
 <span data-ttu-id="43aa1-253">Vytvoří oblouku elipsy mezi aktuálním bodem a zadaným koncový bod.</span><span class="sxs-lookup"><span data-stu-id="43aa1-253">Creates an elliptical arc between the current point and the specified end point.</span></span>  
  
|<span data-ttu-id="43aa1-254">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43aa1-254">Syntax</span></span>|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> <span data-ttu-id="43aa1-255">- nebo -</span><span class="sxs-lookup"><span data-stu-id="43aa1-255">- or -</span></span><br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|<span data-ttu-id="43aa1-256">Termín</span><span class="sxs-lookup"><span data-stu-id="43aa1-256">Term</span></span>|<span data-ttu-id="43aa1-257">Popis</span><span class="sxs-lookup"><span data-stu-id="43aa1-257">Description</span></span>|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-258">X - a y úhlu oblouku.</span><span class="sxs-lookup"><span data-stu-id="43aa1-258">The x- and y-radius of the arc.</span></span>|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-259">Otočení elipsy ve stupních.</span><span class="sxs-lookup"><span data-stu-id="43aa1-259">The rotation of the ellipse, in degrees.</span></span>|  
|`isLargeArcFlag`|<span data-ttu-id="43aa1-260">Nastavíte úhel oblouku by měl být 180stupňový rozsah s orientací na 1 nebo novější; v opačném případě nastavte na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="43aa1-260">Set to 1 if the angle of the arc should be 180 degrees or greater; otherwise, set to 0.</span></span>|  
|`sweepDirectionFlag`|<span data-ttu-id="43aa1-261">Nastavte na 1, pokud oblouku vykreslením ve směru pozitivní úhel; v opačném případě nastavte na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="43aa1-261">Set to 1 if the arc is drawn in a positive-angle direction; otherwise, set to 0.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-262">Bod na oblouk vykreslením.</span><span class="sxs-lookup"><span data-stu-id="43aa1-262">The point to which the arc is drawn.</span></span>|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a><span data-ttu-id="43aa1-263">Příkaz Zavřít</span><span class="sxs-lookup"><span data-stu-id="43aa1-263">The Close Command</span></span>  
 <span data-ttu-id="43aa1-264">Ukončí aktuální obrázek a vytvoří řádek, který spojuje bod aktuální výchozí bod na obrázku.</span><span class="sxs-lookup"><span data-stu-id="43aa1-264">Ends the current figure and creates a line that connects the current point to the starting point of the figure.</span></span> <span data-ttu-id="43aa1-265">Tento příkaz vytvoří řádku spojení (rohu). poslední segment a první segment na obrázku.</span><span class="sxs-lookup"><span data-stu-id="43aa1-265">This command creates a line-join (corner) between the last segment and the first segment of the figure.</span></span>  
  
|<span data-ttu-id="43aa1-266">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43aa1-266">Syntax</span></span>|  
|------------|  
|`Z`<br /><br /> <span data-ttu-id="43aa1-267">- nebo -</span><span class="sxs-lookup"><span data-stu-id="43aa1-267">- or -</span></span><br /><br /> `z`|  

<a name="pointsyntax"></a>   
## <a name="point-syntax"></a><span data-ttu-id="43aa1-268">Syntaxe bodu</span><span class="sxs-lookup"><span data-stu-id="43aa1-268">Point Syntax</span></span>  
 <span data-ttu-id="43aa1-269">Popisuje x - a souřadnice y bodu, kde (0; 0) je levého horního rohu.</span><span class="sxs-lookup"><span data-stu-id="43aa1-269">Describes the x- and y-coordinates of a point where (0,0) is the top left corner.</span></span>
  
|<span data-ttu-id="43aa1-270">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43aa1-270">Syntax</span></span>|  
|------------|  
|`x` `,` `y`<br /><br /> <span data-ttu-id="43aa1-271">- nebo -</span><span class="sxs-lookup"><span data-stu-id="43aa1-271">- or -</span></span><br /><br /> `x` `y`|  
  
|<span data-ttu-id="43aa1-272">Termín</span><span class="sxs-lookup"><span data-stu-id="43aa1-272">Term</span></span>|<span data-ttu-id="43aa1-273">Popis</span><span class="sxs-lookup"><span data-stu-id="43aa1-273">Description</span></span>|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-274">Souřadnice x bodu.</span><span class="sxs-lookup"><span data-stu-id="43aa1-274">The x-coordinate of the point.</span></span>|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="43aa1-275">Souřadnice y bodu.</span><span class="sxs-lookup"><span data-stu-id="43aa1-275">The y-coordinate of the point.</span></span>|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a><span data-ttu-id="43aa1-276">Speciální hodnoty</span><span class="sxs-lookup"><span data-stu-id="43aa1-276">Special Values</span></span>  
 <span data-ttu-id="43aa1-277">Místo standardní číselnou hodnotu můžete také použít následující speciální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="43aa1-277">Instead of a standard numerical value, you can also use the following special values.</span></span> <span data-ttu-id="43aa1-278">Tyto hodnoty jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="43aa1-278">These values are case-sensitive.</span></span>  
  
 <span data-ttu-id="43aa1-279">Infinity</span><span class="sxs-lookup"><span data-stu-id="43aa1-279">Infinity</span></span>  
 <span data-ttu-id="43aa1-280">Představuje <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="43aa1-280">Represents <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="43aa1-281">-Nekonečno</span><span class="sxs-lookup"><span data-stu-id="43aa1-281">-Infinity</span></span>  
 <span data-ttu-id="43aa1-282">Představuje <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="43aa1-282">Represents <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="43aa1-283">NaN</span><span class="sxs-lookup"><span data-stu-id="43aa1-283">NaN</span></span>  
 <span data-ttu-id="43aa1-284">Představuje <xref:System.Double.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="43aa1-284">Represents <xref:System.Double.NaN?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="43aa1-285">Můžete také použít vědecký zápis.</span><span class="sxs-lookup"><span data-stu-id="43aa1-285">You may also use scientific notation.</span></span> <span data-ttu-id="43aa1-286">Například `+1.e17` platná hodnota.</span><span class="sxs-lookup"><span data-stu-id="43aa1-286">For example, `+1.e17` is a valid value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43aa1-287">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43aa1-287">See also</span></span>

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.PathFigureCollection>
- [<span data-ttu-id="43aa1-288">Tvary a základní kresby v přehledu WPF</span><span class="sxs-lookup"><span data-stu-id="43aa1-288">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="43aa1-289">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="43aa1-289">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="43aa1-290">– postupy</span><span class="sxs-lookup"><span data-stu-id="43aa1-290">How-to Topics</span></span>](geometries-how-to-topics.md)
