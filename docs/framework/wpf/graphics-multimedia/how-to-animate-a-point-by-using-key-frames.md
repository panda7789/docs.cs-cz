---
title: 'Postupy: Animace bodu použitím klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: a59ceb62d7feb33d2cc8a747a7bfb85e551d785c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557352"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>Postupy: Animace bodu použitím klíčových snímků
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Point>.  
  
## <a name="example"></a>Příklad  
 Následující příklad přesune elipsy podél trojúhelníkovou cesty. V příkladu se používá <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost <xref:System.Windows.Media.EllipseGeometry>. Tato animace používá tři klíčových snímků následujícím způsobem:  
  
1.  Při první půl sekundy používá instanci <xref:System.Windows.Media.Animation.LinearPointKeyFrame> třídy pro přesun se třemi tečkami podél cesty konstantní rychlostí od počáteční pozice. Lineární klíčových snímků jako <xref:System.Windows.Media.Animation.LinearPointKeyFrame> vytvořit smooth lineární interpolace mezi hodnotami.  
  
2.  Během konec další půl sekundy používá instanci <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> třídy najednou přesuňte se třemi tečkami v cestě pro další. Diskrétní klíčových snímků jako <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> vytvoření nečekané přechodů mezi hodnotami.  
  
3.  Během poslední dvou sekund, používá instanci <xref:System.Windows.Media.Animation.SplinePointKeyFrame> třída k přesunutí se třemi tečkami zpátky na jeho počáteční pozice. Křivkový klíčových snímků jako <xref:System.Windows.Media.Animation.SplinePointKeyFrame> vytvoření proměnné přechod mezi hodnotami podle hodnot <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> vlastnost. V tomto příkladu animace začne pomalu a urychluje exponenciálnímu ke konci čas segmentu.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Z důvodu konzistence s další příklady animace verze kódu v tomto příkladu použijte <xref:System.Windows.Media.Animation.Storyboard> objekt, který chcete použít <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>. Při použití jedné animace v kódu, je však jednodušší použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda místo použití <xref:System.Windows.Media.Animation.Storyboard>. Příklad, naleznete v části [animace vlastnosti bez použití scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.EllipseGeometry>  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Témata s postupy ke klíčovým snímkům](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
