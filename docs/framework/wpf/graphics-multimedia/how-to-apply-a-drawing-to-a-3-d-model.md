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
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="ae278-102">Postupy: Použití kresby na 3D model</span><span class="sxs-lookup"><span data-stu-id="ae278-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="ae278-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.DrawingBrush> jako <xref:System.Windows.Media.Media3D.Material> použít na 3D model.</span><span class="sxs-lookup"><span data-stu-id="ae278-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>  
  
 <span data-ttu-id="ae278-104">Následující kód definuje <xref:System.Windows.Media.DrawingGroup> jako obsahu <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="ae278-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="ae278-105"><xref:System.Windows.Media.DrawingBrush> Je nastaven jako <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> vlastnost <xref:System.Windows.Media.Media3D.DiffuseMaterial> použít na 3D ploše.</span><span class="sxs-lookup"><span data-stu-id="ae278-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>  
  
 <span data-ttu-id="ae278-106">**Poznámka:** Často je třeba definovat složité objekty a hodnoty, jako je vykreslování níže jako prostředky, které je možné využít znovu a zjednodušit kód.</span><span class="sxs-lookup"><span data-stu-id="ae278-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="ae278-107">Zobrazit [prostředky XAML](../advanced/xaml-resources.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="ae278-107">See [XAML Resources](../advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="ae278-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae278-108">Example</span></span>  
 <span data-ttu-id="ae278-109">Následující kód ukazuje celý vzorku.</span><span class="sxs-lookup"><span data-stu-id="ae278-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ae278-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae278-110">See also</span></span>

- [<span data-ttu-id="ae278-111">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="ae278-111">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="ae278-112">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="ae278-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="ae278-113">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="ae278-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="ae278-114">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="ae278-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
