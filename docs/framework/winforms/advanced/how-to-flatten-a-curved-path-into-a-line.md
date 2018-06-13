---
title: 'Postupy: Narovnání zakřivené cesty na čáru'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: a3a8467dc5906a88911672316bb0f2ed3607d3a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521200"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a><span data-ttu-id="7ef11-102">Postupy: Narovnání zakřivené cesty na čáru</span><span class="sxs-lookup"><span data-stu-id="7ef11-102">How to: Flatten a Curved Path into a Line</span></span>
<span data-ttu-id="7ef11-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> objekt ukládá posloupnost čar a Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="7ef11-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> object stores a sequence of lines and Bézier splines.</span></span> <span data-ttu-id="7ef11-104">Můžete přidat několik typů křivek (tři tečky, oblouky, základní křivky vyhlazení) na cestu, ale každý křivky jsou převedeny na Bézierovy křivky předtím, než je uložen v cestě.</span><span class="sxs-lookup"><span data-stu-id="7ef11-104">You can add several types of curves (ellipses, arcs, cardinal splines) to a path, but each curve is converted to a Bézier spline before it is stored in the path.</span></span> <span data-ttu-id="7ef11-105">Vyrovnání cestu se skládá převodu každý Bézierovy křivky v cestě k posloupnost úseček.</span><span class="sxs-lookup"><span data-stu-id="7ef11-105">Flattening a path consists of converting each Bézier spline in the path to a sequence of straight lines.</span></span> <span data-ttu-id="7ef11-106">Následující obrázek znázorňuje cestu před a po shrnutí.</span><span class="sxs-lookup"><span data-stu-id="7ef11-106">The following illustration shows a path before and after flattening.</span></span>  
  
 <span data-ttu-id="7ef11-107">![Přímých čar a křivek](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span><span class="sxs-lookup"><span data-stu-id="7ef11-107">![Straight Lines and Curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span></span>  
  
### <a name="to-flatten-a-path"></a><span data-ttu-id="7ef11-108">Chcete-li narovnání cesty</span><span class="sxs-lookup"><span data-stu-id="7ef11-108">To Flatten a Path</span></span>  
  
-   <span data-ttu-id="7ef11-109">volání <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> metodu <xref:System.Drawing.Drawing2D.GraphicsPath> objektu.</span><span class="sxs-lookup"><span data-stu-id="7ef11-109">call the <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method of a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="7ef11-110"><xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> Metoda přijímá plochosti argument, který určuje maximální vzdálenost mezi plochou cestu a původní cestu.</span><span class="sxs-lookup"><span data-stu-id="7ef11-110">The <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method receives a flatness argument that specifies the maximum distance between the flattened path and the original path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ef11-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ef11-111">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 [<span data-ttu-id="7ef11-112">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="7ef11-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="7ef11-113">Sestavování a kreslení cest</span><span class="sxs-lookup"><span data-stu-id="7ef11-113">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
