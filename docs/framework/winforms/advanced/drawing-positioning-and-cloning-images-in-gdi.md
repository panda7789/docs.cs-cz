---
title: "Kreslení, umisťování a klonování obrázků v GDI+"
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3ba716a36280d2ac08dae907abbdbe05e563dfc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a><span data-ttu-id="6bafb-102">Kreslení, umisťování a klonování obrázků v GDI+</span><span class="sxs-lookup"><span data-stu-id="6bafb-102">Drawing, Positioning, and Cloning Images in GDI+</span></span>
<span data-ttu-id="6bafb-103">Můžete použít <xref:System.Drawing.Bitmap> třída načtení a zobrazuje rastrových obrázků a vy můžete použít <xref:System.Drawing.Imaging.Metafile> třída načtení a zobrazuje vektoru bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="6bafb-103">You can use the <xref:System.Drawing.Bitmap> class to load and display raster images, and you can use the <xref:System.Drawing.Imaging.Metafile> class to load and display vector images.</span></span> <span data-ttu-id="6bafb-104"><xref:System.Drawing.Bitmap> a <xref:System.Drawing.Imaging.Metafile> třídy dědí <xref:System.Drawing.Image> třídy.</span><span class="sxs-lookup"><span data-stu-id="6bafb-104">The <xref:System.Drawing.Bitmap> and <xref:System.Drawing.Imaging.Metafile> classes inherit from the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="6bafb-105">Bitovou kopii vektoru zobrazíte potřebujete instanci <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="6bafb-105">To display a vector image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="6bafb-106">Pokud chcete zobrazit rastrového obrázku, je třeba instanci <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="6bafb-106">To display a raster image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="6bafb-107">Instance <xref:System.Drawing.Graphics> třída poskytuje <xref:System.Drawing.Graphics.DrawImage%2A> metoda, která přijímá <xref:System.Drawing.Imaging.Metafile> nebo <xref:System.Drawing.Bitmap> jako argument.</span><span class="sxs-lookup"><span data-stu-id="6bafb-107">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawImage%2A> method, which receives the <xref:System.Drawing.Imaging.Metafile> or <xref:System.Drawing.Bitmap> as an argument.</span></span>  
  
## <a name="file-types-and-cloning"></a><span data-ttu-id="6bafb-108">Typy souborů a klonování</span><span class="sxs-lookup"><span data-stu-id="6bafb-108">File Types and Cloning</span></span>  
 <span data-ttu-id="6bafb-109">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> ze souboru Climber.jpg a zobrazí bitové mapy.</span><span class="sxs-lookup"><span data-stu-id="6bafb-109">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Climber.jpg and displays the bitmap.</span></span> <span data-ttu-id="6bafb-110">Cílového bodu pro levý horní roh bitové kopie, (10, 10), je zadána v parametrech druhý a třetí.</span><span class="sxs-lookup"><span data-stu-id="6bafb-110">The destination point for the upper-left corner of the image, (10, 10), is specified in the second and third parameters.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 <span data-ttu-id="6bafb-111">Následující obrázek znázorňuje obrázek.</span><span class="sxs-lookup"><span data-stu-id="6bafb-111">The following illustration shows the image.</span></span>  
  
 <span data-ttu-id="6bafb-112">![Obrázek ukázkové](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span><span class="sxs-lookup"><span data-stu-id="6bafb-112">![Image Sample](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span></span>  
  
 <span data-ttu-id="6bafb-113">Můžete vytvořit <xref:System.Drawing.Bitmap> objekty z různých grafiky formáty souborů: BMP, GIF, JPEG, EXIF, PNG, TIFF a ikona.</span><span class="sxs-lookup"><span data-stu-id="6bafb-113">You can construct <xref:System.Drawing.Bitmap> objects from a variety of graphics file formats: BMP, GIF, JPEG, EXIF, PNG, TIFF, and ICON.</span></span>  
  
 <span data-ttu-id="6bafb-114">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> objekty z různých typů souborů a potom zobrazí rastrových obrázků.</span><span class="sxs-lookup"><span data-stu-id="6bafb-114">The following code example shows how to construct <xref:System.Drawing.Bitmap> objects from a variety of file types and then displays the bitmaps.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <span data-ttu-id="6bafb-115"><xref:System.Drawing.Bitmap> Třída poskytuje <xref:System.Drawing.Bitmap.Clone%2A> metodu, kterou můžete použít k vytvoření kopie existujícího <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="6bafb-115">The <xref:System.Drawing.Bitmap> class provides a <xref:System.Drawing.Bitmap.Clone%2A> method that you can use to make a copy of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="6bafb-116"><xref:System.Drawing.Bitmap.Clone%2A> Metoda má parametr obdélníku zdroj, který můžete použít k určení část původní rastrový obrázek, který chcete kopírovat.</span><span class="sxs-lookup"><span data-stu-id="6bafb-116">The <xref:System.Drawing.Bitmap.Clone%2A> method has a source rectangle parameter that you can use to specify the portion of the original bitmap that you want to copy.</span></span> <span data-ttu-id="6bafb-117">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> klonováním horní polovině existující <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="6bafb-117">The following code example shows how to create a <xref:System.Drawing.Bitmap> by cloning the top half of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="6bafb-118">Pak jsou vykreslovány obě bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="6bafb-118">Then both images are drawn.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 <span data-ttu-id="6bafb-119">Následující obrázek znázorňuje dvě bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="6bafb-119">The following illustration shows the two images.</span></span>  
  
 <span data-ttu-id="6bafb-120">![Oříznutí](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span><span class="sxs-lookup"><span data-stu-id="6bafb-120">![Cropping](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bafb-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bafb-121">See Also</span></span>  
 [<span data-ttu-id="6bafb-122">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="6bafb-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="6bafb-123">Postupy: vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="6bafb-123">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="6bafb-124">Práce s obrázky, rastrové obrázky, ikony a metasoubory</span><span class="sxs-lookup"><span data-stu-id="6bafb-124">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
