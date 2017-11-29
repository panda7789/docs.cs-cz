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
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="449e2-102">Postupy: Použití kresby na 3D model</span><span class="sxs-lookup"><span data-stu-id="449e2-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="449e2-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Media.DrawingBrush> jako <xref:System.Windows.Media.Media3D.Material> u [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.</span><span class="sxs-lookup"><span data-stu-id="449e2-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="449e2-104">Následující kód definuje <xref:System.Windows.Media.DrawingGroup> jako obsah <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="449e2-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="449e2-105"><xref:System.Windows.Media.DrawingBrush> Je nastaven jako <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> vlastnost <xref:System.Windows.Media.Media3D.DiffuseMaterial> u [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] roviny.</span><span class="sxs-lookup"><span data-stu-id="449e2-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plane.</span></span>  
  
 <span data-ttu-id="449e2-106">**Poznámka:** je často žádoucí, můžete definovat na komplexní objekty a hodnoty jako kreslení níže jako prostředky, které lze znovu použít a zjednodušit kódu.</span><span class="sxs-lookup"><span data-stu-id="449e2-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="449e2-107">V tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="449e2-107">See [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="449e2-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="449e2-108">Example</span></span>  
 <span data-ttu-id="449e2-109">Následující kód ukazuje celé ukázce.</span><span class="sxs-lookup"><span data-stu-id="449e2-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="449e2-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="449e2-110">See Also</span></span>  
 [<span data-ttu-id="449e2-111">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="449e2-111">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="449e2-112">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="449e2-112">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="449e2-113">Kreslení objekty – přehled</span><span class="sxs-lookup"><span data-stu-id="449e2-113">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="449e2-114">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="449e2-114">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
