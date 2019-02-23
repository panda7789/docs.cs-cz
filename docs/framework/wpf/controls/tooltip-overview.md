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
ms.openlocfilehash: 5378744ea43b72bafb77c9d58c1a8d848c3a8fc9
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745512"
---
# <a name="tooltip-overview"></a><span data-ttu-id="ae06a-102">ToolTip – přehled</span><span class="sxs-lookup"><span data-stu-id="ae06a-102">ToolTip Overview</span></span>
<span data-ttu-id="ae06a-103">Malého vyskakovacího okna, který se zobrazí, když uživatel pozastavení ukazatele myši nad prvkem, například jako více než je ovládací prvek tooltip <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="ae06a-103">A tooltip is a small pop-up window that appears when a user pauses the mouse pointer over an element, such as over a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="ae06a-104">Toto téma představuje popisek a popisuje, jak vytvořit a přizpůsobit obsah popisku.</span><span class="sxs-lookup"><span data-stu-id="ae06a-104">This topic introduces the tooltip and discusses how to create and customize tooltip content.</span></span>  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a><span data-ttu-id="ae06a-105">Co je popisek?</span><span class="sxs-lookup"><span data-stu-id="ae06a-105">What Is a Tooltip?</span></span>  
 <span data-ttu-id="ae06a-106">Když uživatel přesune ukazatel myši nad prvkem, který má popisek, zobrazí se okno, které obsahuje popis obsah (například text, který popisuje funkce ovládacího prvku) pro určenou dobu.</span><span class="sxs-lookup"><span data-stu-id="ae06a-106">When a user moves the mouse pointer over an element that has a tooltip, a window that contains tooltip content (for example, text content that describes the function of a control) appears for a specified amount of time.</span></span> <span data-ttu-id="ae06a-107">Pokud se uživatel přesune ukazatel myši mimo ovládací prvek, v okně zmizí, protože popisek obsah nemůže získat fokus.</span><span class="sxs-lookup"><span data-stu-id="ae06a-107">If the user moves the mouse pointer away from the control, the window disappears because the tooltip content cannot receive focus.</span></span>  
  
 <span data-ttu-id="ae06a-108">Obsah popisek může obsahovat jeden nebo více řádků textu, obrázky, obrazce nebo jiné vizuální obsah.</span><span class="sxs-lookup"><span data-stu-id="ae06a-108">The content of a tooltip can contain one or more lines of text, images, shapes, or other visual content.</span></span> <span data-ttu-id="ae06a-109">Popis tlačítka pro ovládací prvek pomocí nastavení jedné z následujících vlastností můžete definovat popis obsahu.</span><span class="sxs-lookup"><span data-stu-id="ae06a-109">You define a tooltip for a control by setting one of the following properties to the tooltip content.</span></span>  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="ae06a-110">Vlastností, které použijete, závisí na tom, zda ovládací prvek, který definuje popisek dědí z <xref:System.Windows.FrameworkContentElement> nebo <xref:System.Windows.FrameworkElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="ae06a-110">Which property you use depends on whether the control that defines the tooltip inherits from the <xref:System.Windows.FrameworkContentElement> or <xref:System.Windows.FrameworkElement> class.</span></span>  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a><span data-ttu-id="ae06a-111">Vytvoření popisu</span><span class="sxs-lookup"><span data-stu-id="ae06a-111">Creating a ToolTip</span></span>  
 <span data-ttu-id="ae06a-112">Následující příklad ukazuje, jak vytvořit jednoduchý popis tlačítka tak, že nastavíte <xref:System.Windows.FrameworkElement.ToolTip%2A> vlastnost <xref:System.Windows.Controls.Button> ovládací prvek textového řetězce.</span><span class="sxs-lookup"><span data-stu-id="ae06a-112">The following example shows how to create a simple tooltip by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A> property for a <xref:System.Windows.Controls.Button> control to a text string.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 <span data-ttu-id="ae06a-113">Můžete také definovat popisek jako <xref:System.Windows.Controls.ToolTip> objektu.</span><span class="sxs-lookup"><span data-stu-id="ae06a-113">You can also define a tooltip as a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="ae06a-114">Následující příklad používá [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] k určení <xref:System.Windows.Controls.ToolTip> objektu jako text nápovědy <xref:System.Windows.Controls.TextBox> elementu.</span><span class="sxs-lookup"><span data-stu-id="ae06a-114">The following example uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to specify a <xref:System.Windows.Controls.ToolTip> object as the tooltip of a <xref:System.Windows.Controls.TextBox> element.</span></span> <span data-ttu-id="ae06a-115">Všimněte si, že příklad určuje <xref:System.Windows.Controls.ToolTip> nastavením <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ae06a-115">Note that the example specifies the <xref:System.Windows.Controls.ToolTip> by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 <span data-ttu-id="ae06a-116">Následující příklad používá ke generování kódu <xref:System.Windows.Controls.ToolTip> objektu.</span><span class="sxs-lookup"><span data-stu-id="ae06a-116">The following example uses code to generate a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="ae06a-117">V příkladu se vytvoří <xref:System.Windows.Controls.ToolTip> (`tt`) a přidruží ji k <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="ae06a-117">The example creates a <xref:System.Windows.Controls.ToolTip> (`tt`) and associates it with a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 <span data-ttu-id="ae06a-118">Můžete také vytvořit popisek obsah, který není definován jako <xref:System.Windows.Controls.ToolTip> objekt uzavřením popis obsahu v elementu rozložení, jako například <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="ae06a-118">You can also create tooltip content that is not defined as a <xref:System.Windows.Controls.ToolTip> object by enclosing the tooltip content in a layout element, such as a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="ae06a-119">Následující příklad ukazuje, jak nastavit <xref:System.Windows.FrameworkElement.ToolTip%2A> vlastnost <xref:System.Windows.Controls.TextBox> s obsahem, který je uzavřen v <xref:System.Windows.Controls.DockPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ae06a-119">The following example shows how to set the <xref:System.Windows.FrameworkElement.ToolTip%2A> property of a <xref:System.Windows.Controls.TextBox> to content that is enclosed in a <xref:System.Windows.Controls.DockPanel> control.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a><span data-ttu-id="ae06a-120">Pomocí vlastnosti popisku a ToolTipService třídy</span><span class="sxs-lookup"><span data-stu-id="ae06a-120">Using the Properties of the ToolTip and ToolTipService Classes</span></span>  
 <span data-ttu-id="ae06a-121">Popis obsahu můžete upravit nastavení visual vlastností a použitím stylů.</span><span class="sxs-lookup"><span data-stu-id="ae06a-121">You can customize tooltip content by setting visual properties and applying styles.</span></span> <span data-ttu-id="ae06a-122">Pokud definujete obsahu jako popis <xref:System.Windows.Controls.ToolTip> objektu, můžete nastavit vizuální vlastnosti <xref:System.Windows.Controls.ToolTip> objektu.</span><span class="sxs-lookup"><span data-stu-id="ae06a-122">If you define the tooltip content as a <xref:System.Windows.Controls.ToolTip> object, you can set the visual properties of the <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="ae06a-123">V opačném případě je potřeba nastavit ekvivalentní připojené vlastnosti v <xref:System.Windows.Controls.ToolTipService> třídy.</span><span class="sxs-lookup"><span data-stu-id="ae06a-123">Otherwise, you must set equivalent attached properties on the <xref:System.Windows.Controls.ToolTipService> class.</span></span>  
  
 <span data-ttu-id="ae06a-124">Příklad toho, jak nastavit vlastnosti k určení pozice popisku obsah pomocí <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ToolTipService> vlastnosti, viz [umístění objektu ToolTip](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).</span><span class="sxs-lookup"><span data-stu-id="ae06a-124">For an example of how to set properties in order to specify the position of tooltip content by using the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> properties, see [Position a ToolTip](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).</span></span>  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a><span data-ttu-id="ae06a-125">Používání stylů pro popis tlačítka</span><span class="sxs-lookup"><span data-stu-id="ae06a-125">Styling a ToolTip</span></span>  
 <span data-ttu-id="ae06a-126">Můžete nastavit styl <xref:System.Windows.Controls.ToolTip> tak, že definujete vlastní <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="ae06a-126">You can style a <xref:System.Windows.Controls.ToolTip> by defining a custom <xref:System.Windows.Style>.</span></span> <span data-ttu-id="ae06a-127">Následující příklad definuje <xref:System.Windows.Style> volá `Simple` , který ukazuje, jak posun umístění <xref:System.Windows.Controls.ToolTip> a změňte jeho vzhled pomocí nastavení <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, a <xref:System.Windows.Controls.Control.FontWeight%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae06a-127">The following example defines a <xref:System.Windows.Style> called `Simple` that shows how to offset the placement of the <xref:System.Windows.Controls.ToolTip> and change its appearance by setting the <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, and <xref:System.Windows.Controls.Control.FontWeight%2A>.</span></span>  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a><span data-ttu-id="ae06a-128">Pomocí vlastnosti Interval doby ToolTipService</span><span class="sxs-lookup"><span data-stu-id="ae06a-128">Using the Time Interval Properties of ToolTipService</span></span>  
 <span data-ttu-id="ae06a-129"><xref:System.Windows.Controls.ToolTipService> Třída poskytuje následující vlastnosti lze nastavit popisek zobrazí časy: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, a <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae06a-129">The <xref:System.Windows.Controls.ToolTipService> class provides the following properties for you to set tooltip display times: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span></span>  
  
 <span data-ttu-id="ae06a-130">Použití <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> a <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> vlastnosti k určení zpoždění, obvykle (BRIEF), než <xref:System.Windows.Controls.ToolTip> se zobrazí a také k určení, jak dlouho <xref:System.Windows.Controls.ToolTip> zůstává viditelná.</span><span class="sxs-lookup"><span data-stu-id="ae06a-130">Use the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> properties to specify a delay, typically brief, before a <xref:System.Windows.Controls.ToolTip> appears and also to specify how long a <xref:System.Windows.Controls.ToolTip> remains visible.</span></span> <span data-ttu-id="ae06a-131">Další informace najdete v tématu [jak: Prodleva zobrazení popisu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ae06a-131">For more information, see [How to: Delay the Display of a ToolTip](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90)).</span></span>  
  
 <span data-ttu-id="ae06a-132"><xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> Vlastnost určuje, pokud popisky dat pro různé ovládací prvky se zobrazí počáteční neprodleně při přesunutí ukazatele myši rychle mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="ae06a-132">The <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property determines if tooltips for different controls appear without an initial delay when you move the mouse pointer quickly between them.</span></span> <span data-ttu-id="ae06a-133">Další informace o <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> vlastnost, naleznete v tématu [používání vlastnosti BetweenShowDelay](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).</span><span class="sxs-lookup"><span data-stu-id="ae06a-133">For more information about the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property, see [Use the BetweenShowDelay Property](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).</span></span>  
  
 <span data-ttu-id="ae06a-134">Následující příklad ukazuje, jak nastavit tyto vlastnosti pro popis.</span><span class="sxs-lookup"><span data-stu-id="ae06a-134">The following example shows how to set these properties for a tooltip.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="ae06a-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae06a-135">See also</span></span>
- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [<span data-ttu-id="ae06a-136">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="ae06a-136">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
