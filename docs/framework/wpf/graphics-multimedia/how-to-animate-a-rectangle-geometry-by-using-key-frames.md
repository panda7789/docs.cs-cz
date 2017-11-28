---
title: "Postupy: Animace obdélníkové geometrie použitím klíčových snímků"
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
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b6c23f894b6fa93a3889356416bd95f61fff8beb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>Postupy: Animace obdélníkové geometrie použitím klíčových snímků
Tento příklad ukazuje, jak animace <xref:System.Windows.Media.RectangleGeometry.Rect%2A> vlastnost <xref:System.Windows.Media.RectangleGeometry> pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Media.RectangleGeometry.Rect%2A> vlastnost <xref:System.Windows.Media.RectangleGeometry>. Tato animace používá tři klíčových snímků následujícím způsobem:  
  
1.  Při první dvě sekundy používá instanci <xref:System.Windows.Media.Animation.LinearRectKeyFrame> třídy animace postupná změnu pozice, šířky a výšky obdélníku. Lineární klíčových snímků jako <xref:System.Windows.Media.Animation.LinearRectKeyFrame> vytvořit hladký lineární přechod mezi hodnotami.  
  
2.  Během konec další půl sekundy používá instanci <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> třída najednou snížení výška rámečku. Diskrétní klíčových snímků jako <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> vytvořit nečekané změn mezi hodnotami, který je, poklesu výška probíhá rychle a není jemně.  
  
3.  Během poslední dvou sekund, používá instanci <xref:System.Windows.Media.Animation.SplineRectKeyFrame> třída změnit rámeček zpět na původní velikost a umístění. Křivkový klíčových snímků jako <xref:System.Windows.Media.Animation.SplineRectKeyFrame> vytvoření proměnné přechod mezi hodnotami podle hodnot <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> vlastnost. V tomto příkladu změnu začne pomalu a urychluje exponenciálnímu ke konci čas segmentu.  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.RectangleGeometry>  
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>  
 <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>  
 [Přehled animací jednotlivých klíč](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Postupy: témata klíč rámce](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
