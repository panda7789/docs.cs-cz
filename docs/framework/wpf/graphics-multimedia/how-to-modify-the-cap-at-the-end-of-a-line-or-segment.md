---
title: "Postupy: Změna CAP na konci čáry nebo segmentu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d2cd55de403b766344749259068ccd313558f89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
