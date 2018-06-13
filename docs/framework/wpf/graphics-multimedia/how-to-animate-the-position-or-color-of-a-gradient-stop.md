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
ms.openlocfilehash: 2eb528127c8aa66976788ec1f4e5362ca3a1ef26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558665"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Postupy: Animace umístění a barvy ukončení přechodu
Tento příklad ukazuje, jak animace <xref:System.Windows.Media.GradientStop.Color%2A> a <xref:System.Windows.Media.GradientStop.Offset%2A> z <xref:System.Windows.Media.GradientStop> objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad animuje tři ukončení přechodu uvnitř <xref:System.Windows.Media.LinearGradientBrush>. Tento příklad používá tři animací, z nichž každý animuje různé Přechodové zarážky:  
  
-   První animace <xref:System.Windows.Media.Animation.DoubleAnimation>, animuje první Přechodové zarážky <xref:System.Windows.Media.GradientStop.Offset%2A> od 0,0 do 1,0 a pak zpátky na 0,0. V důsledku toho první barvu v přechodu posuny z levé strany na pravé straně obdélníku a pak zpátky na levé straně.  
  
-   Druhý animace <xref:System.Windows.Media.Animation.ColorAnimation>, animuje druhý Přechodové zarážky <xref:System.Windows.Media.GradientStop.Color%2A> z <xref:System.Windows.Media.Colors.Purple%2A> k <xref:System.Windows.Media.Colors.Yellow%2A> a pak zpátky na <xref:System.Windows.Media.Colors.Purple%2A>. V důsledku toho změní střední barvu v přechodu z Fialová žlutý a zpět na fialový.  
  
-   Třetí animace jiné <xref:System.Windows.Media.Animation.ColorAnimation>, animuje krytí třetí Přechodové zarážky <xref:System.Windows.Media.GradientStop.Color%2A> podle -1 a pak zpátky. V důsledku toho třetí barvu v přechodu zmizí a pak stane neprůhledné.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 I když tento příklad používá <xref:System.Windows.Media.LinearGradientBrush>, proces je stejný pro animace <xref:System.Windows.Media.GradientStop> objekty uvnitř <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Další příklady najdete v tématu [štětce ukázka](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.GradientStop>  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
