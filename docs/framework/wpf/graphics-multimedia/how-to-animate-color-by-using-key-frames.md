---
title: 'Postupy: Animace barev použitím klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8a444706f7541b52722ab8257a88e76c3e1b0938
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344753"
---
# <a name="how-to-animate-color-by-using-key-frames"></a>Postupy: Animace barev použitím klíčových snímků
Tento příklad ukazuje, jak <xref:System.Windows.Media.SolidColorBrush.Color%2A> animovat of a <xref:System.Windows.Media.SolidColorBrush> pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> třídu k <xref:System.Windows.Media.SolidColorBrush.Color%2A> animaci vlastnosti <xref:System.Windows.Media.SolidColorBrush>. Tato animace používá tři klíčové snímky následujícím způsobem:  
  
1. Během prvních dvou sekund používá instanci <xref:System.Windows.Media.Animation.LinearColorKeyFrame> třídy k postupné změně barvy ze zelené na červenou. Lineární klíčové <xref:System.Windows.Media.Animation.LinearColorKeyFrame> snímky, jako je vytvoření hladkého lineárního přechodu mezi hodnotami.  
  
2. Na konci další půlsekundy použije instanci <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> třídy k rychlé změně barvy z červené na žlutou. Diskrétní klíčové snímky, <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> jako je vytvoření náhlých změn mezi hodnotami, to znamená, že změna barvy v této části animace nastává rychle a není jemná.  
  
3. Během posledních dvou sekund použije instanci <xref:System.Windows.Media.Animation.SplineColorKeyFrame> třídy ke změně barvy znovu – tentokrát ze žluté zpět na zelenou. Klíčové snímky spline, jako je <xref:System.Windows.Media.Animation.SplineColorKeyFrame> vytvoření proměnné přechodu mezi hodnotami podle hodnot vlastnosti. <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> V tomto příkladu změna barvy začíná pomalu a exponenciálně urychluje ke konci časového segmentu.  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
