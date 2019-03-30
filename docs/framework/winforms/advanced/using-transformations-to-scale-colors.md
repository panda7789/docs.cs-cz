---
title: Použití transformací pro škálování barev
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
ms.openlocfilehash: 9255dd4adba19bfef1332e5e3dfa463ee96f43f0
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653987"
---
# <a name="using-transformations-to-scale-colors"></a><span data-ttu-id="41fbd-102">Použití transformací pro škálování barev</span><span class="sxs-lookup"><span data-stu-id="41fbd-102">Using Transformations to Scale Colors</span></span>
<span data-ttu-id="41fbd-103">Transformace měřítka vynásobí jeden nebo více součástí čtyři barvy podle čísla.</span><span class="sxs-lookup"><span data-stu-id="41fbd-103">A scaling transformation multiplies one or more of the four color components by a number.</span></span> <span data-ttu-id="41fbd-104">V následující tabulce jsou uvedeny položek matice barev, které představují škálování.</span><span class="sxs-lookup"><span data-stu-id="41fbd-104">The color matrix entries that represent scaling are given in the following table.</span></span>  
  
|<span data-ttu-id="41fbd-105">Komponenta škálování</span><span class="sxs-lookup"><span data-stu-id="41fbd-105">Component to be scaled</span></span>|<span data-ttu-id="41fbd-106">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="41fbd-106">Matrix entry</span></span>|  
|----------------------------|------------------|  
|<span data-ttu-id="41fbd-107">Červená</span><span class="sxs-lookup"><span data-stu-id="41fbd-107">Red</span></span>|<span data-ttu-id="41fbd-108">[0][0]</span><span class="sxs-lookup"><span data-stu-id="41fbd-108">[0][0]</span></span>|  
|<span data-ttu-id="41fbd-109">Zelená</span><span class="sxs-lookup"><span data-stu-id="41fbd-109">Green</span></span>|<span data-ttu-id="41fbd-110">[1][1]</span><span class="sxs-lookup"><span data-stu-id="41fbd-110">[1][1]</span></span>|  
|<span data-ttu-id="41fbd-111">Modrá</span><span class="sxs-lookup"><span data-stu-id="41fbd-111">Blue</span></span>|<span data-ttu-id="41fbd-112">[2][2]</span><span class="sxs-lookup"><span data-stu-id="41fbd-112">[2][2]</span></span>|  
|<span data-ttu-id="41fbd-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="41fbd-113">Alpha</span></span>|<span data-ttu-id="41fbd-114">[3][3]</span><span class="sxs-lookup"><span data-stu-id="41fbd-114">[3][3]</span></span>|  
  
