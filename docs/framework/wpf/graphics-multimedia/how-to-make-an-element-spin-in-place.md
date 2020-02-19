---
title: 'Postupy: Zarovnání číselníku'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 2e72389a11e48629c2763fcbd9f7b1945ffff5dd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452789"
---
# <a name="how-to-make-an-element-spin-in-place"></a>Postupy: Zarovnání číselníku
Tento příklad ukazuje, jak nastavit prvek otočením pomocí <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Následující příklad aplikuje <xref:System.Windows.Media.RotateTransform> na vlastnost <xref:System.Windows.UIElement.RenderTransform%2A> elementu. V příkladu se používá <xref:System.Windows.Media.Animation.DoubleAnimation> k animaci <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform>. Aby bylo možné prvek otočit, příklad nastaví vlastnost <xref:System.Windows.UIElement.RenderTransformOrigin%2A> elementu na bod (0,5, 0,5).  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Kompletní ukázku, která zahrnuje další příklady transformace, najdete v [ukázce 2-D transformací](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Přehled transformace](transforms-overview.md)
