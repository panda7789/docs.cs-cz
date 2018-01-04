---
title: "Postupy: Vytvoření složeného tvaru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ecb4ecdc5c83cbb6f2b4faee9cb3654939bd346
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-composite-shape"></a>Postupy: Vytvoření složeného tvaru
Tento příklad ukazuje postup vytvoření složeného obrazců pomocí <xref:System.Windows.Media.Geometry> objekty a jejich zobrazení pomocí <xref:System.Windows.Shapes.Path> elementu. V následujícím příkladu <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>a <xref:System.Windows.Media.RectangleGeometry> se používají s <xref:System.Windows.Media.GeometryGroup> vytvořte kompozitních tvaru. Geometrie jsou pak vykreslovány pomocí <xref:System.Windows.Shapes.Path> elementu.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 Následující obrázek znázorňuje tvar vytvořený v předchozím příkladu.  
  
 ![Kombinovaná geometrie vytvořený objekt GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
Složené geometrie  
  
 Složitější tvary, například mnohoúhelníky a obrazců pomocí zakřivené segmenty, může být vytvořený <xref:System.Windows.Media.PathGeometry>. Příklad způsobu vytvoření obrazce pomocí <xref:System.Windows.Media.PathGeometry>, najdete v části [vytvořit obrazce pomocí Objekt PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  I když v tomto příkladu vykreslí obrazce pomocí obrazovky <xref:System.Windows.Shapes.Path> elementu <xref:System.Windows.Media.Geometry> objekty může taky sloužit k popisu obsahu <xref:System.Windows.Media.GeometryDrawing> nebo <xref:System.Windows.Media.DrawingContext>. Může být rovněž používají pro výstřižek a stiskněte klávesu testování.  
  
 Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v článku [geometrie ukázka](http://go.microsoft.com/fwlink/?LinkID=159989).
