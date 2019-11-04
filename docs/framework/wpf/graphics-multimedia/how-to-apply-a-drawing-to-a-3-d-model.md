---
title: 'Postupy: Použití kresby na 3D model'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 311a3ac1d9fa219a3a365d506d9d0c3e8b6bc229
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459366"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Postupy: Použití kresby na 3D model

Tento příklad ukazuje, jak použít <xref:System.Windows.Media.DrawingBrush> jako <xref:System.Windows.Media.Media3D.Material> použití na 3D model.

Následující kód definuje <xref:System.Windows.Media.DrawingGroup> jako obsah <xref:System.Windows.Media.DrawingBrush>.  <xref:System.Windows.Media.DrawingBrush> se nastaví jako vlastnost <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> <xref:System.Windows.Media.Media3D.DiffuseMaterial> aplikovaná na 3D plochu.

> [!NOTE]
> Často je žádoucí definovat komplexní objekty a hodnoty, jako je vykreslování níže, jako prostředky, které se dají znovu použít a zjednodušit váš kód. Další informace najdete v tématu [prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) .

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>Příklad

Následující kód ukazuje celou ukázku.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>Viz také:

- [Prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Vytvoření 3D scény](how-to-create-a-3-d-scene.md)
- [Přehled nakreslených objektů](drawing-objects-overview.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
