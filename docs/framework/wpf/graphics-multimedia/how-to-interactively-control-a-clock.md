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
ms.openlocfilehash: 93c2d754ec899c96a50fef3dcef680434f564276
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657542"
---
# <a name="how-to-interactively-control-a-clock"></a>Postupy: Interaktivní řízení hodin
A <xref:System.Windows.Media.Animation.Clock> objektu <xref:System.Windows.Media.Animation.ClockController> vlastnost umožňuje interaktivně spuštění, pozastavení, obnovení, hledání, předem hodiny tak, aby svůj a zastavte hodiny. Jenom kořenový hodiny časování stromu lze interaktivně ovládat.  
  
> [!NOTE]
>  Existují jiné způsoby, jak interaktivně ovládacího prvku animace, které nevyžadují pracovat přímo s hodiny: můžete použít také scénáře. Scénáře jsou podporovány v značek a kódu. Příklad najdete v tématu [animace vlastnosti pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) nebo [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 V následujícím příkladu se používají několik tlačítek na interaktivní řízení hodin animace.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>Viz také:
- [Animace vlastnosti pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)
- [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
