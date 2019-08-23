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
ms.openlocfilehash: 2d18f395974750a6b85458f636a27f6101e7978f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951338"
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="c846d-102">Postupy: Interaktivní řízení hodin</span><span class="sxs-lookup"><span data-stu-id="c846d-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="c846d-103">Vlastnost<xref:System.Windows.Media.Animation.ClockController>objektuumožňuje interaktivně spustit, pozastavit, obnovit, vyhledat, posunout hodiny do doby jejich vyplňování a zastavovat hodiny. <xref:System.Windows.Media.Animation.Clock></span><span class="sxs-lookup"><span data-stu-id="c846d-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="c846d-104">Pouze kořenové hodiny stromu časování lze interaktivně kontrolovat.</span><span class="sxs-lookup"><span data-stu-id="c846d-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c846d-105">Existují i jiné způsoby, jak interaktivně kontrolovat animace, které nevyžadují přímou práci s hodinami: můžete také použít scénáře.</span><span class="sxs-lookup"><span data-stu-id="c846d-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="c846d-106">Scénáře jsou podporovány v kódu i kódu.</span><span class="sxs-lookup"><span data-stu-id="c846d-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="c846d-107">Příklad naleznete v tématu [animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md) nebo [přehledu animace](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c846d-107">For an example, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="c846d-108">V následujícím příkladu se pro interaktivní řízení hodin animací používá několik tlačítek.</span><span class="sxs-lookup"><span data-stu-id="c846d-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c846d-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="c846d-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="c846d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c846d-110">See also</span></span>

- [<span data-ttu-id="c846d-111">Animace vlastnosti pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="c846d-111">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="c846d-112">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="c846d-112">Animation Overview</span></span>](animation-overview.md)
