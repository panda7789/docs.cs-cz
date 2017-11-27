---
title: "Postupy: Překlopení prvku UIElement vodorovně nebo svisle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 84d1360246141cfa565d669fff108e3e4db3ce33
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a>Postupy: Překlopení prvku UIElement vodorovně nebo svisle
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.ScaleTransform> k převrácení <xref:System.Windows.UIElement> vodorovně nebo svisle. V tomto příkladu <xref:System.Windows.Controls.Button> ovládací prvek (typ <xref:System.Windows.UIElement>) je obráceně použitím <xref:System.Windows.Media.ScaleTransform> k jeho <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující obrázek znázorňuje tlačítko k převrácení.  
  
 ![Tlačítko s žádná transformace](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")  
Prvků uživatelského rozhraní k převrácení  
  
 Následující zobrazuje kód, který vytvoří tlačítko.  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a>Příklad  
 Chcete-li na tlačítko Překlopit vodorovně, vytvořte <xref:System.Windows.Media.ScaleTransform> a nastavit jeho <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> vlastnost na hodnotu -1. Použít <xref:System.Windows.Media.ScaleTransform> na tlačítko <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 ![Tlačítko překlopení vodorovně o &#40; 0,0 &#41; ] (../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")  
Tlačítko po použití metody ScaleTransform  
  
## <a name="example"></a>Příklad  
 Jak je vidět na předchozím obrázku, tlačítko byl obráceně, ale také byl přesunut. Je to způsobeno tlačítko byl obráceně z levého horního rohu. K převrácení tlačítko na místě, kterou chcete použít <xref:System.Windows.Media.ScaleTransform> jeho Center, ne jeho rohu. Snadný způsob, jak použít <xref:System.Windows.Media.ScaleTransform> tlačítka center je nastaven na tlačítko <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost 0,5, 0,5.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 ![Tlačítko překlopení vodorovně o jeho center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")  
Tlačítko s RenderTransformOrigin 0,5, 0,5  
  
## <a name="example"></a>Příklad  
 Chcete-li na tlačítko Překlopit svisle, nastavte <xref:System.Windows.Media.ScaleTransform> objektu <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> vlastnost místo jeho <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> vlastnost.  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 ![Tlačítko překlopení svisle o jeho center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")  
Tlačítko svisle přetočený  
  
## <a name="see-also"></a>Viz také  
 [Transformuje – přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
