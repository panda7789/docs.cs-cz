---
title: "Syntaxe značek cesty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9cd8f9b14f114060ebec8e336c1212d61fa19c83
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="path-markup-syntax"></a><span data-ttu-id="e6dfd-102">Syntaxe značek cesty</span><span class="sxs-lookup"><span data-stu-id="e6dfd-102">Path Markup Syntax</span></span>
<span data-ttu-id="e6dfd-103">Cesty, které jsou popsané v [tvarů a základní kreslení v přehledu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md) a [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md), ale toto téma popisuje podrobně výkonná a komplexní jazyk malý můžete zadat cestu geometrie více kompaktně pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e6dfd-103">Paths are discussed in [Shapes and Basic Drawing in WPF Overview](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md) and the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md), however, this topic describes in detail the powerful and complex mini-language you can use to specify path geometries more compactly using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a><span data-ttu-id="e6dfd-104">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6dfd-104">Prerequisites</span></span>  
 <span data-ttu-id="e6dfd-105">Zjistit, v tomto tématu, měli byste se seznámit s základní funkce <xref:System.Windows.Media.Geometry> objekty.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-105">To understand this topic, you should be familiar with the basic features of <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="e6dfd-106">Další informace najdete v tématu [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e6dfd-106">For more information, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a><span data-ttu-id="e6dfd-107">StreamGeometry a PathFigureCollection malé – jazyky</span><span class="sxs-lookup"><span data-stu-id="e6dfd-107">StreamGeometry and PathFigureCollection Mini-Languages</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="e6dfd-108">poskytuje dvě třídy, které poskytují malé jazyky pro geometrickou cesty popisující: <xref:System.Windows.Media.StreamGeometry> a <xref:System.Windows.Media.PathFigureCollection>.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-108"> provides two classes that provide mini-languages for describing geometric paths: <xref:System.Windows.Media.StreamGeometry> and <xref:System.Windows.Media.PathFigureCollection>.</span></span>  
  
