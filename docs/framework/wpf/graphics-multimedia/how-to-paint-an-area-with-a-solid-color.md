---
title: 'Postupy: Vykreslení oblasti plnou barvou'
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: be28a0af04c4e43cdf745a5429468aee99e34c40
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849519"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>Postupy: Vykreslení oblasti plnou barvou
Chcete-li malovat oblast plnou barvou, můžete použít předdefinovanou <xref:System.Windows.Media.Brushes.Red%2A> <xref:System.Windows.Media.Brushes.Blue%2A>systémovou stopu, <xref:System.Windows.Media.SolidColorBrush> například <xref:System.Windows.Media.SolidColorBrush.Color%2A> nebo , nebo můžete vytvořit novou a popsat její použití alfa, červené, zelené a modré hodnoty. V XAML můžete také malovat oblast s plnou barvou pomocí hexidecimálního zápisu.  
  
 Následující příklady používají každý z těchto <xref:System.Windows.Shapes.Rectangle> technik malovat modrou.  
  
## <a name="example"></a>Příklad  
 **Použití předdefinované stopy**  
  
 V následujícím příkladu používá <xref:System.Windows.Media.Brushes.Blue%2A> předdefinovanou stopu k malování obdélníku na modrou.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **Použití šestnáctkové zápisu**  
  
 Další příklad používá 8místný šestnáctkový zápis k malování obdélníku modré.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **Použití hodnot ARGB**  
  
 Další příklad vytvoří <xref:System.Windows.Media.SolidColorBrush> a popisuje <xref:System.Windows.Media.SolidColorBrush.Color%2A> jeho použití argb hodnoty pro modrou barvu.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 Další způsoby popisu barev naleznete <xref:System.Windows.Media.Color> ve struktuře.  
  
 **Související témata**  
  
 Další informace <xref:System.Windows.Media.SolidColorBrush> a další příklady naleznete v přehledu [Malování plnými barvami a přechody.](painting-with-solid-colors-and-gradients-overview.md)  
  
 Tento příklad kódu je součástí většípříklad <xref:System.Windows.Media.SolidColorBrush> pro třídu. Úplný vzorek naleznete v části [Ukázka štětců](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Brushes>
