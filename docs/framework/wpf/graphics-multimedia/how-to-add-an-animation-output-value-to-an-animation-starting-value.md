---
title: 'Postupy: Přidání výstupní hodnoty animace do počáteční hodnoty animace'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 945675d03a280e2394fdb0eab27c0978dc7cc320
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102606"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a>Postupy: Přidání výstupní hodnoty animace do počáteční hodnoty animace
Tento příklad ukazuje, jak přidat výstupní hodnoty animace do počáteční hodnoty animace.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Vlastnost určuje, jestli se chcete o výstupní hodnoty animace do počáteční hodnoty (základní hodnoty) animované vlastnosti. Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> vlastnost nejzákladnější animace a většina klíčový snímek animace. Další informace najdete v tématu [přehled animace](animation-overview.md) a [přehled animací klíčových snímků](key-frame-animations-overview.md).  
  
 Následující příklad ukazuje účinek pomocí <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> vlastnost s <xref:System.Windows.Media.Animation.DoubleAnimation> a použití <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> vlastnost s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a>Viz také:

- [Kumulování hodnot animace při opakujících se cyklech](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [Přehled animace](animation-overview.md)
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Animace a časování témata s postupy](animation-and-timing-how-to-topics.md)
