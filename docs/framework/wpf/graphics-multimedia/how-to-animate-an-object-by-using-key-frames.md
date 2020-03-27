---
title: 'Postupy: Animace objektu použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0bc33b189fd856dbe8106c1db35bc18e27ea131e
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344706"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Postupy: Animace objektu použitím klíčových snímků
Tento příklad ukazuje, jak animovat objekt, <xref:System.Windows.Controls.Page.Background%2A> který v <xref:System.Windows.Controls.Page> tomto příkladu je vlastností ovládacího prvku pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> třídu k animaci změn barev pro <xref:System.Windows.Controls.Page.Background%2A> vlastnost ovládacího <xref:System.Windows.Controls.Page> prvku. Ukázková animace se v pravidelných intervalech změní na jiný štětec na pozadí. Tato animace <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> používá třídu k vytvoření tří různých klíčových snímků. Animace používá klíčové snímky následujícím způsobem:  
  
1. Na konci první sekundy animuje instanci třídy. <xref:System.Windows.Media.LinearGradientBrush> Tato část příkladu aplikuje na barvu pozadí lineární přechod tak, aby barva přecházela ze žluté na oranžovou na červenou.  
  
2. Na konci další sekundy animuje instanci třídy. <xref:System.Windows.Media.RadialGradientBrush> Tato část příkladu aplikuje na barvu pozadí kruhový přechod radiálního přechodu tak, aby se barva přecházela z bílé na modrou na černou.  
  
3. Na konci třetí sekundy animuje instanci třídy. <xref:System.Windows.Media.DrawingBrush> Tato část příkladu použije šachovna vzor na pozadí.  
  
4. Animace začíná znovu a opakuje se neomezeně dlouho.  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>je jediný typ klíčového snímku, který <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> můžete použít s třídou. Klíčové snímky, jako <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> je vytvoření náhlých změn hodnot, to znamená, že změny barev v tomto příkladu nastanou náhle.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](key-frame-animation-how-to-topics.md)