## <a name="scaling-one-color"></a><span data-ttu-id="41fbd-115">Škálování jedné barvy</span><span class="sxs-lookup"><span data-stu-id="41fbd-115">Scaling One Color</span></span>  
 <span data-ttu-id="41fbd-116">Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru ColorBars2.bmp.</span><span class="sxs-lookup"><span data-stu-id="41fbd-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="41fbd-117">Kód pak škáluje faktorem 2 modré každý pixel na obrázku.</span><span class="sxs-lookup"><span data-stu-id="41fbd-117">Then the code scales the blue component of each pixel in the image by a factor of 2.</span></span> <span data-ttu-id="41fbd-118">Původní bitové kopie nakreslen spolu s transformovaný bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="41fbd-118">The original image is drawn alongside the transformed image.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 <span data-ttu-id="41fbd-119">Následující obrázek znázorňuje původní obrázek na levé straně a obrazu se změněnou velikostí na pravé straně:</span><span class="sxs-lookup"><span data-stu-id="41fbd-119">The following illustration shows the original image on the left and the scaled image on the right:</span></span>  
  
 ![Snímek obrazovky, který porovnává barvy původní a měřítkem.](./media/using-transformations-to-scale-colors/four-bar-scale-one-color.png)  
  
 <span data-ttu-id="41fbd-121">Následující tabulka uvádí vektory barvu pro čtyři pruhy před a po modré škálování.</span><span class="sxs-lookup"><span data-stu-id="41fbd-121">The following table lists the color vectors for the four bars before and after the blue scaling.</span></span> <span data-ttu-id="41fbd-122">Všimněte si, že hodnota modré ve čtvrtém pruhu barev absolvovanou z 0,8 0.6.</span><span class="sxs-lookup"><span data-stu-id="41fbd-122">Note that the blue component in the fourth color bar went from 0.8 to 0.6.</span></span> <span data-ttu-id="41fbd-123">Důvodem je, že [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zachová pouze desetinná část výsledku.</span><span class="sxs-lookup"><span data-stu-id="41fbd-123">That is because [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] retains only the fractional part of the result.</span></span> <span data-ttu-id="41fbd-124">Například (2)(0.8) = 1.6, a zlomkovou část 1.6 je 0.6.</span><span class="sxs-lookup"><span data-stu-id="41fbd-124">For example, (2)(0.8) = 1.6, and the fractional part of 1.6 is 0.6.</span></span> <span data-ttu-id="41fbd-125">Ponechá pouze zlomkové části zajistí, že výsledek je vždy v intervalu [0, 1].</span><span class="sxs-lookup"><span data-stu-id="41fbd-125">Retaining only the fractional part ensures that the result is always in the interval [0, 1].</span></span>  
  
|<span data-ttu-id="41fbd-126">Původní</span><span class="sxs-lookup"><span data-stu-id="41fbd-126">Original</span></span>|<span data-ttu-id="41fbd-127">Škálovat</span><span class="sxs-lookup"><span data-stu-id="41fbd-127">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="41fbd-128">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-128">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="41fbd-129">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-129">(0.4, 0.4, 0.8, 1)</span></span>|  
|<span data-ttu-id="41fbd-130">(0.4, 0.2, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-130">(0.4, 0.2, 0.2, 1)</span></span>|<span data-ttu-id="41fbd-131">(0.4, 0.2, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-131">(0.4, 0.2, 0.4, 1)</span></span>|  
|<span data-ttu-id="41fbd-132">(0.2, 0.4, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-132">(0.2, 0.4, 0.2, 1)</span></span>|<span data-ttu-id="41fbd-133">(0.2, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-133">(0.2, 0.4, 0.4, 1)</span></span>|  
|<span data-ttu-id="41fbd-134">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-134">(0.4, 0.4, 0.8, 1)</span></span>|<span data-ttu-id="41fbd-135">(0.4, 0.4, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-135">(0.4, 0.4, 0.6, 1)</span></span>|  
  
## <a name="scaling-multiple-colors"></a><span data-ttu-id="41fbd-136">Škálování několika barev</span><span class="sxs-lookup"><span data-stu-id="41fbd-136">Scaling Multiple Colors</span></span>  
 <span data-ttu-id="41fbd-137">Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru ColorBars2.bmp.</span><span class="sxs-lookup"><span data-stu-id="41fbd-137">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="41fbd-138">Potom kód škáluje komponenty červené, zelené a modré každý pixel na obrázku.</span><span class="sxs-lookup"><span data-stu-id="41fbd-138">Then the code scales the red, green, and blue components of each pixel in the image.</span></span> <span data-ttu-id="41fbd-139">Červené komponenty jsou kapacitu vertikálně snížit 25 procent, zelenou komponenty jsou kapacitu vertikálně snížit 35 procent a modré komponenty jsou kapacitu vertikálně snížit 50 procent.</span><span class="sxs-lookup"><span data-stu-id="41fbd-139">The red components are scaled down 25 percent, the green components are scaled down 35 percent, and the blue components are scaled down 50 percent.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 <span data-ttu-id="41fbd-140">Následující obrázek znázorňuje původní obrázek na levé straně a obrazu se změněnou velikostí na pravé straně:</span><span class="sxs-lookup"><span data-stu-id="41fbd-140">The following illustration shows the original image on the left and the scaled image on the right:</span></span>  
  
 ![Snímek obrazovky, který porovnává barvy původní a měřítkem.](./media/using-transformations-to-scale-colors/four-bar-scale-multiple-colors.png)  
  
 <span data-ttu-id="41fbd-142">Následující tabulka uvádí vektory barvu pro čtyři pruhy před a po červené, zelené a modré škálování.</span><span class="sxs-lookup"><span data-stu-id="41fbd-142">The following table lists the color vectors for the four bars before and after the red, green and blue scaling.</span></span>  
  
|<span data-ttu-id="41fbd-143">Původní</span><span class="sxs-lookup"><span data-stu-id="41fbd-143">Original</span></span>|<span data-ttu-id="41fbd-144">Škálovat</span><span class="sxs-lookup"><span data-stu-id="41fbd-144">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="41fbd-145">(0.6, 0.6, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-145">(0.6, 0.6, 0.6, 1)</span></span>|<span data-ttu-id="41fbd-146">(0.45, 0.39, 0.3, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-146">(0.45, 0.39, 0.3, 1)</span></span>|  
|<span data-ttu-id="41fbd-147">(0, 1, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-147">(0, 1, 1, 1)</span></span>|<span data-ttu-id="41fbd-148">(0, 0.65, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-148">(0, 0.65, 0.5, 1)</span></span>|  
|<span data-ttu-id="41fbd-149">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-149">(1, 1, 0, 1)</span></span>|<span data-ttu-id="41fbd-150">(0.75, 0.65, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-150">(0.75, 0.65, 0, 1)</span></span>|  
|<span data-ttu-id="41fbd-151">(1, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-151">(1, 0, 1, 1)</span></span>|<span data-ttu-id="41fbd-152">(0.75, 0, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="41fbd-152">(0.75, 0, 0.5, 1)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41fbd-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41fbd-153">See also</span></span>
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="41fbd-154">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41fbd-154">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="41fbd-155">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="41fbd-155">Recoloring Images</span></span>](recoloring-images.md)
