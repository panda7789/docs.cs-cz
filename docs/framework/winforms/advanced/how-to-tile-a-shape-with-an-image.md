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
ms.openlocfilehash: a906db44a548361df2822efa24d1dd1849cb5a24
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063741"
---
# <a name="how-to-tile-a-shape-with-an-image"></a><span data-ttu-id="9a5bd-102">Postupy: Dlaždicové vyplnění obrazce pomocí obrázku</span><span class="sxs-lookup"><span data-stu-id="9a5bd-102">How to: Tile a Shape with an Image</span></span>
<span data-ttu-id="9a5bd-103">Stejně jako dlaždice mohou být umístěny vedle sebe k pokrytí a podlaží, obdélníkové imagí umístěny vedle sebe na hodnotu fill (dlaždice) tvaru.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-103">Just as tiles can be placed next to each other to cover a floor, rectangular images can be placed next to each other to fill (tile) a shape.</span></span> <span data-ttu-id="9a5bd-104">Na dlaždici vnitřní část obrazce pomocí textury štětce.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-104">To tile the interior of a shape, use a texture brush.</span></span> <span data-ttu-id="9a5bd-105">Při sestavování <xref:System.Drawing.TextureBrush> objekt, jeden z argumentů předat konstruktoru je <xref:System.Drawing.Image> objektu.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-105">When you construct a <xref:System.Drawing.TextureBrush> object, one of the arguments you pass to the constructor is an <xref:System.Drawing.Image> object.</span></span> <span data-ttu-id="9a5bd-106">Když Vymalovat vnitřní část obrazce pomocí textury štětce, tvar je vyplněn opakovaného kopírování tohoto obrázku.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-106">When you use the texture brush to paint the interior of a shape, the shape is filled with repeated copies of this image.</span></span>  
  
 <span data-ttu-id="9a5bd-107">Vlastnost režim zalamování řádků <xref:System.Drawing.TextureBrush> objekt určuje, jak je na obrázku orientovaný jako se opakuje obdélníkové mřížky.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-107">The wrap mode property of the <xref:System.Drawing.TextureBrush> object determines how the image is oriented as it is repeated in a rectangular grid.</span></span> <span data-ttu-id="9a5bd-108">Zkontrolujte všechny dlaždice v mřížce mají stejnou orientaci nebo můžete vytvořit image Převrátit na ose z jedné mřížce pozice na další.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-108">You can make all the tiles in the grid have the same orientation, or you can make the image flip from one grid position to the next.</span></span> <span data-ttu-id="9a5bd-109">Překlopení může být vodorovné, svislé nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-109">The flipping can be horizontal, vertical, or both.</span></span> <span data-ttu-id="9a5bd-110">Následující příklady ukazují dělení do bloků s různými typy překlopení.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-110">The following examples demonstrate tiling with different types of flipping.</span></span>  
  
### <a name="to-tile-an-image"></a><span data-ttu-id="9a5bd-111">Na dlaždici bitovou kopii</span><span class="sxs-lookup"><span data-stu-id="9a5bd-111">To tile an image</span></span>  
  
- <span data-ttu-id="9a5bd-112">Tento příklad používá na dlaždici 200 x 200 obdélníku na následujícím obrázku 75 × 75.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-112">This example uses the following 75×75 image to tile a 200×200 rectangle.</span></span>  
  
 ![Dlaždice obrázku, který se zobrazí červený house a stromu.](./media/how-to-tile-a-shape-with-an-image/rectangle-tile-200x200.gif)  
  
