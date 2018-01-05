---
title: "Postupy: Animace změn velikosti použitím klíčových snímků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30ee897efd01712bf4313da87e1050c5a16e4523
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>Postupy: Animace změn velikosti použitím klíčových snímků
Tento příklad ukazuje, jak pomocí klíčových snímků animace změny velikosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Media.ArcSegment.Size%2A> vlastnost <xref:System.Windows.Media.ArcSegment>. Tato animace používá tři klíčových snímků následujícím způsobem:  
  
1.  Při první poloviční druhé animace používá instanci <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> třídy postupně zvyšovat velikost oblouk. Lineární klíčových snímků jako <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> vytvořit hladký lineární přechod mezi hodnotami.  
  
2.  Na konci další půl sekundy používá instanci <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> třídy najednou zvětšete velikost oblouk. Diskrétní klíčových snímků jako <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> vytvoření nečekané přechodů mezi hodnotami, který je, změny velikosti dojít najednou a nejsou jemně.  
  
3.  Přes do konečné dvou sekund, používá instanci <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> třída zvětšete velikost oblouk. Křivkový klíčových snímků jako <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> vytvoření proměnné přechod mezi hodnotami podle hodnot <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> vlastnost. V tomto příkladu velikost oblouk zvyšuje pomalu nejprve a pak exponenciálnímu ke konci čas segmentu.  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Témata s postupy ke klíčovým snímkům](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
