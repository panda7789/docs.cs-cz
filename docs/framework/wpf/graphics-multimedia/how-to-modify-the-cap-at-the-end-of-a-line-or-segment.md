---
title: 'Postupy: Změna CAP na konci čáry nebo segmentu'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: e69f461d426fc6a587263cea7a18478da53b5b09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559834"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Postupy: Změna CAP na konci čáry nebo segmentu
Tento příklad ukazuje, jak upravit tvaru na začátku nebo na konci otevřenou <xref:System.Windows.Shapes.Shape> elementu. Chcete-li změnit zakončení na začátku otevřenou <xref:System.Windows.Shapes.Shape>, použijte jeho <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> vlastnost. Chcete-li změnit zakončení na konci otevřenou <xref:System.Windows.Shapes.Shape>, použijte jeho <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> vlastnost. Chcete-li zobrazit dostupné čar, najdete v článku <xref:System.Windows.Media.PenLineCap> výčtu.  
  
> [!NOTE]
>  Tato vlastnost ovlivňuje pouze otevřený tvar, například <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Polyline>, nebo otevřenou <xref:System.Windows.Shapes.Path> elementu.  
  
 Následující příklad nevykresluje čtyři <xref:System.Windows.Shapes.Polyline> elementy a používá jinou sadu tvarů na koncích jednotlivých.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Media.PenLineCap>
