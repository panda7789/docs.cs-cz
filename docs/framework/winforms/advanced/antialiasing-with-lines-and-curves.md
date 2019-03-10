---
title: Vyhlazení u čar a křivek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
ms.openlocfilehash: 6ea49c591b43d3f70bfd39058fd5ee256c537ec2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725009"
---
# <a name="antialiasing-with-lines-and-curves"></a><span data-ttu-id="193bc-102">Vyhlazení u čar a křivek</span><span class="sxs-lookup"><span data-stu-id="193bc-102">Antialiasing with Lines and Curves</span></span>
<span data-ttu-id="193bc-103">Při použití [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] nakreslení čáry, zadáte počáteční bod a koncový bod řádku, ale není potřeba poskytovat žádné informace o jednotlivých pixelech na řádku.</span><span class="sxs-lookup"><span data-stu-id="193bc-103">When you use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to draw a line, you provide the starting point and ending point of the line, but you do not have to provide any information about the individual pixels on the line.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="193bc-104">funguje ve spojení s ovladač zobrazení k určení, které pixelů zapne k zobrazení řádku v konkrétní zobrazení zařízení.</span><span class="sxs-lookup"><span data-stu-id="193bc-104">works in conjunction with the display driver software to determine which pixels will be turned on to show the line on a particular display device.</span></span>  
  
