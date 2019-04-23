---
title: 'Postupy: Vykreslení oblasti plnou barvou'
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: c85ba72c858d155f29875bb944824db1c44ffaab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086842"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>Postupy: Vykreslení oblasti plnou barvou
K vykreslení oblasti plnou barvou, můžete použít předdefinovaný systémový štětce, jako například <xref:System.Windows.Media.Brushes.Red%2A> nebo <xref:System.Windows.Media.Brushes.Blue%2A>, nebo můžete vytvořit nový <xref:System.Windows.Media.SolidColorBrush> a popsat její <xref:System.Windows.Media.SolidColorBrush.Color%2A> pomocí hodnoty alfa, červené, zelené a modré. V XAML může také pomocí zápisu hexadecimální vykreslení oblasti plnou barvou.  
  
 Každý z následujících postupů v následujících příkladech používá k vykreslení <xref:System.Windows.Shapes.Rectangle> modrá.  
  
## <a name="example"></a>Příklad  
 **Použití předdefinované štětce**  
  
 V následujícím příkladu používá předdefinované štětce <xref:System.Windows.Media.Brushes.Blue%2A> má Vymalovat modrý obdélník.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **Pomocí šestnáctkové soustavě**  
  
 Následující příklad používá k vykreslení obdélníku modré 8 číslici šestnáctkové soustavě.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **Pomocí hodnoty ARGB**  
  
 Následující příklad vytvoří <xref:System.Windows.Media.SolidColorBrush> a popisuje jeho <xref:System.Windows.Media.SolidColorBrush.Color%2A> pomocí ARGB hodnoty modrou barvu.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 Další způsoby popisu barev, najdete v článku <xref:System.Windows.Media.Color> struktury.  
  
 **Související témata**  
  
 Další informace o <xref:System.Windows.Media.SolidColorBrush> a další příklady najdete v článku [Malování plnými barvami a přechody přehled](painting-with-solid-colors-and-gradients-overview.md) Přehled.  
  
 Tento příklad kódu je součástí většího příkladu určeného pro <xref:System.Windows.Media.SolidColorBrush> třídy. Úplnou ukázku najdete v tématu [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Brushes>
