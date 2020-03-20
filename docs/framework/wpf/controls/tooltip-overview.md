---
title: ToolTip – přehled
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
ms.openlocfilehash: 0fec31b28a21c2e17986210c852b3d630087842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181952"
---
# <a name="tooltip-overview"></a><span data-ttu-id="d1e25-102">ToolTip – přehled</span><span class="sxs-lookup"><span data-stu-id="d1e25-102">ToolTip Overview</span></span>
<span data-ttu-id="d1e25-103">Popisek je malé vyskakovací okno, které se zobrazí, když uživatel <xref:System.Windows.Controls.Button>pozastaví ukazatel myši nad elementem, například nad prvkem .</span><span class="sxs-lookup"><span data-stu-id="d1e25-103">A tooltip is a small pop-up window that appears when a user pauses the mouse pointer over an element, such as over a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="d1e25-104">Toto téma představuje popis ekazičně a popisuje, jak vytvořit a přizpůsobit obsah popisku.</span><span class="sxs-lookup"><span data-stu-id="d1e25-104">This topic introduces the tooltip and discusses how to create and customize tooltip content.</span></span>  

<a name="what_is_a_tooltip"></a>
## <a name="what-is-a-tooltip"></a><span data-ttu-id="d1e25-105">Co je popis?</span><span class="sxs-lookup"><span data-stu-id="d1e25-105">What Is a Tooltip?</span></span>  
 <span data-ttu-id="d1e25-106">Když uživatel přesune ukazatel myši nad element, který má popisek, zobrazí se okno, které obsahuje obsah popisku (například textový obsah popisující funkci ovládacího prvku) po určitou dobu.</span><span class="sxs-lookup"><span data-stu-id="d1e25-106">When a user moves the mouse pointer over an element that has a tooltip, a window that contains tooltip content (for example, text content that describes the function of a control) appears for a specified amount of time.</span></span> <span data-ttu-id="d1e25-107">Pokud uživatel přesune ukazatel myši od ovládacího prvku, okno zmizí, protože obsah popisku nemůže získat fokus.</span><span class="sxs-lookup"><span data-stu-id="d1e25-107">If the user moves the mouse pointer away from the control, the window disappears because the tooltip content cannot receive focus.</span></span>  
  
 <span data-ttu-id="d1e25-108">Obsah popisku může obsahovat jeden nebo více řádků textu, obrázků, tvarů nebo jiného vizuálního obsahu.</span><span class="sxs-lookup"><span data-stu-id="d1e25-108">The content of a tooltip can contain one or more lines of text, images, shapes, or other visual content.</span></span> <span data-ttu-id="d1e25-109">Popisek ovládacího prvku definujete nastavením jedné z následujících vlastností pro obsah popisku.</span><span class="sxs-lookup"><span data-stu-id="d1e25-109">You define a tooltip for a control by setting one of the following properties to the tooltip content.</span></span>  
  
- <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="d1e25-110">Vlastnost, kterou používáte, závisí na tom, zda ovládací <xref:System.Windows.FrameworkContentElement> <xref:System.Windows.FrameworkElement> prvek, který definuje popis dědí z třídy nebo.</span><span class="sxs-lookup"><span data-stu-id="d1e25-110">Which property you use depends on whether the control that defines the tooltip inherits from the <xref:System.Windows.FrameworkContentElement> or <xref:System.Windows.FrameworkElement> class.</span></span>  
  
