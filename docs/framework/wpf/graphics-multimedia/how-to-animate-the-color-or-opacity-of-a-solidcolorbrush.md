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
ms.openlocfilehash: e440cf49b8b16051361650f9659dc6006c2e7b56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789243"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>Postupy: Animace barvy a krytí štětce SolidColorBrush
Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá tři animace pro animaci <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush>.  
  
- První animace <xref:System.Windows.Media.Animation.ColorAnimation>, se změní barva stopy <xref:System.Windows.Media.Colors.Gray%2A> vstupu myší v obdélníku.  
  
- Další animace jiného <xref:System.Windows.Media.Animation.ColorAnimation>, se změní barva stopy <xref:System.Windows.Media.Colors.Orange%2A> když ukazatel myši opustí obdélníku.  
  
- Poslední animace <xref:System.Windows.Media.Animation.DoubleAnimation>, mění neprůhlednost štětce rovnou 0,0, když se stiskne levé tlačítko myši.  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 Ucelenější ukázku, která ukazuje, jak animovat různé druhy štětce, najdete v článku [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973). Další informace o animace, najdete v článku [přehled animace](animation-overview.md).  
  
 Pro zajištění konzistence s další příklady animace, kód verze tohoto příkladu použijte <xref:System.Windows.Media.Animation.Storyboard> objekt jejich animace. Při použití jedné animace v kódu, je ale jednodušší použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda namísto použití <xref:System.Windows.Media.Animation.Storyboard>. Příklad najdete v tématu [animace vlastnosti bez pomoci scénáře](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled animace](animation-overview.md)
- [Přehled scénářů](storyboards-overview.md)
- [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973)
