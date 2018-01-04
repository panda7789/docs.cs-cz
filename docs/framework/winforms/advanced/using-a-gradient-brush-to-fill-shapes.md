---
title: "Použití štětce přechodu k vyplnění obrazců"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a84a68f9082d00559938c2710b6574690fa6ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a><span data-ttu-id="9ffee-102">Použití štětce přechodu k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="9ffee-102">Using a Gradient Brush to Fill Shapes</span></span>
<span data-ttu-id="9ffee-103">Můžete štětce přechodu k vyplnění obrazce postupně změna barvou.</span><span class="sxs-lookup"><span data-stu-id="9ffee-103">You can use a gradient brush to fill a shape with a gradually changing color.</span></span> <span data-ttu-id="9ffee-104">Například můžete vodorovné přechodu k vyplnění obrazce s barvu, která postupně změní, když přesouváte od levého okraje tvaru na pravý okraj.</span><span class="sxs-lookup"><span data-stu-id="9ffee-104">For example, you can use a horizontal gradient to fill a shape with color that changes gradually as you move from the left edge of the shape to the right edge.</span></span> <span data-ttu-id="9ffee-105">Představte si obdélníku s levý okraj, který je černé (znázorněná červené, zelené a modré součásti 0, 0, 0) a pravý okraj, který je červený (představované 255, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="9ffee-105">Imagine a rectangle with a left edge that is black (represented by red, green, and blue components 0, 0, 0) and a right edge that is red (represented by 255, 0, 0).</span></span> <span data-ttu-id="9ffee-106">Pokud rámeček je 256 pixelů, bude jeden znak větší než red součást pixelů na levé straně, red součást dané pixelů.</span><span class="sxs-lookup"><span data-stu-id="9ffee-106">If the rectangle is 256 pixels wide, the red component of a given pixel will be one greater than the red component of the pixel to its left.</span></span> <span data-ttu-id="9ffee-107">Krajní levé pixelů v řádku obsahuje součásti barvu (0, 0, 0), druhý pixelů má (1, 0, 0), třetí pixelů má (2, 0, 0) a tak dále, dokud se nedostanete do úplně vpravo pixelů, která má součásti barvu (255, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="9ffee-107">The leftmost pixel in a row has color components (0, 0, 0), the second pixel has (1, 0, 0), the third pixel has (2, 0, 0), and so on, until you get to the rightmost pixel, which has color components (255, 0, 0).</span></span> <span data-ttu-id="9ffee-108">Tyto hodnoty interpolované barva tvoří přechod barev.</span><span class="sxs-lookup"><span data-stu-id="9ffee-108">These interpolated color values make up the color gradient.</span></span>  
  
 <span data-ttu-id="9ffee-109">Lineárního přechodu změní barvu jako přesunout vodorovně, svisle nebo paralelní na zadaný zkosené řádek.</span><span class="sxs-lookup"><span data-stu-id="9ffee-109">A linear gradient changes color as you move horizontally, vertically, or parallel to a specified slanted line.</span></span> <span data-ttu-id="9ffee-110">Přechodu cesty změní barvu, když přesouváte o interior a hranic cesty.</span><span class="sxs-lookup"><span data-stu-id="9ffee-110">A path gradient changes color as you move about the interior and boundary of a path.</span></span> <span data-ttu-id="9ffee-111">Cesty přechodu k dosažení širokou škálu důsledky můžete přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="9ffee-111">You can customize path gradients to achieve a wide variety of effects.</span></span>  
  
 <span data-ttu-id="9ffee-112">Následující obrázek znázorňuje obdélníku, naplní se lineární štětce přechodu a elipsy plná štětce přechodu cesty.</span><span class="sxs-lookup"><span data-stu-id="9ffee-112">The following illustration shows a rectangle filled with a linear gradient brush and an ellipse filled with a path gradient brush.</span></span>  
  
 <span data-ttu-id="9ffee-113">![Přechodu](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")</span><span class="sxs-lookup"><span data-stu-id="9ffee-113">![Gradient](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ffee-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9ffee-114">In This Section</span></span>  
 [<span data-ttu-id="9ffee-115">Postupy: Vytvoření lineárního přechodu</span><span class="sxs-lookup"><span data-stu-id="9ffee-115">How to: Create a Linear Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 <span data-ttu-id="9ffee-116">Ukazuje postup vytvoření lineárního přechodu pomocí <xref:System.Drawing.Drawing2D.LinearGradientBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="9ffee-116">Shows how to create a linear gradient using the <xref:System.Drawing.Drawing2D.LinearGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="9ffee-117">Postupy: Vytvoření přechodu cesty</span><span class="sxs-lookup"><span data-stu-id="9ffee-117">How to: Create a Path Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 <span data-ttu-id="9ffee-118">Popisuje postup vytvoření přechodu cesty pomocí <xref:System.Drawing.Drawing2D.PathGradientBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="9ffee-118">Describes how to create a path gradient using the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="9ffee-119">Postupy: Použití gama korekce na přechod</span><span class="sxs-lookup"><span data-stu-id="9ffee-119">How to: Apply Gamma Correction to a Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 <span data-ttu-id="9ffee-120">Vysvětluje, jak používat korekce gama s štětce přechodu.</span><span class="sxs-lookup"><span data-stu-id="9ffee-120">Explains how to use gamma correction with a gradient brush.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9ffee-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="9ffee-121">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="9ffee-122">Obsahuje popis této třídy a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="9ffee-122">Contains a description of this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="9ffee-123">Obsahuje popis této třídy a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="9ffee-123">Contains a description of this class and has links to all of its members.</span></span>
