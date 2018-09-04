---
title: 'Postupy: Animace barvy a krytí štětce SolidColorBrush'
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: 194f01d3d5aa4c2b5a08a6c3fdb3dc195b0e9e3e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500326"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>Postupy: Animace barvy a krytí štětce SolidColorBrush
Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá tři animace pro animaci <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush>.  
  
-   První animace <xref:System.Windows.Media.Animation.ColorAnimation>, se změní barva stopy <xref:System.Windows.Media.Colors.Gray%2A> vstupu myší v obdélníku.  
  
-   Další animace jiného <xref:System.Windows.Media.Animation.ColorAnimation>, se změní barva stopy <xref:System.Windows.Media.Colors.Orange%2A> když ukazatel myši opustí obdélníku.  
  
-   Poslední animace <xref:System.Windows.Media.Animation.DoubleAnimation>, mění neprůhlednost štětce rovnou 0,0, když se stiskne levé tlačítko myši.  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 Ucelenější ukázku, která ukazuje, jak animovat různé druhy štětce, najdete v článku [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973). Další informace o animace, najdete v článku [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Pro zajištění konzistence s další příklady animace, kód verze tohoto příkladu použijte <xref:System.Windows.Media.Animation.Storyboard> objekt jejich animace. Při použití jedné animace v kódu, je ale jednodušší použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda namísto použití <xref:System.Windows.Media.Animation.Storyboard>. Příklad najdete v tématu [animace vlastnosti bez pomoci scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973)
