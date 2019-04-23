---
title: 'Postupy: Animace obdélníkové geometrie pomocí klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: 03953b79127ffceeb49e4ece2070d09f382448a5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311341"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>Postupy: Animace obdélníkové geometrie pomocí klíčových snímků
Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.RectangleGeometry.Rect%2A> vlastnost <xref:System.Windows.Media.RectangleGeometry> použitím klíčových snímků.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Media.RectangleGeometry.Rect%2A> vlastnost <xref:System.Windows.Media.RectangleGeometry>. Tato animace používá tři klíčové snímky následujícím způsobem:  
  
1. Během prvních dvou sekund používá instanci <xref:System.Windows.Media.Animation.LinearRectKeyFrame> třídy pro animaci postupné změny v pozici, šířku a výšku obdélníku. Lineární klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.LinearRectKeyFrame> Vytvoření hladkého lineárního přechodu mezi hodnotami.  
  
2. Při ukončení na další půl sekundy, používá instanci <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> třídy se náhle výškou pravoúhelníku. Diskrétní klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> vytvořit náhlých změn mezi hodnotami, to znamená, snížení výšky proběhne rychle a není jednoduchý.  
  
3. Během poslední dvě sekundy, používá instanci <xref:System.Windows.Media.Animation.SplineRectKeyFrame> třídy změnit obdélník zpět na původní velikost a umístění. Klíčové snímky SpLine, jako jsou <xref:System.Windows.Media.Animation.SplineRectKeyFrame> vytvoříte proměnné přechod mezi hodnotami podle hodnoty <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> vlastnost. V tomto příkladu změnu začne pomalu a zrychluje exponenciálně na konci časového úseku.  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
