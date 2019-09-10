---
title: 'Postupy: Použití kresby na 3D model'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 14470d0adeb948ea46a0720b5713c20fb7d8e6d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855881"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Postupy: Použití kresby na 3D model

Tento příklad ukazuje, jak použít <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Media3D.Material> jako aplikovaný na 3D model.

Následující kód definuje <xref:System.Windows.Media.DrawingGroup> jako obsah <xref:System.Windows.Media.DrawingBrush>.  <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> Vlastnost je nastavena jako vlastnost <xref:System.Windows.Media.Media3D.DiffuseMaterial> použitá na 3D rovinu. <xref:System.Windows.Media.DrawingBrush>

> [!NOTE]
> Často je žádoucí definovat komplexní objekty a hodnoty, jako je vykreslování níže, jako prostředky, které se dají znovu použít a zjednodušit váš kód. Další informace najdete v tématu [prostředky XAML](../advanced/xaml-resources.md) .

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>Příklad

Následující kód ukazuje celou ukázku.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>Viz také:

- [Prostředky XAML](../advanced/xaml-resources.md)
- [Vytvoření 3D scény](how-to-create-a-3-d-scene.md)
- [Přehled nakreslených objektů](drawing-objects-overview.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
