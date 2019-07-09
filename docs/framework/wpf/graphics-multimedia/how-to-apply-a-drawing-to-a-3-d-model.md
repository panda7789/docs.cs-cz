---
title: 'Postupy: Použití kresby na 3D model'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 8ac24fdf8d7e407e10764c17fcc12121aa5f51d7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662815"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Postupy: Použití kresby na 3D model
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.DrawingBrush> jako <xref:System.Windows.Media.Media3D.Material> použít na 3D model.  
  
 Následující kód definuje <xref:System.Windows.Media.DrawingGroup> jako obsahu <xref:System.Windows.Media.DrawingBrush>.  <xref:System.Windows.Media.DrawingBrush> Je nastaven jako <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> vlastnost <xref:System.Windows.Media.Media3D.DiffuseMaterial> použít na 3D ploše.  
  
 **Poznámka:** Často je třeba definovat složité objekty a hodnoty, jako je vykreslování níže jako prostředky, které je možné využít znovu a zjednodušit kód. Zobrazit [prostředky XAML](../advanced/xaml-resources.md) Další informace.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celý vzorku.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:

- [Prostředky XAML](../advanced/xaml-resources.md)
- [Vytvoření 3D scény](how-to-create-a-3-d-scene.md)
- [Přehled nakreslených objektů](drawing-objects-overview.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
