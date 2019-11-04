---
title: NavigationWindow – styly a šablony
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
ms.openlocfilehash: 4aae14299b3959e7d2122991954cc62505d2a19e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460201"
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="56027-102">NavigationWindow – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="56027-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="56027-103">Toto téma popisuje styly a šablony pro ovládací prvek <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="56027-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="56027-104">Výchozí <xref:System.Windows.Controls.ControlTemplate> můžete změnit tak, aby měl ovládací prvek jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="56027-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="56027-105">Další informace najdete v tématu [přizpůsobení vzhledu existujícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="56027-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="56027-106">Objektu NavigationWindow části</span><span class="sxs-lookup"><span data-stu-id="56027-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="56027-107">V následující tabulce jsou uvedeny pojmenované části ovládacího prvku <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="56027-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="56027-108">Částí</span><span class="sxs-lookup"><span data-stu-id="56027-108">Part</span></span>|<span data-ttu-id="56027-109">Typ</span><span class="sxs-lookup"><span data-stu-id="56027-109">Type</span></span>|<span data-ttu-id="56027-110">Popis</span><span class="sxs-lookup"><span data-stu-id="56027-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="56027-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="56027-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="56027-112">Oblast obsahu.</span><span class="sxs-lookup"><span data-stu-id="56027-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="56027-113">Objektu NavigationWindow stavy</span><span class="sxs-lookup"><span data-stu-id="56027-113">NavigationWindow States</span></span>  
 <span data-ttu-id="56027-114">V následující tabulce jsou uvedeny vizuální stavy pro ovládací prvek <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="56027-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="56027-115">Název VisualState</span><span class="sxs-lookup"><span data-stu-id="56027-115">VisualState Name</span></span>|<span data-ttu-id="56027-116">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="56027-116">VisualStateGroup Name</span></span>|<span data-ttu-id="56027-117">Popis</span><span class="sxs-lookup"><span data-stu-id="56027-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="56027-118">Platné</span><span class="sxs-lookup"><span data-stu-id="56027-118">Valid</span></span>|<span data-ttu-id="56027-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="56027-119">ValidationStates</span></span>|<span data-ttu-id="56027-120">Ovládací prvek používá třídu <xref:System.Windows.Controls.Validation> a vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `false`.</span><span class="sxs-lookup"><span data-stu-id="56027-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="56027-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="56027-121">InvalidFocused</span></span>|<span data-ttu-id="56027-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="56027-122">ValidationStates</span></span>|<span data-ttu-id="56027-123">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="56027-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="56027-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="56027-124">InvalidUnfocused</span></span>|<span data-ttu-id="56027-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="56027-125">ValidationStates</span></span>|<span data-ttu-id="56027-126">Vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojena je `true` má ovládací prvek fokus.</span><span class="sxs-lookup"><span data-stu-id="56027-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="56027-127">Objektu NavigationWindow ControlTemplate – příklad</span><span class="sxs-lookup"><span data-stu-id="56027-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="56027-128">I když tento příklad obsahuje všechny prvky, které jsou definovány v <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Navigation.NavigationWindow> ve výchozím nastavení, konkrétní hodnoty by se měly představit jako příklady.</span><span class="sxs-lookup"><span data-stu-id="56027-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="56027-129">Předchozí příklad používá jeden nebo více následujících zdrojů.</span><span class="sxs-lookup"><span data-stu-id="56027-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="56027-130">Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="56027-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56027-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56027-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="56027-132">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="56027-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="56027-133">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="56027-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="56027-134">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="56027-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="56027-135">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="56027-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
