---
title: 'Postupy: Použití kresby na 3D model'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: a20b89a7359fc85d9790ac02dd2b173452df8c22
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699093"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="54ec1-102">Postupy: Použití kresby na 3D model</span><span class="sxs-lookup"><span data-stu-id="54ec1-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="54ec1-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.DrawingBrush> jako <xref:System.Windows.Media.Media3D.Material> u [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.</span><span class="sxs-lookup"><span data-stu-id="54ec1-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="54ec1-104">Následující kód definuje <xref:System.Windows.Media.DrawingGroup> jako obsahu <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="54ec1-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="54ec1-105"><xref:System.Windows.Media.DrawingBrush> Je nastaven jako <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> vlastnost <xref:System.Windows.Media.Media3D.DiffuseMaterial> u [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] roviny.</span><span class="sxs-lookup"><span data-stu-id="54ec1-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plane.</span></span>  
  
 <span data-ttu-id="54ec1-106">**Poznámka:** Často je třeba definovat složité objekty a hodnoty, jako je vykreslování níže jako prostředky, které je možné využít znovu a zjednodušit kód.</span><span class="sxs-lookup"><span data-stu-id="54ec1-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="54ec1-107">Zobrazit [prostředky XAML](../advanced/xaml-resources.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="54ec1-107">See [XAML Resources](../advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="54ec1-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="54ec1-108">Example</span></span>  
 <span data-ttu-id="54ec1-109">Následující kód ukazuje celý vzorku.</span><span class="sxs-lookup"><span data-stu-id="54ec1-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="54ec1-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54ec1-110">See also</span></span>

- [<span data-ttu-id="54ec1-111">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="54ec1-111">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="54ec1-112">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="54ec1-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="54ec1-113">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="54ec1-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="54ec1-114">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="54ec1-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
