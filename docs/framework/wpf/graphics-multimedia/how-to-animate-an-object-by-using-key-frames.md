---
title: 'Postupy: Animace objektu použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 7dc49bc6b3f9156507cb821bfc32b269365b206c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558537"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Postupy: Animace objektu použitím klíčových snímků
Tento příklad ukazuje, jak animace objekt, který je v tomto příkladu <xref:System.Windows.Controls.Page.Background%2A> vlastnost <xref:System.Windows.Controls.Page> ovládacího prvku pomocí klíčových snímků.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> třídy animace barva změny pro <xref:System.Windows.Controls.Page.Background%2A> vlastnost <xref:System.Windows.Controls.Page> ovládacího prvku. Příklad animace se změní na různých pozadí štětce v pravidelných intervalech. Používá tento animace <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> třídy za účelem vytvoření tři různé klíčových snímků. Animace používá klíčových snímků následujícím způsobem:  
  
1.  Na konci prvního druhý animuje instanci <xref:System.Windows.Media.LinearGradientBrush> třídy. Tato část v příkladu se týká lineárního přechodu na barvu pozadí tak, aby barva přechází z žlutý do oranžová na červený.  
  
2.  Na konci do příští sekundy animuje instanci <xref:System.Windows.Media.RadialGradientBrush> třídy. Tato část v příkladu se týká kruhového přechodu na barvu pozadí tak, aby barva přechází z prázdné na modrou do černé.  
  
3.  Na konci třetí druhý animuje instanci <xref:System.Windows.Media.DrawingBrush> třídy. Tato část příklad se týká pouze šachovnicový vzorek na pozadí.  
  
4.  Animace začne počítat od začátku a opakuje bez omezení.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> je jediným typem klíče rámce, který můžete použít s <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> třídy. Klíč rámců jako <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> vytvořit nečekané změn v hodnoty, který je, změny barev v tomto příkladu dojde k najednou.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Témata s postupy ke klíčovým snímkům](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
