---
title: "Postupy: Animace barev použitím klíčových snímků"
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
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c6b4dc6ee04b20f47599bad84dda4648da255ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-color-by-using-key-frames"></a>Postupy: Animace barev použitím klíčových snímků
Tento příklad ukazuje, jak animace <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost <xref:System.Windows.Media.SolidColorBrush>. Tato animace používá tři klíčových snímků následujícím způsobem:  
  
1.  Při první dvě sekundy používá instanci <xref:System.Windows.Media.Animation.LinearColorKeyFrame> třídy postupně změnit barvu ze zelené na červený. Lineární klíčových snímků jako <xref:System.Windows.Media.Animation.LinearColorKeyFrame> vytvořit hladký lineární přechod mezi hodnotami.  
  
2.  Během konec další půl sekundy používá instanci <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> třídy rychle změnit barvu red na žlutě. Diskrétní klíčových snímků jako <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> vytvořit nečekané změn mezi hodnotami, který je, změna barvy v této části animace probíhá rychle a není jemně.  
  
3.  Během poslední dvou sekund, používá instanci <xref:System.Windows.Media.Animation.SplineColorKeyFrame> třída znovu Změna barvy – tentokrát z žlutý zpět na zelenou. Křivkový klíčových snímků jako <xref:System.Windows.Media.Animation.SplineColorKeyFrame> vytvoření proměnné přechod mezi hodnotami podle hodnot <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> vlastnost. V tomto příkladu změnu v hodnotě barva začne pomalu a urychluje exponenciálnímu ke konci čas segmentu.  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.SolidColorBrush.Color%2A>  
 <xref:System.Windows.Media.SolidColorBrush>  
 <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Témata s postupy ke klíčovým snímkům](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
