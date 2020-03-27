---
title: 'Postupy: Animace tloušťky ohraničení použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 884b62e88c347449ae39caa9c028d09db39b9f4b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344696"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>Postupy: Animace tloušťky ohraničení použitím klíčových snímků
Tento příklad ukazuje, jak <xref:System.Windows.Controls.Control.BorderThickness%2A> animovat vlastnost <xref:System.Windows.Controls.Border>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> třídu k <xref:System.Windows.Controls.Control.BorderThickness%2A> animaci vlastnosti <xref:System.Windows.Controls.Border>. Tato animace používá tři klíčové snímky následujícím způsobem:  
  
1. Během první poloviny sekundy používá <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> instanci třídy postupně zvyšovat tloušťku ohraničení. Příklad používá <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> k vytvoření hladkého lineárního zvýšení mezi hodnotami.  
  
2. Na konci další poloviny sekundy, používá <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> instance třídy náhle zvýšit tloušťku ohraničení. Diskrétní klíčové snímky, jako jsou <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> ty, které jsou odvozeny z vytvoření náhlé skoky mezi hodnotami, to znamená, že pohyb animace je trhané.  
  
3. Během posledních dvou sekund, používá <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> instance třídy ke snížení tloušťky ohraničení. Klíčové snímky spline, jako <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> jsou ty, které jsou odvozeny <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> z vytvoření proměnné přechodu mezi hodnotami podle hodnot vlastnosti. V tomto klíčovém snímku animace začíná pomalu a exponenciálně urychluje ke konci časového segmentu.  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
- [Animace hodnoty BorderThickness](../controls/how-to-animate-a-borderthickness-value.md)