<a name="create_tooltip"></a>
## <a name="creating-a-tooltip"></a><span data-ttu-id="d1e25-111">Vytvoření popisu</span><span class="sxs-lookup"><span data-stu-id="d1e25-111">Creating a ToolTip</span></span>  
 <span data-ttu-id="d1e25-112">Následující příklad ukazuje, jak vytvořit jednoduchý popis <xref:System.Windows.FrameworkElement.ToolTip%2A> nastavení <xref:System.Windows.Controls.Button> vlastnosti ovládacího prvku na textový řetězec.</span><span class="sxs-lookup"><span data-stu-id="d1e25-112">The following example shows how to create a simple tooltip by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A> property for a <xref:System.Windows.Controls.Button> control to a text string.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 <span data-ttu-id="d1e25-113">Popisek můžete také definovat <xref:System.Windows.Controls.ToolTip> jako objekt.</span><span class="sxs-lookup"><span data-stu-id="d1e25-113">You can also define a tooltip as a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="d1e25-114">Následující příklad [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používá k <xref:System.Windows.Controls.ToolTip> určení objektu jako <xref:System.Windows.Controls.TextBox> popisek prvku.</span><span class="sxs-lookup"><span data-stu-id="d1e25-114">The following example uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to specify a <xref:System.Windows.Controls.ToolTip> object as the tooltip of a <xref:System.Windows.Controls.TextBox> element.</span></span> <span data-ttu-id="d1e25-115">Všimněte si, že <xref:System.Windows.Controls.ToolTip> příklad <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> určuje nastavenívlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d1e25-115">Note that the example specifies the <xref:System.Windows.Controls.ToolTip> by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-xaml[ToolTipSimple#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 <span data-ttu-id="d1e25-116">Následující příklad používá kód <xref:System.Windows.Controls.ToolTip> ke generování objektu.</span><span class="sxs-lookup"><span data-stu-id="d1e25-116">The following example uses code to generate a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="d1e25-117">Příklad vytvoří <xref:System.Windows.Controls.ToolTip> (`tt`) a přidruží <xref:System.Windows.Controls.Button>k .</span><span class="sxs-lookup"><span data-stu-id="d1e25-117">The example creates a <xref:System.Windows.Controls.ToolTip> (`tt`) and associates it with a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-csharp[ToolTipSimple#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 <span data-ttu-id="d1e25-118">Můžete také vytvořit obsah popisů, který <xref:System.Windows.Controls.ToolTip> není definován jako objekt, uzavřením obsahu popisku do prvku rozložení, například <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="d1e25-118">You can also create tooltip content that is not defined as a <xref:System.Windows.Controls.ToolTip> object by enclosing the tooltip content in a layout element, such as a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="d1e25-119">Následující příklad ukazuje, jak <xref:System.Windows.FrameworkElement.ToolTip%2A> nastavit <xref:System.Windows.Controls.TextBox> vlastnost obsahu, který je <xref:System.Windows.Controls.DockPanel> uzavřen v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="d1e25-119">The following example shows how to set the <xref:System.Windows.FrameworkElement.ToolTip%2A> property of a <xref:System.Windows.Controls.TextBox> to content that is enclosed in a <xref:System.Windows.Controls.DockPanel> control.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a><span data-ttu-id="d1e25-120">Použití vlastností tříd popisu a popisu služby</span><span class="sxs-lookup"><span data-stu-id="d1e25-120">Using the Properties of the ToolTip and ToolTipService Classes</span></span>  
 <span data-ttu-id="d1e25-121">Obsah popisů můžete přizpůsobit nastavením vizuálních vlastností a použitím stylů.</span><span class="sxs-lookup"><span data-stu-id="d1e25-121">You can customize tooltip content by setting visual properties and applying styles.</span></span> <span data-ttu-id="d1e25-122">Pokud definujete obsah popisku <xref:System.Windows.Controls.ToolTip> jako objekt, můžete nastavit <xref:System.Windows.Controls.ToolTip> vizuální vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="d1e25-122">If you define the tooltip content as a <xref:System.Windows.Controls.ToolTip> object, you can set the visual properties of the <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="d1e25-123">V opačném případě je nutné nastavit <xref:System.Windows.Controls.ToolTipService> ekvivalentní připojené vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="d1e25-123">Otherwise, you must set equivalent attached properties on the <xref:System.Windows.Controls.ToolTipService> class.</span></span>  
  
 <span data-ttu-id="d1e25-124">Příklad nastavení vlastností za účelem určení polohy obsahu popisku <xref:System.Windows.Controls.ToolTip> pomocí <xref:System.Windows.Controls.ToolTipService> vlastností a naleznete v [tématu Umístění popisu](how-to-position-a-tooltip.md).</span><span class="sxs-lookup"><span data-stu-id="d1e25-124">For an example of how to set properties in order to specify the position of tooltip content by using the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> properties, see [Position a ToolTip](how-to-position-a-tooltip.md).</span></span>  
  
<a name="StylingToolTip"></a>
## <a name="styling-a-tooltip"></a><span data-ttu-id="d1e25-125">Stylování popisku</span><span class="sxs-lookup"><span data-stu-id="d1e25-125">Styling a ToolTip</span></span>  
 <span data-ttu-id="d1e25-126">Můžete styl <xref:System.Windows.Controls.ToolTip> a definováním <xref:System.Windows.Style>vlastní .</span><span class="sxs-lookup"><span data-stu-id="d1e25-126">You can style a <xref:System.Windows.Controls.ToolTip> by defining a custom <xref:System.Windows.Style>.</span></span> <span data-ttu-id="d1e25-127">Následující příklad definuje <xref:System.Windows.Style> volané, `Simple` které ukazuje, jak <xref:System.Windows.Controls.ToolTip> kompenzovat umístění a <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.Foreground%2A>změnit <xref:System.Windows.Controls.Control.FontSize%2A>jeho <xref:System.Windows.Controls.Control.FontWeight%2A>vzhled nastavením , , a .</span><span class="sxs-lookup"><span data-stu-id="d1e25-127">The following example defines a <xref:System.Windows.Style> called `Simple` that shows how to offset the placement of the <xref:System.Windows.Controls.ToolTip> and change its appearance by setting the <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, and <xref:System.Windows.Controls.Control.FontWeight%2A>.</span></span>  
  
 [!code-xaml[ToolTipSimple#Style](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>
## <a name="using-the-time-interval-properties-of-tooltipservice"></a><span data-ttu-id="d1e25-128">Použití vlastností časového intervalu služby ToolTipService</span><span class="sxs-lookup"><span data-stu-id="d1e25-128">Using the Time Interval Properties of ToolTipService</span></span>  
 <span data-ttu-id="d1e25-129">Třída <xref:System.Windows.Controls.ToolTipService> poskytuje následující vlastnosti pro nastavení časů <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>zobrazení <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>popisku: , , a <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span><span class="sxs-lookup"><span data-stu-id="d1e25-129">The <xref:System.Windows.Controls.ToolTipService> class provides the following properties for you to set tooltip display times: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span></span>  
  
 <span data-ttu-id="d1e25-130">Pomocí <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> vlastností a <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> určete zpoždění, obvykle <xref:System.Windows.Controls.ToolTip> stručné, před tím, <xref:System.Windows.Controls.ToolTip> než se zobrazí, a také určete, jak dlouho zůstane viditelné.</span><span class="sxs-lookup"><span data-stu-id="d1e25-130">Use the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> properties to specify a delay, typically brief, before a <xref:System.Windows.Controls.ToolTip> appears and also to specify how long a <xref:System.Windows.Controls.ToolTip> remains visible.</span></span> <span data-ttu-id="d1e25-131">Další informace naleznete v [tématu How to: Delay the Display of a ToolTip](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d1e25-131">For more information, see [How to: Delay the Display of a ToolTip](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90)).</span></span>  
  
 <span data-ttu-id="d1e25-132">Vlastnost <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> určuje, zda popisky pro různé ovládací prvky se zobrazí bez počátečního zpoždění při rychlém přesunutí ukazatele myši mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="d1e25-132">The <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property determines if tooltips for different controls appear without an initial delay when you move the mouse pointer quickly between them.</span></span> <span data-ttu-id="d1e25-133">Další informace o <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> vlastnosti naleznete [v tématu Use the BetweenShowDelay Property](how-to-use-the-betweenshowdelay-property.md).</span><span class="sxs-lookup"><span data-stu-id="d1e25-133">For more information about the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property, see [Use the BetweenShowDelay Property](how-to-use-the-betweenshowdelay-property.md).</span></span>  
  
 <span data-ttu-id="d1e25-134">Následující příklad ukazuje, jak nastavit tyto vlastnosti pro popis.</span><span class="sxs-lookup"><span data-stu-id="d1e25-134">The following example shows how to set these properties for a tooltip.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="d1e25-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1e25-135">See also</span></span>

- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [<span data-ttu-id="d1e25-136">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="d1e25-136">How-to Topics</span></span>](tooltip-how-to-topics.md)
