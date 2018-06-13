---
title: 'Postupy: Použití transformace na element při výskytu události'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
ms.openlocfilehash: bd50b369666a1b65226b2b7eb6f3d866ec670bde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558974"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a>Postupy: Použití transformace na element při výskytu události
Tento příklad ukazuje, jak se má použít <xref:System.Windows.Media.ScaleTransform> při výskytu události. Koncept, které se zobrazí tady je stejný, který používáte pro použití jiné typy transformace. Další informace o dostupných typech transformace najdete v tématu <xref:System.Windows.Media.Transform> třídy nebo [transformuje přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
 Můžete provést transformace pro element v některém z těchto dvou způsobů:  
  
-   V takovém případě *není* má transformace ovlivňují rozložení, použijte <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu.  
  
-   Pokud chcete transformaci, která ovlivňují rozložení, použijte <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost elementu.  
  
 Následující příklad se vztahuje <xref:System.Windows.Media.ScaleTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost tlačítka. Při přesunu na tlačítko myši <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> vlastnosti <xref:System.Windows.Media.ScaleTransform> jsou nastaveny na `2`, což způsobí, že tlačítko na velikost větší. Při přesunu vypnout na tlačítko myši <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> jsou nastaveny na `1`, což způsobí, že na tlačítko Obnovit původní velikost.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
