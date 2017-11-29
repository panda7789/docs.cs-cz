---
title: "Postupy: Animace tloušťky ohraničení použitím klíčových snímků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08950b2b92bfcbd28472327f12a2ee49abfd9fed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>Postupy: Animace tloušťky ohraničení použitím klíčových snímků
Tento příklad ukazuje, jak animace <xref:System.Windows.Controls.Control.BorderThickness%2A> vlastnost <xref:System.Windows.Controls.Border>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Controls.Control.BorderThickness%2A> vlastnost <xref:System.Windows.Controls.Border>. Tato animace používá tři klíčových snímků následujícím způsobem:  
  
1.  Při první půl sekundy používá instanci <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> třídy postupně zvyšovat Tloušťka ohraničení. Tento příklad používá <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> vytvořit smooth lineární nárůst mezi hodnotami.  
  
2.  Na konci další půl sekundy používá instanci <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> třída najednou zvýšit sílu ohraničení. Diskrétní klíčových snímků jako ty, odvozené od <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> vytvoření nečekané přechodů mezi hodnotami, který je, je trhané přesun animace.  
  
3.  Během poslední dvou sekund, používá instanci <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> třída snížení sílu ohraničení. Křivkový klíčových snímků jako ty, odvozené od <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> vytvoření proměnné přechod mezi hodnotami podle hodnot <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> vlastnost. Do tohoto klíče rámce animace spustí pomalu a urychluje exponenciálnímu ke konci čas segmentu.  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>  
 [Přehled animací jednotlivých klíč](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Postupy: témata klíč rámce](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [Animace hodnotu BorderThickness](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)
