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
ms.openlocfilehash: ad7b8737a63028e533cadfa6db56b063eb943f22
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221535"
---
# <a name="how-to-tile-a-shape-with-an-image"></a><span data-ttu-id="45429-102">Postupy: Dlaždicové vyplnění obrazce pomocí obrázku</span><span class="sxs-lookup"><span data-stu-id="45429-102">How to: Tile a Shape with an Image</span></span>
<span data-ttu-id="45429-103">Stejně jako dlaždice mohou být umístěny vedle sebe k pokrytí a podlaží, obdélníkové imagí umístěny vedle sebe na hodnotu fill (dlaždice) tvaru.</span><span class="sxs-lookup"><span data-stu-id="45429-103">Just as tiles can be placed next to each other to cover a floor, rectangular images can be placed next to each other to fill (tile) a shape.</span></span> <span data-ttu-id="45429-104">Na dlaždici vnitřní část obrazce pomocí textury štětce.</span><span class="sxs-lookup"><span data-stu-id="45429-104">To tile the interior of a shape, use a texture brush.</span></span> <span data-ttu-id="45429-105">Při sestavování <xref:System.Drawing.TextureBrush> objekt, jeden z argumentů předat konstruktoru je <xref:System.Drawing.Image> objektu.</span><span class="sxs-lookup"><span data-stu-id="45429-105">When you construct a <xref:System.Drawing.TextureBrush> object, one of the arguments you pass to the constructor is an <xref:System.Drawing.Image> object.</span></span> <span data-ttu-id="45429-106">Když Vymalovat vnitřní část obrazce pomocí textury štětce, tvar je vyplněn opakovaného kopírování tohoto obrázku.</span><span class="sxs-lookup"><span data-stu-id="45429-106">When you use the texture brush to paint the interior of a shape, the shape is filled with repeated copies of this image.</span></span>  
  
 <span data-ttu-id="45429-107">Vlastnost režim zalamování řádků <xref:System.Drawing.TextureBrush> objekt určuje, jak je na obrázku orientovaný jako se opakuje obdélníkové mřížky.</span><span class="sxs-lookup"><span data-stu-id="45429-107">The wrap mode property of the <xref:System.Drawing.TextureBrush> object determines how the image is oriented as it is repeated in a rectangular grid.</span></span> <span data-ttu-id="45429-108">Zkontrolujte všechny dlaždice v mřížce mají stejnou orientaci nebo můžete vytvořit image Převrátit na ose z jedné mřížce pozice na další.</span><span class="sxs-lookup"><span data-stu-id="45429-108">You can make all the tiles in the grid have the same orientation, or you can make the image flip from one grid position to the next.</span></span> <span data-ttu-id="45429-109">Překlopení může být vodorovné, svislé nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="45429-109">The flipping can be horizontal, vertical, or both.</span></span> <span data-ttu-id="45429-110">Následující příklady ukazují dělení do bloků s různými typy překlopení.</span><span class="sxs-lookup"><span data-stu-id="45429-110">The following examples demonstrate tiling with different types of flipping.</span></span>  
  
### <a name="to-tile-an-image"></a><span data-ttu-id="45429-111">Na dlaždici bitovou kopii</span><span class="sxs-lookup"><span data-stu-id="45429-111">To tile an image</span></span>  
  
-   <span data-ttu-id="45429-112">Tento příklad používá na dlaždici 200 x 200 obdélníku na následujícím obrázku 75 × 75.</span><span class="sxs-lookup"><span data-stu-id="45429-112">This example uses the following 75×75 image to tile a 200×200 rectangle.</span></span>  
  
 <span data-ttu-id="45429-113">![Dlaždice 1](./media/tile1.gif "tile1")</span><span class="sxs-lookup"><span data-stu-id="45429-113">![Tile 1](./media/tile1.gif "tile1")</span></span>  
  
