---
title: 'Postupy: Animace ve stylu'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10cd243c633e7a7e458d2026fc5e3d91d2996427
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-in-a-style"></a><span data-ttu-id="ee73b-102">Postupy: Animace ve stylu</span><span class="sxs-lookup"><span data-stu-id="ee73b-102">How to: Animate in a Style</span></span>
<span data-ttu-id="ee73b-103">Tento příklad ukazuje postup animace vlastnosti v rámci styl.</span><span class="sxs-lookup"><span data-stu-id="ee73b-103">This example shows how to animate properties within a style.</span></span> <span data-ttu-id="ee73b-104">Při animaci v rámci styl, pro který je definován styl jenom element framework můžete použít přímo.</span><span class="sxs-lookup"><span data-stu-id="ee73b-104">When animating within a style, only the framework element for which the style is defined can be targeted directly.</span></span> <span data-ttu-id="ee73b-105">Pokud chcete zacílit zmrazitelné objekt, můžete musí "dot dolů" z vlastnosti stylem elementu.</span><span class="sxs-lookup"><span data-stu-id="ee73b-105">To target a freezable object, you must "dot down" from a property of the styled element.</span></span>  
  
 <span data-ttu-id="ee73b-106">V následujícím příkladu jsou definovány v rámci styl a použity pro několik animace <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="ee73b-106">In the following example, several animations are defined within a style and applied to a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="ee73b-107">Když se uživatel přesune na tlačítko myši, je oznámení neprůhledných a částečně průhledné pozadí znovu, opakovaně.</span><span class="sxs-lookup"><span data-stu-id="ee73b-107">When the user moves the mouse over the button, it fades from opaque to partially translucent and back again, repeatedly.</span></span> <span data-ttu-id="ee73b-108">Pokud se uživatel přesune mimo tlačítko myši, stane se zcela neprůhledný.</span><span class="sxs-lookup"><span data-stu-id="ee73b-108">When the user moves the mouse off the button, it becomes completely opaque.</span></span> <span data-ttu-id="ee73b-109">Při kliknutí na tlačítko Barva jeho pozadí změní z oranžová bílé a zálohovat znovu.</span><span class="sxs-lookup"><span data-stu-id="ee73b-109">When the button is clicked, its background color changes from orange to white and back again.</span></span> <span data-ttu-id="ee73b-110">Protože <xref:System.Windows.Media.SolidColorBrush> použita k vyplnění tlačítko nemůžou být cílem přímo, je přístupný pomocí dotting dolů z tlačítka <xref:System.Windows.Controls.Control.Background%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ee73b-110">Because the <xref:System.Windows.Media.SolidColorBrush> used to paint the button can't be targeted directly, it is accessed by dotting down from the button's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee73b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee73b-111">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 <span data-ttu-id="ee73b-112">Všimněte si, že při animaci v rámci styl, je možné cílové objekty, které neexistují.</span><span class="sxs-lookup"><span data-stu-id="ee73b-112">Note that when animating within a style, it's possible to target objects that don't exist.</span></span> <span data-ttu-id="ee73b-113">Předpokládejme například, používá vaše styl <xref:System.Windows.Media.SolidColorBrush> nastavit vlastnost tlačítkem na pozadí, ale na některé bodu styl přepsáno a pozadí na tlačítko nastavena <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="ee73b-113">For example, suppose your style uses a <xref:System.Windows.Media.SolidColorBrush> to set a Button's background property, but at some point the style is overridden and the button's background is set with a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="ee73b-114">Při pokusu o animace <xref:System.Windows.Media.SolidColorBrush> nebude vyvolat výjimku; animace se jednoduše nezdaří bez upozornění.</span><span class="sxs-lookup"><span data-stu-id="ee73b-114">Trying to animate the <xref:System.Windows.Media.SolidColorBrush> won't throw an exception; the animation will simply fail silently.</span></span>  
  
 <span data-ttu-id="ee73b-115">Další informace o storyboard cílení na syntaxi najdete v článku [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ee73b-115">Fore more information about storyboard targeting syntax, see the [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span> <span data-ttu-id="ee73b-116">Další informace o animace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ee73b-116">For more information about animation, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="ee73b-117">Další informace o styly najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="ee73b-117">For more information about styles, see the [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>
