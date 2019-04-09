---
title: 'Postupy: Použití FocusVisualStyle na ovládací prvek'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: 53d4984946143c15c4a2b71095529fb5ee7de4b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133546"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="9536e-102">Postupy: Použití FocusVisualStyle na ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="9536e-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="9536e-103">Tento příklad ukazuje, jak vytvořit vizuální styl fokusu na prostředcích a použít styl na ovládací prvek, pomocí <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9536e-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9536e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9536e-104">Example</span></span>  
 <span data-ttu-id="9536e-105">Následující příklad definuje styl, který vytvoří skládání další ovládací prvek, který platí, pouze pokud je tento ovládací prvek klávesnice, zaměřuje v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9536e-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="9536e-106">To lze provést definováním style, jehož <xref:System.Windows.Controls.ControlTemplate>, ten pak odkazovat tento styl jako prostředek, při nastavení <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9536e-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="9536e-107">Externí obdélník podobné ohraničení je umístěn mimo oblasti obdélníkový.</span><span class="sxs-lookup"><span data-stu-id="9536e-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="9536e-108">Není-li jinak upraven, velikosti styl používá <xref:System.Windows.FrameworkElement.ActualHeight%2A> a <xref:System.Windows.FrameworkElement.ActualWidth%2A> obdélníkové ovládacího prvku, ve kterém se použije vizuální styl fokusu.</span><span class="sxs-lookup"><span data-stu-id="9536e-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="9536e-109">V tomto příkladu nastaví záporné hodnoty <xref:System.Windows.FrameworkElement.Margin%2A> provádět mírně zobrazují mimo cílené ovládací prvek ohraničení.</span><span class="sxs-lookup"><span data-stu-id="9536e-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="9536e-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> je sčítání jakýkoli styl šablony ovládacího prvku, který přichází z explicitní styl nebo stylu motivu; primární stylu pro ovládací prvek může stále možné vytvořit pomocí <xref:System.Windows.Controls.ControlTemplate> a nastavení na hodnotu stylu <xref:System.Windows.FrameworkElement.Style%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9536e-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="9536e-111">Fokus vizuální styly by měly být používány konzistentně napříč motiv nebo uživatelské rozhraní, místo použití jinou používat pro každý prvek může získat fokus.</span><span class="sxs-lookup"><span data-stu-id="9536e-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="9536e-112">Podrobnosti najdete v tématu [stylů pro fokus v ovládacích prvcích a FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).</span><span class="sxs-lookup"><span data-stu-id="9536e-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9536e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9536e-113">See also</span></span>

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [<span data-ttu-id="9536e-114">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="9536e-114">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="9536e-115">Nastavení stylů pro fokus v ovládacích prvcích a FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="9536e-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](styling-for-focus-in-controls-and-focusvisualstyle.md)
