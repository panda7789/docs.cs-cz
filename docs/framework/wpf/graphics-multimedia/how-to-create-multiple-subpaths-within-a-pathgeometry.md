---
title: 'Postupy: Vytvoření několika dílčích cest v rámci PathGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: d7b3d24f8d947d342a2af5484a6620c8379ac664
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638350"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a>Postupy: Vytvoření několika dílčích cest v rámci PathGeometry
Tento příklad ukazuje postup vytvoření několika dílčích cest v <xref:System.Windows.Media.PathGeometry>. K vytvoření několika dílčích cest, můžete vytvořit <xref:System.Windows.Media.PathFigure> pro každý dílčí cestou.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dvě dílčí cesty, každý z nich trojúhelník.  
  
 [!code-xaml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 Následující příklad ukazuje postup vytvoření několika dílčích cest pomocí <xref:System.Windows.Shapes.Path> a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe atributu. Každý `M` tak, aby tento příklad vytvoří dvě dílčí cesty, že každý nakreslit trojúhelník vytvoří novou cestou.  
  
 [!code-xaml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 (Všimněte si, že tato syntaxe atributu ve skutečnosti vytváří <xref:System.Windows.Media.StreamGeometry>, nenáročný verzi <xref:System.Windows.Media.PathGeometry>. Další informace najdete v tématu [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) stránky.)  
  
## <a name="see-also"></a>Viz také:
- [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
