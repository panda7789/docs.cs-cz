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
ms.openlocfilehash: 6d8c1bb5cd133b2ee9d50a7e851d2ca3b4fff023
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368883"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Postupy: Animace umístění a barvy ukončení přechodu
Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.GradientStop.Color%2A> a <xref:System.Windows.Media.GradientStop.Offset%2A> z <xref:System.Windows.Media.GradientStop> objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad animuje tři Přechodové zarážky dovnitř <xref:System.Windows.Media.LinearGradientBrush>. V příkladu tři animace, z nichž každý animuje různé Přechodové zarážky:  
  
-   První animace <xref:System.Windows.Media.Animation.DoubleAnimation>, animuje první ukončení přechodu <xref:System.Windows.Media.GradientStop.Offset%2A> od 0.0 do 1.0 a pak zpátky 0,0. V důsledku toho první barvy v přechodu staffhubu od levého okraje pravé části obdélníku a pak zpátky na levé straně.  
  
-   Druhé animace <xref:System.Windows.Media.Animation.ColorAnimation>, animuje druhý ukončení přechodu <xref:System.Windows.Media.GradientStop.Color%2A> z <xref:System.Windows.Media.Colors.Purple%2A> k <xref:System.Windows.Media.Colors.Yellow%2A> a pak zpátky <xref:System.Windows.Media.Colors.Purple%2A>. Prostřední barva přechodu v důsledku toho změní z nachová na žlutou a zpět na fialový.  
  
-   Třetí animace jiného <xref:System.Windows.Media.Animation.ColorAnimation>, animuje krytí třetí ukončení přechodu <xref:System.Windows.Media.GradientStop.Color%2A> podle -1 a pak zpátky. V důsledku toho třetí barev v gradientu zmizí a pak stane neprůhledné.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Přestože tento příklad používá <xref:System.Windows.Media.LinearGradientBrush>, proces je stejný pro animaci <xref:System.Windows.Media.GradientStop> objektů uvnitř <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Další příklady najdete v článku [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.GradientStop>
- [Přehled animace](animation-overview.md)
- [Přehled scénářů](storyboards-overview.md)
