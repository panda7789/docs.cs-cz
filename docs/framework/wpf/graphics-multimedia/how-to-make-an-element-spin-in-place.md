---
title: 'Postupy: Otáčení elementu na místě'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: aca9bd577f2882e31e8d49abe5eeb5ade86f95f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110661"
---
# <a name="how-to-make-an-element-spin-in-place"></a>Postupy: Otáčení elementu na místě
Tento příklad ukazuje, jak aktivovat pomocí elementu <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Následující příklad se vztahuje <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu. V příkladu se používá <xref:System.Windows.Media.Animation.DoubleAnimation> pro animaci <xref:System.Windows.Media.RotateTransform.Angle%2A> z <xref:System.Windows.Media.RotateTransform>. Chcete-li prvek číselníku na místě, příklad nastaví <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost elementu, který chcete bod (0,5, 0,5).  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Úplnou ukázku, která obsahuje další příklady transformace, najdete v části [2D transformace ukázka](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Viz také:

- [Přehled animace](animation-overview.md)
- [Přehled transformace](transforms-overview.md)
