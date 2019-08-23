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
ms.openlocfilehash: bd760a06150098d0fff17dbdce95b55a0e5fe713
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963848"
---
# <a name="how-to-draw-text-to-a-visual"></a>Postupy: Vykreslení textu do vizuálního objektu
Následující příklad ukazuje, jak nakreslit text na <xref:System.Windows.Media.DrawingVisual> <xref:System.Windows.Media.DrawingContext> objekt pomocí objektu. Kontext vykreslování je vrácen voláním <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metody <xref:System.Windows.Media.DrawingVisual> objektu. Grafiku a text můžete nakreslit do kontextu vykreslování.  
  
 Chcete-li nakreslit text do kontextu vykreslování, <xref:System.Windows.Media.DrawingContext.DrawText%2A> použijte metodu <xref:System.Windows.Media.DrawingContext> objektu. Až dokončíte vykreslování obsahu do kontextu vykreslování, zavolejte <xref:System.Windows.Media.DrawingContext.Close%2A> metodu pro zavření kontextu vykreslování a zachování obsahu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> Kompletní vzorek kódu, ze kterého byl extrahován předchozí příklad kódu, naleznete v tématu [test volání pomocí DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994).
