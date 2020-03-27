---
title: 'Postupy: Animace dvojice použitím klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 9eab794cc8411230226cddc97beaa13c1bdd9405
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344942"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>Postupy: Animace dvojice použitím klíčových snímků
Tento příklad ukazuje, jak animovat hodnotu <xref:System.Double> vlastnosti, která trvá pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad přesune obdélník přes obrazovku. Příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> třídu k <xref:System.Windows.Media.TranslateTransform.X%2A> animaci <xref:System.Windows.Media.TranslateTransform> vlastnosti <xref:System.Windows.Shapes.Rectangle>aplikované na . Tato animace, která se opakuje neomezeně dlouho, používá tři klíčové snímky následujícím způsobem:  
  
1. Během prvních tří sekund používá instanci <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> třídy k přesunutí obdélníku podél cesty stabilní rychlostí od počáteční polohy do polohy 500. Lineární klíčové <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> snímky, jako je vytvoření hladkého lineárního přechodu mezi hodnotami.  
  
2. Na konci čtvrté sekundy, používá instance <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> třídy náhle přesunout obdélník na další pozici. Diskrétní klíčové snímky, <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> jako je vytvoření náhlých skoků mezi hodnotami. V tomto příkladu obdélník je na výchozí pozici a pak se náhle objeví na pozici 500.  
  
3. V posledních dvou sekundách používá <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> instanci třídy k přesunutí obdélníku zpět do výchozí polohy. Klíčové snímky spline, jako je <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> vytvoření proměnné přechodu mezi hodnotami podle hodnoty vlastnosti. <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> V tomto příkladu obdélník začíná pohybem pomalu a pak urychluje exponenciálně ke konci časového segmentu.  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
 Pro konzistenci s jinými příklady animace, verze <xref:System.Windows.Media.Animation.Storyboard> kódu v <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>tomto příkladu použít objekt použít . Alternativně při použití jedné animace v kódu, je <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> jednodušší použít <xref:System.Windows.Media.Animation.Storyboard>metodu namísto použití . Například viz [Animate vlastnost bez použití storyboardu](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
