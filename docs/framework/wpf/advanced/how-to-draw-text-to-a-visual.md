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
# <a name="how-to-draw-text-to-a-visual"></a><span data-ttu-id="94a85-102">Postupy: Vykreslení textu do vizuálního objektu</span><span class="sxs-lookup"><span data-stu-id="94a85-102">How to: Draw Text to a Visual</span></span>
<span data-ttu-id="94a85-103">Následující příklad ukazuje, jak nakreslit text na <xref:System.Windows.Media.DrawingVisual> <xref:System.Windows.Media.DrawingContext> objekt pomocí objektu.</span><span class="sxs-lookup"><span data-stu-id="94a85-103">The following example shows how to draw text to a <xref:System.Windows.Media.DrawingVisual> using a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="94a85-104">Kontext vykreslování je vrácen voláním <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metody <xref:System.Windows.Media.DrawingVisual> objektu.</span><span class="sxs-lookup"><span data-stu-id="94a85-104">A drawing context is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span> <span data-ttu-id="94a85-105">Grafiku a text můžete nakreslit do kontextu vykreslování.</span><span class="sxs-lookup"><span data-stu-id="94a85-105">You can draw graphics and text into a drawing context.</span></span>  
  
 <span data-ttu-id="94a85-106">Chcete-li nakreslit text do kontextu vykreslování, <xref:System.Windows.Media.DrawingContext.DrawText%2A> použijte metodu <xref:System.Windows.Media.DrawingContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="94a85-106">To draw text into the drawing context, use the <xref:System.Windows.Media.DrawingContext.DrawText%2A> method of a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="94a85-107">Až dokončíte vykreslování obsahu do kontextu vykreslování, zavolejte <xref:System.Windows.Media.DrawingContext.Close%2A> metodu pro zavření kontextu vykreslování a zachování obsahu.</span><span class="sxs-lookup"><span data-stu-id="94a85-107">When you are finished drawing content into the drawing context, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the drawing context and persist the content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94a85-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="94a85-108">Example</span></span>  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="94a85-109">Kompletní vzorek kódu, ze kterého byl extrahován předchozí příklad kódu, naleznete v tématu [test volání pomocí DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994).</span><span class="sxs-lookup"><span data-stu-id="94a85-109">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994).</span></span>
