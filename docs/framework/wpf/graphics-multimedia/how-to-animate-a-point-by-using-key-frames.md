---
title: 'Postupy: Animace bodu použitím klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: edcba36644cf78d6e98f934d9bd8b593af38b328
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344884"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>Postupy: Animace bodu použitím klíčových snímků
Tento příklad ukazuje, <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> jak použít třídu k animaci <xref:System.Windows.Point>.  
  
## <a name="example"></a>Příklad  
 Následující příklad přesune elipsu podél trojúhelníkové cesty. Příklad používá <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> třídu k <xref:System.Windows.Media.EllipseGeometry.Center%2A> animaci <xref:System.Windows.Media.EllipseGeometry>vlastnosti . Tato animace používá tři klíčové snímky následujícím způsobem:  
  
1. Během první poloviny sekundy používá <xref:System.Windows.Media.Animation.LinearPointKeyFrame> instanci třídy k přesunutí elipsy podél cesty stabilní rychlostí z počáteční pozice. Lineární klíčové <xref:System.Windows.Media.Animation.LinearPointKeyFrame> snímky, jako je vytvoření hladké lineární interpolace mezi hodnotami.  
  
2. Na konci další půlsekundy použije instanci <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> třídy k náhlému přesunutí elipsy podél cesty na další pozici. Diskrétní klíčové snímky, <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> jako je vytvoření náhlých skoků mezi hodnotami.  
  
3. Během posledních dvou sekund, používá <xref:System.Windows.Media.Animation.SplinePointKeyFrame> instance třídy přesunout elipsu zpět do výchozí polohy. Klíčové snímky spline, jako je <xref:System.Windows.Media.Animation.SplinePointKeyFrame> vytvoření proměnné přechodu mezi hodnotami podle hodnot vlastnosti. <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> V tomto příkladu animace začíná pomalu a zrychluje exponenciálně ke konci časového segmentu.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
 Pro konzistenci s jinými příklady animace, verze <xref:System.Windows.Media.Animation.Storyboard> kódu v <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>tomto příkladu použít objekt použít . Však při použití jedné animace v kódu, je <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> jednodušší použít <xref:System.Windows.Media.Animation.Storyboard>metodu namísto použití . Například viz [Animate vlastnost bez použití storyboardu](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
