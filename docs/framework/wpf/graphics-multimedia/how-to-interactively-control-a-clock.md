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
# <a name="how-to-interactively-control-a-clock"></a>Postupy: Interaktivní řízení hodin
Vlastnost<xref:System.Windows.Media.Animation.ClockController>objektuumožňuje interaktivně spustit, pozastavit, obnovit, vyhledat, posunout hodiny do doby jejich vyplňování a zastavovat hodiny. <xref:System.Windows.Media.Animation.Clock> Pouze kořenové hodiny stromu časování lze interaktivně kontrolovat.  
  
> [!NOTE]
> Existují i jiné způsoby, jak interaktivně kontrolovat animace, které nevyžadují přímou práci s hodinami: můžete také použít scénáře. Scénáře jsou podporovány v kódu i kódu. Příklad naleznete v tématu [animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md) nebo [přehledu animace](animation-overview.md).  
  
 V následujícím příkladu se pro interaktivní řízení hodin animací používá několik tlačítek.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>Viz také:

- [Animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md)
- [Přehled animace](animation-overview.md)
