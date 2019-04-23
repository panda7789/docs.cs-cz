---
title: Přehled automatického rozložení
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 5df6d39bef137bd4005316eac252ca0952df5e7f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098777"
---
# <a name="use-automatic-layout-overview"></a><span data-ttu-id="3de25-102">Přehled automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="3de25-102">Use Automatic Layout Overview</span></span>
<span data-ttu-id="3de25-103">Toto téma popisuje pokyny pro vývojáře na tom, jak psát [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací s lokalizovatelné [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3de25-103">This topic introduces guidelines for developers on how to write [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications with localizable [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span></span> <span data-ttu-id="3de25-104">Lokalizace uživatelského rozhraní v minulosti bylo časově náročný proces.</span><span class="sxs-lookup"><span data-stu-id="3de25-104">In the past, localization of a UI was a time consuming process.</span></span> <span data-ttu-id="3de25-105">Každý jazyk, který byl přizpůsobit uživatelské rozhraní pro požadované úpravy podle pixelů.</span><span class="sxs-lookup"><span data-stu-id="3de25-105">Each language that the UI was adapted for required a pixel by pixel adjustment.</span></span> <span data-ttu-id="3de25-106">Dnes s správný návrh a pravá standardy kódování, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] lze sestavit tak, aby Lokalizátoři menší změny velikosti a přemístění provést.</span><span class="sxs-lookup"><span data-stu-id="3de25-106">Today with the right design and right coding standards, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] can be constructed so that localizers have less resizing and repositioning to do.</span></span> <span data-ttu-id="3de25-107">Přístup k vytváření aplikací, které se dají snadno změněnou velikostí a přemístěných nazývá Automatické rozložení a lze dosáhnout pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] návrhu aplikace.</span><span class="sxs-lookup"><span data-stu-id="3de25-107">The approach to writing applications that can be more easily resized and repositioned is called automatic layout, and can be achieved by using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application design.</span></span>  

<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a><span data-ttu-id="3de25-108">Mezi výhody používání automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="3de25-108">Advantages of Using Automatic Layout</span></span>  
 <span data-ttu-id="3de25-109">Vzhledem k tomu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prezentační systém je výkonná a flexibilní, poskytuje schopnost rozložení prvků v aplikaci, která je možné upravit podle požadavků různých jazycích.</span><span class="sxs-lookup"><span data-stu-id="3de25-109">Because the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] presentation system is powerful and flexible, it provides the ability to layout elements in an application that can be adjusted to fit the requirements of different languages.</span></span> <span data-ttu-id="3de25-110">Následující seznam ukazuje některé z výhod automatické rozložení.</span><span class="sxs-lookup"><span data-stu-id="3de25-110">The following list points out some of the advantages of automatic layout.</span></span>  

-   <span data-ttu-id="3de25-111">Uživatelské rozhraní zobrazí také v jakémkoli jazyce.</span><span class="sxs-lookup"><span data-stu-id="3de25-111">UI displays well  in any language.</span></span>  

-   <span data-ttu-id="3de25-112">Snižuje nutnost znovu nastavte pozici a velikost ovládacích prvků po přeložený text.</span><span class="sxs-lookup"><span data-stu-id="3de25-112">Reduces the need to readjust position and size of controls after text is translated.</span></span>  
  
-   <span data-ttu-id="3de25-113">Snižuje nutnost přizpůsobit velikosti okna.</span><span class="sxs-lookup"><span data-stu-id="3de25-113">Reduces the need to readjust window size.</span></span>  

-   <span data-ttu-id="3de25-114">Uživatelské rozhraní rozložení vykreslí správně v libovolném jazyce.</span><span class="sxs-lookup"><span data-stu-id="3de25-114">UI layout renders properly in any language.</span></span>  

-   <span data-ttu-id="3de25-115">Lokalizace lze snížit, že se jedná o něco více než řetězec překladu bodu.</span><span class="sxs-lookup"><span data-stu-id="3de25-115">Localization can be reduced to the point that it is little more than string translation.</span></span>  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a><span data-ttu-id="3de25-116">Automatické rozložení a ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="3de25-116">Automatic Layout and Controls</span></span>  
 <span data-ttu-id="3de25-117">Automatické rozložení umožňuje aplikaci automaticky upravte velikost ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3de25-117">Automatic layout enables an application to adjust the size of a control automatically.</span></span> <span data-ttu-id="3de25-118">Například ovládací prvek můžete změnit tak, aby vyhovovaly délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="3de25-118">For example, a control can change to accommodate the length of a string.</span></span> <span data-ttu-id="3de25-119">Tato možnost umožňuje Lokalizátoři převodu řetězec. už nepotřebujete pro změnu velikosti ovládacího prvku podle přeložený text.</span><span class="sxs-lookup"><span data-stu-id="3de25-119">This capability enables  localizers to translate the string; they no longer need to resize the control to fit the translated text.</span></span> <span data-ttu-id="3de25-120">Následující příklad vytvoří tlačítko s anglickým obsahem.</span><span class="sxs-lookup"><span data-stu-id="3de25-120">The following example creates a button with English content.</span></span>  
  
 [!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="3de25-121">V příkladu jediné, co musíte udělat, aby Španělština tlačítko se změní celý text.</span><span class="sxs-lookup"><span data-stu-id="3de25-121">In the example, all you have to do to make a Spanish button is change the text.</span></span> <span data-ttu-id="3de25-122">Například</span><span class="sxs-lookup"><span data-stu-id="3de25-122">For example,</span></span>  
  
 [!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="3de25-123">Následující obrázek ukazuje výstup z ukázek kódu:</span><span class="sxs-lookup"><span data-stu-id="3de25-123">The following graphic shows the output of the code samples:</span></span>  
  
 ![Stejné tlačítko s textem v různých jazycích](./media/use-automatic-layout-overview/auto-resizable-button.png)  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a><span data-ttu-id="3de25-125">Automatické rozložení a standardy kódování</span><span class="sxs-lookup"><span data-stu-id="3de25-125">Automatic Layout and Coding Standards</span></span>  
 <span data-ttu-id="3de25-126">Pomocí automatického rozložení přístup vyžaduje sadu psaní kódu a návrhu normy a pravidla, která vytvoří plně lokalizovatelné uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3de25-126">Using the automatic layout approach requires a set of coding and design standards and rules to produce a fully localizable UI.</span></span> <span data-ttu-id="3de25-127">Následující pokyny vám pomůže automatické rozložení psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="3de25-127">The following guidelines will aid your automatic layout coding.</span></span>  

<span data-ttu-id="3de25-128">**Nepoužívejte absolutní umístění**</span><span class="sxs-lookup"><span data-stu-id="3de25-128">**Do not use absolute positions**</span></span>

- <span data-ttu-id="3de25-129">Nepoužívejte <xref:System.Windows.Controls.Canvas> protože naprosto umístí prvky.</span><span class="sxs-lookup"><span data-stu-id="3de25-129">Do not use <xref:System.Windows.Controls.Canvas> because it positions elements absolutely.</span></span>

- <span data-ttu-id="3de25-130">Použití <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.Grid> umístěte ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="3de25-130">Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, and <xref:System.Windows.Controls.Grid> to position controls.</span></span>

<span data-ttu-id="3de25-131">Informace o různých typech panelů najdete v článku [přehled panelů](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3de25-131">For a discussion about various types of panels, see [Panels Overview](../controls/panels-overview.md).</span></span>

<span data-ttu-id="3de25-132">**Nenastavujte pevně danou velikost okna**</span><span class="sxs-lookup"><span data-stu-id="3de25-132">**Do not set a fixed size for a window**</span></span>

- <span data-ttu-id="3de25-133">Použití <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3de25-133">Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3de25-134">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3de25-134">For example:</span></span>

   [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

<span data-ttu-id="3de25-135">**Přidat <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span><span class="sxs-lookup"><span data-stu-id="3de25-135">**Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span></span>

- <span data-ttu-id="3de25-136">Přidat <xref:System.Windows.FrameworkElement.FlowDirection%2A> do kořenového elementu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="3de25-136">Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A> to the root element of your application.</span></span>

   <span data-ttu-id="3de25-137">WPF poskytuje pohodlný způsob, jak podporovat vodorovné, obousměrné a svislé rozložení.</span><span class="sxs-lookup"><span data-stu-id="3de25-137">WPF provides a convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="3de25-138">V rámci prezentace <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost lze použít k definování rozložení.</span><span class="sxs-lookup"><span data-stu-id="3de25-138">In presentation framework, the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="3de25-139">Směr toku vzorky jsou:</span><span class="sxs-lookup"><span data-stu-id="3de25-139">The flow-direction patterns are:</span></span>
   
     - <span data-ttu-id="3de25-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) – vodorovné rozložení pro latinka, východní Asie a tak dále.</span><span class="sxs-lookup"><span data-stu-id="3de25-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — horizontal layout for Latin, East Asian, and so forth.</span></span>
     
     - <span data-ttu-id="3de25-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) – obousměrné pro arabština, hebrejština a tak dále.</span><span class="sxs-lookup"><span data-stu-id="3de25-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirectional for Arabic, Hebrew, and so forth.</span></span>

<span data-ttu-id="3de25-142">**Složená písma nahrazujícím fyzické písma**</span><span class="sxs-lookup"><span data-stu-id="3de25-142">**Use composite fonts instead of physical fonts**</span></span>

- <span data-ttu-id="3de25-143">S složená písma <xref:System.Windows.Controls.Control.FontFamily%2A> vlastnost nemusí být lokalizována.</span><span class="sxs-lookup"><span data-stu-id="3de25-143">With composite fonts, the <xref:System.Windows.Controls.Control.FontFamily%2A> property does not need to be localized.</span></span>

- <span data-ttu-id="3de25-144">Vývojáře můžou použít jednu z následujících písma nebo vytvořit svoje vlastní.</span><span class="sxs-lookup"><span data-stu-id="3de25-144">Developers can use one of the following fonts or create their own.</span></span>

   - <span data-ttu-id="3de25-145">Globální uživatelské rozhraní</span><span class="sxs-lookup"><span data-stu-id="3de25-145">Global User Interface</span></span>
   - <span data-ttu-id="3de25-146">Global San Serif</span><span class="sxs-lookup"><span data-stu-id="3de25-146">Global San Serif</span></span>
   - <span data-ttu-id="3de25-147">Globální Serif</span><span class="sxs-lookup"><span data-stu-id="3de25-147">Global Serif</span></span>

<span data-ttu-id="3de25-148">**XML: lang – přidat**</span><span class="sxs-lookup"><span data-stu-id="3de25-148">**Add xml:lang**</span></span>

- <span data-ttu-id="3de25-149">Přidat `xml:lang` atribut v kořenovém prvku uživatelského rozhraní, jako například `xml:lang="en-US"` anglické aplikace.</span><span class="sxs-lookup"><span data-stu-id="3de25-149">Add the `xml:lang` attribute in the root element of your UI, such as `xml:lang="en-US"` for an English application.</span></span>

- <span data-ttu-id="3de25-150">Vzhledem k tomu použít složená písma `xml:lang` Pokud chcete zjistit, jaká písma používat, nastavte tuto vlastnost na podporu více jazyků scénářů.</span><span class="sxs-lookup"><span data-stu-id="3de25-150">Because composite fonts use `xml:lang` to determine what font to use, set this property to support multilingual scenarios.</span></span>

<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a><span data-ttu-id="3de25-151">Automatické rozložení a mřížky</span><span class="sxs-lookup"><span data-stu-id="3de25-151">Automatic Layout and Grids</span></span>  
 <span data-ttu-id="3de25-152"><xref:System.Windows.Controls.Grid> Elementu, je užitečná pro automatické rozložení, protože umožňuje vývojářům umístění prvků.</span><span class="sxs-lookup"><span data-stu-id="3de25-152">The <xref:System.Windows.Controls.Grid> element, is useful for automatic layout because it enables a developer to position elements.</span></span> <span data-ttu-id="3de25-153">A <xref:System.Windows.Controls.Grid> ovládací prvek je schopen distribuci k dispozici prostor mezi jeho podřízené prvky použitím uspořádání sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="3de25-153">A <xref:System.Windows.Controls.Grid> control is capable of distributing the available space among its child elements, using a column and row arrangement.</span></span> <span data-ttu-id="3de25-154">Prvky uživatelského rozhraní může zahrnovat více buněk, a je možné mít mřížky v rámci mřížky.</span><span class="sxs-lookup"><span data-stu-id="3de25-154">The UI elements can span multiple cells, and it is possible to have grids within grids.</span></span> <span data-ttu-id="3de25-155">Mřížky jsou užitečné, protože umožňují vytvářet a umístěte komplexní uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3de25-155">Grids are useful because they enable you to create and position complex UI.</span></span> <span data-ttu-id="3de25-156">Následující příklad ukazuje použití tabulky na pozici některá tlačítka a text.</span><span class="sxs-lookup"><span data-stu-id="3de25-156">The following example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="3de25-157">Všimněte si, že výšku a šířku buňky jsou nastaveny na <xref:System.Windows.GridUnitType.Auto>; proto se upraví na buňku, která obsahuje tlačítko s imagí podle obrázku.</span><span class="sxs-lookup"><span data-stu-id="3de25-157">Notice that the height and width of the cells are set to <xref:System.Windows.GridUnitType.Auto>; therefore, the cell that contains the button with an image adjusts to fit the image.</span></span>  

 [!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="3de25-158">Následující obrázek znázorňuje mřížky vytvořený v předchozím kódu.</span><span class="sxs-lookup"><span data-stu-id="3de25-158">The following graphic shows the grid produced by the previous code.</span></span>  
  
 <span data-ttu-id="3de25-159">![Grid – příklad](./media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="3de25-159">![Grid example](./media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="3de25-160">Mřížka</span><span class="sxs-lookup"><span data-stu-id="3de25-160">Grid</span></span>  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a><span data-ttu-id="3de25-161">Automatické rozložení a pomocí vlastnosti IsSharedSizeScope mřížky</span><span class="sxs-lookup"><span data-stu-id="3de25-161">Automatic Layout and Grids Using the IsSharedSizeScope Property</span></span>  
 <span data-ttu-id="3de25-162">A <xref:System.Windows.Controls.Grid> prvek je užitečný v lokalizovatelných aplikacích vytvořit ovládací prvky, které se přizpůsobí zobrazení celého obsahu.</span><span class="sxs-lookup"><span data-stu-id="3de25-162">A <xref:System.Windows.Controls.Grid> element is useful in localizable applications to create controls that adjust to fit content.</span></span> <span data-ttu-id="3de25-163">V některých případech ale budete chtít ovládacích prvků pro udržování určité velikosti, bez ohledu na obsah.</span><span class="sxs-lookup"><span data-stu-id="3de25-163">However, at times you want controls to maintain a particular size regardless of content.</span></span> <span data-ttu-id="3de25-164">Například pokud máte "OK", "Storno" a "Procházet" pravděpodobně nechcete, aby tlačítka velikosti podle obsahu tlačítka.</span><span class="sxs-lookup"><span data-stu-id="3de25-164">For example, if you have "OK", "Cancel" and "Browse" buttons you probably do not want the buttons sized to fit the content.</span></span> <span data-ttu-id="3de25-165">V tomto případě <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> připojená vlastnost je užitečná pro sdílení stejné velikosti mezi mnohonásobné elementy mřížky.</span><span class="sxs-lookup"><span data-stu-id="3de25-165">In this case the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> attached property is useful for sharing the same sizing among multiple grid elements.</span></span> <span data-ttu-id="3de25-166">Následující příklad ukazuje, jak sdílet data mezi více změny velikosti řádků a sloupců <xref:System.Windows.Controls.Grid> elementy.</span><span class="sxs-lookup"><span data-stu-id="3de25-166">The following example demonstrates how to share column and row sizing data between multiple <xref:System.Windows.Controls.Grid> elements.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="3de25-167">**Poznámka:** kompletní vzorek kódu, naleznete v tématu [sdílené složky velikosti vlastnosti mezi mřížkami](../controls/how-to-share-sizing-properties-between-grids.md)</span><span class="sxs-lookup"><span data-stu-id="3de25-167">**Note** For the complete code sample, see [Share Sizing Properties Between Grids](../controls/how-to-share-sizing-properties-between-grids.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de25-168">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3de25-168">See also</span></span>

- [<span data-ttu-id="3de25-169">Globalizace pro WPF</span><span class="sxs-lookup"><span data-stu-id="3de25-169">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="3de25-170">Vytvoření tlačítka pomocí automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="3de25-170">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
- [<span data-ttu-id="3de25-171">Automatické rozložení použitím mřížky</span><span class="sxs-lookup"><span data-stu-id="3de25-171">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
