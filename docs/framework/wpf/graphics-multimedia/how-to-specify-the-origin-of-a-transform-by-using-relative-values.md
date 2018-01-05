---
title: "Postupy: Určení počátku transformace použitím relativních hodnot"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d29a572e2989ffb800434fdaab9756cb651c0816
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a>Postupy: Určení počátku transformace použitím relativních hodnot
Tento příklad ukazuje, jak použít relativní hodnoty k určení původu <xref:System.Windows.UIElement.RenderTransform%2A> který se použije pro <xref:System.Windows.FrameworkElement>.  
  
 Při otočení, škálovat nebo zkreslit <xref:System.Windows.FrameworkElement> pomocí <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost, výchozí nastavení pro transformaci se vztahuje na levém horním rohu elementu. Pokud chcete otočit, změnit velikost nebo zkosení z centra elementu, můžete odpovídajícím způsobem nastavením středu transformovat k centru elementu. Toto řešení však vyžaduje, že znáte velikost elementu. Jednodušší způsob použití transformace k centru elementu je nastavit jeho <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnosti (0,5, 0,5), namísto nastavování hodnotu center na transformace sám sebe.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.RotateTransform> otočení <xref:System.Windows.Controls.Button> 45 stupňů po směru hodinových ručiček. Vzhledem k tomu, že v příkladu neurčuje center, tlačítko otočí o bodu (0, 0), což je jeho levého horního rohu. <xref:System.Windows.Media.RotateTransform> Se použijí na <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost.  
  
 Následující obrázek znázorňuje výsledek transformace pro příklad, který následuje dále.  
  
 ![Tlačítko transformované pomocí RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Po směru hodinových ručiček rotaci 45 stupňů pomocí vlastnosti RenderTransform  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 Následující příklad používá také <xref:System.Windows.Media.RotateTransform> otočení <xref:System.Windows.Controls.Button> v tomto příkladu nastaví 45 stupňů po směru hodinových ručiček; však <xref:System.Windows.UIElement.RenderTransformOrigin%2A> u tlačítka (0,5, 0,5). V důsledku toho je oběh se použije k centru tlačítka místo levého horního rohu.  
  
 Následující obrázek znázorňuje výsledek transformace pro příklad, který následuje dále.  
  
 ![Tlačítko transformované o jeho center](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Otočení 45 stupňů pomocí vlastnosti RenderTransform s RenderTransformOrigin z (0,5, 0,5)  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Další informace o transformaci <xref:System.Windows.FrameworkElement> objekty, najdete [transformuje přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Transform>  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
