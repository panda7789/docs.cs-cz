---
title: 'Postupy: Dlaždicové vyplnění obrazce pomocí obrázku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
ms.openlocfilehash: 0905f29b0f74c72979e252cf94e677d1c7e0525d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523120"
---
# <a name="how-to-tile-a-shape-with-an-image"></a><span data-ttu-id="e8b77-102">Postupy: Dlaždicové vyplnění obrazce pomocí obrázku</span><span class="sxs-lookup"><span data-stu-id="e8b77-102">How to: Tile a Shape with an Image</span></span>
<span data-ttu-id="e8b77-103">Stejně jako dlaždice mohou být umístěny vedle sebe tak, aby pokrývalo podlaží, obdélníková bitové kopie můžete umístěny vedle sebe výplně (dlaždice) obrazce.</span><span class="sxs-lookup"><span data-stu-id="e8b77-103">Just as tiles can be placed next to each other to cover a floor, rectangular images can be placed next to each other to fill (tile) a shape.</span></span> <span data-ttu-id="e8b77-104">Na dlaždici vnitřek obrazce pomocí textury štětce.</span><span class="sxs-lookup"><span data-stu-id="e8b77-104">To tile the interior of a shape, use a texture brush.</span></span> <span data-ttu-id="e8b77-105">Když vytvoříte <xref:System.Drawing.TextureBrush> objektu jednoho z argumentů je předat do konstruktoru je <xref:System.Drawing.Image> objektu.</span><span class="sxs-lookup"><span data-stu-id="e8b77-105">When you construct a <xref:System.Drawing.TextureBrush> object, one of the arguments you pass to the constructor is an <xref:System.Drawing.Image> object.</span></span> <span data-ttu-id="e8b77-106">Pokud používáte texture štětce k vyplnění vnitřku tvaru, tvar je vyplněn opakovaných kopie tuto bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="e8b77-106">When you use the texture brush to paint the interior of a shape, the shape is filled with repeated copies of this image.</span></span>  
  
 <span data-ttu-id="e8b77-107">Vlastnost režim zalamování <xref:System.Drawing.TextureBrush> objektu určuje, jak je bitovou kopii orientované jako se opakuje v obdélníková mřížky.</span><span class="sxs-lookup"><span data-stu-id="e8b77-107">The wrap mode property of the <xref:System.Drawing.TextureBrush> object determines how the image is oriented as it is repeated in a rectangular grid.</span></span> <span data-ttu-id="e8b77-108">Zajistěte všechny dlaždice v mřížce mají stejné orientaci, nebo můžete použít bitovou kopii překlopit od pozice jeden mřížky na další.</span><span class="sxs-lookup"><span data-stu-id="e8b77-108">You can make all the tiles in the grid have the same orientation, or you can make the image flip from one grid position to the next.</span></span> <span data-ttu-id="e8b77-109">Překlopení může být vodorovně, vertical nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="e8b77-109">The flipping can be horizontal, vertical, or both.</span></span> <span data-ttu-id="e8b77-110">Následující příklady ukazují dlaždice s různými typy překlopení.</span><span class="sxs-lookup"><span data-stu-id="e8b77-110">The following examples demonstrate tiling with different types of flipping.</span></span>  
  
### <a name="to-tile-an-image"></a><span data-ttu-id="e8b77-111">Na dlaždici bitovou kopii</span><span class="sxs-lookup"><span data-stu-id="e8b77-111">To tile an image</span></span>  
  
-   <span data-ttu-id="e8b77-112">Tento příklad používá následující obrázek 75 × 75 na dlaždici obdélníku 200 × 200.</span><span class="sxs-lookup"><span data-stu-id="e8b77-112">This example uses the following 75×75 image to tile a 200×200 rectangle.</span></span>  
  
 <span data-ttu-id="e8b77-113">![Dlaždice 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")</span><span class="sxs-lookup"><span data-stu-id="e8b77-113">![Tile 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")</span></span>  
  
