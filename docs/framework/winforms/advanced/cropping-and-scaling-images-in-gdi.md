---
title: Oříznutí a změna měřítka obrázků v GDI+
ms.date: 03/30/2017
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
ms.openlocfilehash: 84e2e74e71c13593cb013849c07a6e904a4d2c14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521551"
---
# <a name="cropping-and-scaling-images-in-gdi"></a><span data-ttu-id="9201b-102">Oříznutí a změna měřítka obrázků v GDI+</span><span class="sxs-lookup"><span data-stu-id="9201b-102">Cropping and Scaling Images in GDI+</span></span>
<span data-ttu-id="9201b-103">Můžete použít <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> třída pro kreslení a umístění bitové kopie vektoru a rastrových obrázků.</span><span class="sxs-lookup"><span data-stu-id="9201b-103">You can use the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> class to draw and position vector images and raster images.</span></span> <span data-ttu-id="9201b-104"><xref:System.Drawing.Graphics.DrawImage%2A> je přetížené metody, takže je můžete zadat s argumenty několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="9201b-104"><xref:System.Drawing.Graphics.DrawImage%2A> is an overloaded method, so there are several ways you can supply it with arguments.</span></span>  
  
## <a name="drawimage-variations"></a><span data-ttu-id="9201b-105">DrawImage – variant</span><span class="sxs-lookup"><span data-stu-id="9201b-105">DrawImage Variations</span></span>  
 <span data-ttu-id="9201b-106">Jeden varianta <xref:System.Drawing.Graphics.DrawImage%2A> metoda obdrží <xref:System.Drawing.Bitmap> a <xref:System.Drawing.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="9201b-106">One variation of the <xref:System.Drawing.Graphics.DrawImage%2A> method receives a <xref:System.Drawing.Bitmap> and a <xref:System.Drawing.Rectangle>.</span></span> <span data-ttu-id="9201b-107">Rámeček určuje cíl pro kreslení operaci; To znamená určuje obdélníku, ve kterém k vykreslení bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="9201b-107">The rectangle specifies the destination for the drawing operation; that is, it specifies the rectangle in which to draw the image.</span></span> <span data-ttu-id="9201b-108">Pokud velikost cílové rámeček se liší od velikost původní bitové kopie, bitovou kopii přizpůsobí se rámeček cílový.</span><span class="sxs-lookup"><span data-stu-id="9201b-108">If the size of the destination rectangle is different from the size of the original image, the image is scaled to fit the destination rectangle.</span></span> <span data-ttu-id="9201b-109">Následující příklad kódu ukazuje, jak k vykreslení stejnou bitovou kopii třikrát: jednou pro žádné škálování, jednou pro rozšíření a jednou pro komprese:</span><span class="sxs-lookup"><span data-stu-id="9201b-109">The following code example shows how to draw the same image three times: once with no scaling, once with an expansion, and once with a compression:</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 <span data-ttu-id="9201b-110">Následující obrázek znázorňuje tři obrázky.</span><span class="sxs-lookup"><span data-stu-id="9201b-110">The following illustration shows the three pictures.</span></span>  
  
 <span data-ttu-id="9201b-111">![Škálování](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span><span class="sxs-lookup"><span data-stu-id="9201b-111">![Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span></span>  
  
 <span data-ttu-id="9201b-112">Některé variace <xref:System.Drawing.Graphics.DrawImage%2A> metoda mít parametr zdroj obdélníku, jakož i cílové obdélníku parametr.</span><span class="sxs-lookup"><span data-stu-id="9201b-112">Some variations of the <xref:System.Drawing.Graphics.DrawImage%2A> method have a source-rectangle parameter as well as a destination-rectangle parameter.</span></span> <span data-ttu-id="9201b-113">Parametr zdroj obdélníku určuje část původní bitové kopie k vykreslení.</span><span class="sxs-lookup"><span data-stu-id="9201b-113">The source-rectangle parameter specifies the portion of the original image to draw.</span></span> <span data-ttu-id="9201b-114">Rámeček cílové určuje obdélníku, ve kterém k vykreslení část bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="9201b-114">The destination rectangle specifies the rectangle in which to draw that portion of the image.</span></span> <span data-ttu-id="9201b-115">Pokud velikost cílové rámeček se liší od velikost zdroje obdélníku, na obrázku přizpůsobí se rámeček cílový.</span><span class="sxs-lookup"><span data-stu-id="9201b-115">If the size of the destination rectangle is different from the size of the source rectangle, the picture is scaled to fit the destination rectangle.</span></span>  
  
 <span data-ttu-id="9201b-116">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> ze souboru Runner.jpg.</span><span class="sxs-lookup"><span data-stu-id="9201b-116">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Runner.jpg.</span></span> <span data-ttu-id="9201b-117">Celého obrázku vykreslením s žádné škálování na (0, 0).</span><span class="sxs-lookup"><span data-stu-id="9201b-117">The entire image is drawn with no scaling at (0, 0).</span></span> <span data-ttu-id="9201b-118">Pak malá část obrázku se nevykreslí dvakrát: jednou s komprese a jednou rozšíření.</span><span class="sxs-lookup"><span data-stu-id="9201b-118">Then a small portion of the image is drawn twice: once with a compression and once with an expansion.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 <span data-ttu-id="9201b-119">Následující obrázek znázorňuje bez měřítka bitové kopie a části komprimované a rozšířená bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="9201b-119">The following illustration shows the unscaled image, and the compressed and expanded image portions.</span></span>  
  
 <span data-ttu-id="9201b-120">![Oříznutí a změna měřítka](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span><span class="sxs-lookup"><span data-stu-id="9201b-120">![Cropping and Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9201b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="9201b-121">See Also</span></span>  
 [<span data-ttu-id="9201b-122">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="9201b-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="9201b-123">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="9201b-123">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
