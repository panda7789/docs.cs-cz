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
ms.openlocfilehash: 32d8aac99d40693e66c7b52a6c7d2c116d2f3baf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225804"
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="42623-102">NavigationWindow – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="42623-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="42623-103">Toto téma popisuje styly a šablony pro <xref:System.Windows.Navigation.NavigationWindow> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="42623-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="42623-104">Můžete upravit výchozí <xref:System.Windows.Controls.ControlTemplate> poskytnout jedinečný vzhled ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="42623-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="42623-105">Další informace najdete v tématu [přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="42623-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="42623-106">NavigationWindow – částí</span><span class="sxs-lookup"><span data-stu-id="42623-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="42623-107">V následující tabulce jsou uvedeny pojmenované části pro <xref:System.Windows.Navigation.NavigationWindow> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="42623-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="42623-108">Část</span><span class="sxs-lookup"><span data-stu-id="42623-108">Part</span></span>|<span data-ttu-id="42623-109">Type</span><span class="sxs-lookup"><span data-stu-id="42623-109">Type</span></span>|<span data-ttu-id="42623-110">Popis</span><span class="sxs-lookup"><span data-stu-id="42623-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="42623-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="42623-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="42623-112">Oblasti pro obsah.</span><span class="sxs-lookup"><span data-stu-id="42623-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="42623-113">NavigationWindow – stavy</span><span class="sxs-lookup"><span data-stu-id="42623-113">NavigationWindow States</span></span>  
 <span data-ttu-id="42623-114">V následující tabulce jsou uvedeny vizuálních stavů pro <xref:System.Windows.Navigation.NavigationWindow> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="42623-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="42623-115">Název vizuálního stavu</span><span class="sxs-lookup"><span data-stu-id="42623-115">VisualState Name</span></span>|<span data-ttu-id="42623-116">Název VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="42623-116">VisualStateGroup Name</span></span>|<span data-ttu-id="42623-117">Popis</span><span class="sxs-lookup"><span data-stu-id="42623-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="42623-118">Platné</span><span class="sxs-lookup"><span data-stu-id="42623-118">Valid</span></span>|<span data-ttu-id="42623-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="42623-119">ValidationStates</span></span>|<span data-ttu-id="42623-120">Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídy a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je připojená vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="42623-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="42623-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="42623-121">InvalidFocused</span></span>|<span data-ttu-id="42623-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="42623-122">ValidationStates</span></span>|<span data-ttu-id="42623-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="42623-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="42623-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="42623-124">InvalidUnfocused</span></span>|<span data-ttu-id="42623-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="42623-125">ValidationStates</span></span>|<span data-ttu-id="42623-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Je připojená vlastnost `true` má ovládací prvek nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="42623-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="42623-127">NavigationWindow – příklad šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="42623-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="42623-128">I když v tomto příkladu obsahuje všechny prvky, které jsou definovány v <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Navigation.NavigationWindow> ve výchozím nastavení, by měla být konkrétní hodnoty představit jako příklady.</span><span class="sxs-lookup"><span data-stu-id="42623-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="42623-129">V předchozím příkladu používá jeden nebo více z následujících prostředků.</span><span class="sxs-lookup"><span data-stu-id="42623-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="42623-130">Úplnou ukázku najdete v tématu [stylu s ukázkou ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="42623-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42623-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42623-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="42623-132">Styly a šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="42623-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="42623-133">Přizpůsobení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="42623-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="42623-134">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="42623-134">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="42623-135">Přizpůsobení vzhledu stávajícího ovládacího prvku vytvořením šablony ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="42623-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
