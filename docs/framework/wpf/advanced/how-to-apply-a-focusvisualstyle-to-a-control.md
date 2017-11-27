---
title: "Postupy: Použití FocusVisualStyle na ovládací prvek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f614e244293d08cd836edaf82496ca9e7b51423e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="54dc2-102">Postupy: Použití FocusVisualStyle na ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="54dc2-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="54dc2-103">Tento příklad ukazuje, jak vytvořit vizuální styl fokusu v prostředky a použít styl do ovládacího prvku pomocí <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="54dc2-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54dc2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="54dc2-104">Example</span></span>  
 <span data-ttu-id="54dc2-105">V následujícím příkladu definuje styl, který vytvoří skládání další ovládací prvek, který se vztahuje pouze pokud je tento řízení klávesnice zaměřuje v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54dc2-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="54dc2-106">Toho dosahuje tak, že definujete styl se <xref:System.Windows.Controls.ControlTemplate>, pak odkazující na daný styl jako prostředek, při nastavení <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="54dc2-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="54dc2-107">Externí obdélníku, ohraničení tvaru je umístěn mimo obdélníkovou oblast.</span><span class="sxs-lookup"><span data-stu-id="54dc2-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="54dc2-108">Pokud jinak upraven, velikost styl používá <xref:System.Windows.FrameworkElement.ActualHeight%2A> a <xref:System.Windows.FrameworkElement.ActualWidth%2A> obdélníková ovládacího prvku, kde se použije vizuální styl fokus.</span><span class="sxs-lookup"><span data-stu-id="54dc2-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="54dc2-109">Tento příklad nastavuje záporné hodnoty <xref:System.Windows.FrameworkElement.Margin%2A> aby ohraničení zobrazí mírně mimo cílených ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="54dc2-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="54dc2-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> je sčítání žádné šablony styl ovládací prvek, který pochází buď z explicitní styl nebo styl motiv; primární styl pro ovládací prvek stále možné vytvářet pomocí <xref:System.Windows.Controls.ControlTemplate> a nastavení na této styl <xref:System.Windows.FrameworkElement.Style%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="54dc2-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="54dc2-111">Fokus vizuální styly by měl použít konzistentně napříč motiv nebo uživatelského rozhraní, nikoli pomocí jiného pro každý element může získat fokus.</span><span class="sxs-lookup"><span data-stu-id="54dc2-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="54dc2-112">Podrobnosti najdete v tématu [styly pro výběr v ovládacích prvcích a FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).</span><span class="sxs-lookup"><span data-stu-id="54dc2-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54dc2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="54dc2-113">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [<span data-ttu-id="54dc2-114">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="54dc2-114">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="54dc2-115">Styly pro výběr v ovládacích prvcích a FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="54dc2-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)
