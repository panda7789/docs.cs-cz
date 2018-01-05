---
title: "Postupy: Vytvoření tvaru použitím PathGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 784a8df792ca4dc05e36f5b7e9ec93b02e0e639f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a>Postupy: Vytvoření tvaru použitím PathGeometry
Tento příklad ukazuje, jak vytvořit obrazce pomocí <xref:System.Windows.Media.PathGeometry> třídy. <xref:System.Windows.Media.PathGeometry>objekty, které se skládají z jedné nebo více <xref:System.Windows.Media.PathFigure> objekty; každá <xref:System.Windows.Media.PathFigure> představuje různé "obrázek" nebo tvaru. Každý <xref:System.Windows.Media.PathFigure> se sám skládá z jednoho nebo více <xref:System.Windows.Media.PathSegment> objekty, každý představuje připojené část obrázku nebo tvaru. Segment typy <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, a <xref:System.Windows.Media.BezierSegment>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.PathGeometry> vytvořit trojúhelník. <xref:System.Windows.Media.PathGeometry> Se zobrazí pomocí <xref:System.Windows.Shapes.Path> elementu.  
  
 [!code-xaml[GeometrySample#49](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 Následující obrázek znázorňuje tvar vytvořený v předchozím příkladu.  
  
 ![Objekt PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")  
Trojúhelník vytvořené pomocí Objekt PathGeometry  
  
 Předchozí příklad ukázal, jak vytvořit poměrně jednoduché obrazce trojúhelník. A <xref:System.Windows.Media.PathGeometry> lze také použít k vytvoření složitějších tvarů, včetně oblouky a křivek. Příklady najdete v tématu [vytvořit eliptické oblouk](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md), [vytvořit krychlový Bézierovu křivku](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md), a [vytvořit kvadratické Bézierovy křivky](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).  
  
 Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v článku [geometrie ukázka](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Ukázka geometrie](http://go.microsoft.com/fwlink/?LinkID=159989)
