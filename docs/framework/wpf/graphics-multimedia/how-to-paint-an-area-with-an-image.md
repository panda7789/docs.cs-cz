---
title: "Postupy: Vykreslení obrázku v oblasti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3edbe30347580bb4f9677d7fb98d3b4fd8b92cff
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-paint-an-area-with-an-image"></a><span data-ttu-id="ec0a2-102">Postupy: Vykreslení obrázku v oblasti</span><span class="sxs-lookup"><span data-stu-id="ec0a2-102">How to: Paint an Area with an Image</span></span>
<span data-ttu-id="ec0a2-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.ImageBrush> třídy Malování oblast s bitovou kopií.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-103">This example shows how to use the <xref:System.Windows.Media.ImageBrush> class to paint an area with an image.</span></span> <span data-ttu-id="ec0a2-104"><xref:System.Windows.Media.ImageBrush> Zobrazí jeden obrázek, který je určený jeho <xref:System.Windows.Media.ImageBrush.ImageSource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-104">An <xref:System.Windows.Media.ImageBrush> displays a single image, which is specified by its <xref:System.Windows.Media.ImageBrush.ImageSource%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec0a2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec0a2-105">Example</span></span>  
 <span data-ttu-id="ec0a2-106">Následující příklad barvy <xref:System.Windows.Controls.Control.Background%2A> tlačítka pomocí <xref:System.Windows.Media.ImageBrush>.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-106">The following example paints the <xref:System.Windows.Controls.Control.Background%2A> of a button by using an <xref:System.Windows.Media.ImageBrush>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 <span data-ttu-id="ec0a2-107">Ve výchozím nastavení <xref:System.Windows.Media.ImageBrush> roztahovány jeho image na nejbližší k oblasti, která jsou vykreslování.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-107">By default, an <xref:System.Windows.Media.ImageBrush> stretches its image to completely fill the area that you are painting.</span></span> <span data-ttu-id="ec0a2-108">V předchozím příkladu obrázek je roztažen tak k vyplnění tlačítko, případně narušují bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-108">In the preceding example, the image is stretched to fill the button, possibly distorting the image.</span></span> <span data-ttu-id="ec0a2-109">Toto chování můžete ovládat nastavením <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost <xref:System.Windows.Media.TileBrush> k <xref:System.Windows.Media.Stretch.Uniform> nebo <xref:System.Windows.Media.Stretch.UniformToFill>, což způsobí, že štětce k zachová poměr stran obrázku.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-109">You can control this behavior by setting the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of <xref:System.Windows.Media.TileBrush> to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>, which causes the brush to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="ec0a2-110">Pokud nastavíte <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnosti <xref:System.Windows.Media.ImageBrush>, můžete vytvořit opakující se vzorek.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-110">If you set the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties of an <xref:System.Windows.Media.ImageBrush>, you can create a repeating pattern.</span></span> <span data-ttu-id="ec0a2-111">Následující příklad vybarví tlačítko pomocí vzor, který je vytvořený z image.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-111">The following example paints a button by using a pattern that is created from an image.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 <span data-ttu-id="ec0a2-112">Další informace o <xref:System.Windows.Media.ImageBrush> třídy najdete v tématu [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="ec0a2-112">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="ec0a2-113">Tento příklad kódu je součástí většího příkladu vztahujícího se k <xref:System.Windows.Media.ImageBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-113">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="ec0a2-114">Kompletní příklad, najdete v části [Objekt ImageBrush ukázka](http://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="ec0a2-114">For the complete sample, see [ImageBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec0a2-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec0a2-115">See Also</span></span>  
 [<span data-ttu-id="ec0a2-116">Malování s obrázky, kresby a vizuální prvky</span><span class="sxs-lookup"><span data-stu-id="ec0a2-116">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
