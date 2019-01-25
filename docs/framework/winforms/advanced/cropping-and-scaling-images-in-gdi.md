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
ms.openlocfilehash: 6c3ad0892ea0892b7c4c0e21e14bdb75fe22b447
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554215"
---
# <a name="cropping-and-scaling-images-in-gdi"></a><span data-ttu-id="0688e-102">Oříznutí a změna měřítka obrázků v GDI+</span><span class="sxs-lookup"><span data-stu-id="0688e-102">Cropping and Scaling Images in GDI+</span></span>
<span data-ttu-id="0688e-103">Můžete použít <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> třídu pro vykreslení a umístění vektorové obrázky a rastrové obrázky.</span><span class="sxs-lookup"><span data-stu-id="0688e-103">You can use the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> class to draw and position vector images and raster images.</span></span> <span data-ttu-id="0688e-104"><xref:System.Drawing.Graphics.DrawImage%2A> je přetěžované metody, takže je můžete zadat s argumenty několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="0688e-104"><xref:System.Drawing.Graphics.DrawImage%2A> is an overloaded method, so there are several ways you can supply it with arguments.</span></span>  
  
## <a name="drawimage-variations"></a><span data-ttu-id="0688e-105">DrawImage odchylky</span><span class="sxs-lookup"><span data-stu-id="0688e-105">DrawImage Variations</span></span>  
 <span data-ttu-id="0688e-106">Jeden varianta <xref:System.Drawing.Graphics.DrawImage%2A> metoda přijímá <xref:System.Drawing.Bitmap> a <xref:System.Drawing.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="0688e-106">One variation of the <xref:System.Drawing.Graphics.DrawImage%2A> method receives a <xref:System.Drawing.Bitmap> and a <xref:System.Drawing.Rectangle>.</span></span> <span data-ttu-id="0688e-107">Obdélník Určuje cíl pro kreslení operaci. To znamená určuje obdélník, ve kterém chcete-li nakreslit obrázek.</span><span class="sxs-lookup"><span data-stu-id="0688e-107">The rectangle specifies the destination for the drawing operation; that is, it specifies the rectangle in which to draw the image.</span></span> <span data-ttu-id="0688e-108">Pokud se velikost cílového obdélníku liší od velikosti původní bitové kopie, image se škálovat podle cílového obdélníku.</span><span class="sxs-lookup"><span data-stu-id="0688e-108">If the size of the destination rectangle is different from the size of the original image, the image is scaled to fit the destination rectangle.</span></span> <span data-ttu-id="0688e-109">Následující příklad kódu ukazuje, jak nakreslit stejnou bitovou kopii třikrát: jednou pro žádné škálování, jednou pro rozšíření a jednou pro kompresi:</span><span class="sxs-lookup"><span data-stu-id="0688e-109">The following code example shows how to draw the same image three times: once with no scaling, once with an expansion, and once with a compression:</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 <span data-ttu-id="0688e-110">Následující obrázek znázorňuje tři obrázky.</span><span class="sxs-lookup"><span data-stu-id="0688e-110">The following illustration shows the three pictures.</span></span>  
  
 <span data-ttu-id="0688e-111">![Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span><span class="sxs-lookup"><span data-stu-id="0688e-111">![Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span></span>  
  
 <span data-ttu-id="0688e-112">Některé varianty <xref:System.Drawing.Graphics.DrawImage%2A> metoda mít parametr zdrojového obdélníku, stejně jako parametr cílového obdélníku.</span><span class="sxs-lookup"><span data-stu-id="0688e-112">Some variations of the <xref:System.Drawing.Graphics.DrawImage%2A> method have a source-rectangle parameter as well as a destination-rectangle parameter.</span></span> <span data-ttu-id="0688e-113">Parametr zdrojového obdélníku určuje část původní bitové kopie k vykreslení.</span><span class="sxs-lookup"><span data-stu-id="0688e-113">The source-rectangle parameter specifies the portion of the original image to draw.</span></span> <span data-ttu-id="0688e-114">Cílového obdélníku určuje obdélník, ve kterém chcete-li nakreslit část obrázku.</span><span class="sxs-lookup"><span data-stu-id="0688e-114">The destination rectangle specifies the rectangle in which to draw that portion of the image.</span></span> <span data-ttu-id="0688e-115">Pokud se velikost cílového obdélníku liší od velikosti zdrojového obdélníku, obrázek se škálovat podle cílového obdélníku.</span><span class="sxs-lookup"><span data-stu-id="0688e-115">If the size of the destination rectangle is different from the size of the source rectangle, the picture is scaled to fit the destination rectangle.</span></span>  
  
 <span data-ttu-id="0688e-116">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> ze souboru Runner.jpg.</span><span class="sxs-lookup"><span data-stu-id="0688e-116">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Runner.jpg.</span></span> <span data-ttu-id="0688e-117">Je nakreslit bez škálování na celého obrázku (0, 0).</span><span class="sxs-lookup"><span data-stu-id="0688e-117">The entire image is drawn with no scaling at (0, 0).</span></span> <span data-ttu-id="0688e-118">Vykreslován tak malou část obrázku dvakrát: jednou pro kompresi a posléze s rozšíření.</span><span class="sxs-lookup"><span data-stu-id="0688e-118">Then a small portion of the image is drawn twice: once with a compression and once with an expansion.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 <span data-ttu-id="0688e-119">Následující obrázek znázorňuje bez měřítka image a image komprimované a rozšířené části.</span><span class="sxs-lookup"><span data-stu-id="0688e-119">The following illustration shows the unscaled image, and the compressed and expanded image portions.</span></span>  
  
 <span data-ttu-id="0688e-120">![Oříznutí a změna měřítka](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span><span class="sxs-lookup"><span data-stu-id="0688e-120">![Cropping and Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0688e-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0688e-121">See also</span></span>
- [<span data-ttu-id="0688e-122">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="0688e-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="0688e-123">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="0688e-123">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
