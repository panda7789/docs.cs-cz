---
title: "Oříznutí a změna měřítka obrázků v GDI+"
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
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63e1e55e57d586cbbca87361b95c18f0f53b8c75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cropping-and-scaling-images-in-gdi"></a><span data-ttu-id="3a38a-102">Oříznutí a změna měřítka obrázků v GDI+</span><span class="sxs-lookup"><span data-stu-id="3a38a-102">Cropping and Scaling Images in GDI+</span></span>
<span data-ttu-id="3a38a-103">Můžete použít <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> třída pro kreslení a umístění bitové kopie vektoru a rastrových obrázků.</span><span class="sxs-lookup"><span data-stu-id="3a38a-103">You can use the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> class to draw and position vector images and raster images.</span></span> <span data-ttu-id="3a38a-104"><xref:System.Drawing.Graphics.DrawImage%2A>je přetížené metody, takže je můžete zadat s argumenty několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="3a38a-104"><xref:System.Drawing.Graphics.DrawImage%2A> is an overloaded method, so there are several ways you can supply it with arguments.</span></span>  
  
## <a name="drawimage-variations"></a><span data-ttu-id="3a38a-105">DrawImage – variant</span><span class="sxs-lookup"><span data-stu-id="3a38a-105">DrawImage Variations</span></span>  
 <span data-ttu-id="3a38a-106">Jeden varianta <xref:System.Drawing.Graphics.DrawImage%2A> metoda obdrží <xref:System.Drawing.Bitmap> a <xref:System.Drawing.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="3a38a-106">One variation of the <xref:System.Drawing.Graphics.DrawImage%2A> method receives a <xref:System.Drawing.Bitmap> and a <xref:System.Drawing.Rectangle>.</span></span> <span data-ttu-id="3a38a-107">Rámeček určuje cíl pro kreslení operaci; To znamená určuje obdélníku, ve kterém k vykreslení bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="3a38a-107">The rectangle specifies the destination for the drawing operation; that is, it specifies the rectangle in which to draw the image.</span></span> <span data-ttu-id="3a38a-108">Pokud velikost cílové rámeček se liší od velikost původní bitové kopie, bitovou kopii přizpůsobí se rámeček cílový.</span><span class="sxs-lookup"><span data-stu-id="3a38a-108">If the size of the destination rectangle is different from the size of the original image, the image is scaled to fit the destination rectangle.</span></span> <span data-ttu-id="3a38a-109">Následující příklad kódu ukazuje, jak k vykreslení stejnou bitovou kopii třikrát: jednou pro žádné škálování, jednou pro rozšíření a jednou pro komprese:</span><span class="sxs-lookup"><span data-stu-id="3a38a-109">The following code example shows how to draw the same image three times: once with no scaling, once with an expansion, and once with a compression:</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 <span data-ttu-id="3a38a-110">Následující obrázek znázorňuje tři obrázky.</span><span class="sxs-lookup"><span data-stu-id="3a38a-110">The following illustration shows the three pictures.</span></span>  
  
 <span data-ttu-id="3a38a-111">![Škálování](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span><span class="sxs-lookup"><span data-stu-id="3a38a-111">![Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span></span>  
  
 <span data-ttu-id="3a38a-112">Některé variace <xref:System.Drawing.Graphics.DrawImage%2A> metoda mít parametr zdroj obdélníku, jakož i cílové obdélníku parametr.</span><span class="sxs-lookup"><span data-stu-id="3a38a-112">Some variations of the <xref:System.Drawing.Graphics.DrawImage%2A> method have a source-rectangle parameter as well as a destination-rectangle parameter.</span></span> <span data-ttu-id="3a38a-113">Parametr zdroj obdélníku určuje část původní bitové kopie k vykreslení.</span><span class="sxs-lookup"><span data-stu-id="3a38a-113">The source-rectangle parameter specifies the portion of the original image to draw.</span></span> <span data-ttu-id="3a38a-114">Rámeček cílové určuje obdélníku, ve kterém k vykreslení část bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="3a38a-114">The destination rectangle specifies the rectangle in which to draw that portion of the image.</span></span> <span data-ttu-id="3a38a-115">Pokud velikost cílové rámeček se liší od velikost zdroje obdélníku, na obrázku přizpůsobí se rámeček cílový.</span><span class="sxs-lookup"><span data-stu-id="3a38a-115">If the size of the destination rectangle is different from the size of the source rectangle, the picture is scaled to fit the destination rectangle.</span></span>  
  
 <span data-ttu-id="3a38a-116">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> ze souboru Runner.jpg.</span><span class="sxs-lookup"><span data-stu-id="3a38a-116">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Runner.jpg.</span></span> <span data-ttu-id="3a38a-117">Celého obrázku vykreslením s žádné škálování na (0, 0).</span><span class="sxs-lookup"><span data-stu-id="3a38a-117">The entire image is drawn with no scaling at (0, 0).</span></span> <span data-ttu-id="3a38a-118">Pak malá část obrázku se nevykreslí dvakrát: jednou s komprese a jednou rozšíření.</span><span class="sxs-lookup"><span data-stu-id="3a38a-118">Then a small portion of the image is drawn twice: once with a compression and once with an expansion.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 <span data-ttu-id="3a38a-119">Následující obrázek znázorňuje bez měřítka bitové kopie a části komprimované a rozšířená bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="3a38a-119">The following illustration shows the unscaled image, and the compressed and expanded image portions.</span></span>  
  
 <span data-ttu-id="3a38a-120">![Oříznutí a změna měřítka](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span><span class="sxs-lookup"><span data-stu-id="3a38a-120">![Cropping and Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a38a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a38a-121">See Also</span></span>  
 [<span data-ttu-id="3a38a-122">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="3a38a-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="3a38a-123">Práce s obrázky, rastrové obrázky, ikony a metasoubory</span><span class="sxs-lookup"><span data-stu-id="3a38a-123">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
