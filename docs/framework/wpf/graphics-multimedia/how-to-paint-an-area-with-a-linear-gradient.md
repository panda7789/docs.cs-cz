---
title: 'Postupy: Vyplnění oblasti lineárním přechodem'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: ec07a0c33468681f67d086ec3d1d58b378412ff9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>Postupy: Vyplnění oblasti lineárním přechodem
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.LinearGradientBrush> třídy Malování oblast s lineárního přechodu. V následujícím příkladu <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> vykreslením s diagonálních lineárního přechodu, která přejde z žlutý do červené na modrou k vápna zeleně.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Následující obrázek znázorňuje přechodu vytvořený v předchozím příkladu.  
  
 ![Diagonálních lineárního přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 Chcete-li vytvořit vodorovné lineárního přechodu, změňte <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> k (0,0.5) a (1,0.5). V následujícím příkladu <xref:System.Windows.Shapes.Rectangle> vykreslením s vodorovné lineárního přechodu.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Následující obrázek znázorňuje přechodu vytvořený v předchozím příkladu.  
  
 ![Vodorovné lineárního přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 Chcete-li vytvořit svislé lineárního přechodu, změňte <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> a <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> k (0.5,0) a (0.5,1). V následujícím příkladu <xref:System.Windows.Shapes.Rectangle> vykreslením s svislé lineárního přechodu.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Následující obrázek znázorňuje přechodu vytvořený v předchozím příkladu.  
  
 ![Svislé lineárního přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
>  V příkladech v tomto tématu použijte výchozí souřadnicový systém pro nastavení body počáteční a koncové body. Systém souřadnic výchozí je relativní vzhledem ke ohraničující pole: 0 znamená 0 procent ohraničujícího rámečku a 1 znamená 100 procent ohraničujícího rámečku. Tento systém souřadnic můžete změnit nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> vlastnost na hodnotu <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>. Absolutní souřadnicový systém není relativně k ohraničující pole. Hodnoty se interpretují přímo v místním prostoru.  
  
 Další příklady najdete v tématu [štětce ukázka](http://go.microsoft.com/fwlink/?LinkID=159973). Další informace o přechody a dalších typů štětce najdete v tématu [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).
