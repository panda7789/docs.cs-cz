---
title: 'Postup: Použití výkresu u 3D modelu'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3D models
- 3D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 5b10630ab674fa9489cdf7ad53516a680f19da08
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112177"
---
# <a name="how-to-apply-a-drawing-to-a-3d-model"></a>Postup: Použití výkresu u 3D modelu

Tento příklad ukazuje, <xref:System.Windows.Media.DrawingBrush> jak <xref:System.Windows.Media.Media3D.Material> použít jako aplikovaný na 3D model.

Následující kód definuje <xref:System.Windows.Media.DrawingGroup> jako obsah <xref:System.Windows.Media.DrawingBrush>.  Je <xref:System.Windows.Media.DrawingBrush> nastavena <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> jako vlastnost <xref:System.Windows.Media.Media3D.DiffuseMaterial> aplikované na 3D rovinu.

> [!NOTE]
> Často je žádoucí definovat složité objekty a hodnoty, jako je výkres níže jako prostředky, které lze znovu použít a zjednodušit kód. Další informace naleznete v [tématu XAML Resources.](../../../desktop-wpf/fundamentals/xaml-resources-define.md)

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>Příklad

Následující kód ukazuje celý vzorek.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>Viz také

- [Prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Vytvoření 3D scény](how-to-create-a-3-d-scene.md)
- [Přehled vykreslovaných objektů](drawing-objects-overview.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
