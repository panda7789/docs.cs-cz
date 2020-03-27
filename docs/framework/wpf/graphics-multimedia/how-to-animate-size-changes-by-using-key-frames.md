---
title: 'Postupy: Animace změn velikosti použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 42cecfc9df4304be4033ea39edc0517016de4a92
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344637"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>Postupy: Animace změn velikosti použitím klíčových snímků
Tento příklad ukazuje, jak animovat změny velikosti pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> třídu k <xref:System.Windows.Media.ArcSegment.Size%2A> animaci vlastnosti <xref:System.Windows.Media.ArcSegment>. Tato animace používá tři klíčové snímky následujícím způsobem:  
  
1. Během první poloviny druhé animace používá instance <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> třídy postupně zvětšit velikost oblouku. Lineární klíčové <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> snímky, jako je vytvoření hladkého lineárního přechodu mezi hodnotami.  
  
2. Na konci další poloviny sekundy, používá <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> instance třídy náhle zvětšit velikost oblouku. Diskrétní klíčové snímky, <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> jako je vytvoření náhlých skoků mezi hodnotami, to znamená, že změny velikosti nastávají náhle a nejsou jemné.  
  
3. Během posledních dvou sekund používá instanci třídy <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> ke zvětšení velikosti oblouku. Klíčové snímky spline, jako je <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> vytvoření proměnné přechodu mezi hodnotami podle hodnot vlastnosti. <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> V tomto příkladu se velikost oblouku nejprve zvětšuje pomalu a poté exponenciálně zvyšuje ke konci časového segmentu.  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
