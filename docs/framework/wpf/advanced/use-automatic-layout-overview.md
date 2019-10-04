---
title: Přehled automatického rozložení
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 0253c57f080705b648d9f416368d0fe974ac83ab
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834672"
---
# <a name="use-automatic-layout-overview"></a><span data-ttu-id="f9b9d-102">Přehled automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="f9b9d-102">Use Automatic Layout Overview</span></span>

<span data-ttu-id="f9b9d-103">Toto téma obsahuje pokyny pro vývojáře, jak psát aplikace [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] s možností lokalizace [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9b9d-103">This topic introduces guidelines for developers on how to write [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications with localizable [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span></span> <span data-ttu-id="f9b9d-104">V minulosti byla lokalizace uživatelského rozhraní časově náročná.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-104">In the past, localization of a UI was a time consuming process.</span></span> <span data-ttu-id="f9b9d-105">Každý jazyk, pro který bylo uživatelské rozhraní upraveno, aby vyžadovalo úpravu pixelu podle pixelu.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-105">Each language that the UI was adapted for required a pixel by pixel adjustment.</span></span> <span data-ttu-id="f9b9d-106">V dnešní době se správnou návrhovou a pravou normou kódování lze [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] sestavit tak, aby měly lokalizovat méně změn velikosti a přemístění.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-106">Today with the right design and right coding standards, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] can be constructed so that localizers have less resizing and repositioning to do.</span></span> <span data-ttu-id="f9b9d-107">Přístup k psaní aplikací, jejichž velikost se dá snadněji měnit a kde se přemístí, se nazývá automatické rozložení a dá se dosáhnout pomocí @no__tho návrhu aplikací-0.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-107">The approach to writing applications that can be more easily resized and repositioned is called automatic layout, and can be achieved by using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application design.</span></span>

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a><span data-ttu-id="f9b9d-108">Výhody použití automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="f9b9d-108">Advantages of Using Automatic Layout</span></span>

<span data-ttu-id="f9b9d-109">Vzhledem k tomu, že je prezentační systém [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] výkonný a flexibilní, nabízí možnost rozložení prvků v aplikaci, která se dá upravit tak, aby vyhovovala požadavkům různých jazyků.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-109">Because the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] presentation system is powerful and flexible, it provides the ability to layout elements in an application that can be adjusted to fit the requirements of different languages.</span></span> <span data-ttu-id="f9b9d-110">Následující seznam ukazuje některé výhody automatického rozložení.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-110">The following list points out some of the advantages of automatic layout.</span></span>

- <span data-ttu-id="f9b9d-111">Uživatelské rozhraní se dobře zobrazuje v jakémkoli jazyce.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-111">UI displays well  in any language.</span></span>

- <span data-ttu-id="f9b9d-112">Omezuje nutnost znovu nastavit polohu a velikost ovládacích prvků po převodu textu.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-112">Reduces the need to readjust position and size of controls after text is translated.</span></span>

- <span data-ttu-id="f9b9d-113">Zmenší nutnost přizpůsobení velikosti okna.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-113">Reduces the need to readjust window size.</span></span>

- <span data-ttu-id="f9b9d-114">Rozložení uživatelského rozhraní se v jakémkoli jazyce vykresluje správně.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-114">UI layout renders properly in any language.</span></span>

- <span data-ttu-id="f9b9d-115">Lokalizace může být zmenšena na bod, který je menší než překlad řetězce.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-115">Localization can be reduced to the point that it is little more than string translation.</span></span>

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a><span data-ttu-id="f9b9d-116">Automatické rozložení a ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="f9b9d-116">Automatic Layout and Controls</span></span>

