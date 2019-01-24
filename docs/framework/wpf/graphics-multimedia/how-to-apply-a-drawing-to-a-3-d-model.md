---
title: 'Postupy: Použití kresby na 3D model'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 07811f8c0326827ed90484ce12632589b2f6fc82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611238"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Postupy: Použití kresby na 3D model
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.DrawingBrush> jako <xref:System.Windows.Media.Media3D.Material> u [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.  
  
 Následující kód definuje <xref:System.Windows.Media.DrawingGroup> jako obsahu <xref:System.Windows.Media.DrawingBrush>.  <xref:System.Windows.Media.DrawingBrush> Je nastaven jako <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> vlastnost <xref:System.Windows.Media.Media3D.DiffuseMaterial> u [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] roviny.  
  
 **Poznámka:** Často je třeba definovat složité objekty a hodnoty, jako je vykreslování níže jako prostředky, které je možné využít znovu a zjednodušit kód. Zobrazit [prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) Další informace.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celý vzorku.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:
- [Prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)
- [Vytvoření 3D scény](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [Přehled nakreslených objektů](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
