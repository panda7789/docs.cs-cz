---
title: 'Postupy: Vyplnění oblasti kresbou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- drawings [WPF], painting with
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
ms.openlocfilehash: 6b204ae631912181333e2559ebadcdc37e7693b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010071"
---
# <a name="how-to-paint-an-area-with-a-drawing"></a><span data-ttu-id="40324-102">Postupy: Vyplnění oblasti kresbou</span><span class="sxs-lookup"><span data-stu-id="40324-102">How to: Paint an Area with a Drawing</span></span>
<span data-ttu-id="40324-103">Tento příklad ukazuje způsob vykreslení oblasti kresbou.</span><span class="sxs-lookup"><span data-stu-id="40324-103">This example shows how to paint an area with a drawing.</span></span> <span data-ttu-id="40324-104">Vykreslení oblasti kresbou, použijte <xref:System.Windows.Media.DrawingBrush> a jeden nebo více <xref:System.Windows.Media.Drawing> objekty.</span><span class="sxs-lookup"><span data-stu-id="40324-104">To paint an area with a drawing, you use a <xref:System.Windows.Media.DrawingBrush> and one or more <xref:System.Windows.Media.Drawing> objects.</span></span>   <span data-ttu-id="40324-105">Následující příklad používá <xref:System.Windows.Media.DrawingBrush> k vykreslení objektu kresbou dva tři tečky.</span><span class="sxs-lookup"><span data-stu-id="40324-105">The following example uses a <xref:System.Windows.Media.DrawingBrush> to paint an object with a drawing of two ellipses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40324-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="40324-106">Example</span></span>  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 <span data-ttu-id="40324-107">Následující obrázek znázorňuje výstup v příkladu.</span><span class="sxs-lookup"><span data-stu-id="40324-107">The following illustration shows the example's output.</span></span>  
  
 <span data-ttu-id="40324-108">![Výstup z DrawingBrush](./media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")</span><span class="sxs-lookup"><span data-stu-id="40324-108">![Output from a DrawingBrush](./media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")</span></span>  
  
 <span data-ttu-id="40324-109">(Středu tvaru je důvodů popsaného v bílé [řízení výplně složeného tvaru](how-to-control-the-fill-of-a-composite-shape.md).)</span><span class="sxs-lookup"><span data-stu-id="40324-109">(The center of the shape is white for reasons described in     [Control the Fill of a Composite Shape](how-to-control-the-fill-of-a-composite-shape.md).)</span></span>  
  
 <span data-ttu-id="40324-110">Nastavením <xref:System.Windows.Media.DrawingBrush> objektu <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnosti, můžete vytvořit s opakováním vzoru.</span><span class="sxs-lookup"><span data-stu-id="40324-110">By setting a <xref:System.Windows.Media.DrawingBrush> object's <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties, you can create a repeating pattern.</span></span> <span data-ttu-id="40324-111">V následujícím příkladu jsou vykreslovány objekt pomocí vzoru vytvořené z kresbu dva tři tečky.</span><span class="sxs-lookup"><span data-stu-id="40324-111">The following example paints an object with a pattern created from a drawing of two ellipses.</span></span>  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 <span data-ttu-id="40324-112">Následující obrázek znázorňuje rozdělovanou verzi <xref:System.Windows.Media.DrawingBrush> výstup.</span><span class="sxs-lookup"><span data-stu-id="40324-112">The following illustration shows the tiled <xref:System.Windows.Media.DrawingBrush> output.</span></span>  
  
 <span data-ttu-id="40324-113">![Vedle sebe výstup DrawingBrush](./media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")</span><span class="sxs-lookup"><span data-stu-id="40324-113">![Tiled output from a DrawingBrush](./media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")</span></span>  
  
 <span data-ttu-id="40324-114">Další informace o vykreslování štětce, naleznete v tématu [Malování pomocí obrázků, kreseb a vizuálních](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="40324-114">For more information about drawing brushes, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span> <span data-ttu-id="40324-115">Další informace o <xref:System.Windows.Media.Drawing> objekty, najdete [kreslení objekty – přehled](drawing-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="40324-115">For more information about <xref:System.Windows.Media.Drawing> objects, see the [Drawing Objects Overview](drawing-objects-overview.md).</span></span>
