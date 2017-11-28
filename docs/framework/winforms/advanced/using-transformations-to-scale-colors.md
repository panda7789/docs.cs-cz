---
title: "Použití transformací pro škálování barev"
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
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4584b74cd7a394f7dd04d0cfba150b907ca7c82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-transformations-to-scale-colors"></a><span data-ttu-id="889cf-102">Použití transformací pro škálování barev</span><span class="sxs-lookup"><span data-stu-id="889cf-102">Using Transformations to Scale Colors</span></span>
<span data-ttu-id="889cf-103">Škálování transformace vynásobí jednu nebo více součástí čtyři barvu podle čísla.</span><span class="sxs-lookup"><span data-stu-id="889cf-103">A scaling transformation multiplies one or more of the four color components by a number.</span></span> <span data-ttu-id="889cf-104">V následující tabulce jsou uvedeny položek matice barev, které představují škálování.</span><span class="sxs-lookup"><span data-stu-id="889cf-104">The color matrix entries that represent scaling are given in the following table.</span></span>  
  
|<span data-ttu-id="889cf-105">Součást, kterou je možné škálovat</span><span class="sxs-lookup"><span data-stu-id="889cf-105">Component to be scaled</span></span>|<span data-ttu-id="889cf-106">Položka matice</span><span class="sxs-lookup"><span data-stu-id="889cf-106">Matrix entry</span></span>|  
|----------------------------|------------------|  
|<span data-ttu-id="889cf-107">červená</span><span class="sxs-lookup"><span data-stu-id="889cf-107">Red</span></span>|<span data-ttu-id="889cf-108">[0][0]</span><span class="sxs-lookup"><span data-stu-id="889cf-108">[0][0]</span></span>|  
|<span data-ttu-id="889cf-109">zelená</span><span class="sxs-lookup"><span data-stu-id="889cf-109">Green</span></span>|<span data-ttu-id="889cf-110">[1][1]</span><span class="sxs-lookup"><span data-stu-id="889cf-110">[1][1]</span></span>|  
|<span data-ttu-id="889cf-111">modrá</span><span class="sxs-lookup"><span data-stu-id="889cf-111">Blue</span></span>|<span data-ttu-id="889cf-112">[2][2]</span><span class="sxs-lookup"><span data-stu-id="889cf-112">[2][2]</span></span>|  
|<span data-ttu-id="889cf-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="889cf-113">Alpha</span></span>|<span data-ttu-id="889cf-114">[3][3]</span><span class="sxs-lookup"><span data-stu-id="889cf-114">[3][3]</span></span>|  
  
