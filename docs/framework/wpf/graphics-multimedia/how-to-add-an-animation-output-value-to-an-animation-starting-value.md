---
title: 'Postupy: Přidání výstupní hodnoty animace do počáteční hodnoty animace'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: bae7bf57507e3345c92cbbaf24491d86772425a4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501593"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a>Postupy: Přidání výstupní hodnoty animace do počáteční hodnoty animace
Tento příklad ukazuje, jak přidat výstupní hodnoty animace do počáteční hodnoty animace.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Vlastnost určuje, jestli se chcete o výstupní hodnoty animace do počáteční hodnoty (základní hodnoty) animované vlastnosti. Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> vlastnost nejzákladnější animace a většina klíčový snímek animace. Další informace najdete v tématu [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) a [přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 Následující příklad ukazuje účinek pomocí <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> vlastnost s <xref:System.Windows.Media.Animation.DoubleAnimation> a použití <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> vlastnost s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Kumulování hodnot animace při opakujících se cyklech](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Animace a časování](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
