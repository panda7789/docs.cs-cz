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
ms.openlocfilehash: 4fbb0931ee7d17d4b3264de512353dc75caf070d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-text-to-a-visual"></a>Postupy: Vykreslení textu do vizuálního objektu
Následující příklad ukazuje, jak nakreslit text, který má <xref:System.Windows.Media.DrawingVisual> pomocí <xref:System.Windows.Media.DrawingContext> objektu. Kreslení kontextu se vrátí při volání <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metodu <xref:System.Windows.Media.DrawingVisual> objektu. Grafika a text můžete zakreslit do výkresu kontextu.  
  
 Chcete-li do výkresu kontextu kreslení textu, použijte <xref:System.Windows.Media.DrawingContext.DrawText%2A> metodu <xref:System.Windows.Media.DrawingContext> objektu. Po skončení kreslení obsah do výkresu kontextu, volejte <xref:System.Windows.Media.DrawingContext.Close%2A> metoda zavřete kreslení kontextu a zachovat obsah.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  Ukázka dokončení kódu, ze kterého jste extrahovali v předchozím příkladu kódu, najdete v části [ukázka průchodu testu DrawingVisuals](http://go.microsoft.com/fwlink/?LinkID=159994).
