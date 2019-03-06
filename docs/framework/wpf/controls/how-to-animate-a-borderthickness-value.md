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
ms.openlocfilehash: 4f38895f58e1a41a8a66b31a116e94f5b02492f7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368935"
---
# <a name="how-to-animate-a-borderthickness-value"></a>Postupy: Animace hodnoty BorderThickness
Tento příklad ukazuje, jak animace změny tloušťky ohraničení použitím <xref:System.Windows.Media.Animation.ThicknessAnimation> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad animuje tloušťky ohraničení pomocí <xref:System.Windows.Media.Animation.ThicknessAnimation>. V příkladu se používá <xref:System.Windows.Controls.Border.BorderThickness%2A> vlastnost <xref:System.Windows.Controls.Border>.  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 Úplnou ukázku najdete v tématu [animace příkladu Galerie](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [Přehled animace](../graphics-multimedia/animation-overview.md)
- [Animace a časování témata s postupy](../graphics-multimedia/animation-and-timing-how-to-topics.md)
- [Animace tloušťky ohraničení pomocí klíčových snímků](../graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)
