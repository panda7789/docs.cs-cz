---
title: 'Postupy: Interaktivní řízení hodin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 05989b6a03e03fb5723a70c9c36d5e32f9117049
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186586"
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="42066-102">Postupy: Interaktivní řízení hodin</span><span class="sxs-lookup"><span data-stu-id="42066-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="42066-103">A <xref:System.Windows.Media.Animation.Clock> objektu <xref:System.Windows.Media.Animation.ClockController> vlastnost umožňuje interaktivně spuštění, pozastavení, obnovení, hledání, předem hodiny tak, aby svůj a zastavte hodiny.</span><span class="sxs-lookup"><span data-stu-id="42066-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="42066-104">Jenom kořenový hodiny časování stromu lze interaktivně ovládat.</span><span class="sxs-lookup"><span data-stu-id="42066-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42066-105">Existují jiné způsoby, jak interaktivně ovládacího prvku animace, které nevyžadují pracovat přímo s hodiny: můžete použít také scénáře.</span><span class="sxs-lookup"><span data-stu-id="42066-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="42066-106">Scénáře jsou podporovány v značek a kódu.</span><span class="sxs-lookup"><span data-stu-id="42066-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="42066-107">Příklad najdete v tématu [animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md) nebo [přehled animace](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="42066-107">For an example, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="42066-108">V následujícím příkladu se používají několik tlačítek na interaktivní řízení hodin animace.</span><span class="sxs-lookup"><span data-stu-id="42066-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42066-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="42066-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="42066-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42066-110">See also</span></span>

- [<span data-ttu-id="42066-111">Animace vlastnosti pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="42066-111">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="42066-112">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="42066-112">Animation Overview</span></span>](animation-overview.md)
