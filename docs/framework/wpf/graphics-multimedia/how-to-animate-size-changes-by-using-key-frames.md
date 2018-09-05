---
title: 'Postupy: Animace změn velikosti použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 69845d1d75f81042bbeb20ee6b1015f5c2f53b81
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672555"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>Postupy: Animace změn velikosti použitím klíčových snímků
Tento příklad ukazuje, jak animace změn velikosti použitím klíčových snímků.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Media.ArcSegment.Size%2A> vlastnost <xref:System.Windows.Media.ArcSegment>. Tato animace používá tři klíčové snímky následujícím způsobem:  
  
1.  Během prvního půl sekundy animace používá instanci <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> třídy postupně zvyšovat velikost oblouk. Lineární klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> Vytvoření hladkého lineárního přechodu mezi hodnotami.  
  
2.  Na konci další půl sekundy, používá instanci <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> třídy prudce zvýšit velikost oblouku. Diskrétní klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> vytvoření i s náhlými přechodů mezi hodnotami, to znamená, dojde k náhlému změny velikosti a nejsou drobným.  
  
3.  Za poslední 2 sekundy, používá instanci <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> třídy zvýšit velikost oblouk. Klíčové snímky SpLine, jako jsou <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> vytvoříte proměnné přechod mezi hodnotami podle hodnoty <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> vlastnost. V tomto příkladu velikost oblouk zvyšuje pomalu zpočátku a pak exponenciálně zvyšuje na konci časového úseku.  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Témata s postupy ke klíčovým snímkům](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
