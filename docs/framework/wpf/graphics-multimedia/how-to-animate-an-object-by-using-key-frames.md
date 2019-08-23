---
title: 'Postupy: Animace objektu pomocí klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: ffbe1845b634c8f94eb6a10dfa44fcf9903e0cd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933910"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Postupy: Animace objektu pomocí klíčových snímků
Tento příklad ukazuje, jak animovat objekt, který v tomto příkladu je <xref:System.Windows.Controls.Page.Background%2A> vlastností <xref:System.Windows.Controls.Page> ovládacího prvku pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> třídu k animaci změn barvy <xref:System.Windows.Controls.Page.Background%2A> pro vlastnost <xref:System.Windows.Controls.Page> ovládacího prvku. Ukázková animace se v pravidelných intervalech mění na jiný štětec na pozadí. Tato animace používá <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> třídu k vytvoření tří různých klíčových snímků. Animace používá klíčové snímky následujícím způsobem:  
  
1. Na konci první sekundy animuje instanci <xref:System.Windows.Media.LinearGradientBrush> třídy. Tato část příkladu aplikuje lineární přechod na barvu pozadí, aby se barvy od žlutého po oranžová do červené.  
  
2. Na konci další sekundy animuje instanci <xref:System.Windows.Media.RadialGradientBrush> třídy. Tato část příkladu aplikuje paprskový přechod na barvu pozadí, aby se barvy přechází z bílé na modrou na černou.  
  
3. Na konci třetí sekundy animuje instanci <xref:System.Windows.Media.DrawingBrush> třídy. Tato část příkladu aplikuje na pozadí šachovnicový vzor.  
  
4. Animace se znovu spustí a zopakuje se neomezeně.  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>je jediným typem klíčového snímku, který lze použít s <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> třídou. Klíčové snímky, <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> jako je vytváření náhlých změn v hodnotách, to znamená, že se změny barev v tomto příkladu vyskytují náhle.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Úplnou ukázku najdete v tématu [Ukázka animace klíčových snímků](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
