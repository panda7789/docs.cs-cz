---
title: 'Postupy: Přidání výstupní hodnoty animace do počáteční hodnoty animace'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 7f60a3cd3fc88c5bb2460864be6cee008dc672fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557616"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a>Postupy: Přidání výstupní hodnoty animace do počáteční hodnoty animace
Tento příklad ukazuje, jak přidat hodnotu výstup animace na výchozí hodnotu animace.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Vlastnost určuje, zda chcete, aby hodnota výstupu animace přidány do počáteční hodnotu (základní hodnotu) animovaný vlastnosti. Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> vlastnost nejzákladnější animace a většina klíčových snímků animace. Další informace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) a [klíč rámce animací přehled](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 Následující příklad ukazuje účinek použití <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> vlastnost s <xref:System.Windows.Media.Animation.DoubleAnimation> a pomocí <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> vlastnost s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Kumulování hodnot animace při opakujících se cyklech](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Animace a časování](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
