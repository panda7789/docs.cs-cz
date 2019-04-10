---
title: 'Postupy: Ověření pozice objektu Geometry ve vizuálním objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: 87b626e575d889447ef061d1ed62ef28efe5dfeb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227337"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a>Postupy: Ověření pozice objektu Geometry ve vizuálním objektu
Tento příklad ukazuje, jak provádět ověření pozice ve vizuální objekt, který se skládá z jedné nebo více <xref:System.Windows.Media.Geometry> objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst <xref:System.Windows.Media.DrawingGroup> z visual objektu, který používá <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metody. Ověření pozice je pak provede na vykreslovaný obsah každého kreslení <xref:System.Windows.Media.DrawingGroup> k určení, které geometrie bylo dosaženo.  
  
> [!NOTE]
>  Ve většině případů byste použili <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodou ke zjištění, zda bod protíná některý vykreslený obsah vizuálu.  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <xref:System.Windows.Media.Geometry.FillContains%2A> Je metoda přetížená metoda, která umožňuje spuštění testu s použitím zadaného <xref:System.Windows.Point> nebo <xref:System.Windows.Media.Geometry>. Pokud je vytažený geometrii, protože byl zdvih můžete rozšířit mimo hranice výplně. V takovém případě můžete chtít volat <xref:System.Windows.Media.Geometry.StrokeContains%2A> kromě <xref:System.Windows.Media.Geometry.FillContains%2A>.  
  
 Můžete také zadat <xref:System.Windows.Media.ToleranceType> , který se používá pro účely sloučení Bézierovy křivky.  
  
> [!NOTE]
>  Tato ukázka není vezměte v úvahu všechny transformace nebo oříznutí, který může použít pro geometrii. Kromě toho tato ukázka nebude fungovat u upravený ovládací prvek, protože nemá žádné kreslení přímo s ním spojená.  
  
## <a name="see-also"></a>Viz také:

- [Spuštění testování ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
- [Ověřování pozice pomocí objektu Geometry jako parametru](how-to-hit-test-using-geometry-as-a-parameter.md)
