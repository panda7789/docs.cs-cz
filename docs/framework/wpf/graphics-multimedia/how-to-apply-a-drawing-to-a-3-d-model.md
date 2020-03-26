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
# <a name="how-to-apply-a-drawing-to-a-3d-model"></a><span data-ttu-id="3782b-102">Postup: Použití výkresu u 3D modelu</span><span class="sxs-lookup"><span data-stu-id="3782b-102">How to: Apply a Drawing to a 3D Model</span></span>

<span data-ttu-id="3782b-103">Tento příklad ukazuje, <xref:System.Windows.Media.DrawingBrush> jak <xref:System.Windows.Media.Media3D.Material> použít jako aplikovaný na 3D model.</span><span class="sxs-lookup"><span data-stu-id="3782b-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3D model.</span></span>

<span data-ttu-id="3782b-104">Následující kód definuje <xref:System.Windows.Media.DrawingGroup> jako obsah <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="3782b-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="3782b-105">Je <xref:System.Windows.Media.DrawingBrush> nastavena <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> jako vlastnost <xref:System.Windows.Media.Media3D.DiffuseMaterial> aplikované na 3D rovinu.</span><span class="sxs-lookup"><span data-stu-id="3782b-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="3782b-106">Často je žádoucí definovat složité objekty a hodnoty, jako je výkres níže jako prostředky, které lze znovu použít a zjednodušit kód.</span><span class="sxs-lookup"><span data-stu-id="3782b-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="3782b-107">Další informace naleznete v [tématu XAML Resources.](../../../desktop-wpf/fundamentals/xaml-resources-define.md)</span><span class="sxs-lookup"><span data-stu-id="3782b-107">See [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="3782b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="3782b-108">Example</span></span>

<span data-ttu-id="3782b-109">Následující kód ukazuje celý vzorek.</span><span class="sxs-lookup"><span data-stu-id="3782b-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="3782b-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="3782b-110">See also</span></span>

- [<span data-ttu-id="3782b-111">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="3782b-111">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="3782b-112">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="3782b-112">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="3782b-113">Přehled vykreslovaných objektů</span><span class="sxs-lookup"><span data-stu-id="3782b-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="3782b-114">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="3782b-114">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
