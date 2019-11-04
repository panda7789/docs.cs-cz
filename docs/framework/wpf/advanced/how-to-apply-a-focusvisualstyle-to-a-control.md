---
title: 'Postupy: Použití FocusVisualStyle na ovládací prvek'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: b44330ee7554f953389556bd62ff49db120b5db9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459817"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="f0f68-102">Postupy: Použití FocusVisualStyle na ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="f0f68-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="f0f68-103">Tento příklad ukazuje, jak vytvořit vizuální styl fokusu v prostředcích a použít styl pro ovládací prvek pomocí vlastnosti <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0f68-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0f68-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0f68-104">Example</span></span>  
 <span data-ttu-id="f0f68-105">Následující příklad definuje styl, který vytváří další skládání ovládacího prvku, který je použit pouze v případě, že je tento ovládací prvek zaměřen na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0f68-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="f0f68-106">To je dosaženo definováním stylu pomocí <xref:System.Windows.Controls.ControlTemplate>a pak odkazem na tento styl jako prostředek při nastavení vlastnosti <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0f68-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="f0f68-107">Vnější obdélník, který se podobá ohraničení, je umístěn mimo obdélníkovou oblast.</span><span class="sxs-lookup"><span data-stu-id="f0f68-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="f0f68-108">Pokud není jinak změněno, velikost stylu používá <xref:System.Windows.FrameworkElement.ActualHeight%2A> a <xref:System.Windows.FrameworkElement.ActualWidth%2A> obdélníkového ovládacího prvku, kde je použit styl vizuálu fokusu.</span><span class="sxs-lookup"><span data-stu-id="f0f68-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="f0f68-109">V tomto příkladu jsou nastaveny záporné hodnoty pro <xref:System.Windows.FrameworkElement.Margin%2A>, aby se ohraničení mírně vytvářely mimo ovládací prvek s fokusem.</span><span class="sxs-lookup"><span data-stu-id="f0f68-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="f0f68-110"><xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> je aditivní pro libovolný styl šablony ovládacího prvku, který se nachází buď z explicitního stylu, nebo stylu motivu. primární styl ovládacího prvku lze stále vytvořit pomocí <xref:System.Windows.Controls.ControlTemplate> a nastavením tohoto stylu na vlastnost <xref:System.Windows.FrameworkElement.Style%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0f68-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="f0f68-111">Vizuální styly fokusu by se měly používat konzistentně napříč motivem nebo uživatelským rozhraním namísto použití jiného pro každý prvek s fokusem.</span><span class="sxs-lookup"><span data-stu-id="f0f68-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="f0f68-112">Podrobnosti najdete v tématu [styly pro fokus v ovládacích prvcích a FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).</span><span class="sxs-lookup"><span data-stu-id="f0f68-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f68-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0f68-113">See also</span></span>

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [<span data-ttu-id="f0f68-114">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="f0f68-114">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f0f68-115">Nastavení stylů pro fokus v ovládacích prvcích a FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="f0f68-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](styling-for-focus-in-controls-and-focusvisualstyle.md)
