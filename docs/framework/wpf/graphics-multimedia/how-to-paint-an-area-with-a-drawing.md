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
# <a name="how-to-paint-an-area-with-a-drawing"></a>Postupy: Vyplnění oblasti kresbou
Tento příklad ukazuje způsob vykreslení oblasti kresbou. Vykreslení oblasti kresbou, použijte <xref:System.Windows.Media.DrawingBrush> a jeden nebo více <xref:System.Windows.Media.Drawing> objekty.   Následující příklad používá <xref:System.Windows.Media.DrawingBrush> k vykreslení objektu kresbou dva tři tečky.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 Následující obrázek znázorňuje výstup v příkladu.  
  
 ![Výstup z DrawingBrush](./media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")  
  
 (Středu tvaru je důvodů popsaného v bílé [řízení výplně složeného tvaru](how-to-control-the-fill-of-a-composite-shape.md).)  
  
 Nastavením <xref:System.Windows.Media.DrawingBrush> objektu <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnosti, můžete vytvořit s opakováním vzoru. V následujícím příkladu jsou vykreslovány objekt pomocí vzoru vytvořené z kresbu dva tři tečky.  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 Následující obrázek znázorňuje rozdělovanou verzi <xref:System.Windows.Media.DrawingBrush> výstup.  
  
 ![Vedle sebe výstup DrawingBrush](./media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")  
  
 Další informace o vykreslování štětce, naleznete v tématu [Malování pomocí obrázků, kreseb a vizuálních](painting-with-images-drawings-and-visuals.md). Další informace o <xref:System.Windows.Media.Drawing> objekty, najdete [kreslení objekty – přehled](drawing-objects-overview.md).
