---
title: 'Postupy: Změna rychlosti hodin bez úpravy rychlosti časové osy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- speed of Clock [WPF], changing
- clocks [WPF], changing speed of
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
ms.openlocfilehash: 126d260fbd59c1c35d8f56be6aa7dabe7688fa32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-speed-of-a-clock-without-changing-the-speed-of-its-timeline"></a>Postupy: Změna rychlosti hodin bez úpravy rychlosti časové osy
A <xref:System.Windows.Media.Animation.ClockController> objektu <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> vlastnost umožňuje změnit rychlosti <xref:System.Windows.Media.Animation.Clock> beze změny <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> hodin na <xref:System.Windows.Media.Animation.Timeline>. V následujícím příkladu <xref:System.Windows.Media.Animation.ClockController> slouží k úpravě interaktivně <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> hodin. <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> Události a na hodinách <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> vlastnost slouží k zobrazení taktovací aktuální globální pokaždé, když jeho interaktivní <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> se změnilo.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]
