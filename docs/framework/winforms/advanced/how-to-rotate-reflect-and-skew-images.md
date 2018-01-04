---
title: "Postupy: Otáčení, převrácení a zkosení obrázků"
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
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 163af74d27adcb7ec720a54bfd969bd704f7b1e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-reflect-and-skew-images"></a><span data-ttu-id="58ff0-102">Postupy: Otáčení, převrácení a zkosení obrázků</span><span class="sxs-lookup"><span data-stu-id="58ff0-102">How to: Rotate, Reflect, and Skew Images</span></span>
<span data-ttu-id="58ff0-103">Otočit, odrážel a zkreslit bitovou kopii zadáním cílového body pro rozích levém horním pravém horním a dolním původní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="58ff0-103">You can rotate, reflect, and skew an image by specifying destination points for the upper-left, upper-right, and lower-left corners of the original image.</span></span> <span data-ttu-id="58ff0-104">Tři cílové body určit afinní transformace, která se mapuje na rovnoběžník původní obdélníková bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="58ff0-104">The three destination points determine an affine transformation that maps the original rectangular image to a parallelogram.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58ff0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="58ff0-105">Example</span></span>  
 <span data-ttu-id="58ff0-106">Předpokládejme například, původní bitové kopie je obdélník se v levém horním rohu (0, 0), v pravém horním rohu (100, 0) a v levém dolním rohu (0, 50).</span><span class="sxs-lookup"><span data-stu-id="58ff0-106">For example, suppose the original image is a rectangle with upper-left corner at (0, 0), upper-right corner at (100, 0), and lower-left corner at (0, 50).</span></span> <span data-ttu-id="58ff0-107">Nyní předpokládejme, že ty namapujete tři odkazuje na cílový body následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="58ff0-107">Now suppose you map those three points to destination points as follows.</span></span>  
  
|<span data-ttu-id="58ff0-108">Původní bodu</span><span class="sxs-lookup"><span data-stu-id="58ff0-108">Original point</span></span>|<span data-ttu-id="58ff0-109">Cílového bodu</span><span class="sxs-lookup"><span data-stu-id="58ff0-109">Destination point</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="58ff0-110">Levý horní (0, 0)</span><span class="sxs-lookup"><span data-stu-id="58ff0-110">Upper-left (0, 0)</span></span>|<span data-ttu-id="58ff0-111">(200, 20)</span><span class="sxs-lookup"><span data-stu-id="58ff0-111">(200, 20)</span></span>|  
|<span data-ttu-id="58ff0-112">Pravém (100, 0)</span><span class="sxs-lookup"><span data-stu-id="58ff0-112">Upper-right (100, 0)</span></span>|<span data-ttu-id="58ff0-113">(110, 100)</span><span class="sxs-lookup"><span data-stu-id="58ff0-113">(110, 100)</span></span>|  
|<span data-ttu-id="58ff0-114">Dolním (0, 50)</span><span class="sxs-lookup"><span data-stu-id="58ff0-114">Lower-left (0, 50)</span></span>|<span data-ttu-id="58ff0-115">(250, 30)</span><span class="sxs-lookup"><span data-stu-id="58ff0-115">(250, 30)</span></span>|  
  
 <span data-ttu-id="58ff0-116">Následující obrázek znázorňuje původní bitové kopie a bitovou kopii namapované na Kosoúhelník.</span><span class="sxs-lookup"><span data-stu-id="58ff0-116">The following illustration shows the original image and the image mapped to the parallelogram.</span></span> <span data-ttu-id="58ff0-117">Původní bitové kopie byly nesouměrně rozdělí, projeví, otáčet a přeložit.</span><span class="sxs-lookup"><span data-stu-id="58ff0-117">The original image has been skewed, reflected, rotated, and translated.</span></span> <span data-ttu-id="58ff0-118">Osy x podél horního okraje původní bitové kopie je namapovaná na řádek, který spouští prostřednictvím (200, 20) a (110, 100).</span><span class="sxs-lookup"><span data-stu-id="58ff0-118">The x-axis along the top edge of the original image is mapped to the line that runs through (200, 20) and (110, 100).</span></span> <span data-ttu-id="58ff0-119">Osy y podél levého okraje původní bitové kopie je namapovaná na řádek, který spouští prostřednictvím (200, 20) a (250, 30).</span><span class="sxs-lookup"><span data-stu-id="58ff0-119">The y-axis along the left edge of the original image is mapped to the line that runs through (200, 20) and (250, 30).</span></span>  
  
 <span data-ttu-id="58ff0-120">![Rozděluje](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span><span class="sxs-lookup"><span data-stu-id="58ff0-120">![Stripes](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span></span>  
  
 <span data-ttu-id="58ff0-121">Následující obrázek znázorňuje podobné transformace do bitové photographic.</span><span class="sxs-lookup"><span data-stu-id="58ff0-121">The following illustration shows a similar transformation applied to a photographic image.</span></span>  
  
 <span data-ttu-id="58ff0-122">![Transformovat horolezec](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span><span class="sxs-lookup"><span data-stu-id="58ff0-122">![Transformed Climber](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span></span>  
  
 <span data-ttu-id="58ff0-123">Následující obrázek znázorňuje podobně jako u metasoubory transformace.</span><span class="sxs-lookup"><span data-stu-id="58ff0-123">The following illustration shows a similar transformation applied to a metafile.</span></span>  
  
 <span data-ttu-id="58ff0-124">![Transformovat Metafile](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span><span class="sxs-lookup"><span data-stu-id="58ff0-124">![Transformed Metafile](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span></span>  
  
 <span data-ttu-id="58ff0-125">Následující příklad vytvoří bitové kopie na první obrázku je vidět.</span><span class="sxs-lookup"><span data-stu-id="58ff0-125">The following example produces the images shown in the first illustration.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="58ff0-126">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="58ff0-126">Compiling the Code</span></span>  
 <span data-ttu-id="58ff0-127">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="58ff0-127">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="58ff0-128">Nezapomeňte nahradit `Stripes.bmp` s cestou na obrázek, který je platný v systému.</span><span class="sxs-lookup"><span data-stu-id="58ff0-128">Make sure to replace `Stripes.bmp` with the path to an image that is valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ff0-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="58ff0-129">See Also</span></span>  
 [<span data-ttu-id="58ff0-130">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="58ff0-130">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
