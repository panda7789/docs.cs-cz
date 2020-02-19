---
title: 'Postupy: Změna CAP na konci čáry nebo segmentu'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 5f755d7b4d1682755ea461121f91c0666d450ad1
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452776"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Postupy: Změna CAP na konci čáry nebo segmentu
Tento příklad ukazuje, jak změnit tvar na začátku nebo konci elementu Open <xref:System.Windows.Shapes.Shape>. Chcete-li změnit zakončení na začátku otevřeného <xref:System.Windows.Shapes.Shape>, použijte jeho vlastnost <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>. Chcete-li změnit zakončení na konci otevřeného <xref:System.Windows.Shapes.Shape>, použijte jeho vlastnost <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>. Chcete-li zobrazit dostupná zakončení řádků, přečtěte si <xref:System.Windows.Media.PenLineCap> výčtu.  
  
> [!NOTE]
> Tato vlastnost má vliv pouze na otevřený tvar, například <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Polyline>nebo element Open <xref:System.Windows.Shapes.Path>.  
  
 Následující příklad kreslí čtyři prvky <xref:System.Windows.Shapes.Polyline> a používá jinou sadu tvarů na koncích každého.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
