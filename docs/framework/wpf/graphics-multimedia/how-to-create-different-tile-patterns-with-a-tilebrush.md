---
title: 'Postupy: Vytváření jiných vzorů dlaždic pomocí TileBrush'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
ms.openlocfilehash: 01004c66a8bd820f05e6e1f6c77a9fe7d30bca46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559597"
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a><span data-ttu-id="ddcca-102">Postupy: Vytváření jiných vzorů dlaždic pomocí TileBrush</span><span class="sxs-lookup"><span data-stu-id="ddcca-102">How to: Create Different Tile Patterns with a TileBrush</span></span>
<span data-ttu-id="ddcca-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost <xref:System.Windows.Media.TileBrush> vzorek.</span><span class="sxs-lookup"><span data-stu-id="ddcca-103">This example shows how to use the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.TileBrush> to create a pattern.</span></span>  
  
 <span data-ttu-id="ddcca-104"><xref:System.Windows.Media.TileBrush.TileMode%2A> Vlastnost umožňuje určit jak obsah <xref:System.Windows.Media.TileBrush> se opakuje, který je, rozložen formou dlaždic k vyplnění oblast výstup.</span><span class="sxs-lookup"><span data-stu-id="ddcca-104">The <xref:System.Windows.Media.TileBrush.TileMode%2A> property enables you to specify how the content of a <xref:System.Windows.Media.TileBrush> is repeated, that is, tiled to fill an output area.</span></span> <span data-ttu-id="ddcca-105">Pokud chcete vytvořit vzor, nastavíte <xref:System.Windows.Media.TileBrush.TileMode%2A> k <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, nebo <xref:System.Windows.Media.TileMode.FlipXY>.</span><span class="sxs-lookup"><span data-stu-id="ddcca-105">To create a pattern, you set the <xref:System.Windows.Media.TileBrush.TileMode%2A> to <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, or <xref:System.Windows.Media.TileMode.FlipXY>.</span></span> <span data-ttu-id="ddcca-106">Je nutné také nastavit <xref:System.Windows.Media.TileBrush.Viewport%2A> z <xref:System.Windows.Media.TileBrush> tak, aby byla menší než k oblasti, která jste jsou vykreslování; jinak, pouze jedna dlaždice je vytvořené, bez ohledu na to který <xref:System.Windows.Media.TileBrush.TileMode%2A> nastavení, které používáte.</span><span class="sxs-lookup"><span data-stu-id="ddcca-106">You must also set the <xref:System.Windows.Media.TileBrush.Viewport%2A> of the <xref:System.Windows.Media.TileBrush> so that it is smaller than the area that you are painting; otherwise, only a single tile is produced, regardless which <xref:System.Windows.Media.TileBrush.TileMode%2A> setting you use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddcca-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ddcca-107">Example</span></span>  
 <span data-ttu-id="ddcca-108">Následující příklad vytvoří pět <xref:System.Windows.Media.DrawingBrush> objekty, poskytne jim každý v jiné <xref:System.Windows.Media.TileBrush.TileMode%2A> nastavení a použije je k vyplnění pět obdélníky.</span><span class="sxs-lookup"><span data-stu-id="ddcca-108">The following example creates five <xref:System.Windows.Media.DrawingBrush> objects, gives them each a different <xref:System.Windows.Media.TileBrush.TileMode%2A> setting, and uses them to paint five rectangles.</span></span> <span data-ttu-id="ddcca-109">I když tento příklad používá <xref:System.Windows.Media.DrawingBrush> třída k předvedení <xref:System.Windows.Media.TileBrush.TileMode%2A> chování, <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost funguje stejně jako u všech <xref:System.Windows.Media.TileBrush> objekty, který je pro <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, a <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="ddcca-109">Although this example uses the <xref:System.Windows.Media.DrawingBrush> class to demonstrate <xref:System.Windows.Media.TileBrush.TileMode%2A> behavior, the <xref:System.Windows.Media.TileBrush.TileMode%2A> property works identically for all the <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, and <xref:System.Windows.Media.DrawingBrush>.</span></span>  
  
 <span data-ttu-id="ddcca-110">Následující obrázek znázorňuje výstupu, který tento příklad vytvoří.</span><span class="sxs-lookup"><span data-stu-id="ddcca-110">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="ddcca-111">![TileBrush dlaždice příklad výstupu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")</span><span class="sxs-lookup"><span data-stu-id="ddcca-111">![TileBrush tiling example output](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")</span></span>  
<span data-ttu-id="ddcca-112">Vzory dlaždice, které jsou vytvořeny s vlastnosti TileMode objektu</span><span class="sxs-lookup"><span data-stu-id="ddcca-112">Tile patterns created with the TileMode property</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="ddcca-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddcca-113">See Also</span></span>  
 [<span data-ttu-id="ddcca-114">Nastavení velikosti dlaždice pro TileBrush</span><span class="sxs-lookup"><span data-stu-id="ddcca-114">Set the Tile Size for a TileBrush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)  
 [<span data-ttu-id="ddcca-115">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="ddcca-115">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
