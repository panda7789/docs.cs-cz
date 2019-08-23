---
title: 'Postupy: Vyčíslení vykreslovaného vizuálního obsahu'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 25aa0c3706005c1e16cedd7e06914db764545ebb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930073"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="abefb-102">Postupy: Vyčíslení vykreslovaného vizuálního obsahu</span><span class="sxs-lookup"><span data-stu-id="abefb-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="abefb-103">Objekt poskytují objektový model pro vytváření výčtu obsahu <xref:System.Windows.Media.Visual>. <xref:System.Windows.Media.Drawing></span><span class="sxs-lookup"><span data-stu-id="abefb-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abefb-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="abefb-104">Example</span></span>  
 <span data-ttu-id="abefb-105">Následující příklad používá <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodu k <xref:System.Windows.Media.DrawingGroup> načtení hodnoty <xref:System.Windows.Media.Visual> a k jejímu vytvoření.</span><span class="sxs-lookup"><span data-stu-id="abefb-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="abefb-106">Při vytváření výčtu obsahu vizuálu načítáte <xref:System.Windows.Media.Drawing> objekty, a ne základní reprezentace dat vykreslování jako seznam instrukcí pro vektorovou grafiku.</span><span class="sxs-lookup"><span data-stu-id="abefb-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="abefb-107">Další informace naleznete v tématu [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="abefb-107">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="abefb-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abefb-108">See also</span></span>

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="abefb-109">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="abefb-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="abefb-110">Přehled vykreslování grafiky WPF</span><span class="sxs-lookup"><span data-stu-id="abefb-110">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
