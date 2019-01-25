---
title: 'Postupy: Animace objektu použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: eb9de4098c5fb9bde74fa93dda6dd5a878ed0339
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697527"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Postupy: Animace objektu použitím klíčových snímků
Tento příklad ukazuje, jak pro animaci objektu, který v tomto příkladu je <xref:System.Windows.Controls.Page.Background%2A> vlastnost <xref:System.Windows.Controls.Page> ovládacího prvku s použitím klíčových snímků.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> třídy animace barev změní pro <xref:System.Windows.Controls.Page.Background%2A> vlastnost <xref:System.Windows.Controls.Page> ovládacího prvku. Příklad animace změní na štětec pozadí různých v pravidelných intervalech. Používá tato animace <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> třídy za účelem vytvoření tří různých klíčových snímků. Animace pomocí klíčových snímků následujícím způsobem:  
  
1.  Na konci prvního druhé animuje instance <xref:System.Windows.Media.LinearGradientBrush> třídy. Tato část. Příklad se týká lineárního přechodu na barvu pozadí tak, aby změní barvu z žlutá na oranžovou na červenou.  
  
2.  Na konci do příští sekundy animuje instance <xref:System.Windows.Media.RadialGradientBrush> třídy. Tato část. Příklad se týká paprskového přechodu na barvu pozadí tak, aby změní barvu z prázdné na modrou na černou.  
  
3.  Na konci třetího druhé animuje instance <xref:System.Windows.Media.DrawingBrush> třídy. Tato část příklad se týká šachovnicový vzor na pozadí.  
  
4.  Animace začne znovu a opakuje bez omezení.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> je jediným typem klíčový snímek, který vám pomůže s <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> třídy. Klíč snímků jako <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> vytvořit náhlých změn v hodnotách, to znamená, změny barev v tomto příkladu dojde k náhlému.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [Témata s postupy ke klíčovým snímkům](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
