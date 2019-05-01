---
title: Použití štětce přechodu k vyplnění obrazců
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
ms.openlocfilehash: 5771aaabd283d71f5fa6934f86a1c24a57f38dca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954454"
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a><span data-ttu-id="7a743-102">Použití štětce přechodu k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="7a743-102">Using a Gradient Brush to Fill Shapes</span></span>
<span data-ttu-id="7a743-103">Můžete použít štětce přechodu k vyplnění obrazce postupně měnící barvou.</span><span class="sxs-lookup"><span data-stu-id="7a743-103">You can use a gradient brush to fill a shape with a gradually changing color.</span></span> <span data-ttu-id="7a743-104">Například můžete použít vodorovný přechodu k vyplnění obrazce pomocí barev, která se mění postupně při přesunu z levého okraje tvaru do pravého okraje.</span><span class="sxs-lookup"><span data-stu-id="7a743-104">For example, you can use a horizontal gradient to fill a shape with color that changes gradually as you move from the left edge of the shape to the right edge.</span></span> <span data-ttu-id="7a743-105">Představte si obdélníku s levého okraje, která je černá (reprezentovaný identifikátorem komponenty červené, zelené a modré 0, 0, 0) a pravý okraj, který je red (reprezentovaný identifikátorem 255, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="7a743-105">Imagine a rectangle with a left edge that is black (represented by red, green, and blue components 0, 0, 0) and a right edge that is red (represented by 255, 0, 0).</span></span> <span data-ttu-id="7a743-106">Pokud obdélníku je 256 pixelů na šířku, bude hodnota červené dané pixelu větší než hodnota červené pixelu na levé straně.</span><span class="sxs-lookup"><span data-stu-id="7a743-106">If the rectangle is 256 pixels wide, the red component of a given pixel will be one greater than the red component of the pixel to its left.</span></span> <span data-ttu-id="7a743-107">Úplně vlevo obrazových bodů za sebou má barevným (0, 0, 0), je druhý pixel má (1, 0, 0), třetí pixel má (2, 0, 0) a tak dále, dokud se nedostanete na úplně vpravo pixel, který má barevným (255, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="7a743-107">The leftmost pixel in a row has color components (0, 0, 0), the second pixel has (1, 0, 0), the third pixel has (2, 0, 0), and so on, until you get to the rightmost pixel, which has color components (255, 0, 0).</span></span> <span data-ttu-id="7a743-108">Tyto hodnoty interpolovaná barva tvoří barev přechodu.</span><span class="sxs-lookup"><span data-stu-id="7a743-108">These interpolated color values make up the color gradient.</span></span>  
  
 <span data-ttu-id="7a743-109">Lineární přechod změní barvu, jak přesunout vodorovně, svisle, nebo paralelní na určený řádek zkosené.</span><span class="sxs-lookup"><span data-stu-id="7a743-109">A linear gradient changes color as you move horizontally, vertically, or parallel to a specified slanted line.</span></span> <span data-ttu-id="7a743-110">Cesty přechodu změní barvu při přesunu o vnitřních a hranice cesty.</span><span class="sxs-lookup"><span data-stu-id="7a743-110">A path gradient changes color as you move about the interior and boundary of a path.</span></span> <span data-ttu-id="7a743-111">Můžete přizpůsobit cesty přechodu k dosažení širokou škálu účinky.</span><span class="sxs-lookup"><span data-stu-id="7a743-111">You can customize path gradients to achieve a wide variety of effects.</span></span>  
  
 <span data-ttu-id="7a743-112">Následující obrázek znázorňuje obdélník vyplněny štětec lineárního přechodu a elipsa se štětce přechodu cesty.</span><span class="sxs-lookup"><span data-stu-id="7a743-112">The following illustration shows a rectangle filled with a linear gradient brush and an ellipse filled with a path gradient brush.</span></span>  
  
 <span data-ttu-id="7a743-113">![Gradient](./media/gradient2.png "gradient2")</span><span class="sxs-lookup"><span data-stu-id="7a743-113">![Gradient](./media/gradient2.png "gradient2")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7a743-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7a743-114">In This Section</span></span>  
 [<span data-ttu-id="7a743-115">Postupy: Vytvoření lineárního přechodu</span><span class="sxs-lookup"><span data-stu-id="7a743-115">How to: Create a Linear Gradient</span></span>](how-to-create-a-linear-gradient.md)  
 <span data-ttu-id="7a743-116">Ukazuje, jak vytvořit lineárního přechodu pomocí <xref:System.Drawing.Drawing2D.LinearGradientBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="7a743-116">Shows how to create a linear gradient using the <xref:System.Drawing.Drawing2D.LinearGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="7a743-117">Postupy: Vytvoření přechodu cesty</span><span class="sxs-lookup"><span data-stu-id="7a743-117">How to: Create a Path Gradient</span></span>](how-to-create-a-path-gradient.md)  
 <span data-ttu-id="7a743-118">Popisuje, jak vytvořit cestu přechodu pomocí <xref:System.Drawing.Drawing2D.PathGradientBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="7a743-118">Describes how to create a path gradient using the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="7a743-119">Postupy: Použití gama korekce na přechod</span><span class="sxs-lookup"><span data-stu-id="7a743-119">How to: Apply Gamma Correction to a Gradient</span></span>](how-to-apply-gamma-correction-to-a-gradient.md)  
 <span data-ttu-id="7a743-120">Vysvětluje způsob použití gama korekce s štětce přechodu.</span><span class="sxs-lookup"><span data-stu-id="7a743-120">Explains how to use gamma correction with a gradient brush.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7a743-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="7a743-121">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="7a743-122">Obsahuje popis této třídy a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="7a743-122">Contains a description of this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="7a743-123">Obsahuje popis této třídy a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="7a743-123">Contains a description of this class and has links to all of its members.</span></span>
