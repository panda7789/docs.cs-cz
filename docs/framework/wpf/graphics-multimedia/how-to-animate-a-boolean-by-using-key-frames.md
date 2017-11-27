---
title: "Postupy: Animace logické hodnoty použitím klíčových snímků"
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
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ac129bf133cca88a6d2f6a724d25ea2519cb72e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a>Postupy: Animace logické hodnoty použitím klíčových snímků
Tento příklad ukazuje, jak animace hodnotu vlastnost typu Boolean <xref:System.Windows.Controls.Button> ovládacího prvku pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> třídy animace <xref:System.Windows.UIElement.IsEnabled%2A> vlastnost <xref:System.Windows.Controls.Button> ovládacího prvku. Všechny klíče rámce v tomto příkladu použít instanci systému <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> třídy. Diskrétní klíčových snímků jako <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> vytvoření nečekané přechodů mezi hodnotami, který je, je trhané přesun animace.  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>  
 <xref:System.Windows.UIElement.IsEnabled%2A>  
 <xref:System.Windows.Controls.Button>  
 [Přehled animací jednotlivých klíč](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Postupy: témata klíč rámce](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