<span data-ttu-id="f9b9d-117">Automatické rozložení umožňuje aplikaci automaticky upravit velikost ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-117">Automatic layout enables an application to adjust the size of a control automatically.</span></span> <span data-ttu-id="f9b9d-118">Například ovládací prvek může být změněn tak, aby odpovídal délce řetězce.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-118">For example, a control can change to accommodate the length of a string.</span></span> <span data-ttu-id="f9b9d-119">Tato možnost umožňuje, aby lokalizovat mohli řetězec přeložit; již nepotřebují měnit velikost ovládacího prvku tak, aby odpovídal přeloženému textu.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-119">This capability enables  localizers to translate the string; they no longer need to resize the control to fit the translated text.</span></span> <span data-ttu-id="f9b9d-120">Následující příklad vytvoří tlačítko s anglickým obsahem.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-120">The following example creates a button with English content.</span></span>

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

<span data-ttu-id="f9b9d-121">V tomto příkladu stačí, když uděláte tlačítko pro španělštinu, aby se změnil text.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-121">In the example, all you have to do to make a Spanish button is change the text.</span></span> <span data-ttu-id="f9b9d-122">Například</span><span class="sxs-lookup"><span data-stu-id="f9b9d-122">For example,</span></span>

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

<span data-ttu-id="f9b9d-123">Následující obrázek ukazuje výstup ukázek kódu:</span><span class="sxs-lookup"><span data-stu-id="f9b9d-123">The following graphic shows the output of the code samples:</span></span>