- <span data-ttu-id="9a5bd-114">Následující obrázek znázorňuje, jak je obdélník tiled v obrázku.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-114">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="9a5bd-115">Všimněte si, že všechny dlaždice mají stejnou orientaci; neexistuje žádné překlopení.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-115">Note that all tiles have the same orientation; there is no flipping.</span></span>  
  
 ![Obdélník tiled image pomocí stejné orientace pro všemi dlaždicemi.](./media/how-to-tile-a-shape-with-an-image/rectangle-tiled-image-no-flip.gif)  
  
 [!code-csharp[System.Drawing.UsingABrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a><span data-ttu-id="9a5bd-117">Chcete-li Převrátit obrázek vodorovně při dělení do bloků</span><span class="sxs-lookup"><span data-stu-id="9a5bd-117">To flip an image horizontally while tiling</span></span>  
  
- <span data-ttu-id="9a5bd-118">Tento příklad používá stejnou bitovou kopii 75 × 75 tak, aby vyplnil 200 x 200 obdélník.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-118">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="9a5bd-119">Režim zalamování nastavena na Převrátit obrázek vodorovně.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-119">The wrap mode is set to flip the image horizontally.</span></span> <span data-ttu-id="9a5bd-120">Následující obrázek znázorňuje, jak je obdélník tiled v obrázku.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-120">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="9a5bd-121">Všimněte si, že při přesunu z jedné dlaždice na další na daném řádku, je obrázek vodorovně obráceně.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-121">Note that as you move from one tile to the next in a given row, the image is flipped horizontally.</span></span>  
  
 ![Obdélník vedle sebe s imagí obráceně vodorovně.](./media/how-to-tile-a-shape-with-an-image/rectangle-tiled-image-horizontal-flip.gif)  
  
 [!code-csharp[System.Drawing.UsingABrush#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a><span data-ttu-id="9a5bd-123">Chcete-li Převrátit obrázek svisle při dělení do bloků</span><span class="sxs-lookup"><span data-stu-id="9a5bd-123">To flip an image vertically while tiling</span></span>  
  
- <span data-ttu-id="9a5bd-124">Tento příklad používá stejnou bitovou kopii 75 × 75 tak, aby vyplnil 200 x 200 obdélník.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-124">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="9a5bd-125">Režim zalamování nastavena na Převrátit obrázek svisle.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-125">The wrap mode is set to flip the image vertically.</span></span>  
  
     [!code-csharp[System.Drawing.UsingABrush#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a><span data-ttu-id="9a5bd-126">Chcete-li Převrátit obrázek vodorovně a svisle při dělení do bloků</span><span class="sxs-lookup"><span data-stu-id="9a5bd-126">To flip an image horizontally and vertically while tiling</span></span>  
  
- <span data-ttu-id="9a5bd-127">Tento příklad používá stejnou bitovou kopii 75 × 75 na dlaždici 200 x 200 obdélník.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-127">This example uses the same 75×75 image to tile a 200×200 rectangle.</span></span> <span data-ttu-id="9a5bd-128">Režim zalamování nastavena na Převrátit obrázek vodorovně i svisle.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-128">The wrap mode is set to flip the image both horizontally and vertically.</span></span> <span data-ttu-id="9a5bd-129">Následující obrázek znázorňuje, jak je obdélník rozložen formou dlaždic imagí.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-129">The following illustration shows how the rectangle is tiled by the image.</span></span> <span data-ttu-id="9a5bd-130">Všimněte si, že při přesunu z jedné dlaždice na další na daném řádku, je obrázek vodorovně překlopení a při přesunu z jedné dlaždice na další v daném sloupci, obrázek svisle obráceně.</span><span class="sxs-lookup"><span data-stu-id="9a5bd-130">Note that as you move from one tile to the next in a given row, the image is flipped horizontally, and as you move from one tile to the next in a given column, the image is flipped vertically.</span></span>  
  
 ![Obdélník s použitím image obráceně vodorovně a svisle vedle sebe.](./media/how-to-tile-a-shape-with-an-image/rectangle-tiled-image-horizontal-vertical-flip.gif)  
  
 [!code-csharp[System.Drawing.UsingABrush#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="9a5bd-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a5bd-132">See also</span></span>

- [<span data-ttu-id="9a5bd-133">Použití štětce k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="9a5bd-133">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
