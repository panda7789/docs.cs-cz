---
title: 'Postupy: Animace umístění a barvy ukončení přechodu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: aeae33f5f3c8016808988f58d61969e9b6f05039
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452841"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Postupy: Animace umístění a barvy ukončení přechodu
Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.GradientStop.Color%2A> a <xref:System.Windows.Media.GradientStop.Offset%2A> objektů <xref:System.Windows.Media.GradientStop>.  
  
## <a name="example"></a>Příklad  
 Následující příklad animuje tři zarážky přechodu v rámci <xref:System.Windows.Media.LinearGradientBrush>. V tomto příkladu se používají tři animace, z nichž každá animuje jiné zarážky přechodu:  
  
- První animace, <xref:System.Windows.Media.Animation.DoubleAnimation>, animuje první <xref:System.Windows.Media.GradientStop.Offset%2A> zastavení přechodu z 0,0 na 1,0 a pak zpět na 0,0. V důsledku toho se první barva v přechodu posouvá od levé strany obdélníku k pravé straně obdélníku a pak se vrátí na levou stranu.  
  
- Druhá animace, <xref:System.Windows.Media.Animation.ColorAnimation>, animuje druhé <xref:System.Windows.Media.GradientStop.Color%2A> zastavení přechodu z <xref:System.Windows.Media.Colors.Purple%2A> na <xref:System.Windows.Media.Colors.Yellow%2A> a následně zpět na <xref:System.Windows.Media.Colors.Purple%2A>. V důsledku toho se Prostřední barva v přechodu změní ze fialová na žlutou a zpátky na fialovou.  
  
- Třetí animace, další <xref:System.Windows.Media.Animation.ColorAnimation>, animuje neprůhlednost třetí <xref:System.Windows.Media.GradientStop.Color%2A> zastavení přechodu na-1 a pak zpět. V důsledku toho se třetí barva v přechodu zmizí a pak se znovu neprůhledná.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 I když tento příklad používá <xref:System.Windows.Media.LinearGradientBrush>, proces je stejný pro animování <xref:System.Windows.Media.GradientStop> objektů uvnitř <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Další příklady naleznete v [ukázce štětce](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.GradientStop>
- [Přehled animace](animation-overview.md)
- [Přehled scénářů](storyboards-overview.md)
