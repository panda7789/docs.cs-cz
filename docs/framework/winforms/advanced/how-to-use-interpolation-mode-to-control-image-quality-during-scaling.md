---
title: 'Postupy: Použití režimu interpolace pro řízení kvality obrázku během změny měřítka'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: 75f5077c2d969f026a28834144c219f289843dd6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080979"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a><span data-ttu-id="6a8a7-102">Postupy: Použití režimu interpolace pro řízení kvality obrázku během změny měřítka</span><span class="sxs-lookup"><span data-stu-id="6a8a7-102">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>
<span data-ttu-id="6a8a7-103">Režim interpolace <xref:System.Drawing.Graphics> objekt ovlivňuje způsob, jakým [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] imagí škálování (úseky a zmenší).</span><span class="sxs-lookup"><span data-stu-id="6a8a7-103">The interpolation mode of a <xref:System.Drawing.Graphics> object influences the way [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] scales (stretches and shrinks) images.</span></span> <span data-ttu-id="6a8a7-104"><xref:System.Drawing.Drawing2D.InterpolationMode> Výčet definuje několik režimů interpolace, z nichž některé jsou uvedeny v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="6a8a7-104">The <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration defines several interpolation modes, some of which are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 <span data-ttu-id="6a8a7-105">Roztáhnout obrázek, každý pixel v původní bitové kopie musí být namapován na skupinu větší obrázku v pixelech.</span><span class="sxs-lookup"><span data-stu-id="6a8a7-105">To stretch an image, each pixel in the original image must be mapped to a group of pixels in the larger image.</span></span> <span data-ttu-id="6a8a7-106">Zmenšení bitovou kopii, skupiny pixelů v původní bitové kopie musí být namapován na jeden pixelů v menším obrázkem.</span><span class="sxs-lookup"><span data-stu-id="6a8a7-106">To shrink an image, groups of pixels in the original image must be mapped to single pixels in the smaller image.</span></span> <span data-ttu-id="6a8a7-107">Účinnost algoritmy, které provádějí tato mapování určuje kvalitu obrazu se změněnou velikostí.</span><span class="sxs-lookup"><span data-stu-id="6a8a7-107">The effectiveness of the algorithms that perform these mappings determines the quality of a scaled image.</span></span> <span data-ttu-id="6a8a7-108">Algoritmy, které vytvářejí škálován imagí kvalitnější většinou vyžaduje více času na zpracování.</span><span class="sxs-lookup"><span data-stu-id="6a8a7-108">Algorithms that produce higher-quality scaled images tend to require more processing time.</span></span> <span data-ttu-id="6a8a7-109">V předchozím seznamu <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> je režim nejnižší kvality a <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> je režim nejvyšší kvality.</span><span class="sxs-lookup"><span data-stu-id="6a8a7-109">In the preceding list, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> is the lowest-quality mode and <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> is the highest-quality mode.</span></span>  
  
 <span data-ttu-id="6a8a7-110">Nastavení režimu interpolace, přiřadit jeden z členů <xref:System.Drawing.Drawing2D.InterpolationMode> výčet <xref:System.Drawing.Graphics.InterpolationMode%2A> vlastnost <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="6a8a7-110">To set the interpolation mode, assign one of the members of the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to the <xref:System.Drawing.Graphics.InterpolationMode%2A> property of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a8a7-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a8a7-111">Example</span></span>  
 <span data-ttu-id="6a8a7-112">V následujícím příkladu nakreslí obrázek a potom zmenšuje bitová kopie se tři interpolace různé režimy.</span><span class="sxs-lookup"><span data-stu-id="6a8a7-112">The following example draws an image and then shrinks the image with three different interpolation modes.</span></span>  
  
 <span data-ttu-id="6a8a7-113">Následující obrázek znázorňuje původní bitové kopie a tři menší Image.</span><span class="sxs-lookup"><span data-stu-id="6a8a7-113">The following illustration shows the original image and the three smaller images.</span></span>  
  
 ![Snímek obrazovky zobrazující image s rozdílnými interpolace nastavení.](./media/how-to-use-interpolation-mode-to-control-image-quality-during-scaling/varied-interpolation-settings.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6a8a7-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6a8a7-115">Compiling the Code</span></span>  
 <span data-ttu-id="6a8a7-116">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6a8a7-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a8a7-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a8a7-117">See also</span></span>

- [<span data-ttu-id="6a8a7-118">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="6a8a7-118">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="6a8a7-119">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="6a8a7-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
