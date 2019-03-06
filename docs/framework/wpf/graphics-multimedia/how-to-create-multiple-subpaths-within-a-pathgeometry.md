---
title: 'Postupy: Vytvoření několika dílčích cest v rámci PathGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 0b57d0441c1aa9d5972af1f1c6b989aacba7f87f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353362"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a><span data-ttu-id="f94e9-102">Postupy: Vytvoření několika dílčích cest v rámci PathGeometry</span><span class="sxs-lookup"><span data-stu-id="f94e9-102">How to: Create Multiple Subpaths Within a PathGeometry</span></span>
<span data-ttu-id="f94e9-103">Tento příklad ukazuje postup vytvoření několika dílčích cest v <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="f94e9-103">This example shows how to create multiple subpaths in a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="f94e9-104">K vytvoření několika dílčích cest, můžete vytvořit <xref:System.Windows.Media.PathFigure> pro každý dílčí cestou.</span><span class="sxs-lookup"><span data-stu-id="f94e9-104">To create multiple subpaths, you create a <xref:System.Windows.Media.PathFigure> for each subpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f94e9-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f94e9-105">Example</span></span>  
 <span data-ttu-id="f94e9-106">Následující příklad vytvoří dvě dílčí cesty, každý z nich trojúhelník.</span><span class="sxs-lookup"><span data-stu-id="f94e9-106">The following example creates two subpaths, each one a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#38](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 <span data-ttu-id="f94e9-107">Následující příklad ukazuje postup vytvoření několika dílčích cest pomocí <xref:System.Windows.Shapes.Path> a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="f94e9-107">The following example shows how to create multiple subpaths by using a <xref:System.Windows.Shapes.Path> and [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax.</span></span> <span data-ttu-id="f94e9-108">Každý `M` tak, aby tento příklad vytvoří dvě dílčí cesty, že každý nakreslit trojúhelník vytvoří novou cestou.</span><span class="sxs-lookup"><span data-stu-id="f94e9-108">Each `M` creates a new subpath so that the example creates two subpaths that each draw a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#58](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 <span data-ttu-id="f94e9-109">(Všimněte si, že tato syntaxe atributu ve skutečnosti vytváří <xref:System.Windows.Media.StreamGeometry>, nenáročný verzi <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="f94e9-109">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="f94e9-110">Další informace najdete v tématu [syntaxe značek cesty](path-markup-syntax.md) stránky.)</span><span class="sxs-lookup"><span data-stu-id="f94e9-110">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f94e9-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f94e9-111">See also</span></span>
- [<span data-ttu-id="f94e9-112">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="f94e9-112">Geometry Overview</span></span>](geometry-overview.md)
