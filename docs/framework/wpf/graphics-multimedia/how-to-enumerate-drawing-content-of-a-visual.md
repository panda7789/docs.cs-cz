---
title: 'Postupy: Vyčíslení vykreslovaného vizuálního obsahu'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 6414026090766544585c8e5e940ef9f0c62566d2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360007"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="c68f0-102">Postupy: Vyčíslení vykreslovaného vizuálního obsahu</span><span class="sxs-lookup"><span data-stu-id="c68f0-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="c68f0-103"><xref:System.Windows.Media.Drawing> Objekt neposkytuje objektový model pro vytvoření výčtu obsah <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="c68f0-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c68f0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c68f0-104">Example</span></span>  
 <span data-ttu-id="c68f0-105">V následujícím příkladu <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodu pro načtení <xref:System.Windows.Media.DrawingGroup> hodnotu <xref:System.Windows.Media.Visual> a výčet ho.</span><span class="sxs-lookup"><span data-stu-id="c68f0-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c68f0-106">Když jsou výčet obsah vizuálu, jsou načítání <xref:System.Windows.Media.Drawing> objekty a není základní reprezentace dat vykreslení jako seznam vektorové grafiky instrukce.</span><span class="sxs-lookup"><span data-stu-id="c68f0-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="c68f0-107">Další informace najdete v tématu [přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c68f0-107">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="c68f0-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c68f0-108">See also</span></span>
- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="c68f0-109">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="c68f0-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="c68f0-110">Přehled vykreslování grafiky WPF</span><span class="sxs-lookup"><span data-stu-id="c68f0-110">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
