---
title: Animace řetězce pomocí klíčových snímků
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 5219ce11667c84d3ceca380d5a4ddd52695736b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561056"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>Animace řetězce pomocí klíčových snímků
Tento příklad ukazuje, jak animace řetězec, který je v tomto příkladu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.Button> ovládacího prvku pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.Button>.  
  
 Všechny klíče rámce v tomto příkladu použít instanci systému <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> třídy protože animace řetězec, který je vytvořen s klíčových snímků lze použít pouze diskrétní klíčových snímků. Diskrétní klíčových snímků jako <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> vytvoření nečekané přechodů mezi hodnotami, který je, změny animace dojít rychle a nejsou jemně.  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.ContentControl.Content%2A>  
 <xref:System.Windows.Controls.Button>  
 <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Témata s postupy ke klíčovým snímkům](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
