---
title: 'Postupy: Vytváření několika dílčích cest v rámci PathGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 5b129b1bacb5dc2cba87376e8df70e115a5ebd72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559320"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a>Postupy: Vytváření několika dílčích cest v rámci PathGeometry
Tento příklad ukazuje, jak vytvořit více dílčích cest v <xref:System.Windows.Media.PathGeometry>. Pokud chcete vytvořit několik dílčích cest, vytvoříte <xref:System.Windows.Media.PathFigure> pro každý dílčí cestou.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dvě dílčí cesty, každé z nich trojúhelník.  
  
 [!code-xaml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 Následující příklad ukazuje, jak vytvořit více dílčích cest pomocí <xref:System.Windows.Shapes.Path> a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atribut syntaxe. Každý `M` tak, aby v příkladu se vytvoří dvě dílčí cesty, že každý kreslení trojúhelník vytvoří nový dílčí cestou.  
  
 [!code-xaml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 (Všimněte si, že tento atribut syntaxe ve skutečnosti vytvoří <xref:System.Windows.Media.StreamGeometry>, světlejšího váhy verzi <xref:System.Windows.Media.PathGeometry>. Další informace najdete v tématu [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) stránky.)  
  
## <a name="see-also"></a>Viz také  
 [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
