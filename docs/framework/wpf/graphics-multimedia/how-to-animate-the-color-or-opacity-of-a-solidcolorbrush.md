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
ms.openlocfilehash: 08b85935e0cb1ababd1fb63b9d02518ea3fcfa17
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452880"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>Postupy: Animace barvy a krytí štětce SolidColorBrush
Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.Brush.Opacity%2A> <xref:System.Windows.Media.SolidColorBrush>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá tři animace k animaci <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.Brush.Opacity%2A> <xref:System.Windows.Media.SolidColorBrush>.  
  
- První animace, <xref:System.Windows.Media.Animation.ColorAnimation>, změní barvu štětce na <xref:System.Windows.Media.Colors.Gray%2A>, když ukazatel myši vstoupí do obdélníku.  
  
- Další animace, jinou <xref:System.Windows.Media.Animation.ColorAnimation>, změní barvu štětce na <xref:System.Windows.Media.Colors.Orange%2A>, když myš opustí obdélník.  
  
- Poslední animace, <xref:System.Windows.Media.Animation.DoubleAnimation>, změní krytí štětce na 0,0 při stisknutí levého tlačítka myši.  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 Úplnější ukázku, která ukazuje, jak animovat různé typy štětců, naleznete v [ukázce štětce](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Další informace o animacích najdete v [přehledu animace](animation-overview.md).  
  
 Pro zajištění konzistence s dalšími příklady animací používají verze kódu v tomto příkladu objekt <xref:System.Windows.Media.Animation.Storyboard> k aplikování animací. Nicméně při použití jedné animace v kódu je jednodušší použít metodu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> namísto použití <xref:System.Windows.Media.Animation.Storyboard>. Příklad naleznete v tématu [animace vlastnosti bez použití scénáře](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Přehled scénářů](storyboards-overview.md)
- [Ukázka štětců](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
