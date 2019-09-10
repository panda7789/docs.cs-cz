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
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="6d769-102">Postupy: Použití kresby na 3D model</span><span class="sxs-lookup"><span data-stu-id="6d769-102">How to: Apply a Drawing to a 3-D Model</span></span>

<span data-ttu-id="6d769-103">Tento příklad ukazuje, jak použít <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Media3D.Material> jako aplikovaný na 3D model.</span><span class="sxs-lookup"><span data-stu-id="6d769-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>

<span data-ttu-id="6d769-104">Následující kód definuje <xref:System.Windows.Media.DrawingGroup> jako obsah <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="6d769-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="6d769-105"><xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> Vlastnost je nastavena jako vlastnost <xref:System.Windows.Media.Media3D.DiffuseMaterial> použitá na 3D rovinu. <xref:System.Windows.Media.DrawingBrush></span><span class="sxs-lookup"><span data-stu-id="6d769-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="6d769-106">Často je žádoucí definovat komplexní objekty a hodnoty, jako je vykreslování níže, jako prostředky, které se dají znovu použít a zjednodušit váš kód.</span><span class="sxs-lookup"><span data-stu-id="6d769-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="6d769-107">Další informace najdete v tématu [prostředky XAML](../advanced/xaml-resources.md) .</span><span class="sxs-lookup"><span data-stu-id="6d769-107">See [XAML Resources](../advanced/xaml-resources.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="6d769-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d769-108">Example</span></span>

<span data-ttu-id="6d769-109">Následující kód ukazuje celou ukázku.</span><span class="sxs-lookup"><span data-stu-id="6d769-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="6d769-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d769-110">See also</span></span>

- [<span data-ttu-id="6d769-111">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="6d769-111">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="6d769-112">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="6d769-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="6d769-113">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="6d769-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="6d769-114">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="6d769-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
