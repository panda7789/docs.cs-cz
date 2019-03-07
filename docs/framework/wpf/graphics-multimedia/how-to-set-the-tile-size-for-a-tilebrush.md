---
title: 'Postupy: Nastavení velikosti dlaždice pro TileBrush'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: ecac41b0ca40abf59dfcba1efffc076687c2f1ff
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502225"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="23c48-102">Postupy: Nastavení velikosti dlaždice pro TileBrush</span><span class="sxs-lookup"><span data-stu-id="23c48-102">How to: Set the Tile Size for a TileBrush</span></span>

<span data-ttu-id="23c48-103">Tento příklad ukazuje, jak nastavení velikosti dlaždice pro <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="23c48-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="23c48-104">Ve výchozím nastavení <xref:System.Windows.Media.TileBrush> vytváří jednu dlaždici, která úplně vyplňuje oblast, kterou vymalováváte.</span><span class="sxs-lookup"><span data-stu-id="23c48-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="23c48-105">Toto chování můžete přepsat tak, že nastavíte <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="23c48-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>

<span data-ttu-id="23c48-106"><xref:System.Windows.Media.TileBrush.Viewport%2A> Vlastnost určuje velikost dlaždice <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="23c48-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="23c48-107">Výchozí hodnota <xref:System.Windows.Media.TileBrush.Viewport%2A> vlastnost je relativní vzhledem k velikosti oblasti se překreslit.</span><span class="sxs-lookup"><span data-stu-id="23c48-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="23c48-108">Chcete-li <xref:System.Windows.Media.TileBrush.Viewport%2A> vlastnost určovat velikost absolutní dlaždice nastavit <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnost <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="23c48-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>

## <a name="example"></a><span data-ttu-id="23c48-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="23c48-109">Example</span></span>

<span data-ttu-id="23c48-110">Následující příklad používá <xref:System.Windows.Media.ImageBrush>, typu <xref:System.Windows.Media.TileBrush>k vykreslení obdélníku s dlaždicemi.</span><span class="sxs-lookup"><span data-stu-id="23c48-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="23c48-111">Příklad nastaví Každá dlaždice na 50 % 50 procent výstupní oblasti (obdélník).</span><span class="sxs-lookup"><span data-stu-id="23c48-111">The example sets each tile to  50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="23c48-112">V důsledku toho obdélník vybarvené čtyři projekce bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="23c48-112">As a result, the rectangle is painted with four projections of the image.</span></span>

<span data-ttu-id="23c48-113">Následující obrázek znázorňuje výstup v příkladu vytvoří.</span><span class="sxs-lookup"><span data-stu-id="23c48-113">The following illustration shows the output that the example produces.</span></span>

<span data-ttu-id="23c48-114">![Příklad dělení do bloků s obrázkový štětec](./media/0.png "0")</span><span class="sxs-lookup"><span data-stu-id="23c48-114">![Example of tiling with an image brush](./media/0.png "0")</span></span>

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

<span data-ttu-id="23c48-115">Následující příklad vytvoří <xref:System.Windows.Media.ImageBrush>, nastaví jeho <xref:System.Windows.Media.TileBrush.Viewport%2A> k `0,0,25,25` a jeho <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> k <xref:System.Windows.Media.BrushMappingMode.Absolute>a použije ho k vykreslení jiného obdélník.</span><span class="sxs-lookup"><span data-stu-id="23c48-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="23c48-116">V důsledku toho vytváří štětec, které mají šířku 25 pixelů a výšku v pixelech 25.</span><span class="sxs-lookup"><span data-stu-id="23c48-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>

<span data-ttu-id="23c48-117">Následující obrázek znázorňuje výstup v příkladu vytvoří.</span><span class="sxs-lookup"><span data-stu-id="23c48-117">The following illustration shows the output that the example produces.</span></span>

<span data-ttu-id="23c48-118">![A vedle sebe TileBrush se oblast zobrazení 0,0,0.25,0.25](./media/25x25viewport.png "25x25viewport")</span><span class="sxs-lookup"><span data-stu-id="23c48-118">![A tiled TileBrush with a Viewport of 0,0,0.25,0.25](./media/25x25viewport.png "25x25viewport")</span></span>

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

<span data-ttu-id="23c48-119">Předchozí příklady jsou součástí větší ukázky.</span><span class="sxs-lookup"><span data-stu-id="23c48-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="23c48-120">Úplnou ukázku najdete v tématu [ImageBrush ukázka](https://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="23c48-120">For the complete sample, see [ImageBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160005).</span></span>

<span data-ttu-id="23c48-121">I když v tomto příkladu <xref:System.Windows.Media.ImageBrush> třídy, <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnosti se chovají stejně jako pro ostatní <xref:System.Windows.Media.TileBrush> objekty, to znamená, pro <xref:System.Windows.Media.DrawingBrush> a <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="23c48-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="23c48-122">Další informace o <xref:System.Windows.Media.ImageBrush> a druhý <xref:System.Windows.Media.TileBrush> objekty, najdete [Malování pomocí obrázků, kreseb a vizuálních](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="23c48-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="23c48-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23c48-123">See also</span></span>

- <xref:System.Windows.Media.TileBrush>
- [<span data-ttu-id="23c48-124">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="23c48-124">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="23c48-125">Vytvoření jiných vzorů dlaždic pomocí prvku TileBrush</span><span class="sxs-lookup"><span data-stu-id="23c48-125">Create Different Tile Patterns with a TileBrush</span></span>](how-to-create-different-tile-patterns-with-a-tilebrush.md)
