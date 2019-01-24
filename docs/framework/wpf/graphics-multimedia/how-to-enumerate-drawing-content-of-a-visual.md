---
title: 'Postupy: Vyčíslení vykreslovaného vizuálního obsahu'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: a3131b6c86b0f6a7aa79cca305b9c3b2496346f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561945"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="11845-102">Postupy: Vyčíslení vykreslovaného vizuálního obsahu</span><span class="sxs-lookup"><span data-stu-id="11845-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="11845-103"><xref:System.Windows.Media.Drawing> Objekt neposkytuje objektový model pro vytvoření výčtu obsah <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="11845-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11845-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="11845-104">Example</span></span>  
 <span data-ttu-id="11845-105">V následujícím příkladu <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodu pro načtení <xref:System.Windows.Media.DrawingGroup> hodnotu <xref:System.Windows.Media.Visual> a výčet ho.</span><span class="sxs-lookup"><span data-stu-id="11845-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11845-106">Když jsou výčet obsah vizuálu, jsou načítání <xref:System.Windows.Media.Drawing> objekty a není základní reprezentace dat vykreslení jako seznam vektorové grafiky instrukce.</span><span class="sxs-lookup"><span data-stu-id="11845-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="11845-107">Další informace najdete v tématu [přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="11845-107">For more information, see [WPF Graphics Rendering Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="11845-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11845-108">See also</span></span>
- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="11845-109">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="11845-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="11845-110">Přehled vykreslování grafiky WPF</span><span class="sxs-lookup"><span data-stu-id="11845-110">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
