---
title: 'Postupy: Animace EllipseGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], EllipseGeometry objects [WPF]
- EllipseGeometry objects [WPF], animating
- graphics [WPF], animation
ms.assetid: 767b9b6e-9cb7-482e-b6c2-fee7750c3995
ms.openlocfilehash: 0f8174a2144435c9ad65904ee587355e8b38e935
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126006"
---
# <a name="how-to-animate-an-ellipsegeometry"></a><span data-ttu-id="5a82f-102">Postupy: Animace EllipseGeometry</span><span class="sxs-lookup"><span data-stu-id="5a82f-102">How to: Animate an EllipseGeometry</span></span>
<span data-ttu-id="5a82f-103">Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.Geometry> v rámci <xref:System.Windows.Shapes.Path> elementu.</span><span class="sxs-lookup"><span data-stu-id="5a82f-103">This example shows how to animate a <xref:System.Windows.Media.Geometry> within a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="5a82f-104">V následujícím příkladu <xref:System.Windows.Media.Animation.PointAnimation> je použít pro animaci <xref:System.Windows.Media.EllipseGeometry.Center%2A> ze <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="5a82f-104">In the following example, a <xref:System.Windows.Media.Animation.PointAnimation> is used to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> of an <xref:System.Windows.Media.EllipseGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a82f-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a82f-105">Example</span></span>  
 [!code-xaml[animatepath_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/animatepath_snip_XAML/CS/EllipseGeometryExample.xaml#1)]  
  
 [!code-csharp[animatepath_snip#101](~/samples/snippets/csharp/VS_Snippets_Wpf/animatepath_snip/CSharp/EllipseGeometryExample.cs#101)]  
  
 [!code-vb[animatepath_snip#201](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animatepath_snip/VisualBasic/EllipseGeometryExample.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="5a82f-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a82f-106">See also</span></span>

- [<span data-ttu-id="5a82f-107">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="5a82f-107">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="5a82f-108">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="5a82f-108">Geometry Overview</span></span>](geometry-overview.md)
