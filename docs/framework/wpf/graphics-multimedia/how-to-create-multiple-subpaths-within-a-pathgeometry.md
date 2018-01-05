---
title: "Postupy: Vytváření několika dílčích cest v rámci PathGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7945728386c01d6137cbc422f0d7fb410a18d57e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a><span data-ttu-id="e8f75-102">Postupy: Vytváření několika dílčích cest v rámci PathGeometry</span><span class="sxs-lookup"><span data-stu-id="e8f75-102">How to: Create Multiple Subpaths Within a PathGeometry</span></span>
<span data-ttu-id="e8f75-103">Tento příklad ukazuje, jak vytvořit více dílčích cest v <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e8f75-103">This example shows how to create multiple subpaths in a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="e8f75-104">Pokud chcete vytvořit několik dílčích cest, vytvoříte <xref:System.Windows.Media.PathFigure> pro každý dílčí cestou.</span><span class="sxs-lookup"><span data-stu-id="e8f75-104">To create multiple subpaths, you create a <xref:System.Windows.Media.PathFigure> for each subpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8f75-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8f75-105">Example</span></span>  
 <span data-ttu-id="e8f75-106">Následující příklad vytvoří dvě dílčí cesty, každé z nich trojúhelník.</span><span class="sxs-lookup"><span data-stu-id="e8f75-106">The following example creates two subpaths, each one a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 <span data-ttu-id="e8f75-107">Následující příklad ukazuje, jak vytvořit více dílčích cest pomocí <xref:System.Windows.Shapes.Path> a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atribut syntaxe.</span><span class="sxs-lookup"><span data-stu-id="e8f75-107">The following example shows how to create multiple subpaths by using a <xref:System.Windows.Shapes.Path> and [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax.</span></span> <span data-ttu-id="e8f75-108">Každý `M` tak, aby v příkladu se vytvoří dvě dílčí cesty, že každý kreslení trojúhelník vytvoří nový dílčí cestou.</span><span class="sxs-lookup"><span data-stu-id="e8f75-108">Each `M` creates a new subpath so that the example creates two subpaths that each draw a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 <span data-ttu-id="e8f75-109">(Všimněte si, že tento atribut syntaxe ve skutečnosti vytvoří <xref:System.Windows.Media.StreamGeometry>, světlejšího váhy verzi <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e8f75-109">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="e8f75-110">Další informace najdete v tématu [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) stránky.)</span><span class="sxs-lookup"><span data-stu-id="e8f75-110">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f75-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8f75-111">See Also</span></span>  
 [<span data-ttu-id="e8f75-112">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="e8f75-112">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
