---
title: 'Postupy: Definice a odkaz zdroje'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 322ac3e5ebfe2d820a4711d877396b9a1a2759a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-and-reference-a-resource"></a><span data-ttu-id="3069e-102">Postupy: Definice a odkaz zdroje</span><span class="sxs-lookup"><span data-stu-id="3069e-102">How to: Define and Reference a Resource</span></span>
<span data-ttu-id="3069e-103">Tento příklad ukazuje, jak definovat prostředku a odkazovat pomocí atributu v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3069e-103">This example shows how to define a resource and reference it by using an attribute in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="3069e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3069e-104">Example</span></span>  
 <span data-ttu-id="3069e-105">V následujícím příkladu definuje dva typy prostředků: <xref:System.Windows.Media.SolidColorBrush> prostředků a několik <xref:System.Windows.Style> prostředky.</span><span class="sxs-lookup"><span data-stu-id="3069e-105">The following example defines two types of resources: a <xref:System.Windows.Media.SolidColorBrush> resource, and several <xref:System.Windows.Style> resources.</span></span> <span data-ttu-id="3069e-106"><xref:System.Windows.Media.SolidColorBrush> Prostředků `MyBrush` slouží k poskytování hodnotu několik vlastností, že každý trvat <xref:System.Windows.Media.Brush> zadejte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3069e-106">The <xref:System.Windows.Media.SolidColorBrush> resource `MyBrush` is used to provide the value of several properties that each take a <xref:System.Windows.Media.Brush> type value.</span></span> <span data-ttu-id="3069e-107"><xref:System.Windows.Style> Prostředky `PageBackground`, `TitleText` a `Label` každý cílí na určitý ovládací prvek typu.</span><span class="sxs-lookup"><span data-stu-id="3069e-107">The <xref:System.Windows.Style> resources `PageBackground`, `TitleText` and `Label` each target a particular control type.</span></span> <span data-ttu-id="3069e-108">Styly nastavit celou řadu jiné vlastnosti na cílové ovládacích prvků, když styl prostředku je odkazován objektem klíč prostředku a slouží k nastavení <xref:System.Windows.FrameworkElement.Style%2A> vlastnost několik konkrétní ovládací prvky, které jsou definované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3069e-108">The styles set a variety of different properties on the targeted controls, when that style resource is referenced by resource key and is used to set the <xref:System.Windows.FrameworkElement.Style%2A> property of several specific control elements defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="3069e-109">Všimněte si, že jedna z vlastností v rámci nastavením `Label` styl také odkazuje `MyBrush` prostředků definovaného dříve.</span><span class="sxs-lookup"><span data-stu-id="3069e-109">Note that one of the properties within the setters of the `Label` style also references the `MyBrush` resource defined earlier.</span></span> <span data-ttu-id="3069e-110">To je běžné technika, ale je důležité si pamatovat, že jsou analyzovat a zadán do slovník prostředků, a pořadí, které jsou uvedené prostředky.</span><span class="sxs-lookup"><span data-stu-id="3069e-110">This is a common technique, but it is important to remember that resources are parsed and entered into a resource dictionary in the order that they are given.</span></span> <span data-ttu-id="3069e-111">Prostředky jsou také požadoval pořadí v rámci slovníku nalezen, pokud použijete [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) Chcete-li je ze v rámci jiný prostředek.</span><span class="sxs-lookup"><span data-stu-id="3069e-111">Resources are also requested by the order found within the dictionary if you use the [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) to reference them from within another resource.</span></span> <span data-ttu-id="3069e-112">Ujistěte se, že jakémukoli prostředku, který odkazujete je definována dříve v rámci kolekce prostředků než kde je pak požadovaný prostředku.</span><span class="sxs-lookup"><span data-stu-id="3069e-112">Make sure that any resource that you reference is defined earlier within the resources collection than where that resource is then requested.</span></span> <span data-ttu-id="3069e-113">Pokud potřeby můžete obejít pořadí striktní vytváření prostředků refererences pomocí [DynamicResource – rozšíření značek](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) tak, aby odkazovaly prostředků v době běhu místo toho byste měli vědět, ale který tento DynamicResource technika má důsledky výkonu.</span><span class="sxs-lookup"><span data-stu-id="3069e-113">If necessary, you can work around the strict creation order of resource refererences by using a [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) to reference the resource at runtime instead, but you should be aware that this DynamicResource technique has performance consequences.</span></span> <span data-ttu-id="3069e-114">Podrobnosti najdete v tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="3069e-114">For details, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a><span data-ttu-id="3069e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3069e-115">See Also</span></span>  
 [<span data-ttu-id="3069e-116">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="3069e-116">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="3069e-117">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="3069e-117">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