![Stejné tlačítko s textem v různých jazycích](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a><span data-ttu-id="f9b9d-125">Automatické rozložení a standardy kódování</span><span class="sxs-lookup"><span data-stu-id="f9b9d-125">Automatic Layout and Coding Standards</span></span>

<span data-ttu-id="f9b9d-126">Použití přístupu automatickým rozložením vyžaduje sadu standardů kódování a návrhu a pravidla pro vytváření plně lokalizovatelnýho uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-126">Using the automatic layout approach requires a set of coding and design standards and rules to produce a fully localizable UI.</span></span> <span data-ttu-id="f9b9d-127">Následující pokyny vám pomohou při kódování vašeho automatického rozložení.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-127">The following guidelines will aid your automatic layout coding.</span></span>

<span data-ttu-id="f9b9d-128">**Nepoužívat absolutní umístění**</span><span class="sxs-lookup"><span data-stu-id="f9b9d-128">**Do not use absolute positions**</span></span>

- <span data-ttu-id="f9b9d-129">Nepoužívejte <xref:System.Windows.Controls.Canvas>, protože umisťuje prvky absolutně.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-129">Do not use <xref:System.Windows.Controls.Canvas> because it positions elements absolutely.</span></span>

- <span data-ttu-id="f9b9d-130">Ovládací prvky umístěte pomocí <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel> a <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-130">Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, and <xref:System.Windows.Controls.Grid> to position controls.</span></span>

<span data-ttu-id="f9b9d-131">Diskuzi o různých typech panelů najdete v tématu [Přehled panelů](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f9b9d-131">For a discussion about various types of panels, see [Panels Overview](../controls/panels-overview.md).</span></span>

<span data-ttu-id="f9b9d-132">**Nenastavit pevnou velikost okna**</span><span class="sxs-lookup"><span data-stu-id="f9b9d-132">**Do not set a fixed size for a window**</span></span>

- <span data-ttu-id="f9b9d-133">Použijte <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-133">Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f9b9d-134">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f9b9d-134">For example:</span></span>

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

<span data-ttu-id="f9b9d-135">**Přidat <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span><span class="sxs-lookup"><span data-stu-id="f9b9d-135">**Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span></span>

- <span data-ttu-id="f9b9d-136">Přidejte <xref:System.Windows.FrameworkElement.FlowDirection%2A> do kořenového prvku vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-136">Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A> to the root element of your application.</span></span>

  <span data-ttu-id="f9b9d-137">WPF nabízí pohodlný způsob, jak podporovat vodorovná, obousměrná a vertikální rozložení.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-137">WPF provides a convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="f9b9d-138">V prezentačním rozhraní lze pomocí vlastnosti <xref:System.Windows.FrameworkElement.FlowDirection%2A> definovat rozložení.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-138">In presentation framework, the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="f9b9d-139">Vzory směrového směru jsou:</span><span class="sxs-lookup"><span data-stu-id="f9b9d-139">The flow-direction patterns are:</span></span>

  - <span data-ttu-id="f9b9d-140">@no__t – 0 (LrTb) – horizontální rozložení pro latinku, východní Asii a tak dále.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — horizontal layout for Latin, East Asian, and so forth.</span></span>

  - <span data-ttu-id="f9b9d-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) – obousměrný pro arabštinu, hebrejštinu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirectional for Arabic, Hebrew, and so forth.</span></span>

<span data-ttu-id="f9b9d-142">**Místo fyzických písem použít složená písma**</span><span class="sxs-lookup"><span data-stu-id="f9b9d-142">**Use composite fonts instead of physical fonts**</span></span>

- <span data-ttu-id="f9b9d-143">U složených písem není nutné lokalizovat vlastnost <xref:System.Windows.Controls.Control.FontFamily%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-143">With composite fonts, the <xref:System.Windows.Controls.Control.FontFamily%2A> property does not need to be localized.</span></span>

- <span data-ttu-id="f9b9d-144">Vývojáři mohou použít jedno z následujících písem nebo vytvořit vlastní.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-144">Developers can use one of the following fonts or create their own.</span></span>

  - <span data-ttu-id="f9b9d-145">Globální uživatelské rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9b9d-145">Global User Interface</span></span>
  - <span data-ttu-id="f9b9d-146">Globální síť San Serif</span><span class="sxs-lookup"><span data-stu-id="f9b9d-146">Global San Serif</span></span>
  - <span data-ttu-id="f9b9d-147">Globální Serif</span><span class="sxs-lookup"><span data-stu-id="f9b9d-147">Global Serif</span></span>

<span data-ttu-id="f9b9d-148">**Přidat XML: lang**</span><span class="sxs-lookup"><span data-stu-id="f9b9d-148">**Add xml:lang**</span></span>

- <span data-ttu-id="f9b9d-149">Přidejte atribut `xml:lang` do kořenového elementu uživatelského rozhraní, jako je například `xml:lang="en-US"` pro anglickou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-149">Add the `xml:lang` attribute in the root element of your UI, such as `xml:lang="en-US"` for an English application.</span></span>

- <span data-ttu-id="f9b9d-150">Vzhledem k tomu, že složená písma používají `xml:lang` k určení používaného písma, nastavte tuto vlastnost na podporu vícejazyčných scénářů.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-150">Because composite fonts use `xml:lang` to determine what font to use, set this property to support multilingual scenarios.</span></span>

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a><span data-ttu-id="f9b9d-151">Automatické rozložení a mřížky</span><span class="sxs-lookup"><span data-stu-id="f9b9d-151">Automatic Layout and Grids</span></span>

<span data-ttu-id="f9b9d-152">Element <xref:System.Windows.Controls.Grid> je vhodný pro automatické rozložení, protože umožňuje vývojářům umístit prvky.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-152">The <xref:System.Windows.Controls.Grid> element, is useful for automatic layout because it enables a developer to position elements.</span></span> <span data-ttu-id="f9b9d-153">Ovládací prvek <xref:System.Windows.Controls.Grid> je schopný distribuovat dostupný prostor mezi jeho podřízené prvky pomocí uspořádání sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-153">A <xref:System.Windows.Controls.Grid> control is capable of distributing the available space among its child elements, using a column and row arrangement.</span></span> <span data-ttu-id="f9b9d-154">Prvky uživatelského rozhraní mohou zahrnovat více buněk a je možné mít mřížky v rámci gridů.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-154">The UI elements can span multiple cells, and it is possible to have grids within grids.</span></span> <span data-ttu-id="f9b9d-155">Mřížky jsou užitečné, protože umožňují vytvořit a umístit komplexní uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-155">Grids are useful because they enable you to create and position complex UI.</span></span> <span data-ttu-id="f9b9d-156">Následující příklad ukazuje použití mřížky k umístění některých tlačítek a textu.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-156">The following example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="f9b9d-157">Všimněte si, že výška a šířka buněk jsou nastaveny na <xref:System.Windows.GridUnitType.Auto>; Proto buňka, která obsahuje tlačítko s obrázkem, se upraví tak, aby odpovídala obrázku.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-157">Notice that the height and width of the cells are set to <xref:System.Windows.GridUnitType.Auto>; therefore, the cell that contains the button with an image adjusts to fit the image.</span></span>

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

<span data-ttu-id="f9b9d-158">Následující obrázek znázorňuje mřížku vytvořenou předchozím kódem.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-158">The following graphic shows the grid produced by the previous code.</span></span>

<span data-ttu-id="f9b9d-159">Mřížka – ![příklad](./media/glob-grid.png "glob_grid") mřížky</span><span class="sxs-lookup"><span data-stu-id="f9b9d-159">![Grid example](./media/glob-grid.png "glob_grid") Grid</span></span>

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a><span data-ttu-id="f9b9d-160">Automatické rozložení a mřížky pomocí vlastnosti IsSharedSizeScope</span><span class="sxs-lookup"><span data-stu-id="f9b9d-160">Automatic Layout and Grids Using the IsSharedSizeScope Property</span></span>

<span data-ttu-id="f9b9d-161">Element <xref:System.Windows.Controls.Grid> je užitečný v lokalizovatelných aplikacích pro vytváření ovládacích prvků, které se přizpůsobí obsahu.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-161">A <xref:System.Windows.Controls.Grid> element is useful in localizable applications to create controls that adjust to fit content.</span></span> <span data-ttu-id="f9b9d-162">Občas ale chcete, aby ovládací prvky zachovaly určitou velikost bez ohledu na obsah.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-162">However, at times you want controls to maintain a particular size regardless of content.</span></span> <span data-ttu-id="f9b9d-163">Například pokud máte tlačítka "OK", "Storno" a "Procházet", pravděpodobně nechcete, aby se tlačítka vešla do velikosti obsahu.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-163">For example, if you have "OK", "Cancel" and "Browse" buttons you probably do not want the buttons sized to fit the content.</span></span> <span data-ttu-id="f9b9d-164">V tomto případě je <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> připojená vlastnost užitečná pro sdílení stejné velikosti mezi více prvky mřížky.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-164">In this case the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> attached property is useful for sharing the same sizing among multiple grid elements.</span></span> <span data-ttu-id="f9b9d-165">Následující příklad ukazuje, jak sdílet data o velikosti sloupců a řádků mezi více prvky <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="f9b9d-165">The following example demonstrates how to share column and row sizing data between multiple <xref:System.Windows.Controls.Grid> elements.</span></span>

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> <span data-ttu-id="f9b9d-166">Úplnou ukázku kódu naleznete v tématu [sdílení vlastností velikosti mezi mřížkami](../controls/how-to-share-sizing-properties-between-grids.md).</span><span class="sxs-lookup"><span data-stu-id="f9b9d-166">For the complete code sample, see [Share Sizing Properties Between Grids](../controls/how-to-share-sizing-properties-between-grids.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9b9d-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9b9d-167">See also</span></span>

- [<span data-ttu-id="f9b9d-168">Globalizace pro WPF</span><span class="sxs-lookup"><span data-stu-id="f9b9d-168">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="f9b9d-169">Vytvoření tlačítka pomocí automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="f9b9d-169">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
- [<span data-ttu-id="f9b9d-170">Automatické rozložení použitím mřížky</span><span class="sxs-lookup"><span data-stu-id="f9b9d-170">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
