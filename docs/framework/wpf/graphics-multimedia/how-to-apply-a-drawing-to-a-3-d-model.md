---
title: "Postupy: Použití kresby na 3D model"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a44607498c6870a598122f41bf2b7ddc5968c61d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Postupy: Použití kresby na 3D model
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.DrawingBrush> jako <xref:System.Windows.Media.Media3D.Material> u [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.  
  
 Následující kód definuje <xref:System.Windows.Media.DrawingGroup> jako obsah <xref:System.Windows.Media.DrawingBrush>.  <xref:System.Windows.Media.DrawingBrush> Je nastaven jako <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> vlastnost <xref:System.Windows.Media.Media3D.DiffuseMaterial> u [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] roviny.  
  
 **Poznámka:** je často žádoucí, můžete definovat na komplexní objekty a hodnoty jako kreslení níže jako prostředky, které lze znovu použít a zjednodušit kódu. V tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md) Další informace.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celé ukázce.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Vytvoření 3D scény](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
