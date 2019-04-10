---
title: 'Postupy: Animace změn velikosti pomocí klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 0629b6600444bd172af451fd7e970bff894d8047
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342359"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>Postupy: Animace změn velikosti pomocí klíčových snímků
Tento příklad ukazuje, jak animace změn velikosti použitím klíčových snímků.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Media.ArcSegment.Size%2A> vlastnost <xref:System.Windows.Media.ArcSegment>. Tato animace používá tři klíčové snímky následujícím způsobem:  
  
1. Během prvního půl sekundy animace používá instanci <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> třídy postupně zvyšovat velikost oblouk. Lineární klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> Vytvoření hladkého lineárního přechodu mezi hodnotami.  
  
2. Na konci další půl sekundy, používá instanci <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> třídy prudce zvýšit velikost oblouku. Diskrétní klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> vytvoření i s náhlými přechodů mezi hodnotami, to znamená, dojde k náhlému změny velikosti a nejsou drobným.  
  
3. Za poslední 2 sekundy, používá instanci <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> třídy zvýšit velikost oblouk. Klíčové snímky SpLine, jako jsou <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> vytvoříte proměnné přechod mezi hodnotami podle hodnoty <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> vlastnost. V tomto příkladu velikost oblouk zvyšuje pomalu zpočátku a pak exponenciálně zvyšuje na konci časového úseku.  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
