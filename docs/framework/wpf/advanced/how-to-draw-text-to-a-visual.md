---
title: 'Postupy: Vykreslení textu do vizuálního objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
ms.openlocfilehash: 654bfadb42f053b6dcf353d4423bddf281d69478
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094550"
---
# <a name="how-to-draw-text-to-a-visual"></a>Postupy: Vykreslení textu do vizuálního objektu
Následující příklad ukazuje, jak nakreslit text do <xref:System.Windows.Media.DrawingVisual> pomocí objektu <xref:System.Windows.Media.DrawingContext>. Kontext vykreslování je vrácen voláním metody <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> objektu <xref:System.Windows.Media.DrawingVisual>. Grafiku a text můžete nakreslit do kontextu vykreslování.  
  
 Chcete-li nakreslit text do kontextu vykreslování, použijte metodu <xref:System.Windows.Media.DrawingContext.DrawText%2A> objektu <xref:System.Windows.Media.DrawingContext>. Až dokončíte vykreslování obsahu do kontextu vykreslování, zavolejte metodu <xref:System.Windows.Media.DrawingContext.Close%2A> pro zavření kontextu vykreslování a zachování obsahu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> Kompletní vzorek kódu, ze kterého byl extrahován předchozí příklad kódu, naleznete v tématu [test volání pomocí DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).
