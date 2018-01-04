---
title: "Postupy: Vytvoření kvadratické Bézierovy křivky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cd349ae11a76acda81e44652ca5463b18e1dda8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a>Postupy: Vytvoření kvadratické Bézierovy křivky
Tento příklad ukazuje postup vytvoření kvadratické Bézierovy křivky.  Chcete-li vytvořit kvadratické Bézierovy křivky, použijte <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, a <xref:System.Windows.Media.QuadraticBezierSegment> třídy.  
  
## <a name="example"></a>Příklad  
 V následujících příkladech je kvadratické Bézierovy křivky čerpají z (10,100) na (300,100). Křivku má řídicí bod (200,200).  
  
 [xaml]  
  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete pomocí syntaxe atribut popisující cestu.  
  
 [!code-xaml[GeometrySample#54](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 [xaml]  
  
 (Všimněte si, že tento atribut syntaxe ve skutečnosti vytvoří <xref:System.Windows.Media.StreamGeometry>, světlejšího váhy verzi <xref:System.Windows.Media.PathGeometry>. Další informace najdete v tématu [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) stránky.)  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], může také kreslení kvadratické Bézierovy křivky pomocí syntaxe element objektu. Tady je ekvivalentem předchozího [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad.  
  
 [!code-xaml[GeometrySample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v článku [geometrie ukázka](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření oblouku elipsy](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [Vytvoření kubické Bézierovy křivky](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
