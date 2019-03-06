---
title: 'Postupy: Vytvoření kombinované geometrie'
ms.date: 03/30/2017
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
ms.openlocfilehash: c5ebe87abd4c2cf70f8fa17f1fcc773293f3ad27
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364785"
---
# <a name="how-to-create-a-combined-geometry"></a>Postupy: Vytvoření kombinované geometrie
Tento příklad ukazuje způsob kombinování geometrií. Kombinování geometrií dvě, použijte <xref:System.Windows.Media.CombinedGeometry> objektu. Nastavte jeho <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> dvě geometrie sloučit, a nastavte vlastnosti <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> vlastnost, která určuje, jak geometrie se dá zkopírovat dohromady, k `Union`, `Intersect`, `Exclude`, nebo `Xor`.  
  
 K vytvoření geometrie složený ze dvou nebo více geometrie, použijte <xref:System.Windows.Media.GeometryGroup>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Media.CombinedGeometry> je definována s režim geometrie kombinování `Exclude`.  Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejného protokolu radius, ale s posunem centra 50.  
  
 [!code-xaml[GeometrySample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 ![Výsledky vyřadit kombinování režimu](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")  
Vyloučení kombinované geometrie  
  
 V následujícím kódu <xref:System.Windows.Media.CombinedGeometry> je definována s kombinování režimu `Intersect`.  Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejného protokolu radius, ale s posunem centra 50.  
  
 [!code-xaml[GeometrySample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 ![Výsledky Intersect kombinování režimu](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")  
Intersect kombinované geometrie  
  
 V následujícím kódu <xref:System.Windows.Media.CombinedGeometry> je definována s kombinování režimu `Union`.  Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejného protokolu radius, ale s posunem centra 50.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Výsledky sjednocení kombinování režimu](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
Sjednocení kombinované geometrie  
  
 V následujícím kódu <xref:System.Windows.Media.CombinedGeometry> je definována s kombinování režimu `Xor`.  Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejného protokolu radius, ale s posunem centra 50.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Výsledky Xor kombinování režimu](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
Xor kombinované geometrie
