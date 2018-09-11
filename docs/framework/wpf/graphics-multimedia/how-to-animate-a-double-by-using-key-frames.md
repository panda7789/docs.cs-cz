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
ms.openlocfilehash: 67466bbb5fd7e7a46c312e14666c23048bf43d80
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339331"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>Postupy: Animace dvojice použitím klíčových snímků
Tento příklad ukazuje, jak animovat hodnotu vlastnosti, která přijímá <xref:System.Double> použitím klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad přesune obdélník obrazovce. V příkladu se používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> u <xref:System.Windows.Shapes.Rectangle>. Tuto animaci, která se stále opakuje, používá tři klíčové snímky následujícím způsobem:  
  
1.  Během první tři sekundy, používá instanci <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> třídy přesunout obdélník podél cesty stabilní rychlostí z jeho výchozí pozice na 500 pozici. Lineární klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> Vytvoření hladkého lineárního přechodu mezi hodnotami.  
  
2.  Na konci čtvrtý druhý používá instanci <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> třídy náhle obdélník přesunout na další pozici. Diskrétní klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> vytvořit i s náhlými rozdíly mezi jednotlivými hodnotami. V tomto příkladu obdélníku je počáteční pozice a se pak náhle objeví na 500 pozici.  
  
3.  Do dvou sekund konečná používá instanci <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> třídy přesunout obdélník zpět na počáteční pozici. Klíčové snímky SpLine, jako jsou <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> vytvoříte proměnné přechod mezi hodnotami podle hodnoty <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> vlastnost. V tomto příkladu obdélník začíná přesunutím pomalu a pak zrychluje exponenciálně na konci časového úseku.  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Pro zajištění konzistence s další příklady animace, kód verze tohoto příkladu použijte <xref:System.Windows.Media.Animation.Storyboard> objektu, který chcete použít <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Můžete také při použití jedné animace v kódu, je jednodušší použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda namísto použití <xref:System.Windows.Media.Animation.Storyboard>. Příklad najdete v tématu [animace vlastnosti bez pomoci scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Shapes.Rectangle>  
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Témata s postupy ke klíčovým snímkům](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
