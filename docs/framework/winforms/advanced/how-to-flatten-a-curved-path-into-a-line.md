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
ms.openlocfilehash: a151b4244e14d3704fd5fa1c55de92211981232f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781363"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a><span data-ttu-id="60712-102">Postupy: Narovnání zakřivené cesty na čáru</span><span class="sxs-lookup"><span data-stu-id="60712-102">How to: Flatten a Curved Path into a Line</span></span>
<span data-ttu-id="60712-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> ukládá posloupnost řádky a Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="60712-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> object stores a sequence of lines and Bézier splines.</span></span> <span data-ttu-id="60712-104">Několik typů křivky (symbol tří teček, elipsy, základní křivky vyhlazení) můžete přidat do cesty, ale každý křivka je převést na Bézierovy křivky před jejich uložením v cestě.</span><span class="sxs-lookup"><span data-stu-id="60712-104">You can add several types of curves (ellipses, arcs, cardinal splines) to a path, but each curve is converted to a Bézier spline before it is stored in the path.</span></span> <span data-ttu-id="60712-105">Sloučení cesta se skládá z převodu jednotlivých Bézierovy křivky v cestě na řadu rovné čáry.</span><span class="sxs-lookup"><span data-stu-id="60712-105">Flattening a path consists of converting each Bézier spline in the path to a sequence of straight lines.</span></span> <span data-ttu-id="60712-106">Následující obrázek zobrazuje cestu, před a po sloučení.</span><span class="sxs-lookup"><span data-stu-id="60712-106">The following illustration shows a path before and after flattening.</span></span>  
  
 <span data-ttu-id="60712-107">![Přímých čar a křivek](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span><span class="sxs-lookup"><span data-stu-id="60712-107">![Straight Lines and Curves](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span></span>  
  
### <a name="to-flatten-a-path"></a><span data-ttu-id="60712-108">Chcete-li narovnání cesty</span><span class="sxs-lookup"><span data-stu-id="60712-108">To Flatten a Path</span></span>  
  
- <span data-ttu-id="60712-109">volání <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> metodu <xref:System.Drawing.Drawing2D.GraphicsPath> objektu.</span><span class="sxs-lookup"><span data-stu-id="60712-109">call the <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method of a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="60712-110"><xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> Metoda obdrží plochosti argument, který určuje maximální vzdálenost mezi plochá cestu a původní cestu.</span><span class="sxs-lookup"><span data-stu-id="60712-110">The <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method receives a flatness argument that specifies the maximum distance between the flattened path and the original path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60712-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60712-111">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- [<span data-ttu-id="60712-112">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="60712-112">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="60712-113">Sestavování a kreslení cest</span><span class="sxs-lookup"><span data-stu-id="60712-113">Constructing and Drawing Paths</span></span>](constructing-and-drawing-paths.md)
