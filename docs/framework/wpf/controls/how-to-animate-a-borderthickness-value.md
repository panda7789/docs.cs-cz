---
title: 'Postupy: Animace hodnoty BorderThickness'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF], animating changes to
- animation [WPF], changes to border thickness
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
ms.openlocfilehash: 4533ce6f2a1fe7243267ee8d638e2ad0a4f9cf3a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124660"
---
# <a name="how-to-animate-a-borderthickness-value"></a>Postupy: Animace hodnoty BorderThickness
Tento příklad ukazuje, jak animovat změny tloušťky ohraničení pomocí třídy <xref:System.Windows.Media.Animation.ThicknessAnimation>.  
  
## <a name="example"></a>Příklad  
 Následující příklad animuje tloušťku ohraničení pomocí <xref:System.Windows.Media.Animation.ThicknessAnimation>. V příkladu se používá vlastnost <xref:System.Windows.Controls.Border.BorderThickness%2A> <xref:System.Windows.Controls.Border>.  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 Úplnou ukázku najdete v tématu [animace příkladu Galerie](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [Přehled animace](../graphics-multimedia/animation-overview.md)
- [Postupy: Témata animace a časování](../graphics-multimedia/animation-and-timing-how-to-topics.md)
- [Animace tloušťky ohraničení pomocí klíčových snímků](../graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)
