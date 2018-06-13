---
title: 'Postupy: Vytvoření kombinované geometrie'
ms.date: 03/30/2017
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
ms.openlocfilehash: 107e0342b822633ccb4f51f256c121cc80c297f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561118"
---
# <a name="how-to-create-a-combined-geometry"></a>Postupy: Vytvoření kombinované geometrie
Tento příklad ukazuje, jak kombinovat geometrie. Spojí dva geometrie, použijte <xref:System.Windows.Media.CombinedGeometry> objektu. Nastavit jeho <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> vlastnosti s dvě geometrie kombinovat a nastavit <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> vlastnosti, která určuje, jak geometrie se spojí dohromady, k `Union`, `Intersect`, `Exclude`, nebo `Xor`.  
  
 K vytvoření složeného geometrie ze dvou nebo více geometrie, použijte <xref:System.Windows.Media.GeometryGroup>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Media.CombinedGeometry> je definovaná pomocí režim geometrie zkombinujte `Exclude`.  Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejné radius, ale s posunem centrech 50.  
  
 [!code-xaml[GeometrySample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 ![Výsledky vyřadit kombinování režimu](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")  
Kombinovaná geometrie vyloučení  
  
 V následující kód <xref:System.Windows.Media.CombinedGeometry> je definován s kombinační režim `Intersect`.  Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejné radius, ale s posunem centrech 50.  
  
 [!code-xaml[GeometrySample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 ![Výsledky Intersect kombinování režimu](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")  
Kombinovaná geometrie Intersect  
  
 V následující kód <xref:System.Windows.Media.CombinedGeometry> je definován s kombinační režim `Union`.  Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejné radius, ale s posunem centrech 50.  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Výsledky sjednocení kombinování režimu](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
Kombinovaná geometrie sjednocení  
  
 V následující kód <xref:System.Windows.Media.CombinedGeometry> je definován s kombinační režim `Xor`.  Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejné radius, ale s posunem centrech 50.  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Výsledky Xor kombinování režimu](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
Kombinovaná geometrie Xor
