---
title: 'Postupy: Vykreslení oblasti plnou barvou'
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: 7e8e3fa5a379f02c3bb126c17bbe37fc0f3d57cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561328"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>Postupy: Vykreslení oblasti plnou barvou
K vyplnění oblast plnou barvou, můžete použít předdefinované systému štětce, například <xref:System.Windows.Media.Brushes.Red%2A> nebo <xref:System.Windows.Media.Brushes.Blue%2A>, nebo můžete vytvořit nový <xref:System.Windows.Media.SolidColorBrush> a popisují jeho <xref:System.Windows.Media.SolidColorBrush.Color%2A> pomocí hodnoty alfa, červené, zelené a modré. V jazyce XAML může také pomocí zápisu hexadecimální malovat oblast plnou barvou.  
  
 Následující příklady používá každý z těchto postupů pro malování <xref:System.Windows.Shapes.Rectangle> blue.  
  
## <a name="example"></a>Příklad  
 **Použití předdefinovaného štětce**  
  
 V následujícím příkladu používá předdefinovanou štětce <xref:System.Windows.Media.Brushes.Blue%2A> k vyplnění obdélníku blue.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **Hexadecimální notaci**  
  
 Další příklad používá šestnáctkové soustavě 8 číslic k vyplnění obdélníku blue.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **Pomocí ARGB hodnot**  
  
 V dalším příkladu se vytváří <xref:System.Windows.Media.SolidColorBrush> a popisuje jeho <xref:System.Windows.Media.SolidColorBrush.Color%2A> pomocí ARGB hodnoty pro modrou barvu.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 Další způsoby, jak popisuje barvu, najdete v článku <xref:System.Windows.Media.Color> struktura.  
  
 **Související témata**  
  
 Další informace o <xref:System.Windows.Media.SolidColorBrush> a další příklady najdete v článku [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) Přehled.  
  
 Tento příklad kódu je součástí většího příkladu vztahujícího se pro <xref:System.Windows.Media.SolidColorBrush> třídy. Kompletní příklad, najdete v článku [štětce ukázka](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Brushes>
