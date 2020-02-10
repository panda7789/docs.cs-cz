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
# <a name="how-to-draw-text-to-a-visual"></a><span data-ttu-id="3db1b-102">Postupy: Vykreslení textu do vizuálního objektu</span><span class="sxs-lookup"><span data-stu-id="3db1b-102">How to: Draw Text to a Visual</span></span>
<span data-ttu-id="3db1b-103">Následující příklad ukazuje, jak nakreslit text do <xref:System.Windows.Media.DrawingVisual> pomocí objektu <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="3db1b-103">The following example shows how to draw text to a <xref:System.Windows.Media.DrawingVisual> using a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="3db1b-104">Kontext vykreslování je vrácen voláním metody <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> objektu <xref:System.Windows.Media.DrawingVisual>.</span><span class="sxs-lookup"><span data-stu-id="3db1b-104">A drawing context is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span> <span data-ttu-id="3db1b-105">Grafiku a text můžete nakreslit do kontextu vykreslování.</span><span class="sxs-lookup"><span data-stu-id="3db1b-105">You can draw graphics and text into a drawing context.</span></span>  
  
 <span data-ttu-id="3db1b-106">Chcete-li nakreslit text do kontextu vykreslování, použijte metodu <xref:System.Windows.Media.DrawingContext.DrawText%2A> objektu <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="3db1b-106">To draw text into the drawing context, use the <xref:System.Windows.Media.DrawingContext.DrawText%2A> method of a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="3db1b-107">Až dokončíte vykreslování obsahu do kontextu vykreslování, zavolejte metodu <xref:System.Windows.Media.DrawingContext.Close%2A> pro zavření kontextu vykreslování a zachování obsahu.</span><span class="sxs-lookup"><span data-stu-id="3db1b-107">When you are finished drawing content into the drawing context, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the drawing context and persist the content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3db1b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="3db1b-108">Example</span></span>  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="3db1b-109">Kompletní vzorek kódu, ze kterého byl extrahován předchozí příklad kódu, naleznete v tématu [test volání pomocí DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).</span><span class="sxs-lookup"><span data-stu-id="3db1b-109">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).</span></span>
