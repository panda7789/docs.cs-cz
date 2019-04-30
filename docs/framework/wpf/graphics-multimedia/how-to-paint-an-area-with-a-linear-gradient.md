---
title: 'Postupy: Vykreslení oblasti lineárním přechodem'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: c48ff13811d784ecc7042b73b964a9e6f2d42a34
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921884"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>Postupy: Vykreslení oblasti lineárním přechodem
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.LinearGradientBrush> třídu pro vykreslení oblasti lineárním přechodem. V následujícím příkladu <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> vymalováním Úhlopříčný lineárním přechodem, který změní z žlutá červená na modrou k Limetkově zelená.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Následující obrázek znázorňuje přechodu vytvořené v předchozím příkladu.  
  
 ![Úhlopříčný lineárního přechodu](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 Chcete-li vytvořit horizontální lineárního přechodu, změňte <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> k (0,0.5) a (1,0.5). V následujícím příkladu <xref:System.Windows.Shapes.Rectangle> vymalováním s vodorovné lineárního přechodu.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Následující obrázek znázorňuje přechodu vytvořené v předchozím příkladu.  
  
 ![Vodorovné lineárního přechodu](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 Chcete-li vytvořit svislé lineárního přechodu, změňte <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> k (0.5,0) a (0.5,1). V následujícím příkladu <xref:System.Windows.Shapes.Rectangle> vymalováním s svislé lineárního přechodu.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Následující obrázek znázorňuje přechodu vytvořené v předchozím příkladu.  
  
 ![Svislé lineárního přechodu](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
>  Příklady v tomto tématu použijte výchozí souřadnicový systém pro nastavení bodů počáteční a koncové body. Systém souřadnic výchozí je relativní vzhledem k ohraničujícího rámečku: 0 označuje procento ohraničujícího rámečku, 0 a 1 znamená 100 procent ohraničujícího rámečku. Tento systém souřadnic můžete změnit nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> k hodnotě <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>. Absolutní souřadnicový systém není vzhledem k ohraničujícího rámečku. Hodnoty jsou interpretovány přímo v místním prostoru.  
  
 Další příklady najdete v tématu [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973). Další informace o přechody a dalších typů štětce, naleznete v tématu [Malování plnými barvami a přechody přehled](painting-with-solid-colors-and-gradients-overview.md).
