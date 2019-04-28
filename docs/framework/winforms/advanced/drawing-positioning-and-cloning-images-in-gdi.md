---
title: Kreslení, umisťování a klonování obrázků v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- raster images [Windows Forms]
- images [Windows Forms], positioning
- drawing [Windows Forms], images
- drawing [Windows Forms], raster images
- images [Windows Forms], cloning
- images [Windows Forms], drawing
- GDI+, drawing images
- GDI+, cloning images
- GDI+, positioning images
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
ms.openlocfilehash: b5f98e7bdef9ff8ed0a4cd0e040cb92a31f30503
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756908"
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a><span data-ttu-id="03682-102">Kreslení, umisťování a klonování obrázků v GDI+</span><span class="sxs-lookup"><span data-stu-id="03682-102">Drawing, Positioning, and Cloning Images in GDI+</span></span>
<span data-ttu-id="03682-103">Můžete použít <xref:System.Drawing.Bitmap> třída načíst a zobrazit rastrové obrázky kde můžete použít <xref:System.Drawing.Imaging.Metafile> třídy načíst a zobrazit vektorové obrázky.</span><span class="sxs-lookup"><span data-stu-id="03682-103">You can use the <xref:System.Drawing.Bitmap> class to load and display raster images, and you can use the <xref:System.Drawing.Imaging.Metafile> class to load and display vector images.</span></span> <span data-ttu-id="03682-104"><xref:System.Drawing.Bitmap> a <xref:System.Drawing.Imaging.Metafile> třídy dědí <xref:System.Drawing.Image> třídy.</span><span class="sxs-lookup"><span data-stu-id="03682-104">The <xref:System.Drawing.Bitmap> and <xref:System.Drawing.Imaging.Metafile> classes inherit from the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="03682-105">K zobrazení bitovou kopii vektoru, je třeba instance <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="03682-105">To display a vector image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="03682-106">K zobrazení rastrového obrázku, je třeba instance <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="03682-106">To display a raster image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="03682-107">Instance <xref:System.Drawing.Graphics> třída poskytuje <xref:System.Drawing.Graphics.DrawImage%2A> metodu, která přijímá <xref:System.Drawing.Imaging.Metafile> nebo <xref:System.Drawing.Bitmap> jako argument.</span><span class="sxs-lookup"><span data-stu-id="03682-107">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawImage%2A> method, which receives the <xref:System.Drawing.Imaging.Metafile> or <xref:System.Drawing.Bitmap> as an argument.</span></span>  
  
## <a name="file-types-and-cloning"></a><span data-ttu-id="03682-108">Typy souborů a klonování</span><span class="sxs-lookup"><span data-stu-id="03682-108">File Types and Cloning</span></span>  
 <span data-ttu-id="03682-109">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> ze souboru Climber.jpg a zobrazí rastrový obrázek.</span><span class="sxs-lookup"><span data-stu-id="03682-109">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Climber.jpg and displays the bitmap.</span></span> <span data-ttu-id="03682-110">Cílový bod pro levý horní roh obrázku, (10, 10), je zadané v druhý a třetí parametr.</span><span class="sxs-lookup"><span data-stu-id="03682-110">The destination point for the upper-left corner of the image, (10, 10), is specified in the second and third parameters.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 <span data-ttu-id="03682-111">Následující obrázek znázorňuje obrázek.</span><span class="sxs-lookup"><span data-stu-id="03682-111">The following illustration shows the image.</span></span>  
  
 <span data-ttu-id="03682-112">![Image Sample](./media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span><span class="sxs-lookup"><span data-stu-id="03682-112">![Image Sample](./media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span></span>  
  
 <span data-ttu-id="03682-113">Můžete vytvořit <xref:System.Drawing.Bitmap> objekty z různých grafiky formáty souborů: BMP, GIF, JPEG, EXIF, PNG, TIFF a ikonu.</span><span class="sxs-lookup"><span data-stu-id="03682-113">You can construct <xref:System.Drawing.Bitmap> objects from a variety of graphics file formats: BMP, GIF, JPEG, EXIF, PNG, TIFF, and ICON.</span></span>  
  
 <span data-ttu-id="03682-114">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> objekty z různých typů souborů a poté zobrazí rastrové obrázky.</span><span class="sxs-lookup"><span data-stu-id="03682-114">The following code example shows how to construct <xref:System.Drawing.Bitmap> objects from a variety of file types and then displays the bitmaps.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <span data-ttu-id="03682-115"><xref:System.Drawing.Bitmap> Poskytuje třídy <xref:System.Drawing.Bitmap.Clone%2A> metodu, která vám umožní vytvořit kopii existující <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="03682-115">The <xref:System.Drawing.Bitmap> class provides a <xref:System.Drawing.Bitmap.Clone%2A> method that you can use to make a copy of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="03682-116"><xref:System.Drawing.Bitmap.Clone%2A> Metoda má parametr zdrojového obdélníku, který můžete použít k určení část původní rastrový obrázek, který chcete zkopírovat.</span><span class="sxs-lookup"><span data-stu-id="03682-116">The <xref:System.Drawing.Bitmap.Clone%2A> method has a source rectangle parameter that you can use to specify the portion of the original bitmap that you want to copy.</span></span> <span data-ttu-id="03682-117">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> klonováním existujícího v horní polovině <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="03682-117">The following code example shows how to create a <xref:System.Drawing.Bitmap> by cloning the top half of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="03682-118">Poté jsou vykreslovány vedle obě bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="03682-118">Then both images are drawn.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 <span data-ttu-id="03682-119">Následující obrázek znázorňuje dvě bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="03682-119">The following illustration shows the two images.</span></span>  
  
 <span data-ttu-id="03682-120">![Cropping](./media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span><span class="sxs-lookup"><span data-stu-id="03682-120">![Cropping](./media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03682-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03682-121">See also</span></span>

- [<span data-ttu-id="03682-122">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="03682-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="03682-123">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="03682-123">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="03682-124">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="03682-124">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
