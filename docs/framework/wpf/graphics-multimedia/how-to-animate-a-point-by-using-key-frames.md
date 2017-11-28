---
title: "Postupy: Animace bodu použitím klíčových snímků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f574f85a5840e8bbe2d6c026d57a4cc28bd8a797
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Přehled animací jednotlivých klíč](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Postupy: témata klíč rámce](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
