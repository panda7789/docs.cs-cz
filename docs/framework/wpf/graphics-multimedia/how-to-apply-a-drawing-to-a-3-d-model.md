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
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="38b4f-102">Postupy: Použití kresby na 3D model</span><span class="sxs-lookup"><span data-stu-id="38b4f-102">How to: Apply a Drawing to a 3-D Model</span></span>

<span data-ttu-id="38b4f-103">Tento příklad ukazuje, jak použít <xref:System.Windows.Media.DrawingBrush> jako <xref:System.Windows.Media.Media3D.Material> použití na 3D model.</span><span class="sxs-lookup"><span data-stu-id="38b4f-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>

<span data-ttu-id="38b4f-104">Následující kód definuje <xref:System.Windows.Media.DrawingGroup> jako obsah <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="38b4f-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="38b4f-105"><xref:System.Windows.Media.DrawingBrush> se nastaví jako vlastnost <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> <xref:System.Windows.Media.Media3D.DiffuseMaterial> aplikovaná na 3D plochu.</span><span class="sxs-lookup"><span data-stu-id="38b4f-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="38b4f-106">Často je žádoucí definovat komplexní objekty a hodnoty, jako je vykreslování níže, jako prostředky, které se dají znovu použít a zjednodušit váš kód.</span><span class="sxs-lookup"><span data-stu-id="38b4f-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="38b4f-107">Další informace najdete v tématu [prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) .</span><span class="sxs-lookup"><span data-stu-id="38b4f-107">See [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="38b4f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="38b4f-108">Example</span></span>

<span data-ttu-id="38b4f-109">Následující kód ukazuje celou ukázku.</span><span class="sxs-lookup"><span data-stu-id="38b4f-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="38b4f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38b4f-110">See also</span></span>

- [<span data-ttu-id="38b4f-111">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="38b4f-111">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="38b4f-112">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="38b4f-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="38b4f-113">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="38b4f-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="38b4f-114">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="38b4f-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
