---
title: 'Postupy: Vykreslení zavřeného tvaru použitím mnohoúhelníku'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 4105139e159783cf0197f4e56c82001835077cbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559458"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>Postupy: Vykreslení zavřeného tvaru použitím mnohoúhelníku
Tento příklad ukazuje, jak k vykreslení uzavřený obrazec pomocí <xref:System.Windows.Shapes.Polygon> elementu. Kreslení uzavřený obrazec, vytvoření <xref:System.Windows.Shapes.Polygon> elementu a použít jeho <xref:System.Windows.Shapes.Polygon.Points%2A> vlastnosti k určení vrcholy obrazce. Řádek automaticky vykreslením, který se připojuje první a poslední bod. Nakonec zadejte <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>, nebo obojí.  
  
## <a name="example"></a>Příklad  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], platná syntaxe pro body je mezerami oddělený seznam párů textový soubor s oddělovači x - a -souřadnici y.  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 I když tento příklad používá <xref:System.Windows.Controls.Canvas> tak, aby obsahovala polygonů, můžete použít elementy mnohoúhelníku (a všechny ostatní elementy obrazce) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> bez textového obsahu, která podporuje.  
  
 Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).
