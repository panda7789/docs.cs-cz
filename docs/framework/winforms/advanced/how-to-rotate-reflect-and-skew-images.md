---
title: 'Postupy: Otáčení, převrácení a zkosení obrázků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
ms.openlocfilehash: 2150e7797095b88227b499ec5481a3ce521270e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667908"
---
# <a name="how-to-rotate-reflect-and-skew-images"></a><span data-ttu-id="07484-102">Postupy: Otáčení, převrácení a zkosení obrázků</span><span class="sxs-lookup"><span data-stu-id="07484-102">How to: Rotate, Reflect, and Skew Images</span></span>
<span data-ttu-id="07484-103">Můžete otáčení, převrácení a zkosení obrázku tak, že určíte cílové body pro levého horního, pravého horního a levého dolního rohu původní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="07484-103">You can rotate, reflect, and skew an image by specifying destination points for the upper-left, upper-right, and lower-left corners of the original image.</span></span> <span data-ttu-id="07484-104">Tři cílovými body určit afinní transformace, která mapuje původní obrázek obdélníkové se z něj rovnoběžník.</span><span class="sxs-lookup"><span data-stu-id="07484-104">The three destination points determine an affine transformation that maps the original rectangular image to a parallelogram.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07484-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="07484-105">Example</span></span>  
 <span data-ttu-id="07484-106">Předpokládejme například, že původní bitové kopie je obdélník se v levém horním rohu (0, 0), v pravém horním rohu (100, 0) a v levém dolním rohu (0, 50).</span><span class="sxs-lookup"><span data-stu-id="07484-106">For example, suppose the original image is a rectangle with upper-left corner at (0, 0), upper-right corner at (100, 0), and lower-left corner at (0, 50).</span></span> <span data-ttu-id="07484-107">Nyní předpokládejme, že můžete namapovat tyto tři odkazuje na cílové body následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="07484-107">Now suppose you map those three points to destination points as follows.</span></span>  
  
|<span data-ttu-id="07484-108">Původní bod</span><span class="sxs-lookup"><span data-stu-id="07484-108">Original point</span></span>|<span data-ttu-id="07484-109">Cílový bod</span><span class="sxs-lookup"><span data-stu-id="07484-109">Destination point</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="07484-110">Levý horní (0, 0)</span><span class="sxs-lookup"><span data-stu-id="07484-110">Upper-left (0, 0)</span></span>|<span data-ttu-id="07484-111">(200, 20)</span><span class="sxs-lookup"><span data-stu-id="07484-111">(200, 20)</span></span>|  
|<span data-ttu-id="07484-112">Upper-right (100, 0)</span><span class="sxs-lookup"><span data-stu-id="07484-112">Upper-right (100, 0)</span></span>|<span data-ttu-id="07484-113">(110, 100)</span><span class="sxs-lookup"><span data-stu-id="07484-113">(110, 100)</span></span>|  
|<span data-ttu-id="07484-114">Levém (0, 50)</span><span class="sxs-lookup"><span data-stu-id="07484-114">Lower-left (0, 50)</span></span>|<span data-ttu-id="07484-115">(250, 30)</span><span class="sxs-lookup"><span data-stu-id="07484-115">(250, 30)</span></span>|  
  
 <span data-ttu-id="07484-116">Následující obrázek znázorňuje původní image a image, namapované rovnoběžník.</span><span class="sxs-lookup"><span data-stu-id="07484-116">The following illustration shows the original image and the image mapped to the parallelogram.</span></span> <span data-ttu-id="07484-117">Původní bitové kopie má byla zkosený, projeví, otáčet a přeložit.</span><span class="sxs-lookup"><span data-stu-id="07484-117">The original image has been skewed, reflected, rotated, and translated.</span></span> <span data-ttu-id="07484-118">Osa x podél horního okraje původní bitové kopie je namapována na řádek, který prochází (200, 20) a (110, 100).</span><span class="sxs-lookup"><span data-stu-id="07484-118">The x-axis along the top edge of the original image is mapped to the line that runs through (200, 20) and (110, 100).</span></span> <span data-ttu-id="07484-119">Osa y podél levého okraje původní bitové kopie je namapována na řádek, který prochází (200, 20) a (250, 30).</span><span class="sxs-lookup"><span data-stu-id="07484-119">The y-axis along the left edge of the original image is mapped to the line that runs through (200, 20) and (250, 30).</span></span>  
  
 <span data-ttu-id="07484-120">![Rozděluje](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span><span class="sxs-lookup"><span data-stu-id="07484-120">![Stripes](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span></span>  
  
 <span data-ttu-id="07484-121">Následující obrázek znázorňuje podobné transformaci u photographic obrázku.</span><span class="sxs-lookup"><span data-stu-id="07484-121">The following illustration shows a similar transformation applied to a photographic image.</span></span>  
  
 <span data-ttu-id="07484-122">![Transformuje horolezec](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span><span class="sxs-lookup"><span data-stu-id="07484-122">![Transformed Climber](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span></span>  
  
 <span data-ttu-id="07484-123">Následující obrázek znázorňuje podobné transformací do metasouboru.</span><span class="sxs-lookup"><span data-stu-id="07484-123">The following illustration shows a similar transformation applied to a metafile.</span></span>  
  
 <span data-ttu-id="07484-124">![Transformuje metasoubor](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span><span class="sxs-lookup"><span data-stu-id="07484-124">![Transformed Metafile](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span></span>  
  
 <span data-ttu-id="07484-125">Následující příklad vytvoří Image je znázorněno na prvním obrázku.</span><span class="sxs-lookup"><span data-stu-id="07484-125">The following example produces the images shown in the first illustration.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="07484-126">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="07484-126">Compiling the Code</span></span>  
 <span data-ttu-id="07484-127">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="07484-127">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="07484-128">Nezapomeňte nahradit `Stripes.bmp` cestou k obrázku, který je platný v systému.</span><span class="sxs-lookup"><span data-stu-id="07484-128">Make sure to replace `Stripes.bmp` with the path to an image that is valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07484-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07484-129">See also</span></span>
- [<span data-ttu-id="07484-130">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="07484-130">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
