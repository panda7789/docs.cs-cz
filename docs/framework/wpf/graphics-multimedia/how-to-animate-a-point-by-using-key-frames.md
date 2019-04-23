---
title: 'Postupy: Animace bodu pomocí klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: b706568a0e8221aac737780592882f728f0f9e9c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328774"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>Postupy: Animace bodu pomocí klíčových snímků
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Point>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se přesune elipsa trojúhelníkové cestě. V příkladu se používá <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost <xref:System.Windows.Media.EllipseGeometry>. Tato animace používá tři klíčové snímky následujícím způsobem:  
  
1. Během prvního půl sekundy, používá instanci <xref:System.Windows.Media.Animation.LinearPointKeyFrame> třídy pro přesun na tři tečky podél cesty stabilní rychlostí z jeho výchozí pozice. Lineární klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.LinearPointKeyFrame> Vytvoření hladkého lineární interpolaci mezi hodnotami.  
  
2. Při ukončení na další půl sekundy, používá instanci <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> třídy náhle přesunout na tři tečky na cestě na další pozici. Diskrétní klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> vytvořit i s náhlými rozdíly mezi jednotlivými hodnotami.  
  
3. Během poslední dvě sekundy, používá instanci <xref:System.Windows.Media.Animation.SplinePointKeyFrame> třídy pro přechod na tři tečky na počáteční pozici. Klíčové snímky SpLine, jako jsou <xref:System.Windows.Media.Animation.SplinePointKeyFrame> vytvoříte proměnné přechod mezi hodnotami podle hodnoty <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> vlastnost. V tomto příkladu animace začne pomalu a zrychluje exponenciálně na konci časového úseku.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Pro zajištění konzistence s další příklady animace, kód verze tohoto příkladu použijte <xref:System.Windows.Media.Animation.Storyboard> objektu, který chcete použít <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>. Při použití jedné animace v kódu, je ale jednodušší použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda namísto použití <xref:System.Windows.Media.Animation.Storyboard>. Příklad najdete v tématu [animace vlastnosti bez pomoci scénáře](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
