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
ms.openlocfilehash: bc7a4f989137ec2b021d27a6e112ff1aebd99d07
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523240"
---
# <a name="how-to-draw-text-to-a-visual"></a><span data-ttu-id="1c9c9-102">Postupy: Vykreslení textu do vizuálního objektu</span><span class="sxs-lookup"><span data-stu-id="1c9c9-102">How to: Draw Text to a Visual</span></span>
<span data-ttu-id="1c9c9-103">Následující příklad ukazuje, jak nakreslit text, který má <xref:System.Windows.Media.DrawingVisual> pomocí <xref:System.Windows.Media.DrawingContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="1c9c9-103">The following example shows how to draw text to a <xref:System.Windows.Media.DrawingVisual> using a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="1c9c9-104">Kreslení kontext je vrácený voláním <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metodu <xref:System.Windows.Media.DrawingVisual> objektu.</span><span class="sxs-lookup"><span data-stu-id="1c9c9-104">A drawing context is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span> <span data-ttu-id="1c9c9-105">Kreslení kontextu lze nakreslit grafiku a text.</span><span class="sxs-lookup"><span data-stu-id="1c9c9-105">You can draw graphics and text into a drawing context.</span></span>  
  
 <span data-ttu-id="1c9c9-106">Vykreslení textu do výkresu kontextu, použijte <xref:System.Windows.Media.DrawingContext.DrawText%2A> metodu <xref:System.Windows.Media.DrawingContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="1c9c9-106">To draw text into the drawing context, use the <xref:System.Windows.Media.DrawingContext.DrawText%2A> method of a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="1c9c9-107">Po dokončení vykreslení obsahu do výkresu kontextu volat <xref:System.Windows.Media.DrawingContext.Close%2A> metoda zavřete výkresu kontextu a zachovat obsah.</span><span class="sxs-lookup"><span data-stu-id="1c9c9-107">When you are finished drawing content into the drawing context, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the drawing context and persist the content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c9c9-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c9c9-108">Example</span></span>  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="1c9c9-109">Kompletní kód ukázku, ze které byla extrahována v předchozím příkladu kódu najdete v tématu [ukázka spuštění testu DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994).</span><span class="sxs-lookup"><span data-stu-id="1c9c9-109">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994).</span></span>
