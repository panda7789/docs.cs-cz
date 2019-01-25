---
title: 'Postupy: Určení počátku transformace použitím relativních hodnot'
ms.date: 03/30/2017
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
ms.openlocfilehash: 55007575435ada809b8fba43d08abdd2ce9ddd73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570613"
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a>Postupy: Určení počátku transformace použitím relativních hodnot
Tento příklad ukazuje, jak použít relativní hodnoty k určení počátku <xref:System.Windows.UIElement.RenderTransform%2A> , která je použita na <xref:System.Windows.FrameworkElement>.  
  
 Při otočení, škálování nebo zkosení <xref:System.Windows.FrameworkElement> pomocí <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost, výchozí nastavení se týká transformací, která se levém horním rohu elementu. Pokud chcete k otočení, škálování nebo zkosení v centru elementu, může kompenzovat nastavením center transformací, která se k centru elementu. Toto řešení vyžaduje znát velikost prvku. Snadnější použití transformace na System center elementu je nastavit jeho <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnosti (0,5, 0,5), namísto nastavení středovou hodnotou na samotný transformace.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.RotateTransform> otočíte <xref:System.Windows.Controls.Button> 45 stupňů po směru hodinových ručiček. Protože příklad neurčuje System center, tlačítko otočí o bod (0, 0), který je jeho levého horního rohu. <xref:System.Windows.Media.RotateTransform> Aplikován <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost.  
  
 Následující obrázek ukazuje výsledek transformace pro příklad, který následuje.  
  
 ![Tlačítko transformovat pomocí RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
45 stupňů po směru hodinových ručiček otočení pomocí RenderTransform – vlastnost  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 V následujícím příkladu se používá také <xref:System.Windows.Media.RotateTransform> otočíte <xref:System.Windows.Controls.Button> v tomto příkladu nastaví 45 stupňů po směru hodinových ručiček, nicméně <xref:System.Windows.UIElement.RenderTransformOrigin%2A> tlačítka (0,5, 0,5). Otočení v důsledku toho se použije pro Centrum tlačítko místo do levého horního rohu.  
  
 Následující obrázek ukazuje výsledek transformace pro příklad, který následuje.  
  
 ![Tlačítko transformované o jeho střed](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Otočení kolem osy 45 stupňů, pomocí RenderTransformOrigin z RenderTransform – vlastnost (0,5, 0,5)  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Další informace o transformaci <xref:System.Windows.FrameworkElement> objekty, najdete [transformuje přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.Transform>
- [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
