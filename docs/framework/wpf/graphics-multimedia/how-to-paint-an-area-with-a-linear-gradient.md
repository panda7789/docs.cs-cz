---
title: 'Postupy: Vykreslení oblasti lineárním přechodem'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: 92c9ccd846dbbce043d13e6ba82b9fa8e72fa8b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916167"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>Postupy: Vykreslení oblasti lineárním přechodem
Tento příklad ukazuje, jak použít <xref:System.Windows.Media.LinearGradientBrush> třídu k vykreslení oblasti lineárním přechodem. V následujícím příkladu <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> je vykreslen s úhlopříčným lineárním přechodem, který přechází ze žluté na červenou na modrou zelenou.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Následující ilustrace znázorňuje přechod vytvořený předchozím příkladem.  
  
 ![Diagonální lineární přechod](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 Chcete-li vytvořit vodorovný lineární přechod, <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> změňte <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush> na (0, 0,5) a (1, 0,5). V následujícím příkladu <xref:System.Windows.Shapes.Rectangle> je vykreslen s vodorovným lineárním přechodem.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Následující ilustrace znázorňuje přechod vytvořený předchozím příkladem.  
  
 ![Vodorovný lineární přechod](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 Chcete-li vytvořit svislý lineární přechod, změňte <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> hodnotu <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush> na (0.5, 0) a (0,5, 1). V následujícím příkladu <xref:System.Windows.Shapes.Rectangle> je vykreslen se svislým lineárním přechodem.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Následující ilustrace znázorňuje přechod vytvořený předchozím příkladem.  
  
 ![Svislý lineární přechod](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
> Příklady v tomto tématu používají výchozí systém souřadnic pro nastavení počátečních bodů a koncových bodů. Výchozí souřadnicový systém je relativní vzhledem k ohraničujícímu poli: 0 značí 0 procent ohraničovacího rámečku a 1 označuje 100% ohraničovacího rámečku. Můžete změnit tento systém souřadnic nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> vlastnosti na hodnotu. <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType> Absolutní souřadnicový systém není relativní vzhledem k ohraničujícímu poli. Hodnoty jsou interpretovány přímo v místním prostoru.  
  
 Další příklady naleznete v tématu [Ukázka štětce](https://go.microsoft.com/fwlink/?LinkID=159973). Další informace o přechodech a dalších typech štětců naleznete v tématu [Malování s plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md).
