---
title: 'Postupy: Animace barev použitím klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: cb09a54df3d99e05e89ec0f3d9f17b0e9fe78647
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419074"
---
# <a name="how-to-animate-color-by-using-key-frames"></a>Postupy: Animace barev použitím klíčových snímků
Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> použitím klíčových snímků.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost <xref:System.Windows.Media.SolidColorBrush>. Tato animace používá tři klíčové snímky následujícím způsobem:  
  
1.  Během prvních dvou sekund používá instanci <xref:System.Windows.Media.Animation.LinearColorKeyFrame> třídy postupně od zelené Změna barvy na červenou. Lineární klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.LinearColorKeyFrame> Vytvoření hladkého lineárního přechodu mezi hodnotami.  
  
2.  Při ukončení na další půl sekundy, používá instanci <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> třídy rychle změnit barvu z červené na žlutou. Diskrétní klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> vytvořit náhlých změn mezi hodnotami, to znamená, změna barvy v této části animace dojde k rychlému a není jednoduchý.  
  
3.  Během poslední dvě sekundy, používá instanci <xref:System.Windows.Media.Animation.SplineColorKeyFrame> třídy a změňte barvu znovu, tentokrát z žlutý zpět na zelenou. Klíčové snímky SpLine, jako jsou <xref:System.Windows.Media.Animation.SplineColorKeyFrame> vytvoříte proměnné přechod mezi hodnotami podle hodnoty <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> vlastnost. V tomto příkladu změní barva začne pomalu a zrychluje exponenciálně na konci časového úseku.  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.SolidColorBrush.Color%2A>  
 <xref:System.Windows.Media.SolidColorBrush>  
 <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Témata s postupy ke klíčovým snímkům](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
