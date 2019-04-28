---
title: 'Postupy: Překlopení prvku UIElement vodorovně nebo svisle'
ms.date: 03/30/2017
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
ms.openlocfilehash: 6b3da322493d17e4f8e36a35b9a0e40fdc9dc685
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767026"
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a>Postupy: Překlopení prvku UIElement vodorovně nebo svisle
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.ScaleTransform> k převrácení <xref:System.Windows.UIElement> vodorovně nebo svisle. V tomto příkladu <xref:System.Windows.Controls.Button> ovládacího prvku (typ <xref:System.Windows.UIElement>) obráceně použitím <xref:System.Windows.Media.ScaleTransform> k jeho <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Tlačítko k převrácení naleznete na následujícím obrázku.  
  
 ![Tlačítko s žádná transformace](./media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")  
UIElement k převrácení  
  
 Následuje kód, který vytvoří tlačítko.  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a>Příklad  
 Převrátit vodorovně na tlačítko, vytvořit <xref:System.Windows.Media.ScaleTransform> a nastavte jeho <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> vlastnost na hodnotu -1. Použít <xref:System.Windows.Media.ScaleTransform> na tlačítko <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 ![Tlačítko obráceně vodorovně o &#40;0,0&#41;](./media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")  
Po použití ScaleTransform – tlačítko  
  
## <a name="example"></a>Příklad  
 Jak je vidět z na předchozím obrázku, bylo na tlačítko obráceně, ale také byl přesunut. Důvodem je, na tlačítko se obráceně z levého horního rohu. K převrácení tlačítka na místě, které chcete použít <xref:System.Windows.Media.ScaleTransform> k jeho střed, nikoli jeho rohu. Snadný způsob, jak použít <xref:System.Windows.Media.ScaleTransform> na tlačítka je nastavit na tlačítko center <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost 0,5, 0,5.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 ![Tlačítko obráceně vodorovně o jeho střed](./media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")  
Tlačítko s RenderTransformOrigin 0,5, 0.5  
  
## <a name="example"></a>Příklad  
 Chcete-li svisle Převrátit tlačítko, nastavte <xref:System.Windows.Media.ScaleTransform> objektu <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> vlastnosti namísto jeho <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> vlastnost.  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 ![Tlačítko obráceně svisle o jeho střed](./media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")  
Svisle přetočený tlačítko  
  
## <a name="see-also"></a>Viz také:

- [Přehled transformace](../graphics-multimedia/transforms-overview.md)
