---
title: "Postupy: Interaktivní řízení hodin"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: debe65ef1587171dc2f324a19da4b43e7274c438
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="10815-102">Postupy: Interaktivní řízení hodin</span><span class="sxs-lookup"><span data-stu-id="10815-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="10815-103">A <xref:System.Windows.Media.Animation.Clock> objektu <xref:System.Windows.Media.Animation.ClockController> vlastnost umožňuje interaktivně spuštění, pozastavení, obnovení, Hledat, posunutí hodiny na jeho výplně období a zastavte hodiny.</span><span class="sxs-lookup"><span data-stu-id="10815-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="10815-104">Pouze kořenové hodiny stromu časování lze řídit interaktivně.</span><span class="sxs-lookup"><span data-stu-id="10815-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10815-105">Existují další způsoby, jak interaktivně ovládacího prvku animace, které nevyžadují pracovat přímo s hodiny: Můžete taky scénářů.</span><span class="sxs-lookup"><span data-stu-id="10815-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="10815-106">Scénářů jsou podporovány v značek a kódu.</span><span class="sxs-lookup"><span data-stu-id="10815-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="10815-107">Příklad, naleznete v části [animace vlastnost pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) nebo [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="10815-107">For an example, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
 <span data-ttu-id="10815-108">V následujícím příkladu je možné několik tlačítka interaktivně určit hodiny animace.</span><span class="sxs-lookup"><span data-stu-id="10815-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10815-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="10815-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="10815-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="10815-110">See Also</span></span>  
 [<span data-ttu-id="10815-111">Animace vlastnost pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="10815-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="10815-112">Animace – přehled</span><span class="sxs-lookup"><span data-stu-id="10815-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
