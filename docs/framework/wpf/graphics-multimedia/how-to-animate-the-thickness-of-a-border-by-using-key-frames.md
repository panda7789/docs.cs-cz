---
title: 'Postupy: Animace tloušťky ohraničení použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: a601fd6779a4d912166366652435aff9ae37613f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421407"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>Postupy: Animace tloušťky ohraničení použitím klíčových snímků
Tento příklad ukazuje, jak animovat <xref:System.Windows.Controls.Control.BorderThickness%2A> vlastnost <xref:System.Windows.Controls.Border>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Controls.Control.BorderThickness%2A> vlastnost <xref:System.Windows.Controls.Border>. Tato animace používá tři klíčové snímky následujícím způsobem:  
  
1.  Během prvního půl sekundy, používá instanci <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> třídy postupně zvyšovat tloušťku ohraničení. V příkladu <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> k vytvoření hladkého lineární zvýšení mezi hodnotami.  
  
2.  Na konci další půl sekundy, používá instanci <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> třídy prudce zvýšit tloušťku ohraničení. Diskrétní klíčových snímků jako odvozený od <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> vytvoření i s náhlými přechodů mezi hodnotami, to znamená, je přehrávat nepravidelně přesun animace.  
  
3.  Během poslední dvě sekundy, používá instanci <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> třídy snížení tloušťku ohraničení. Klíčové snímky SpLine podobné těm odvozený od <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> vytvoříte proměnné přechod mezi hodnotami podle hodnoty <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> vlastnost. V této klíčový snímek animace začíná pomalé a zrychluje exponenciálně na konci časového úseku.  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Témata s postupy ke klíčovým snímkům](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [Animace hodnoty BorderThickness](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)
