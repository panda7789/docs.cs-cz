---
title: 'Postupy: Nastavení velikosti dlaždice pro TileBrush'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: af7bab59a292549b29dad9b6a7417f22b1b84e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186839"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="cd099-102">Postupy: Nastavení velikosti dlaždice pro TileBrush</span><span class="sxs-lookup"><span data-stu-id="cd099-102">How to: Set the Tile Size for a TileBrush</span></span>

<span data-ttu-id="cd099-103">Tento příklad ukazuje, jak nastavit <xref:System.Windows.Media.TileBrush>velikost dlaždice pro .</span><span class="sxs-lookup"><span data-stu-id="cd099-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="cd099-104">Ve výchozím <xref:System.Windows.Media.TileBrush> nastavení vytvoří jedna dlaždice, která zcela vyplní oblast, kterou malujete.</span><span class="sxs-lookup"><span data-stu-id="cd099-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="cd099-105">Toto chování můžete přepsat <xref:System.Windows.Media.TileBrush.Viewport%2A> nastavením vlastností a. <xref:System.Windows.Media.TileBrush.ViewportUnits%2A></span><span class="sxs-lookup"><span data-stu-id="cd099-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>

<span data-ttu-id="cd099-106">Vlastnost <xref:System.Windows.Media.TileBrush.Viewport%2A> určuje velikost dlaždice pro <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="cd099-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="cd099-107">Ve výchozím nastavení je <xref:System.Windows.Media.TileBrush.Viewport%2A> hodnota vlastnosti relativní k velikosti oblasti, která je vybarvena.</span><span class="sxs-lookup"><span data-stu-id="cd099-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="cd099-108">Chcete-li, <xref:System.Windows.Media.TileBrush.Viewport%2A> aby vlastnost určovat <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> absolutní <xref:System.Windows.Media.BrushMappingMode.Absolute>velikost dlaždice, nastavte vlastnost na .</span><span class="sxs-lookup"><span data-stu-id="cd099-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>

## <a name="example"></a><span data-ttu-id="cd099-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd099-109">Example</span></span>

<span data-ttu-id="cd099-110">Následující příklad používá <xref:System.Windows.Media.ImageBrush>, typ <xref:System.Windows.Media.TileBrush>, malovat obdélník s dlaždicemi.</span><span class="sxs-lookup"><span data-stu-id="cd099-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="cd099-111">Příklad nastaví každou dlaždici na 50 procent o 50 procent výstupní oblasti (obdélník).</span><span class="sxs-lookup"><span data-stu-id="cd099-111">The example sets each tile to 50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="cd099-112">V důsledku toho je obdélník vymalován čtyřmi projekcemi obrazu.</span><span class="sxs-lookup"><span data-stu-id="cd099-112">As a result, the rectangle is painted with four projections of the image.</span></span>

<span data-ttu-id="cd099-113">Následující obrázek znázorňuje výstup, který v příkladu vytváří:</span><span class="sxs-lookup"><span data-stu-id="cd099-113">The following illustration shows the output that the example produces:</span></span>

![Obdélník se čtyřmi třešněmi demonstrujícími obklady s obrazovým štětcem.](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

<span data-ttu-id="cd099-115">Další příklad vytvoří <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.TileBrush.Viewport%2A> nastaví <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> jeho <xref:System.Windows.Media.BrushMappingMode.Absolute>a `0,0,25,25` jeho na , a používá jej k malování jiného obdélníku.</span><span class="sxs-lookup"><span data-stu-id="cd099-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="cd099-116">V důsledku toho stopa vytváří dlaždice, které mají šířku 25 pixelů a výšku 25 pixelů .</span><span class="sxs-lookup"><span data-stu-id="cd099-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>

<span data-ttu-id="cd099-117">Následující obrázek znázorňuje výstup, který v příkladu vytváří:</span><span class="sxs-lookup"><span data-stu-id="cd099-117">The following illustration shows the output that the example produces:</span></span>

![Obdélník s čtyřicet osm třešní demonstrovat kachlová TileBrush s výřez.](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

<span data-ttu-id="cd099-119">Předchozí příklady jsou součástí větší ukázky.</span><span class="sxs-lookup"><span data-stu-id="cd099-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="cd099-120">Kompletní ukázku naleznete v tématu [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span><span class="sxs-lookup"><span data-stu-id="cd099-120">For the complete sample, see [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span></span>

<span data-ttu-id="cd099-121">Ačkoli tento příklad <xref:System.Windows.Media.ImageBrush> používá <xref:System.Windows.Media.TileBrush.Viewport%2A> třídu, vlastnosti <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> a <xref:System.Windows.Media.TileBrush> se chovají stejně <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush>pro ostatní objekty, to znamená pro a .</span><span class="sxs-lookup"><span data-stu-id="cd099-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="cd099-122">Další informace <xref:System.Windows.Media.ImageBrush> o ostatních <xref:System.Windows.Media.TileBrush> objektech naleznete v [tématu Malování obrázky, kresbami a vizuály](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="cd099-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cd099-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd099-123">See also</span></span>

- <xref:System.Windows.Media.TileBrush>
- [<span data-ttu-id="cd099-124">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="cd099-124">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="cd099-125">Vytvoření jiných vzorů dlaždic pomocí prvku TileBrush</span><span class="sxs-lookup"><span data-stu-id="cd099-125">Create Different Tile Patterns with a TileBrush</span></span>](how-to-create-different-tile-patterns-with-a-tilebrush.md)
