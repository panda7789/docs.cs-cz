---
title: "Postupy: Změna rychlosti hodin bez úpravy rychlosti časové osy"
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
- speed of Clock [WPF], changing
- clocks [WPF], changing speed of
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 98cfa63eac4bc697c5412616de71395624408c63
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-speed-of-a-clock-without-changing-the-speed-of-its-timeline"></a><span data-ttu-id="79929-102">Postupy: Změna rychlosti hodin bez úpravy rychlosti časové osy</span><span class="sxs-lookup"><span data-stu-id="79929-102">How to: Change the Speed of a Clock Without Changing the Speed of Its Timeline</span></span>
<span data-ttu-id="79929-103">A <xref:System.Windows.Media.Animation.ClockController> objektu <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> vlastnost umožňuje změnit rychlosti <xref:System.Windows.Media.Animation.Clock> beze změny <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> hodin na <xref:System.Windows.Media.Animation.Timeline>.</span><span class="sxs-lookup"><span data-stu-id="79929-103">A <xref:System.Windows.Media.Animation.ClockController> object's <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> property enables you to change the speed of a <xref:System.Windows.Media.Animation.Clock> without altering the <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> of the clock's <xref:System.Windows.Media.Animation.Timeline>.</span></span> <span data-ttu-id="79929-104">V následujícím příkladu <xref:System.Windows.Media.Animation.ClockController> slouží k úpravě interaktivně <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> hodin.</span><span class="sxs-lookup"><span data-stu-id="79929-104">In the following example, a <xref:System.Windows.Media.Animation.ClockController> is used to interactively modify the <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> of a clock.</span></span> <span data-ttu-id="79929-105"><xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> Události a na hodinách <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> vlastnost slouží k zobrazení taktovací aktuální globální pokaždé, když jeho interaktivní <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> se změnilo.</span><span class="sxs-lookup"><span data-stu-id="79929-105">The <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> event and the clock's <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> property are used to display the clock's current global speed each time its interactive <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> is changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79929-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="79929-106">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]
