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
ms.openlocfilehash: c1db803aacad85ce90fec519b5eabdd8df7bb584
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369120"
---
# <a name="how-to-paint-an-area-with-an-image"></a><span data-ttu-id="a8471-102">Postupy: Vykreslení obrázku v oblasti</span><span class="sxs-lookup"><span data-stu-id="a8471-102">How to: Paint an Area with an Image</span></span>
<span data-ttu-id="a8471-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.ImageBrush> třídu pro vykreslení oblasti obrázkem.</span><span class="sxs-lookup"><span data-stu-id="a8471-103">This example shows how to use the <xref:System.Windows.Media.ImageBrush> class to paint an area with an image.</span></span> <span data-ttu-id="a8471-104"><xref:System.Windows.Media.ImageBrush> Zobrazí jedné image, která je určená jeho <xref:System.Windows.Media.ImageBrush.ImageSource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a8471-104">An <xref:System.Windows.Media.ImageBrush> displays a single image, which is specified by its <xref:System.Windows.Media.ImageBrush.ImageSource%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8471-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8471-105">Example</span></span>  
 <span data-ttu-id="a8471-106">Následující příklad barvy <xref:System.Windows.Controls.Control.Background%2A> tlačítka pomocí <xref:System.Windows.Media.ImageBrush>.</span><span class="sxs-lookup"><span data-stu-id="a8471-106">The following example paints the <xref:System.Windows.Controls.Control.Background%2A> of a button by using an <xref:System.Windows.Media.ImageBrush>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 <span data-ttu-id="a8471-107">Ve výchozím nastavení <xref:System.Windows.Media.ImageBrush> roztáhne, aby jeho image pro úplně naplnění oblasti, kterou vymalováváte.</span><span class="sxs-lookup"><span data-stu-id="a8471-107">By default, an <xref:System.Windows.Media.ImageBrush> stretches its image to completely fill the area that you are painting.</span></span> <span data-ttu-id="a8471-108">V předchozím příkladu je na obrázku roztažený tak, aby vyplnil tlačítko, případně narušují bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="a8471-108">In the preceding example, the image is stretched to fill the button, possibly distorting the image.</span></span> <span data-ttu-id="a8471-109">Toto chování můžete ovládat nastavením <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost <xref:System.Windows.Media.TileBrush> k <xref:System.Windows.Media.Stretch.Uniform> nebo <xref:System.Windows.Media.Stretch.UniformToFill>, což způsobí, že štětce, který se zachovat poměr stran obrázku.</span><span class="sxs-lookup"><span data-stu-id="a8471-109">You can control this behavior by setting the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of <xref:System.Windows.Media.TileBrush> to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>, which causes the brush to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="a8471-110">Pokud jste nastavili <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnosti <xref:System.Windows.Media.ImageBrush>, můžete vytvořit s opakováním vzoru.</span><span class="sxs-lookup"><span data-stu-id="a8471-110">If you set the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties of an <xref:System.Windows.Media.ImageBrush>, you can create a repeating pattern.</span></span> <span data-ttu-id="a8471-111">V následujícím příkladu jsou vykreslovány tlačítko s použitím vzoru, který je vytvořený z image.</span><span class="sxs-lookup"><span data-stu-id="a8471-111">The following example paints a button by using a pattern that is created from an image.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 <span data-ttu-id="a8471-112">Další informace o <xref:System.Windows.Media.ImageBrush> najdete v tématu [Malování pomocí obrázků, kreseb a vizuálních](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="a8471-112">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="a8471-113">Tento příklad kódu je součástí většího příkladu, která je k dispozici pro <xref:System.Windows.Media.ImageBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="a8471-113">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="a8471-114">Úplnou ukázku najdete v tématu [ImageBrush ukázka](https://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="a8471-114">For the complete sample, see [ImageBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8471-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8471-115">See also</span></span>
- [<span data-ttu-id="a8471-116">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="a8471-116">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
