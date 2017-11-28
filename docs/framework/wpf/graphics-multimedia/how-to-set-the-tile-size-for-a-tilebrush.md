---
title: "Postupy: Nastavení velikosti dlaždice pro TileBrush"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 484419c05c3d607212ea6d565777cf49cbfdbc19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="29e3c-102">Postupy: Nastavení velikosti dlaždice pro TileBrush</span><span class="sxs-lookup"><span data-stu-id="29e3c-102">How to: Set the Tile Size for a TileBrush</span></span>
<span data-ttu-id="29e3c-103">Tento příklad ukazuje, jak nastavit velikost dlaždice pro <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="29e3c-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="29e3c-104">Ve výchozím nastavení <xref:System.Windows.Media.TileBrush> vytvoří jedna dlaždice, který kompletně vyplní celé oblasti, která jsou vykreslování.</span><span class="sxs-lookup"><span data-stu-id="29e3c-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="29e3c-105">Toto chování můžete přepsat pomocí nastavení <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="29e3c-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>  
  
 <span data-ttu-id="29e3c-106"><xref:System.Windows.Media.TileBrush.Viewport%2A> Vlastnost určuje velikost dlaždice <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="29e3c-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="29e3c-107">Výchozí hodnota <xref:System.Windows.Media.TileBrush.Viewport%2A> vlastnost je relativní vzhledem k velikosti oblasti se vykresluje.</span><span class="sxs-lookup"><span data-stu-id="29e3c-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="29e3c-108">Chcete-li <xref:System.Windows.Media.TileBrush.Viewport%2A> vlastnost stanovit velikost absolutní dlaždice, nastavit <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnost <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="29e3c-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29e3c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="29e3c-109">Example</span></span>  
 <span data-ttu-id="29e3c-110">Následující příklad používá <xref:System.Windows.Media.ImageBrush>, typ <xref:System.Windows.Media.TileBrush>, k vyplnění obdélníku s dlaždice.</span><span class="sxs-lookup"><span data-stu-id="29e3c-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="29e3c-111">V příkladu nastaví každou dlaždici na 50 procent o 50 procent výstupní oblasti (rámeček).</span><span class="sxs-lookup"><span data-stu-id="29e3c-111">The example sets each tile to  50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="29e3c-112">V důsledku toho rámeček vykreslením s čtyři projekce bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="29e3c-112">As a result, the rectangle is painted with four projections of the image.</span></span>  
  
 <span data-ttu-id="29e3c-113">Následující obrázek znázorňuje výstupu, který vytváří v příkladu.</span><span class="sxs-lookup"><span data-stu-id="29e3c-113">The following illustration shows the output that the example produces.</span></span>
  
 <span data-ttu-id="29e3c-114">![Příklad dlaždice s štětce image](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")</span><span class="sxs-lookup"><span data-stu-id="29e3c-114">![Example of tiling with an image brush](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 <span data-ttu-id="29e3c-115">Další příklad vytvoří <xref:System.Windows.Media.ImageBrush>, nastaví její <xref:System.Windows.Media.TileBrush.Viewport%2A> k `0,0,25,25` a jeho <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> k <xref:System.Windows.Media.BrushMappingMode.Absolute>a používá ho k vyplnění jiné obdélníku.</span><span class="sxs-lookup"><span data-stu-id="29e3c-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="29e3c-116">V důsledku toho stopy vytvoří dlaždice, které mají 25 pixelů šířka a výška 25 pixelů.</span><span class="sxs-lookup"><span data-stu-id="29e3c-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>  
  
 <span data-ttu-id="29e3c-117">Následující obrázek znázorňuje výstupu, který vytváří v příkladu.</span><span class="sxs-lookup"><span data-stu-id="29e3c-117">The following illustration shows the output that the example produces.</span></span>  
  
 <span data-ttu-id="29e3c-118">![A na dlaždicích TileBrush se zobrazení 0,0,0.25,0.25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")</span><span class="sxs-lookup"><span data-stu-id="29e3c-118">![A tiled TileBrush with a Viewport of 0,0,0.25,0.25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 <span data-ttu-id="29e3c-119">V předchozích příkladech jsou součástí větší ukázky.</span><span class="sxs-lookup"><span data-stu-id="29e3c-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="29e3c-120">Kompletní příklad, najdete v části [Objekt ImageBrush ukázka](http://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="29e3c-120">For the complete sample, see [ImageBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
 <span data-ttu-id="29e3c-121">I když tento příklad používá <xref:System.Windows.Media.ImageBrush> třídy, <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnosti chovají stejně jako pro druhý <xref:System.Windows.Media.TileBrush> objekty, který je pro <xref:System.Windows.Media.DrawingBrush> a <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="29e3c-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="29e3c-122">Další informace o <xref:System.Windows.Media.ImageBrush> a dalších <xref:System.Windows.Media.TileBrush> objekty, najdete v části [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="29e3c-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e3c-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="29e3c-123">See Also</span></span>  
 <xref:System.Windows.Media.TileBrush>  
 [<span data-ttu-id="29e3c-124">Malování s obrázky, kresby a vizuální prvky</span><span class="sxs-lookup"><span data-stu-id="29e3c-124">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="29e3c-125">Vytvořte různé dlaždice vzory s Objekt TileBrush</span><span class="sxs-lookup"><span data-stu-id="29e3c-125">Create Different Tile Patterns with a TileBrush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
