---
title: "Vyhlazení u čar a křivek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d69d635fbdd8720937cd189826c1496b8126ddef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="antialiasing-with-lines-and-curves"></a><span data-ttu-id="ad664-102">Vyhlazení u čar a křivek</span><span class="sxs-lookup"><span data-stu-id="ad664-102">Antialiasing with Lines and Curves</span></span>
<span data-ttu-id="ad664-103">Při použití [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kreslení čáry, zadejte výchozí bod a koncový bod řádku, ale není nutné poskytovat žádné informace o jednotlivých pixelů na řádek.</span><span class="sxs-lookup"><span data-stu-id="ad664-103">When you use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to draw a line, you provide the starting point and ending point of the line, but you do not have to provide any information about the individual pixels on the line.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="ad664-104">funguje ve spojení s software ovladače zobrazení k určení, které pixelů bude zapnuto zobrazíte řádek na konkrétní zobrazení zařízení.</span><span class="sxs-lookup"><span data-stu-id="ad664-104"> works in conjunction with the display driver software to determine which pixels will be turned on to show the line on a particular display device.</span></span>  
  
## <a name="aliasing"></a><span data-ttu-id="ad664-105">Aliasy</span><span class="sxs-lookup"><span data-stu-id="ad664-105">Aliasing</span></span>  
 <span data-ttu-id="ad664-106">Vezměte v úvahu rovnou red řádek, který přejde z bodu (4, 2) do bodu (16, 10).</span><span class="sxs-lookup"><span data-stu-id="ad664-106">Consider the straight red line that goes from the point (4, 2) to the point (16, 10).</span></span> <span data-ttu-id="ad664-107">Předpokládejme souřadnicový systém má původ v levém horním rohu a zda Měrná jednotka služby pixelech.</span><span class="sxs-lookup"><span data-stu-id="ad664-107">Assume the coordinate system has its origin in the upper-left corner and that the unit of measure is the pixel.</span></span> <span data-ttu-id="ad664-108">Také předpokládají, že osy x bodů vpravo a body osy y dolů.</span><span class="sxs-lookup"><span data-stu-id="ad664-108">Also assume that the x-axis points to the right and the y-axis points down.</span></span> <span data-ttu-id="ad664-109">Následující obrázek znázorňuje zvětšeným zobrazením červené linií na barevné pozadí.</span><span class="sxs-lookup"><span data-stu-id="ad664-109">The following illustration shows an enlarged view of the red line drawn on a multicolored background.</span></span>  
  
 <span data-ttu-id="ad664-110">![Řádek, žádné vyhlazení](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span><span class="sxs-lookup"><span data-stu-id="ad664-110">![Line, no antialiasing](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span></span>  
  
 <span data-ttu-id="ad664-111">Red pixelů použitý k vykreslení řádku jsou neprůhledné.</span><span class="sxs-lookup"><span data-stu-id="ad664-111">The red pixels used to render the line are opaque.</span></span> <span data-ttu-id="ad664-112">V řádku nejsou žádné částečně transparentní pixelů.</span><span class="sxs-lookup"><span data-stu-id="ad664-112">There are no partially transparent pixels in the line.</span></span> <span data-ttu-id="ad664-113">Tento typ řádku vykreslování nabízí řádek vícenásobná vzhled a řádek vypadal něco jako schodiště.</span><span class="sxs-lookup"><span data-stu-id="ad664-113">This type of line rendering gives the line a jagged appearance, and the line looks somewhat like a staircase.</span></span> <span data-ttu-id="ad664-114">Tato technika reprezentace čáry s schodiště nazývá aliasy; schodiště je alias teoretické řádku.</span><span class="sxs-lookup"><span data-stu-id="ad664-114">This technique of representing a line with a staircase is called aliasing; the staircase is an alias for the theoretical line.</span></span>  
  
## <a name="antialiasing"></a><span data-ttu-id="ad664-115">Vyhlazení</span><span class="sxs-lookup"><span data-stu-id="ad664-115">Antialiasing</span></span>  
 <span data-ttu-id="ad664-116">Složitější technika pro vykreslování řádku, která využívá částečně transparentní pixelů společně s neprůhledností pixelů.</span><span class="sxs-lookup"><span data-stu-id="ad664-116">A more sophisticated technique for rendering a line involves using partially transparent pixels along with opaque pixels.</span></span> <span data-ttu-id="ad664-117">Pixelů jsou nastaveny na čistý červený, nebo na některé blend red a barvu pozadí v závislosti na tom, jak zavřít jsou na řádek.</span><span class="sxs-lookup"><span data-stu-id="ad664-117">Pixels are set to pure red, or to some blend of red and the background color, depending on how close they are to the line.</span></span> <span data-ttu-id="ad664-118">Tento typ vykreslování se nazývá vyhlazení a výsledkem řádek, který zjistí lidské oko jako více smooth.</span><span class="sxs-lookup"><span data-stu-id="ad664-118">This type of rendering is called antialiasing and results in a line that the human eye perceives as more smooth.</span></span> <span data-ttu-id="ad664-119">Následující obrázek znázorňuje, jak jsou s na pozadí k vytvoření řádku s antialiased smíšení určité pixelů.</span><span class="sxs-lookup"><span data-stu-id="ad664-119">The following illustration shows how certain pixels are blended with the background to produce an antialiased line.</span></span>  
  
 <span data-ttu-id="ad664-120">![Vyhlazení řádek](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span><span class="sxs-lookup"><span data-stu-id="ad664-120">![Antialiasing a Line](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span></span>  
  
 <span data-ttu-id="ad664-121">Vyhlazení, označované taky jako vyhlazování, je použít také pro křivek.</span><span class="sxs-lookup"><span data-stu-id="ad664-121">Antialiasing, also called smoothing, can also be applied to curves.</span></span> <span data-ttu-id="ad664-122">Následující obrázek znázorňuje zvětšeným zobrazením vyhlazenými třemi tečkami.</span><span class="sxs-lookup"><span data-stu-id="ad664-122">The following illustration shows an enlarged view of a smoothed ellipse.</span></span>  
  
 <span data-ttu-id="ad664-123">![Křivky vyhlazení](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span><span class="sxs-lookup"><span data-stu-id="ad664-123">![Antialiasing Curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span></span>  
  
 <span data-ttu-id="ad664-124">Následující obrázek znázorňuje stejné elipsy v jeho skutečná velikost jednou bez vyhlazení a posléze s vyhlazení.</span><span class="sxs-lookup"><span data-stu-id="ad664-124">The following illustration shows the same ellipse in its actual size, once without antialiasing and once with antialiasing.</span></span>  
  
 <span data-ttu-id="ad664-125">![Příklad vyhlazení](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span><span class="sxs-lookup"><span data-stu-id="ad664-125">![Antialiasing example](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span></span>  
  
 <span data-ttu-id="ad664-126">Kreslení čar a křivek, které používají vyhlazení, vytvořte instanci <xref:System.Drawing.Graphics> a nastavit jeho <xref:System.Drawing.Graphics.SmoothingMode%2A> vlastnost <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> nebo <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span><span class="sxs-lookup"><span data-stu-id="ad664-126">To draw lines and curves that use antialiasing, create an instance of the <xref:System.Drawing.Graphics> class and set its <xref:System.Drawing.Graphics.SmoothingMode%2A> property to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> or <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span></span> <span data-ttu-id="ad664-127">Potom zavolejte jednu z metod vykreslování této stejné <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="ad664-127">Then call one of the drawing methods of that same <xref:System.Drawing.Graphics> class.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a><span data-ttu-id="ad664-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad664-128">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>  
 [<span data-ttu-id="ad664-129">Čar, křivek a obrazců</span><span class="sxs-lookup"><span data-stu-id="ad664-129">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="ad664-130">Postupy: použití vyhlazení s textem</span><span class="sxs-lookup"><span data-stu-id="ad664-130">How to: Use Antialiasing with Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)
