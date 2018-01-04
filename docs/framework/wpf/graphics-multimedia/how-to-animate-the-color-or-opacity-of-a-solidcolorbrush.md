---
title: "Postupy: Animace barvy a krytí štětce SolidColorBrush"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4bac3ae90fa0fa2229e236f46b8884c942b99bef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>Postupy: Animace barvy a krytí štětce SolidColorBrush
Tento příklad ukazuje, jak animace <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá tři animací pro animaci <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush>.  
  
-   První animace <xref:System.Windows.Media.Animation.ColorAnimation>, se změní štětce barva <xref:System.Windows.Media.Colors.Gray%2A> vstupu myší v rámeček.  
  
-   Další animace jiné <xref:System.Windows.Media.Animation.ColorAnimation>, se změní štětce barva <xref:System.Windows.Media.Colors.Orange%2A> při přesunutí myši opustí rámeček.  
  
-   Poslední animace <xref:System.Windows.Media.Animation.DoubleAnimation>, změny štětce krytí 0,0 při stisknutí levé tlačítko.  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 Více ucelenou ukázku, která ukazuje, jak animace různé typy štětce, najdete v článku [štětce ukázka](http://go.microsoft.com/fwlink/?LinkID=159973). Další informace o animace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Z důvodu konzistence s další příklady animace verze kódu v tomto příkladu použijte <xref:System.Windows.Media.Animation.Storyboard> objekt, který chcete použít jejich animace. Při použití jedné animace v kódu, je však jednodušší použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda místo použití <xref:System.Windows.Media.Animation.Storyboard>. Příklad, naleznete v části [animace vlastnosti bez použití scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Ukázka štětce](http://go.microsoft.com/fwlink/?LinkID=159973)
