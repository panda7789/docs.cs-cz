---
title: "Postupy: Zachování poměru stran u obrázku na pozadí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9716d91a99eb79e38b729424389b2962d1eb6b1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a><span data-ttu-id="55dc5-102">Postupy: Zachování poměru stran u obrázku na pozadí</span><span class="sxs-lookup"><span data-stu-id="55dc5-102">How to: Preserve the Aspect Ratio of an Image Used as a Background</span></span>
<span data-ttu-id="55dc5-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost <xref:System.Windows.Media.ImageBrush> Chcete-li zachovat poměr stran obrázku.</span><span class="sxs-lookup"><span data-stu-id="55dc5-103">This example shows how to use the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of an <xref:System.Windows.Media.ImageBrush> in order to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="55dc5-104">Ve výchozím nastavení se při použití <xref:System.Windows.Media.ImageBrush> k vyplnění oblast, její obsah roztahovány úplně zaplnění výstupní oblasti.</span><span class="sxs-lookup"><span data-stu-id="55dc5-104">By default, when you use an <xref:System.Windows.Media.ImageBrush> to paint an area, its content stretches to completely fill the output area.</span></span> <span data-ttu-id="55dc5-105">Pokud mají různé poměrům stran oblasti výstup a bitovou kopii, bitovou kopii je poškozený, podle této roztažení.</span><span class="sxs-lookup"><span data-stu-id="55dc5-105">When the output area and the image have different aspect ratios, the image is distorted by this stretching.</span></span>  
  
 <span data-ttu-id="55dc5-106">Chcete-li <xref:System.Windows.Media.ImageBrush> zachová poměr stran jeho bitové kopie, nastavte <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost <xref:System.Windows.Media.Stretch.Uniform> nebo <xref:System.Windows.Media.Stretch.UniformToFill>.</span><span class="sxs-lookup"><span data-stu-id="55dc5-106">To make an <xref:System.Windows.Media.ImageBrush> preserve the aspect ratio of its image, set the <xref:System.Windows.Media.TileBrush.Stretch%2A> property to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55dc5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="55dc5-107">Example</span></span>  
 <span data-ttu-id="55dc5-108">Následující příklad používá dva <xref:System.Windows.Media.ImageBrush> objekty k vyplnění dvou tvaru.</span><span class="sxs-lookup"><span data-stu-id="55dc5-108">The following example uses two <xref:System.Windows.Media.ImageBrush> objects to paint two rectangles.</span></span> <span data-ttu-id="55dc5-109">Každý rámeček je 300 o 150 pixelů a každý obsahuje bitovou kopii 300 podle 300 pixelů.</span><span class="sxs-lookup"><span data-stu-id="55dc5-109">Each rectangle is 300 by 150 pixels and each contains a 300 by 300 pixel image.</span></span> <span data-ttu-id="55dc5-110"><xref:System.Windows.Media.TileBrush.Stretch%2A> První stopy je nastavena na <xref:System.Windows.Media.Stretch.Uniform>a <xref:System.Windows.Media.TileBrush.Stretch%2A> druhý štětce je nastavena na <xref:System.Windows.Media.Stretch.UniformToFill>.</span><span class="sxs-lookup"><span data-stu-id="55dc5-110">The <xref:System.Windows.Media.TileBrush.Stretch%2A> property of the first brush is set to <xref:System.Windows.Media.Stretch.Uniform>, and the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of the second brush is set to <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 <span data-ttu-id="55dc5-111">Následující obrázek ukazuje výstup první štětce, který má <xref:System.Windows.Media.TileBrush.Stretch%2A> nastavení <xref:System.Windows.Media.Stretch.Uniform>.</span><span class="sxs-lookup"><span data-stu-id="55dc5-111">The following illustration shows the output of the first brush, which has a <xref:System.Windows.Media.TileBrush.Stretch%2A> setting of <xref:System.Windows.Media.Stretch.Uniform>.</span></span>  
  
 <span data-ttu-id="55dc5-112">![Objekt ImageBrush s Uniform roztažení](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")</span><span class="sxs-lookup"><span data-stu-id="55dc5-112">![ImageBrush with Uniform stretching](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")</span></span>  
  
 <span data-ttu-id="55dc5-113">Následující obrázek znázorňuje, výstup druhý štětce, který má <xref:System.Windows.Media.TileBrush.Stretch%2A> nastavení <xref:System.Windows.Media.Stretch.UniformToFill>.</span><span class="sxs-lookup"><span data-stu-id="55dc5-113">The next illustration shows the output of the second brush, which has a <xref:System.Windows.Media.TileBrush.Stretch%2A> setting of <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
 <span data-ttu-id="55dc5-114">![Objekt ImageBrush s roztažením UniformToFill](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")</span><span class="sxs-lookup"><span data-stu-id="55dc5-114">![ImageBrush with UniformToFill stretching](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")</span></span>  
  
 <span data-ttu-id="55dc5-115">Všimněte si, že <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost se chová stejně pro druhý <xref:System.Windows.Media.TileBrush> objekty, který je pro <xref:System.Windows.Media.DrawingBrush> a <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="55dc5-115">Note that the <xref:System.Windows.Media.TileBrush.Stretch%2A> property behaves identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="55dc5-116">Další informace o <xref:System.Windows.Media.ImageBrush> a dalších <xref:System.Windows.Media.TileBrush> objekty, najdete v části [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="55dc5-116">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="55dc5-117">Všimněte si také, že i když <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnosti se zobrazí, zadejte jak <xref:System.Windows.Media.TileBrush> obsah roztahovány podle jeho výstup oblasti, ve skutečnosti určuje, jak <xref:System.Windows.Media.TileBrush> obsahu úsecích k vyplnění jeho základní dlaždice.</span><span class="sxs-lookup"><span data-stu-id="55dc5-117">Note also that, although the <xref:System.Windows.Media.TileBrush.Stretch%2A> property appears to specify how the <xref:System.Windows.Media.TileBrush> content stretches to fit its output area, it actually specifies how the <xref:System.Windows.Media.TileBrush> content stretches to fill its base tile.</span></span> <span data-ttu-id="55dc5-118">Další informace naleznete v tématu <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="55dc5-118">For more information, see <xref:System.Windows.Media.TileBrush>.</span></span>  
  
 <span data-ttu-id="55dc5-119">Tento příklad kódu je součástí většího příkladu vztahujícího se k <xref:System.Windows.Media.ImageBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="55dc5-119">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="55dc5-120">Kompletní příklad, najdete v části [Objekt ImageBrush ukázka](http://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="55dc5-120">For the complete sample, see [ImageBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55dc5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="55dc5-121">See Also</span></span>  
 <xref:System.Windows.Media.TileBrush>  
 [<span data-ttu-id="55dc5-122">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="55dc5-122">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
