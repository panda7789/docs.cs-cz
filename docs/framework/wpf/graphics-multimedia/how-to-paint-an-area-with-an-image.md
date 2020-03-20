---
title: 'Postupy: Vykreslení obrázku v oblasti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 92969778c04c6ac634a2964c402d6c3439b96b49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186056"
---
# <a name="how-to-paint-an-area-with-an-image"></a><span data-ttu-id="a9c94-102">Postupy: Vykreslení obrázku v oblasti</span><span class="sxs-lookup"><span data-stu-id="a9c94-102">How to: Paint an Area with an Image</span></span>
<span data-ttu-id="a9c94-103">Tento příklad ukazuje, <xref:System.Windows.Media.ImageBrush> jak použít třídu k malování oblasti s obrazem.</span><span class="sxs-lookup"><span data-stu-id="a9c94-103">This example shows how to use the <xref:System.Windows.Media.ImageBrush> class to paint an area with an image.</span></span> <span data-ttu-id="a9c94-104">Zobrazí <xref:System.Windows.Media.ImageBrush> jeden obrázek, který je <xref:System.Windows.Media.ImageBrush.ImageSource%2A> určen jeho vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a9c94-104">An <xref:System.Windows.Media.ImageBrush> displays a single image, which is specified by its <xref:System.Windows.Media.ImageBrush.ImageSource%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9c94-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9c94-105">Example</span></span>  
 <span data-ttu-id="a9c94-106">Následující příklad maluje <xref:System.Windows.Controls.Control.Background%2A> tlačítko pomocí <xref:System.Windows.Media.ImageBrush>.</span><span class="sxs-lookup"><span data-stu-id="a9c94-106">The following example paints the <xref:System.Windows.Controls.Control.Background%2A> of a button by using an <xref:System.Windows.Media.ImageBrush>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 <span data-ttu-id="a9c94-107">Ve výchozím <xref:System.Windows.Media.ImageBrush> nastavení roztáhne obraz tak, aby zcela vyplnil oblast, kterou malujete.</span><span class="sxs-lookup"><span data-stu-id="a9c94-107">By default, an <xref:System.Windows.Media.ImageBrush> stretches its image to completely fill the area that you are painting.</span></span> <span data-ttu-id="a9c94-108">V předchozím příkladu je obraz roztažen tak, aby vyplnil tlačítko, což může obrázek zkreslit.</span><span class="sxs-lookup"><span data-stu-id="a9c94-108">In the preceding example, the image is stretched to fill the button, possibly distorting the image.</span></span> <span data-ttu-id="a9c94-109">Toto chování můžete řídit <xref:System.Windows.Media.TileBrush.Stretch%2A> nastavením <xref:System.Windows.Media.Stretch.Uniform> <xref:System.Windows.Media.Stretch.UniformToFill>vlastnosti <xref:System.Windows.Media.TileBrush> nebo , která způsobí, že stopa zachová poměr stran obrazu.</span><span class="sxs-lookup"><span data-stu-id="a9c94-109">You can control this behavior by setting the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of <xref:System.Windows.Media.TileBrush> to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>, which causes the brush to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="a9c94-110">Pokud nastavíte <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnosti <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.TileBrush.Viewport%2A> a , můžete vytvořit opakující se vzorek.</span><span class="sxs-lookup"><span data-stu-id="a9c94-110">If you set the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties of an <xref:System.Windows.Media.ImageBrush>, you can create a repeating pattern.</span></span> <span data-ttu-id="a9c94-111">Následující příklad maluje tlačítko pomocí vzoru, který je vytvořen z obrazu.</span><span class="sxs-lookup"><span data-stu-id="a9c94-111">The following example paints a button by using a pattern that is created from an image.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 <span data-ttu-id="a9c94-112">Další informace o <xref:System.Windows.Media.ImageBrush> třídě naleznete v tématu [Malování obrázky, kresby a vizuály](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="a9c94-112">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="a9c94-113">Tento příklad kódu je součástí většípříklad, který <xref:System.Windows.Media.ImageBrush> je k dispozici pro třídu.</span><span class="sxs-lookup"><span data-stu-id="a9c94-113">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="a9c94-114">Kompletní ukázku naleznete v tématu [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span><span class="sxs-lookup"><span data-stu-id="a9c94-114">For the complete sample, see [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c94-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9c94-115">See also</span></span>

- [<span data-ttu-id="a9c94-116">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="a9c94-116">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
