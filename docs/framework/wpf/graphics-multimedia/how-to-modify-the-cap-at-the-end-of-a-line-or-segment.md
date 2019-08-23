---
title: 'Postupy: Změna zakončení na konci čáry nebo segmentu'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 53487417636dae8d855fe70b7b9255351a2dfb1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916136"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Postupy: Změna zakončení na konci čáry nebo segmentu
Tento příklad ukazuje, jak změnit tvar na začátku nebo konci otevřeného <xref:System.Windows.Shapes.Shape> elementu. Chcete-li změnit zakončení na začátku otevřeného <xref:System.Windows.Shapes.Shape>objektu, použijte <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> jeho vlastnost. Chcete-li změnit zakončení na konci otevřeného <xref:System.Windows.Shapes.Shape>objektu, použijte <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> jeho vlastnost. Chcete-li zobrazit dostupná zakončení řádků, <xref:System.Windows.Media.PenLineCap> Podívejte se na výčet.  
  
> [!NOTE]
> Tato vlastnost má vliv pouze na otevřený tvar, jako <xref:System.Windows.Shapes.Line>je <xref:System.Windows.Shapes.Polyline>,, nebo otevřený <xref:System.Windows.Shapes.Path> element.  
  
 Následující příklad kreslí čtyři <xref:System.Windows.Shapes.Polyline> prvky a používá jinou sadu tvarů na koncích každého.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
