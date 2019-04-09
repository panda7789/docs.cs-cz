---
title: Omezení kreslicí plochy v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
ms.openlocfilehash: d0508166f905b45789ce638b03d0747dd6fa904e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074955"
---
# <a name="restricting-the-drawing-surface-in-gdi"></a><span data-ttu-id="8c994-102">Omezení kreslicí plochy v GDI+</span><span class="sxs-lookup"><span data-stu-id="8c994-102">Restricting the Drawing Surface in GDI+</span></span>
<span data-ttu-id="8c994-103">Výstřižek zahrnuje omezení kreslení obdélníku nebo oblasti.</span><span class="sxs-lookup"><span data-stu-id="8c994-103">Clipping involves restricting drawing to a certain rectangle or region.</span></span> <span data-ttu-id="8c994-104">Následující obrázek znázorňuje řetězec "Hello" přichycena ve tvaru srdce oblast.</span><span class="sxs-lookup"><span data-stu-id="8c994-104">The following illustration shows the string "Hello" clipped to a heart-shaped region.</span></span>  
  
 <span data-ttu-id="8c994-105">![Omezený kreslicí ploše](./media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span><span class="sxs-lookup"><span data-stu-id="8c994-105">![Restricted Drawing Surface](./media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span></span>  
  
## <a name="clipping-with-regions"></a><span data-ttu-id="8c994-106">Oříznutí s oblastí</span><span class="sxs-lookup"><span data-stu-id="8c994-106">Clipping with Regions</span></span>  
 <span data-ttu-id="8c994-107">Oblasti lze zkonstruovat z cesty a cesty mohou obsahovat jsou podrobněji popsány dále řetězců, takže textu osnovy můžete použít pro oříznutí.</span><span class="sxs-lookup"><span data-stu-id="8c994-107">Regions can be constructed from paths, and paths can contain the outlines of strings, so you can use outlined text for clipping.</span></span> <span data-ttu-id="8c994-108">Následující obrázek znázorňuje sadu soustředných symbol tří teček přichycena vnitřní části textového řetězce.</span><span class="sxs-lookup"><span data-stu-id="8c994-108">The following illustration shows a set of concentric ellipses clipped to the interior of a string of text.</span></span>  
  
 <span data-ttu-id="8c994-109">![Omezený kreslicí ploše](./media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span><span class="sxs-lookup"><span data-stu-id="8c994-109">![Restricted Drawing Surface](./media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span></span>  
  
 <span data-ttu-id="8c994-110">Kreslení pomocí oříznutí, vytvořit <xref:System.Drawing.Graphics> objektu, nastavte jeho <xref:System.Drawing.Graphics.Clip%2A> vlastnost a poté zavolá stejné výkresu metody, která <xref:System.Drawing.Graphics> objektu:</span><span class="sxs-lookup"><span data-stu-id="8c994-110">To draw with clipping, create a <xref:System.Drawing.Graphics> object, set its <xref:System.Drawing.Graphics.Clip%2A> property, and then call the drawing methods of that same <xref:System.Drawing.Graphics> object:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#91](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a><span data-ttu-id="8c994-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c994-111">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [<span data-ttu-id="8c994-112">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="8c994-112">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="8c994-113">Použití oblastí</span><span class="sxs-lookup"><span data-stu-id="8c994-113">Using Regions</span></span>](using-regions.md)