-   <span data-ttu-id="45429-114">Následující obrázek znázorňuje, jak je obdélník tiled v obrázku.</span><span class="sxs-lookup"><span data-stu-id="45429-114">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="45429-115">Všimněte si, že všechny dlaždice mají stejnou orientaci; neexistuje žádné překlopení.</span><span class="sxs-lookup"><span data-stu-id="45429-115">Note that all tiles have the same orientation; there is no flipping.</span></span>  
  
 <span data-ttu-id="45429-116">![Dlaždici 2](./media/tile2.gif "tile2")</span><span class="sxs-lookup"><span data-stu-id="45429-116">![Tile 2](./media/tile2.gif "tile2")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a><span data-ttu-id="45429-117">Chcete-li Převrátit obrázek vodorovně při dělení do bloků</span><span class="sxs-lookup"><span data-stu-id="45429-117">To flip an image horizontally while tiling</span></span>  
  
-   <span data-ttu-id="45429-118">Tento příklad používá stejnou bitovou kopii 75 × 75 tak, aby vyplnil 200 x 200 obdélník.</span><span class="sxs-lookup"><span data-stu-id="45429-118">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="45429-119">Režim zalamování nastavena na Převrátit obrázek vodorovně.</span><span class="sxs-lookup"><span data-stu-id="45429-119">The wrap mode is set to flip the image horizontally.</span></span> <span data-ttu-id="45429-120">Následující obrázek znázorňuje, jak je obdélník tiled v obrázku.</span><span class="sxs-lookup"><span data-stu-id="45429-120">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="45429-121">Všimněte si, že při přesunu z jedné dlaždice na další na daném řádku, je obrázek vodorovně obráceně.</span><span class="sxs-lookup"><span data-stu-id="45429-121">Note that as you move from one tile to the next in a given row, the image is flipped horizontally.</span></span>  
  
 <span data-ttu-id="45429-122">![Dlaždici 3](./media/tile3.gif "tile3")</span><span class="sxs-lookup"><span data-stu-id="45429-122">![Tile 3](./media/tile3.gif "tile3")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a><span data-ttu-id="45429-123">Chcete-li Převrátit obrázek svisle při dělení do bloků</span><span class="sxs-lookup"><span data-stu-id="45429-123">To flip an image vertically while tiling</span></span>  
  
-   <span data-ttu-id="45429-124">Tento příklad používá stejnou bitovou kopii 75 × 75 tak, aby vyplnil 200 x 200 obdélník.</span><span class="sxs-lookup"><span data-stu-id="45429-124">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="45429-125">Režim zalamování nastavena na Převrátit obrázek svisle.</span><span class="sxs-lookup"><span data-stu-id="45429-125">The wrap mode is set to flip the image vertically.</span></span>  
  
     [!code-csharp[System.Drawing.UsingABrush#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a><span data-ttu-id="45429-126">Chcete-li Převrátit obrázek vodorovně a svisle při dělení do bloků</span><span class="sxs-lookup"><span data-stu-id="45429-126">To flip an image horizontally and vertically while tiling</span></span>  
  
-   <span data-ttu-id="45429-127">Tento příklad používá stejnou bitovou kopii 75 × 75 na dlaždici 200 x 200 obdélník.</span><span class="sxs-lookup"><span data-stu-id="45429-127">This example uses the same 75×75 image to tile a 200×200 rectangle.</span></span> <span data-ttu-id="45429-128">Režim zalamování nastavena na Převrátit obrázek vodorovně i svisle.</span><span class="sxs-lookup"><span data-stu-id="45429-128">The wrap mode is set to flip the image both horizontally and vertically.</span></span> <span data-ttu-id="45429-129">Následující obrázek znázorňuje, jak je obdélník rozložen formou dlaždic imagí.</span><span class="sxs-lookup"><span data-stu-id="45429-129">The following illustration shows how the rectangle is tiled by the image.</span></span> <span data-ttu-id="45429-130">Všimněte si, že při přesunu z jedné dlaždice na další na daném řádku, je obrázek vodorovně překlopení a při přesunu z jedné dlaždice na další v daném sloupci, obrázek svisle obráceně.</span><span class="sxs-lookup"><span data-stu-id="45429-130">Note that as you move from one tile to the next in a given row, the image is flipped horizontally, and as you move from one tile to the next in a given column, the image is flipped vertically.</span></span>  
  
 <span data-ttu-id="45429-131">![Dlaždici 5](./media/tile5.gif "tile5")</span><span class="sxs-lookup"><span data-stu-id="45429-131">![Tile 5](./media/tile5.gif "tile5")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="45429-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45429-132">See also</span></span>

- [<span data-ttu-id="45429-133">Použití štětce k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="45429-133">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
