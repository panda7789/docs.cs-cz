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
# <a name="how-to-interactively-control-a-clock"></a>Postupy: Interaktivní řízení hodin
A <xref:System.Windows.Media.Animation.Clock> objektu <xref:System.Windows.Media.Animation.ClockController> vlastnost umožňuje interaktivně spuštění, pozastavení, obnovení, hledání, předem hodiny tak, aby svůj a zastavte hodiny. Jenom kořenový hodiny časování stromu lze interaktivně ovládat.  
  
> [!NOTE]
>  Existují jiné způsoby, jak interaktivně ovládacího prvku animace, které nevyžadují pracovat přímo s hodiny: můžete použít také scénáře. Scénáře jsou podporovány v značek a kódu. Příklad najdete v tématu [animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md) nebo [přehled animace](animation-overview.md).  
  
 V následujícím příkladu se používají několik tlačítek na interaktivní řízení hodin animace.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>Viz také:

- [Animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md)
- [Přehled animace](animation-overview.md)
