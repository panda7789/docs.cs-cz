---
title: 'Postupy: Vykreslení oblasti radiálním přechodem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 8a53d5d7247f82905816265f7c92b22f287591c5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452750"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>Postupy: Vykreslení oblasti radiálním přechodem
Tento příklad ukazuje, jak použít třídu <xref:System.Windows.Media.RadialGradientBrush> k vykreslení oblasti s paprskovým přechodem.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.RadialGradientBrush> k vykreslení obdélníku s paprskovým přechodem, který přechází ze žluté na červenou na modrou zelenou.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 Následující ilustrace znázorňuje přechod z předchozího příkladu. Byla zvýrazněna zastávka přechodu.  
  
 ![Přechodové zarážky v paprskovém přechodu](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
> Příklady v tomto tématu používají výchozí systém souřadnic pro nastavení řídicích bodů. Výchozí souřadnicový systém je relativní vzhledem k ohraničujícímu poli: 0 označuje 0 procent ohraničovacího rámečku a 1 označuje 100% ohraničovacího rámečku. Tento systém souřadnic můžete změnit nastavením vlastnosti <xref:System.Windows.Media.GradientBrush.MappingMode%2A> na hodnotu <xref:System.Windows.Media.BrushMappingMode.Absolute>. Absolutní souřadnicový systém není relativní vzhledem k ohraničujícímu poli. Hodnoty jsou interpretovány přímo v místním prostoru.  
  
 Další příklady <xref:System.Windows.Media.RadialGradientBrush> naleznete v [ukázce štětce](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Další informace o přechodech a dalších typech štětců naleznete v tématu [Malování s plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md).
