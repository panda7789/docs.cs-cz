---
title: 'Postupy: Změna CAP na konci čáry nebo segmentu'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: ba61b30b4ff575bb504f792f8990bbfc64a6c33e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371473"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Postupy: Změna CAP na konci čáry nebo segmentu
Tento příklad ukazuje, jak upravit obrazec na začátku nebo konci otevřenou <xref:System.Windows.Shapes.Shape> elementu. Změna cap na začátku otevřenou <xref:System.Windows.Shapes.Shape>, použijte jeho <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> vlastnost. Změna cap na konci otevřenou <xref:System.Windows.Shapes.Shape>, použijte jeho <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> vlastnost. Chcete-li zobrazit dostupné čar, najdete v článku <xref:System.Windows.Media.PenLineCap> výčtu.  
  
> [!NOTE]
>  Tato vlastnost ovlivňuje pouze otevřený tvar, například <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Polyline>, nebo otevřenou <xref:System.Windows.Shapes.Path> elementu.  
  
 Následující příklad nakreslí čtyři <xref:System.Windows.Shapes.Polyline> prvků a používá jinou sadu tvarů na koncích každého.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [ukázka prvky tvar](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
