---
title: 'Postupy: Animace obdélníkové geometrie použitím klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: bcc9e7f198b8a20ffe13daf6508fb8a735937652
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344683"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>Postupy: Animace obdélníkové geometrie použitím klíčových snímků
Tento příklad ukazuje, jak <xref:System.Windows.Media.RectangleGeometry.Rect%2A> animovat vlastnost a <xref:System.Windows.Media.RectangleGeometry> pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> třídu k <xref:System.Windows.Media.RectangleGeometry.Rect%2A> animaci vlastnosti <xref:System.Windows.Media.RectangleGeometry>. Tato animace používá tři klíčové snímky následujícím způsobem:  
  
1. Během prvních dvou sekund použije instanci <xref:System.Windows.Media.Animation.LinearRectKeyFrame> třídy k animaci postupné změny polohy, šířky a výšky obdélníku. Lineární klíčové <xref:System.Windows.Media.Animation.LinearRectKeyFrame> snímky, jako je vytvoření hladkého lineárního přechodu mezi hodnotami.  
  
2. Během konce další poloviny sekundy, používá <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> instance třídy náhle snížit výšku obdélníku. Diskrétní klíčové snímky, <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> jako je vytvoření náhlých změn mezi hodnotami, to znamená, že snížení výšky dochází rychle a není jemné.  
  
3. Během posledních dvou sekund, používá <xref:System.Windows.Media.Animation.SplineRectKeyFrame> instance třídy změnit obdélník zpět na původní velikost a umístění. Klíčové snímky spline, jako je <xref:System.Windows.Media.Animation.SplineRectKeyFrame> vytvoření proměnné přechodu mezi hodnotami podle hodnot vlastnosti. <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> V tomto příkladu změna začíná pomalu a exponenciálně urychluje ke konci časového segmentu.  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
