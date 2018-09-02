---
title: 'Postupy: Překlad elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 04e1e8288bcccc4a310f05abff01fbdf160cdb11
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421000"
---
# <a name="how-to-translate-an-element"></a>Postupy: Překlad elementu
Tento příklad ukazuje způsob převodu (přesunout) elementu s použitím <xref:System.Windows.Media.TranslateTransform>.  
  
 <xref:System.Windows.Media.TranslateTransform> Třídy je zvláště užitečná pro přesouvání elementů v rámci panely, které nepodporují absolutní pozici. Například použitím <xref:System.Windows.Media.TranslateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu, můžete přesunout element v rámci <xref:System.Windows.Controls.StackPanel> nebo <xref:System.Windows.Controls.DockPanel>.  
  
 Použití <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> k určení rozsahu jsou v pixelech, chcete-li přesunout element podél osy x. Použití <xref:System.Windows.Media.TranslateTransform.Y%2A> vlastnosti k určení rozsahu jsou v pixelech, chcete-li přesunout element podél osy y. Nakonec platí <xref:System.Windows.Media.TranslateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu.  
  
 Následující příklad používá <xref:System.Windows.Media.TranslateTransform> k dolů element 50 pixelů na vpravo a 50 pixelů.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Úplnou ukázku najdete v tématu [2D transformace ukázka](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Viz také  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