## <a name="scaling-one-color"></a><span data-ttu-id="889cf-115">Škálování jedné barvy</span><span class="sxs-lookup"><span data-stu-id="889cf-115">Scaling One Color</span></span>  
 <span data-ttu-id="889cf-116">Následující příklad vytvoří <xref:System.Drawing.Image> objektu ze souboru ColorBars2.bmp.</span><span class="sxs-lookup"><span data-stu-id="889cf-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="889cf-117">Kód pak škáluje faktorem 2 blue součást každý pixelů v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="889cf-117">Then the code scales the blue component of each pixel in the image by a factor of 2.</span></span> <span data-ttu-id="889cf-118">Původní bitové kopie vykreslením spolu s transformovaných bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="889cf-118">The original image is drawn alongside the transformed image.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 <span data-ttu-id="889cf-119">Následující obrázek znázorňuje původní bitové kopie na levé straně a bitovou kopii škálovat na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="889cf-119">The following illustration shows the original image on the left and the scaled image on the right.</span></span>  
  
 <span data-ttu-id="889cf-120">![Škálování barev](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")</span><span class="sxs-lookup"><span data-stu-id="889cf-120">![Scale Colors](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")</span></span>  
  
 <span data-ttu-id="889cf-121">Následující tabulka uvádí vektory barvu pro pruhy čtyři před a po blue škálování.</span><span class="sxs-lookup"><span data-stu-id="889cf-121">The following table lists the color vectors for the four bars before and after the blue scaling.</span></span> <span data-ttu-id="889cf-122">Všimněte si, že blue součástí čtvrtý pruhu barev byl přesunut z 0,8 do 0,6.</span><span class="sxs-lookup"><span data-stu-id="889cf-122">Note that the blue component in the fourth color bar went from 0.8 to 0.6.</span></span> <span data-ttu-id="889cf-123">Je to způsobeno [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zachová pouze zlomkové části výsledku.</span><span class="sxs-lookup"><span data-stu-id="889cf-123">That is because [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] retains only the fractional part of the result.</span></span> <span data-ttu-id="889cf-124">Například (2)(0.8) = 1.6, a zlomkové části 1.6 je 0,6.</span><span class="sxs-lookup"><span data-stu-id="889cf-124">For example, (2)(0.8) = 1.6, and the fractional part of 1.6 is 0.6.</span></span> <span data-ttu-id="889cf-125">Ponechá pouze zlomkové části zajistí, že výsledkem je vždy v intervalu [0, 1].</span><span class="sxs-lookup"><span data-stu-id="889cf-125">Retaining only the fractional part ensures that the result is always in the interval [0, 1].</span></span>  
  
|<span data-ttu-id="889cf-126">Původní</span><span class="sxs-lookup"><span data-stu-id="889cf-126">Original</span></span>|<span data-ttu-id="889cf-127">Škálovat</span><span class="sxs-lookup"><span data-stu-id="889cf-127">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="889cf-128">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-128">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="889cf-129">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-129">(0.4, 0.4, 0.8, 1)</span></span>|  
|<span data-ttu-id="889cf-130">(0.4, 0.2, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-130">(0.4, 0.2, 0.2, 1)</span></span>|<span data-ttu-id="889cf-131">(0.4, 0.2, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-131">(0.4, 0.2, 0.4, 1)</span></span>|  
|<span data-ttu-id="889cf-132">(0.2, 0.4, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-132">(0.2, 0.4, 0.2, 1)</span></span>|<span data-ttu-id="889cf-133">(0.2, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-133">(0.2, 0.4, 0.4, 1)</span></span>|  
|<span data-ttu-id="889cf-134">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-134">(0.4, 0.4, 0.8, 1)</span></span>|<span data-ttu-id="889cf-135">(0.4, 0.4, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-135">(0.4, 0.4, 0.6, 1)</span></span>|  
  
## <a name="scaling-multiple-colors"></a><span data-ttu-id="889cf-136">Škálování více barev</span><span class="sxs-lookup"><span data-stu-id="889cf-136">Scaling Multiple Colors</span></span>  
 <span data-ttu-id="889cf-137">Následující příklad vytvoří <xref:System.Drawing.Image> objektu ze souboru ColorBars2.bmp.</span><span class="sxs-lookup"><span data-stu-id="889cf-137">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="889cf-138">Potom kód škáluje červené, zelené a modré součástí každého pixelů v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="889cf-138">Then the code scales the red, green, and blue components of each pixel in the image.</span></span> <span data-ttu-id="889cf-139">Red součásti jsou škálovat dolů 25 procent, komponenty zelená zmenšování 35 procent a komponenty blue zmenšování 50 procent.</span><span class="sxs-lookup"><span data-stu-id="889cf-139">The red components are scaled down 25 percent, the green components are scaled down 35 percent, and the blue components are scaled down 50 percent.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 <span data-ttu-id="889cf-140">Následující obrázek znázorňuje původní bitové kopie na levé straně a bitovou kopii škálovat na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="889cf-140">The following illustration shows the original image on the left and the scaled image on the right.</span></span>  
  
 <span data-ttu-id="889cf-141">![Škálování barev](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")</span><span class="sxs-lookup"><span data-stu-id="889cf-141">![Scale Colors](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")</span></span>  
  
 <span data-ttu-id="889cf-142">Následující tabulka uvádí vektory barvu pro pruhy čtyři před a po červené, zelené a modré škálování.</span><span class="sxs-lookup"><span data-stu-id="889cf-142">The following table lists the color vectors for the four bars before and after the red, green and blue scaling.</span></span>  
  
|<span data-ttu-id="889cf-143">Původní</span><span class="sxs-lookup"><span data-stu-id="889cf-143">Original</span></span>|<span data-ttu-id="889cf-144">Škálovat</span><span class="sxs-lookup"><span data-stu-id="889cf-144">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="889cf-145">(0.6, 0.6, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-145">(0.6, 0.6, 0.6, 1)</span></span>|<span data-ttu-id="889cf-146">(0.45, 0.39, 0.3, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-146">(0.45, 0.39, 0.3, 1)</span></span>|  
|<span data-ttu-id="889cf-147">(0, 1, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-147">(0, 1, 1, 1)</span></span>|<span data-ttu-id="889cf-148">(0, 0.65, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-148">(0, 0.65, 0.5, 1)</span></span>|  
|<span data-ttu-id="889cf-149">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-149">(1, 1, 0, 1)</span></span>|<span data-ttu-id="889cf-150">(0.75, 0.65, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-150">(0.75, 0.65, 0, 1)</span></span>|  
|<span data-ttu-id="889cf-151">(1, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-151">(1, 0, 1, 1)</span></span>|<span data-ttu-id="889cf-152">(0.75, 0, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="889cf-152">(0.75, 0, 0.5, 1)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="889cf-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="889cf-153">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="889cf-154">Grafika a kreslení v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="889cf-154">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="889cf-155">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="889cf-155">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