-   <span data-ttu-id="e8b77-114">Následující obrázek znázorňuje, jak je rámeček rozložen formou dlaždic s bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="e8b77-114">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="e8b77-115">Všimněte si, že všechny dlaždice mají stejné orientaci; není žádný překlopení.</span><span class="sxs-lookup"><span data-stu-id="e8b77-115">Note that all tiles have the same orientation; there is no flipping.</span></span>  
  
 <span data-ttu-id="e8b77-116">![Dlaždice 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")</span><span class="sxs-lookup"><span data-stu-id="e8b77-116">![Tile 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a><span data-ttu-id="e8b77-117">K převrácení bitovou kopii vodorovně při vedle sebe</span><span class="sxs-lookup"><span data-stu-id="e8b77-117">To flip an image horizontally while tiling</span></span>  
  
-   <span data-ttu-id="e8b77-118">Tento příklad používá stejnou bitovou kopii 75 × 75 k vyplnění obdélníku 200 × 200.</span><span class="sxs-lookup"><span data-stu-id="e8b77-118">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="e8b77-119">Režim zalamování nastavena na bitovou kopii Překlopit vodorovně.</span><span class="sxs-lookup"><span data-stu-id="e8b77-119">The wrap mode is set to flip the image horizontally.</span></span> <span data-ttu-id="e8b77-120">Následující obrázek znázorňuje, jak je rámeček rozložen formou dlaždic s bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="e8b77-120">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="e8b77-121">Všimněte si, jak přesunout z jednoho dlaždice na další v daném řádku je obrázek vodorovně obráceně.</span><span class="sxs-lookup"><span data-stu-id="e8b77-121">Note that as you move from one tile to the next in a given row, the image is flipped horizontally.</span></span>  
  
 <span data-ttu-id="e8b77-122">![Dlaždice 3](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")</span><span class="sxs-lookup"><span data-stu-id="e8b77-122">![Tile 3](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a><span data-ttu-id="e8b77-123">K převrácení image ve svislém směru při vedle sebe</span><span class="sxs-lookup"><span data-stu-id="e8b77-123">To flip an image vertically while tiling</span></span>  
  
-   <span data-ttu-id="e8b77-124">Tento příklad používá stejnou bitovou kopii 75 × 75 k vyplnění obdélníku 200 × 200.</span><span class="sxs-lookup"><span data-stu-id="e8b77-124">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="e8b77-125">Režim zalamování nastavena na bitovou kopii Překlopit svisle.</span><span class="sxs-lookup"><span data-stu-id="e8b77-125">The wrap mode is set to flip the image vertically.</span></span>  
  
     [!code-csharp[System.Drawing.UsingABrush#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a><span data-ttu-id="e8b77-126">K převrácení bitovou kopii při dlaždice vodorovně a svisle</span><span class="sxs-lookup"><span data-stu-id="e8b77-126">To flip an image horizontally and vertically while tiling</span></span>  
  
-   <span data-ttu-id="e8b77-127">Tento příklad používá stejnou bitovou kopii 75 × 75 na dlaždici obdélníku 200 × 200.</span><span class="sxs-lookup"><span data-stu-id="e8b77-127">This example uses the same 75×75 image to tile a 200×200 rectangle.</span></span> <span data-ttu-id="e8b77-128">Režim zalamování nastaven k převrácení bitovou kopii, vodorovně i svisle.</span><span class="sxs-lookup"><span data-stu-id="e8b77-128">The wrap mode is set to flip the image both horizontally and vertically.</span></span> <span data-ttu-id="e8b77-129">Následující obrázek znázorňuje, jak je rámeček rozložen formou dlaždic imagí.</span><span class="sxs-lookup"><span data-stu-id="e8b77-129">The following illustration shows how the rectangle is tiled by the image.</span></span> <span data-ttu-id="e8b77-130">Pamatujte, že jako přesunout z jednoho dlaždice na další v daném řádku, bitovou kopii je obráceno vodorovně a jak přesunout z jednoho dlaždice na další v daném sloupci bitovou kopii Svisle obráceně.</span><span class="sxs-lookup"><span data-stu-id="e8b77-130">Note that as you move from one tile to the next in a given row, the image is flipped horizontally, and as you move from one tile to the next in a given column, the image is flipped vertically.</span></span>  
  
 <span data-ttu-id="e8b77-131">![Dlaždice 5](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")</span><span class="sxs-lookup"><span data-stu-id="e8b77-131">![Tile 5](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="e8b77-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8b77-132">See Also</span></span>  
 [<span data-ttu-id="e8b77-133">Použití štětce k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="e8b77-133">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