-   <span data-ttu-id="e6dfd-109">Používáte <xref:System.Windows.Media.StreamGeometry> jazyk malý při nastavování vlastnosti typu <xref:System.Windows.Media.Geometry>, například <xref:System.Windows.UIElement.Clip%2A> vlastnost <xref:System.Windows.UIElement> nebo <xref:System.Windows.Shapes.Path.Data%2A> vlastnost <xref:System.Windows.Shapes.Path> element.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-109">You use the <xref:System.Windows.Media.StreamGeometry> mini-language when setting a property of type <xref:System.Windows.Media.Geometry>, such as the <xref:System.Windows.UIElement.Clip%2A> property of a <xref:System.Windows.UIElement> or the <xref:System.Windows.Shapes.Path.Data%2A> property of a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="e6dfd-110">Následující příklad používá syntaxi atributů k vytvoření <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-110">The following example uses attribute syntax to create a <xref:System.Windows.Media.StreamGeometry>.</span></span>  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   <span data-ttu-id="e6dfd-111">Můžete použít <xref:System.Windows.Media.PathFigureCollection> jazyk malý při nastavení <xref:System.Windows.Media.PathGeometry.Figures%2A> vlastnost <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-111">You use the <xref:System.Windows.Media.PathFigureCollection> mini-language when setting the <xref:System.Windows.Media.PathGeometry.Figures%2A> property of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="e6dfd-112">Následující příklad používá syntaxi atributů k vytvoření <xref:System.Windows.Media.PathFigureCollection> pro <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-112">The following example uses a attribute syntax to create a <xref:System.Windows.Media.PathFigureCollection> for a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 <span data-ttu-id="e6dfd-113">Jak je vidět v předchozích příkladech jsou velmi podobné dvou malé jazyků.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-113">As you can see from the preceding examples, the two mini-languages are very similar.</span></span> <span data-ttu-id="e6dfd-114">Vždy je možné použít <xref:System.Windows.Media.PathGeometry> v každé situaci, kde můžete použít <xref:System.Windows.Media.StreamGeometry>; Ano která mám použít?</span><span class="sxs-lookup"><span data-stu-id="e6dfd-114">It's always possible to use a <xref:System.Windows.Media.PathGeometry> in any situation where you could use a <xref:System.Windows.Media.StreamGeometry>; so which one should you use?</span></span> <span data-ttu-id="e6dfd-115">Použít <xref:System.Windows.Media.StreamGeometry> použít při nemusíte po vytvoření změňte cestu <xref:System.Windows.Media.PathGeometry> Pokud potřebujete změnit cestu.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-115">Use a <xref:System.Windows.Media.StreamGeometry> when you don't need to modify the path after creating it; use a <xref:System.Windows.Media.PathGeometry> if you do need to modify the path.</span></span>  
  
 <span data-ttu-id="e6dfd-116">Další informace o rozdílech mezi <xref:System.Windows.Media.PathGeometry> a <xref:System.Windows.Media.StreamGeometry> objekty, najdete [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e6dfd-116">For more information about the differences between <xref:System.Windows.Media.PathGeometry> and <xref:System.Windows.Media.StreamGeometry> objects, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
### <a name="a-note-about-white-space"></a><span data-ttu-id="e6dfd-117">Poznámka o mezer</span><span class="sxs-lookup"><span data-stu-id="e6dfd-117">A Note about White Space</span></span>  
 <span data-ttu-id="e6dfd-118">Jako stručný výtah a jedna mezera se zobrazí v části syntaxe, které následují, ale více prostory jsou přijatelné taky všude, kde se zobrazí a jedna mezera.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-118">For brevity, a single space is shown in the syntax sections that follow, but multiple spaces are also acceptable wherever a single space is shown.</span></span>  
  
 <span data-ttu-id="e6dfd-119">Dvou čísel nemusí ve skutečnosti oddělených čárkou nebo prázdný znak, ale to provést pouze po jednoznačným výsledný řetězec.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-119">Two numbers don’t actually have to be separated by a comma or whitespace, but this can only be done when the resulting string is unambiguous.</span></span> <span data-ttu-id="e6dfd-120">Například `2..3` je ve skutečnosti dvě čísla: "2".</span><span class="sxs-lookup"><span data-stu-id="e6dfd-120">For instance, `2..3` is actually two numbers: "2."</span></span> <span data-ttu-id="e6dfd-121">A ". 3".</span><span class="sxs-lookup"><span data-stu-id="e6dfd-121">And ".3".</span></span> <span data-ttu-id="e6dfd-122">Podobně `2-3` je "2" a "-3".</span><span class="sxs-lookup"><span data-stu-id="e6dfd-122">Similarly, `2-3` is "2" and "-3".</span></span> <span data-ttu-id="e6dfd-123">Mezery nejsou vyžadovány před nebo po příkazy, buď.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-123">Spaces are not required before or after commands, either.</span></span>  
  
### <a name="syntax"></a><span data-ttu-id="e6dfd-124">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6dfd-124">Syntax</span></span>  
 <span data-ttu-id="e6dfd-125">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Atribut použití syntaxe <xref:System.Windows.Media.StreamGeometry> se skládá z volitelný <xref:System.Windows.Media.FillRule> hodnotu a jednu nebo více obrázek popisy.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-125">The [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] attribute usage syntax for a <xref:System.Windows.Media.StreamGeometry> is composed of an optional <xref:System.Windows.Media.FillRule> value and one or more figure descriptions.</span></span>  
  
|<span data-ttu-id="e6dfd-126">Použití atributu StreamGeometry XAML</span><span class="sxs-lookup"><span data-stu-id="e6dfd-126">StreamGeometry XAML Attribute Usage</span></span>|  
|-----------------------------------------|  
|<span data-ttu-id="e6dfd-127">`<`*objekt* *vlastnost* `="`[ `fillRule`] `figureDescription`[ `figureDescription`] *`" ... />`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-127">`<` *object* *property* `="`[ `fillRule`] `figureDescription`[ `figureDescription`]* `" ... />`</span></span>|  
  
 <span data-ttu-id="e6dfd-128">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Atribut použití syntaxe <xref:System.Windows.Media.PathFigureCollection> se skládá z jednoho nebo více popisy obrázek.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-128">The [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] attribute usage syntax for a <xref:System.Windows.Media.PathFigureCollection> is composed of one or more figure descriptions.</span></span>  
  
|<span data-ttu-id="e6dfd-129">Použití atributu PathFigureCollection XAML</span><span class="sxs-lookup"><span data-stu-id="e6dfd-129">PathFigureCollection XAML Attribute Usage</span></span>|  
|-----------------------------------------------|  
|<span data-ttu-id="e6dfd-130">`<`*objekt* *vlastnost* `="` `figureDescription`[ `figureDescription`] *`" ... />`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-130">`<` *object* *property* `="` `figureDescription`[ `figureDescription`]* `" ... />`</span></span>|  
  
|<span data-ttu-id="e6dfd-131">Termín</span><span class="sxs-lookup"><span data-stu-id="e6dfd-131">Term</span></span>|<span data-ttu-id="e6dfd-132">Popis</span><span class="sxs-lookup"><span data-stu-id="e6dfd-132">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="e6dfd-133">*fillRule*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-133">*fillRule*</span></span>|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-134">Určuje, zda <xref:System.Windows.Media.StreamGeometry> používá <xref:System.Windows.Media.FillRule.EvenOdd> nebo <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-134">Specifies whether the <xref:System.Windows.Media.StreamGeometry> uses the <xref:System.Windows.Media.FillRule.EvenOdd> or <xref:System.Windows.Media.FillRule.Nonzero><xref:System.Windows.Media.PathGeometry.FillRule%2A>.</span></span><br /><br /> <span data-ttu-id="e6dfd-135">-   `F0`Určuje, <xref:System.Windows.Media.FillRule.EvenOdd> výplně pravidlo.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-135">-   `F0` specifies the <xref:System.Windows.Media.FillRule.EvenOdd> fill rule.</span></span><br /><span data-ttu-id="e6dfd-136">-   `F1`Určuje, <xref:System.Windows.Media.FillRule.Nonzero> výplně pravidlo.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-136">-   `F1` specifies the <xref:System.Windows.Media.FillRule.Nonzero> fill rule.</span></span><br /><br /> <span data-ttu-id="e6dfd-137">Pokud není tento příkaz, na dílčí cestu použije výchozí chování, což je <xref:System.Windows.Media.FillRule.EvenOdd>.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-137">If you omit this command, the subpath uses the default behavior, which is <xref:System.Windows.Media.FillRule.EvenOdd>.</span></span> <span data-ttu-id="e6dfd-138">Pokud zadáte tento příkaz, musíte ji nejprve umístit.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-138">If you specify this command, you must place it first.</span></span>|  
|<span data-ttu-id="e6dfd-139">*figureDescription*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-139">*figureDescription*</span></span>|<span data-ttu-id="e6dfd-140">Obrázek, tvořený move příkazu kreslení příkazy a volitelný příkaz Zavřít.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-140">A figure composed of a move command, draw commands, and an optional close command.</span></span><br /><br /> <span data-ttu-id="e6dfd-141">`moveCommand` `drawCommands`  `[` `closeCommand` `]`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-141">`moveCommand` `drawCommands`  `[` `closeCommand` `]`</span></span>|  
|<span data-ttu-id="e6dfd-142">*moveCommand*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-142">*moveCommand*</span></span>|<span data-ttu-id="e6dfd-143">Přesunutí příkaz, který určuje počáteční bod na obrázku.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-143">A move command that specifies the start point of the figure.</span></span> <span data-ttu-id="e6dfd-144">Najdete v článku [příkaz přesunout](#themovecommand) části.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-144">See the [Move Command](#themovecommand) section.</span></span>|  
|<span data-ttu-id="e6dfd-145">*drawCommands*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-145">*drawCommands*</span></span>|<span data-ttu-id="e6dfd-146">Jeden nebo více kreslení příkazy, které popisují obsah na obrázku.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-146">One or more drawing commands that describe the figure's contents.</span></span> <span data-ttu-id="e6dfd-147">Najdete v článku [kreslení příkazy](#drawcommands) části.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-147">See the [Draw Commands](#drawcommands) section.</span></span>|  
|<span data-ttu-id="e6dfd-148">*closeCommand*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-148">*closeCommand*</span></span>|<span data-ttu-id="e6dfd-149">Volitelné zavřít příkaz, který zavře obrázek.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-149">An optional close command that closes figure.</span></span> <span data-ttu-id="e6dfd-150">Najdete v článku [zavřít příkaz](#closecommand) části.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-150">See the [Close Command](#closecommand) section.</span></span>|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a><span data-ttu-id="e6dfd-151">Příkaz přesunout</span><span class="sxs-lookup"><span data-stu-id="e6dfd-151">Move Command</span></span>  
 <span data-ttu-id="e6dfd-152">Určuje počáteční bod nový obrázek.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-152">Specifies the start point of a new figure.</span></span>  
  
|<span data-ttu-id="e6dfd-153">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6dfd-153">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="e6dfd-154">`M`*startPoint*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-154">`M` *startPoint*</span></span><br /><br /> <span data-ttu-id="e6dfd-155">- nebo -</span><span class="sxs-lookup"><span data-stu-id="e6dfd-155">- or -</span></span><br /><br /> <span data-ttu-id="e6dfd-156">`m`*startPoint*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-156">`m` *startPoint*</span></span>|  
  
|<span data-ttu-id="e6dfd-157">Termín</span><span class="sxs-lookup"><span data-stu-id="e6dfd-157">Term</span></span>|<span data-ttu-id="e6dfd-158">Popis</span><span class="sxs-lookup"><span data-stu-id="e6dfd-158">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="e6dfd-159">*startPoint*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-159">*startPoint*</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-160">Počáteční bod nový obrázek.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-160">The start point of a new figure.</span></span>|  
  
 <span data-ttu-id="e6dfd-161">Velká `M` znamená, že `startPoint` jako absolutní hodnota; jedno malé písmeno `m` znamená, že `startPoint` je posun předchozího bodu nebo (0,0), pokud žádný neexistuje.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-161">An uppercase `M` indicates that `startPoint` is an absolute value; a lowercase `m` indicates that `startPoint` is an offset to the previous point, or (0,0) if none exists.</span></span> <span data-ttu-id="e6dfd-162">Pokud uvedete více bodů po příkaz přesunutí, řádek vykreslením do těchto bodů, když jste zadali příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-162">If you list multiple points after the move command, a line is drawn to those points though you specified the line command.</span></span>  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a><span data-ttu-id="e6dfd-163">Kreslení příkazy</span><span class="sxs-lookup"><span data-stu-id="e6dfd-163">Draw Commands</span></span>  
 <span data-ttu-id="e6dfd-164">Příkaz kreslení se může skládat z několika příkazy tvaru.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-164">A draw command can consist of several shape commands.</span></span> <span data-ttu-id="e6dfd-165">Jsou k dispozici následující příkazy tvar: řádku, vodorovném řádku, svislá čára, krychlový Bézierovu křivku, kvadratické Bézierovy křivky, technologie smooth krychlový Bézierovu křivku, technologie smooth kvadratické Bézierovy křivky a eliptické oblouk.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-165">The following shape commands are available: line, horizontal line, vertical line, cubic Bezier curve, quadratic Bezier curve, smooth cubic Bezier curve, smooth quadratic Bezier curve, and elliptical arc.</span></span>  
  
 <span data-ttu-id="e6dfd-166">Zadejte každý příkaz pomocí velké nebo malé písmeno: velká písmena označují absolutní hodnoty a malá písmena označují relativní hodnoty: kontrolní body pro tento segment jsou relativní vzhledem k koncového bodu v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-166">You enter each command by using either an uppercase or a lowercase letter: uppercase letters denote absolute values and lowercase letters denote relative values: the control points for that segment are relative to the end point of the preceding example.</span></span> <span data-ttu-id="e6dfd-167">Při zadávání postupně víc než jednoho příkazu stejného typu, můžete vynechat příkaz duplicitní položky. například `L 100,200 300,400` je ekvivalentní `L 100,200 L 300,400`.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-167">When sequentially entering more than one command of the same type, you can omit the duplicate command entry; for example, `L 100,200 300,400` is equivalent to `L 100,200 L 300,400`.</span></span> <span data-ttu-id="e6dfd-168">V následující tabulce jsou popsány **přesunout** a **kreslení** příkazy.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-168">The following table describes the **move** and **draw** commands.</span></span>  
  
### <a name="line-command"></a><span data-ttu-id="e6dfd-169">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="e6dfd-169">Line Command</span></span>  
 <span data-ttu-id="e6dfd-170">Vytvoří přímku mezi bodem aktuální a zadaný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-170">Creates a straight line between the current point and the specified end point.</span></span> <span data-ttu-id="e6dfd-171">`l 20 30`a `L 20,30` jsou příklady platný **řádku** příkazy.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-171">`l 20 30` and `L 20,30` are examples of valid **line** commands.</span></span>  
  
|<span data-ttu-id="e6dfd-172">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6dfd-172">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="e6dfd-173">`L`*koncový bod*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-173">`L` *endPoint*</span></span><br /><br /> <span data-ttu-id="e6dfd-174">- nebo -</span><span class="sxs-lookup"><span data-stu-id="e6dfd-174">- or -</span></span><br /><br /> <span data-ttu-id="e6dfd-175">`l`*koncový bod*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-175">`l` *endPoint*</span></span>|  
  
|<span data-ttu-id="e6dfd-176">Termín</span><span class="sxs-lookup"><span data-stu-id="e6dfd-176">Term</span></span>|<span data-ttu-id="e6dfd-177">Popis</span><span class="sxs-lookup"><span data-stu-id="e6dfd-177">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="e6dfd-178">*koncový bod*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-178">*endPoint*</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-179">Koncový bod řádku.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-179">The end point of the line.</span></span>|  

<span data-ttu-id="e6dfd-180">Velká `L` znamená, že `endPoint` jako absolutní hodnota; jedno malé písmeno `l` znamená, že `endPoint` je posun předchozího bodu nebo (0,0), pokud žádný neexistuje.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-180">An uppercase `L` indicates that `endPoint` is an absolute value; a lowercase `l` indicates that `endPoint` is an offset to the previous point, or (0,0) if none exists.</span></span>

### <a name="horizontal-line-command"></a><span data-ttu-id="e6dfd-181">Příkaz Vodorovná čára</span><span class="sxs-lookup"><span data-stu-id="e6dfd-181">Horizontal Line Command</span></span>  
 <span data-ttu-id="e6dfd-182">Vytvoří na vodorovném řádku mezi bodem aktuální a zadaný souřadnice x.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-182">Creates a horizontal line between the current point and the specified x-coordinate.</span></span> <span data-ttu-id="e6dfd-183">`H 90`je příklad příkazu platný vodorovném řádku.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-183">`H 90` is an example of a valid horizontal line command.</span></span>

  
|<span data-ttu-id="e6dfd-184">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6dfd-184">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="e6dfd-185">`H`  *x*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-185">`H`  *x*</span></span><br /><br /> <span data-ttu-id="e6dfd-186">- nebo -</span><span class="sxs-lookup"><span data-stu-id="e6dfd-186">- or -</span></span><br /><br /> <span data-ttu-id="e6dfd-187">`h`  *x*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-187">`h`  *x*</span></span>|  
  
|<span data-ttu-id="e6dfd-188">Termín</span><span class="sxs-lookup"><span data-stu-id="e6dfd-188">Term</span></span>|<span data-ttu-id="e6dfd-189">Popis</span><span class="sxs-lookup"><span data-stu-id="e6dfd-189">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="e6dfd-190">*x*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-190">*x*</span></span>|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-191">Souřadnice x koncového bodu čáry.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-191">The x-coordinate of the end point of the line.</span></span>|  
  
<span data-ttu-id="e6dfd-192">Velká `H` znamená, že `x` jako absolutní hodnota; jedno malé písmeno `h` znamená, že `x` je posun předchozího bodu nebo (0,0), pokud žádný neexistuje.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-192">An uppercase `H` indicates that `x` is an absolute value; a lowercase `h` indicates that `x` is an offset to the previous point, or (0,0) if none exists.</span></span>
  
### <a name="vertical-line-command"></a><span data-ttu-id="e6dfd-193">Příkaz svislá čára</span><span class="sxs-lookup"><span data-stu-id="e6dfd-193">Vertical Line Command</span></span>  
 <span data-ttu-id="e6dfd-194">Vytvoří svislice mezi bodem aktuální a zadaný souřadnici y.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-194">Creates a vertical line between the current point and the specified y-coordinate.</span></span> <span data-ttu-id="e6dfd-195">`v 90`je příklad příkazu platný svislá čára.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-195">`v 90` is an example of a valid vertical line command.</span></span>

  
|<span data-ttu-id="e6dfd-196">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6dfd-196">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="e6dfd-197">`V`  *y*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-197">`V`  *y*</span></span><br /><br /> <span data-ttu-id="e6dfd-198">- nebo -</span><span class="sxs-lookup"><span data-stu-id="e6dfd-198">- or -</span></span><br /><br /> <span data-ttu-id="e6dfd-199">`v`  *y*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-199">`v`  *y*</span></span>|  
  
|<span data-ttu-id="e6dfd-200">Termín</span><span class="sxs-lookup"><span data-stu-id="e6dfd-200">Term</span></span>|<span data-ttu-id="e6dfd-201">Popis</span><span class="sxs-lookup"><span data-stu-id="e6dfd-201">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="e6dfd-202">*y*</span><span class="sxs-lookup"><span data-stu-id="e6dfd-202">*y*</span></span>|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-203">Souřadnice y koncového bodu čáry.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-203">The y-coordinate of the end point of the line.</span></span>|  

<span data-ttu-id="e6dfd-204">Velká `V` znamená, že `y` jako absolutní hodnota; jedno malé písmeno `v` znamená, že `y` je posun předchozího bodu nebo (0,0), pokud žádný neexistuje.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-204">An uppercase `V` indicates that `y` is an absolute value; a lowercase `v` indicates that `y` is an offset to the previous point, or (0,0) if none exists.</span></span>  
    
### <a name="cubic-bezier-curve-command"></a><span data-ttu-id="e6dfd-205">Příkaz krychlový Bézierovu křivku</span><span class="sxs-lookup"><span data-stu-id="e6dfd-205">Cubic Bezier Curve Command</span></span>  
 <span data-ttu-id="e6dfd-206">Vytvoří krychlový Bézierovu křivku mezi bodem aktuální a zadaný koncový bod pomocí dva body ovládací prvek (`controlPoint`1 a `controlPoint`2).</span><span class="sxs-lookup"><span data-stu-id="e6dfd-206">Creates a cubic Bezier curve between the current point and the specified end point by using the two specified control points (`controlPoint`1 and `controlPoint`2).</span></span> <span data-ttu-id="e6dfd-207">`C 100,200 200,400 300,200`je příkladem křivky platný příkaz.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-207">`C 100,200 200,400 300,200` is an example of a valid curve command.</span></span>  
  
|<span data-ttu-id="e6dfd-208">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6dfd-208">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="e6dfd-209">`C` `controlPoint`1`controlPoint`2`endPoint`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-209">`C` `controlPoint`1`controlPoint`2`endPoint`</span></span><br /><br /> <span data-ttu-id="e6dfd-210">- nebo -</span><span class="sxs-lookup"><span data-stu-id="e6dfd-210">- or -</span></span><br /><br /> <span data-ttu-id="e6dfd-211">`c` `controlPoint`1`controlPoint`2`endPoint`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-211">`c` `controlPoint`1`controlPoint`2`endPoint`</span></span>|  
  
|<span data-ttu-id="e6dfd-212">Termín</span><span class="sxs-lookup"><span data-stu-id="e6dfd-212">Term</span></span>|<span data-ttu-id="e6dfd-213">Popis</span><span class="sxs-lookup"><span data-stu-id="e6dfd-213">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="e6dfd-214">`controlPoint`1</span><span class="sxs-lookup"><span data-stu-id="e6dfd-214">`controlPoint`1</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-215">První řídicí bod křivky, která určuje počáteční tangens křivku.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-215">The first control point of the curve, which determines the starting tangent of the curve.</span></span>|  
|<span data-ttu-id="e6dfd-216">`controlPoint`2</span><span class="sxs-lookup"><span data-stu-id="e6dfd-216">`controlPoint`2</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-217">Druhý řídicí bod křivky, která určuje koncovou tangens křivku.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-217">The second control point of the curve, which determines the ending tangent of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-218">Bod na křivku vykreslením.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-218">The point to which the curve is drawn.</span></span>|  
  
### <a name="quadratic-bezier-curve-command"></a><span data-ttu-id="e6dfd-219">Příkaz kvadratické Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="e6dfd-219">Quadratic Bezier Curve Command</span></span>  
 <span data-ttu-id="e6dfd-220">Vytvoří kvadratické Bézierovy křivky mezi bodem aktuální a zadaný koncový bod pomocí zadané řídicí bod (`controlPoint`).</span><span class="sxs-lookup"><span data-stu-id="e6dfd-220">Creates a quadratic Bezier curve between the current point and the specified end point by using the specified control point (`controlPoint`).</span></span> <span data-ttu-id="e6dfd-221">`q 100,200 300,200`je příkladem platný příkaz kvadratické Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-221">`q 100,200 300,200` is an example of a valid quadratic Bezier curve command.</span></span>  
  
|<span data-ttu-id="e6dfd-222">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6dfd-222">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="e6dfd-223">`Q` `controlPoint` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-223">`Q` `controlPoint` `endPoint`</span></span><br /><br /> <span data-ttu-id="e6dfd-224">- nebo -</span><span class="sxs-lookup"><span data-stu-id="e6dfd-224">- or -</span></span><br /><br /> <span data-ttu-id="e6dfd-225">`q` `controlPoint` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-225">`q` `controlPoint` `endPoint`</span></span>|  
  
|<span data-ttu-id="e6dfd-226">Termín</span><span class="sxs-lookup"><span data-stu-id="e6dfd-226">Term</span></span>|<span data-ttu-id="e6dfd-227">Popis</span><span class="sxs-lookup"><span data-stu-id="e6dfd-227">Description</span></span>|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-228">Řídicí bod křivky, která určuje počáteční a koncovou tangent křivky.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-228">The control point of the curve, which determines the starting and ending tangents of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-229">Bod na křivku vykreslením.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-229">The point to which the curve is drawn.</span></span>|  
  
### <a name="smooth-cubic-bezier-curve-command"></a><span data-ttu-id="e6dfd-230">Funkce Smooth krychlový Bézierovu křivku příkaz</span><span class="sxs-lookup"><span data-stu-id="e6dfd-230">Smooth cubic Bezier curve Command</span></span>  
 <span data-ttu-id="e6dfd-231">Vytvoří krychlový Bézierovu křivku mezi bodem aktuální a zadaný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-231">Creates a cubic Bezier curve between the current point and the specified end point.</span></span> <span data-ttu-id="e6dfd-232">První řídicí bod se považuje za odraz druhý řídicí bod předchozí příkaz relativně k aktuálnímu bodu.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-232">The first control point is assumed to be the reflection of the second control point of the previous command relative to the current point.</span></span> <span data-ttu-id="e6dfd-233">Pokud není žádná předchozí příkaz nebo pokud nebyla předchozí příkaz krychlový příkaz Bézierovy křivky nebo smooth krychlový příkaz Bézierovy křivky, předpokládají, že první řídicí bod je totožná se aktuálnímu bodu.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-233">If there is no previous command or if the previous command was not a cubic Bezier curve command or a smooth cubic Bezier curve command, assume the first control point is coincident with the current point.</span></span> <span data-ttu-id="e6dfd-234">Druhý řídicí bod, kontrolního bodu pro element end křivky, je zadána `controlPoint`2.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-234">The second control point, the control point for the end of the curve, is specified by `controlPoint`2.</span></span> <span data-ttu-id="e6dfd-235">Například `S 100,200 200,300` je platný smooth krychlový Bézierovy křivky příkaz.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-235">For example, `S 100,200 200,300` is a valid smooth cubic Bezier curve command.</span></span>  
  
|<span data-ttu-id="e6dfd-236">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6dfd-236">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="e6dfd-237">`S` `controlPoint`2`endPoint`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-237">`S` `controlPoint`2`endPoint`</span></span><br /><br /> <span data-ttu-id="e6dfd-238">- nebo -</span><span class="sxs-lookup"><span data-stu-id="e6dfd-238">- or -</span></span><br /><br /> <span data-ttu-id="e6dfd-239">`s` `controlPoint`2`endPoint`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-239">`s` `controlPoint`2`endPoint`</span></span>|  
  
|<span data-ttu-id="e6dfd-240">Termín</span><span class="sxs-lookup"><span data-stu-id="e6dfd-240">Term</span></span>|<span data-ttu-id="e6dfd-241">Popis</span><span class="sxs-lookup"><span data-stu-id="e6dfd-241">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="e6dfd-242">`controlPoint`2</span><span class="sxs-lookup"><span data-stu-id="e6dfd-242">`controlPoint`2</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-243">Řídicí bod křivky, která určuje koncovou tangens křivku.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-243">The control point of the curve, which determines the ending tangent of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-244">Bod na křivku vykreslením.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-244">The point to which the curve is drawn.</span></span>|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a><span data-ttu-id="e6dfd-245">Funkce Smooth kvadratické Bézierovy křivky příkaz</span><span class="sxs-lookup"><span data-stu-id="e6dfd-245">Smooth quadratic Bezier curve Command</span></span>  
 <span data-ttu-id="e6dfd-246">Vytvoří kvadratické Bézierovy křivky mezi bodem aktuální a zadaný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-246">Creates a quadratic Bezier curve between the current point and the specified end point.</span></span> <span data-ttu-id="e6dfd-247">Řídicí bod se považuje za odraz řídicího bodu pro předchozí příkaz relativně k aktuálnímu bodu.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-247">The control point is assumed to be the reflection of the control point of the previous command relative to the current point.</span></span> <span data-ttu-id="e6dfd-248">Pokud není žádná předchozí příkaz nebo pokud nebyla předchozí příkaz kvadratické Bézierovy křivky příkaz nebo smooth kvadratické Bézierovy křivky příkaz, je totožnou s bodem aktuální řídicí bod.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-248">If there is no previous command or if the previous command was not a quadratic Bezier curve command or a smooth quadratic Bezier curve command, the control point is coincident with the current point.</span></span>  
  
|<span data-ttu-id="e6dfd-249">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6dfd-249">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="e6dfd-250">`T` `controlPoint` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-250">`T` `controlPoint` `endPoint`</span></span><br /><br /> <span data-ttu-id="e6dfd-251">- nebo -</span><span class="sxs-lookup"><span data-stu-id="e6dfd-251">- or -</span></span><br /><br /> <span data-ttu-id="e6dfd-252">`t` `controlPoint` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-252">`t` `controlPoint` `endPoint`</span></span>|  
  
|<span data-ttu-id="e6dfd-253">Termín</span><span class="sxs-lookup"><span data-stu-id="e6dfd-253">Term</span></span>|<span data-ttu-id="e6dfd-254">Popis</span><span class="sxs-lookup"><span data-stu-id="e6dfd-254">Description</span></span>|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-255">Řídicí bod křivky, která určuje počáteční a tečný křivky.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-255">The control point of the curve, which determines the starting and tangent of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-256">Bod na křivku vykreslením.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-256">The point to which the curve is drawn.</span></span>|  
  
### <a name="elliptical-arc-command"></a><span data-ttu-id="e6dfd-257">Příkaz eliptické oblouk</span><span class="sxs-lookup"><span data-stu-id="e6dfd-257">Elliptical Arc Command</span></span>  
 <span data-ttu-id="e6dfd-258">Vytvoří oblouk eliptické mezi bodem aktuální a zadaný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-258">Creates an elliptical arc between the current point and the specified end point.</span></span>  
  
|<span data-ttu-id="e6dfd-259">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6dfd-259">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="e6dfd-260">`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-260">`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`</span></span><br /><br /> <span data-ttu-id="e6dfd-261">- nebo -</span><span class="sxs-lookup"><span data-stu-id="e6dfd-261">- or -</span></span><br /><br /> <span data-ttu-id="e6dfd-262">`a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-262">`a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`</span></span>|  
  
|<span data-ttu-id="e6dfd-263">Termín</span><span class="sxs-lookup"><span data-stu-id="e6dfd-263">Term</span></span>|<span data-ttu-id="e6dfd-264">Popis</span><span class="sxs-lookup"><span data-stu-id="e6dfd-264">Description</span></span>|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-265">Hodnota x - a y úhlu oblouk.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-265">The x- and y-radius of the arc.</span></span>|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-266">Otočení se třemi tečkami ve stupních.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-266">The rotation of the ellipse, in degrees.</span></span>|  
|`isLargeArcFlag`|<span data-ttu-id="e6dfd-267">Pokud úhel oblouku by měla být 180 stupňů nastavena na hodnotu 1 nebo novější; jinak hodnota nastavena na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-267">Set to 1 if the angle of the arc should be 180 degrees or greater; otherwise, set to 0.</span></span>|  
|`sweepDirectionFlag`|<span data-ttu-id="e6dfd-268">Nastavena na hodnotu 1, pokud oblouk vykreslením kladnou úhel směrem; jinak hodnota nastavena na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-268">Set to 1 if the arc is drawn in a positive-angle direction; otherwise, set to 0.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-269">Bod na oblouk vykreslením.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-269">The point to which the arc is drawn.</span></span>|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a><span data-ttu-id="e6dfd-270">Příkaz Zavřít</span><span class="sxs-lookup"><span data-stu-id="e6dfd-270">The Close Command</span></span>  
 <span data-ttu-id="e6dfd-271">Končí na aktuální obrázku a vytvoří řádek, který spojuje bod aktuální výchozí bod na obrázku.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-271">Ends the current figure and creates a line that connects the current point to the starting point of the figure.</span></span> <span data-ttu-id="e6dfd-272">Tento příkaz vytvoří řádku spojení (rohu) mezi poslední segment a první segment na obrázku.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-272">This command creates a line-join (corner) between the last segment and the first segment of the figure.</span></span>  
  
|<span data-ttu-id="e6dfd-273">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6dfd-273">Syntax</span></span>|  
|------------|  
|`Z`<br /><br /> <span data-ttu-id="e6dfd-274">- nebo -</span><span class="sxs-lookup"><span data-stu-id="e6dfd-274">- or -</span></span><br /><br /> `z`|  

<a name="pointsyntax"></a>   
## <a name="point-syntax"></a><span data-ttu-id="e6dfd-275">Syntaxe bodu</span><span class="sxs-lookup"><span data-stu-id="e6dfd-275">Point Syntax</span></span>  
 <span data-ttu-id="e6dfd-276">Popisuje a y souřadnice x bodu, kde (0,0) je levého horního rohu.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-276">Describes the x- and y-coordinates of a point where (0,0) is the top left corner.</span></span>
  
|<span data-ttu-id="e6dfd-277">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6dfd-277">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="e6dfd-278">`x` `,` `y`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-278">`x` `,` `y`</span></span><br /><br /> <span data-ttu-id="e6dfd-279">- nebo -</span><span class="sxs-lookup"><span data-stu-id="e6dfd-279">- or -</span></span><br /><br /> <span data-ttu-id="e6dfd-280">`x``y`</span><span class="sxs-lookup"><span data-stu-id="e6dfd-280">`x` `y`</span></span>|  
  
|<span data-ttu-id="e6dfd-281">Termín</span><span class="sxs-lookup"><span data-stu-id="e6dfd-281">Term</span></span>|<span data-ttu-id="e6dfd-282">Popis</span><span class="sxs-lookup"><span data-stu-id="e6dfd-282">Description</span></span>|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-283">Souřadnice x bodu.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-283">The x-coordinate of the point.</span></span>|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="e6dfd-284">Souřadnice y bodu.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-284">The y-coordinate of the point.</span></span>|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a><span data-ttu-id="e6dfd-285">Speciální hodnoty</span><span class="sxs-lookup"><span data-stu-id="e6dfd-285">Special Values</span></span>  
 <span data-ttu-id="e6dfd-286">Místo standardní číselnou hodnotu můžete také použít následující zvláštní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-286">Instead of a standard numerical value, you can also use the following special values.</span></span> <span data-ttu-id="e6dfd-287">Tyto hodnoty jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-287">These values are case-sensitive.</span></span>  
  
 <span data-ttu-id="e6dfd-288">Infinity</span><span class="sxs-lookup"><span data-stu-id="e6dfd-288">Infinity</span></span>  
 <span data-ttu-id="e6dfd-289">Představuje <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-289">Represents <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="e6dfd-290">-Infinity</span><span class="sxs-lookup"><span data-stu-id="e6dfd-290">-Infinity</span></span>  
 <span data-ttu-id="e6dfd-291">Představuje <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-291">Represents <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="e6dfd-292">NaN</span><span class="sxs-lookup"><span data-stu-id="e6dfd-292">NaN</span></span>  
 <span data-ttu-id="e6dfd-293">Představuje <xref:System.Double.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-293">Represents <xref:System.Double.NaN?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="e6dfd-294">Můžete také používat exponenciální notace.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-294">You may also use scientific notation.</span></span> <span data-ttu-id="e6dfd-295">Například `+1.e17` platná hodnota.</span><span class="sxs-lookup"><span data-stu-id="e6dfd-295">For example, `+1.e17` is a valid value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6dfd-296">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6dfd-296">See Also</span></span>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.PathFigureCollection>  
 [<span data-ttu-id="e6dfd-297">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="e6dfd-297">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="e6dfd-298">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="e6dfd-298">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="e6dfd-299">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="e6dfd-299">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)