## <a name="aliasing"></a><span data-ttu-id="193bc-105">Vyhlazení</span><span class="sxs-lookup"><span data-stu-id="193bc-105">Aliasing</span></span>  
 <span data-ttu-id="193bc-106">Vezměte v úvahu přímo červená čára, která přejde z bodu (4, 2) na bod (16, 10).</span><span class="sxs-lookup"><span data-stu-id="193bc-106">Consider the straight red line that goes from the point (4, 2) to the point (16, 10).</span></span> <span data-ttu-id="193bc-107">Předpokládejme souřadnicový systém má původu v levém horním rohu a zda je jednotka měření je pixel.</span><span class="sxs-lookup"><span data-stu-id="193bc-107">Assume the coordinate system has its origin in the upper-left corner and that the unit of measure is the pixel.</span></span> <span data-ttu-id="193bc-108">Taky se předpokládá, že osa x odkazuje na pravé straně a osy y body dolů.</span><span class="sxs-lookup"><span data-stu-id="193bc-108">Also assume that the x-axis points to the right and the y-axis points down.</span></span> <span data-ttu-id="193bc-109">Následující obrázek znázorňuje zvětšeným zobrazením červené čáry vykreslen na barevné pozadí.</span><span class="sxs-lookup"><span data-stu-id="193bc-109">The following illustration shows an enlarged view of the red line drawn on a multicolored background.</span></span>  
  
 <span data-ttu-id="193bc-110">![Řádek, bez antialiasingu](./media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span><span class="sxs-lookup"><span data-stu-id="193bc-110">![Line, no antialiasing](./media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span></span>  
  
 <span data-ttu-id="193bc-111">Červené pixelů použitý k vykreslení čáry jsou neprůhledné.</span><span class="sxs-lookup"><span data-stu-id="193bc-111">The red pixels used to render the line are opaque.</span></span> <span data-ttu-id="193bc-112">V řádku nejsou žádné pixelech částečně transparentní.</span><span class="sxs-lookup"><span data-stu-id="193bc-112">There are no partially transparent pixels in the line.</span></span> <span data-ttu-id="193bc-113">Tento typ čáry vykreslování poskytuje řádku vícenásobná vzhled a řádek vypadal něco jako schodiště.</span><span class="sxs-lookup"><span data-stu-id="193bc-113">This type of line rendering gives the line a jagged appearance, and the line looks somewhat like a staircase.</span></span> <span data-ttu-id="193bc-114">Tato technika reprezentovat čáry s schodiště se nazývá aliasing, schodiště je alias pro teoretické řádek.</span><span class="sxs-lookup"><span data-stu-id="193bc-114">This technique of representing a line with a staircase is called aliasing; the staircase is an alias for the theoretical line.</span></span>  
  
## <a name="antialiasing"></a><span data-ttu-id="193bc-115">Vyhlazení</span><span class="sxs-lookup"><span data-stu-id="193bc-115">Antialiasing</span></span>  
 <span data-ttu-id="193bc-116">Složitější techniku pro vykreslení čáry zahrnuje použití částečně transparentní pixelů spolu s neprůhledné pixelů.</span><span class="sxs-lookup"><span data-stu-id="193bc-116">A more sophisticated technique for rendering a line involves using partially transparent pixels along with opaque pixels.</span></span> <span data-ttu-id="193bc-117">Obrazové body jsou nastaveny na čistě červenou nebo některé blendu červené a barva pozadí v závislosti na tom, jak blízko se na řádek.</span><span class="sxs-lookup"><span data-stu-id="193bc-117">Pixels are set to pure red, or to some blend of red and the background color, depending on how close they are to the line.</span></span> <span data-ttu-id="193bc-118">Tento typ vykreslování se nazývá vyhlazení a výsledkem řádek, který zjistí z pohledu uživatele jako více hladký průběh.</span><span class="sxs-lookup"><span data-stu-id="193bc-118">This type of rendering is called antialiasing and results in a line that the human eye perceives as more smooth.</span></span> <span data-ttu-id="193bc-119">Následující obrázek znázorňuje, jak jsou prolnuty určité pixelů na pozadí a k vytvoření řádku antialiased.</span><span class="sxs-lookup"><span data-stu-id="193bc-119">The following illustration shows how certain pixels are blended with the background to produce an antialiased line.</span></span>  
  
 <span data-ttu-id="193bc-120">![Vyhlazení řádku](./media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span><span class="sxs-lookup"><span data-stu-id="193bc-120">![Antialiasing a Line](./media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span></span>  
  
 <span data-ttu-id="193bc-121">Vyhlazení, také nazývané vyhlazování, můžete použít také pro křivky.</span><span class="sxs-lookup"><span data-stu-id="193bc-121">Antialiasing, also called smoothing, can also be applied to curves.</span></span> <span data-ttu-id="193bc-122">Následující obrázek znázorňuje zvětšeným zobrazením vyhlazenými elipsy.</span><span class="sxs-lookup"><span data-stu-id="193bc-122">The following illustration shows an enlarged view of a smoothed ellipse.</span></span>  
  
 <span data-ttu-id="193bc-123">![Antialiasing Curves](./media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span><span class="sxs-lookup"><span data-stu-id="193bc-123">![Antialiasing Curves](./media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span></span>  
  
 <span data-ttu-id="193bc-124">Následující obrázek znázorňuje stejné elipsy ve skutečné velikosti, bez vyhlazení a posléze s vyhlazení.</span><span class="sxs-lookup"><span data-stu-id="193bc-124">The following illustration shows the same ellipse in its actual size, once without antialiasing and once with antialiasing.</span></span>  
  
 <span data-ttu-id="193bc-125">![Antialiasing example](./media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span><span class="sxs-lookup"><span data-stu-id="193bc-125">![Antialiasing example](./media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span></span>  
  
 <span data-ttu-id="193bc-126">Kreslení čar a křivek, které používají vyhlazení, vytvoření instance <xref:System.Drawing.Graphics> třídy a nastavit jeho <xref:System.Drawing.Graphics.SmoothingMode%2A> vlastnost <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> nebo <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span><span class="sxs-lookup"><span data-stu-id="193bc-126">To draw lines and curves that use antialiasing, create an instance of the <xref:System.Drawing.Graphics> class and set its <xref:System.Drawing.Graphics.SmoothingMode%2A> property to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> or <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span></span> <span data-ttu-id="193bc-127">Pak volání jedné z metod výkresu, který stejné <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="193bc-127">Then call one of the drawing methods of that same <xref:System.Drawing.Graphics> class.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#81](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a><span data-ttu-id="193bc-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="193bc-128">See also</span></span>
- <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>
- [<span data-ttu-id="193bc-129">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="193bc-129">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="193bc-130">Postupy: Použití vyhlazení s textem</span><span class="sxs-lookup"><span data-stu-id="193bc-130">How to: Use Antialiasing with Text</span></span>](how-to-use-antialiasing-with-text.md)
