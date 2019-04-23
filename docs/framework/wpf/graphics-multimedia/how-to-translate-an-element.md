---
title: 'Postupy: Překlad elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 9c1b873a89820e85efb99789f483c4832fb23cf7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231185"
---
# <a name="how-to-translate-an-element"></a>Postupy: Překlad elementu
Tento příklad ukazuje způsob převodu (přesunout) elementu s použitím <xref:System.Windows.Media.TranslateTransform>.  
  
 <xref:System.Windows.Media.TranslateTransform> Třídy je zvláště užitečná pro přesouvání elementů v rámci panely, které nepodporují absolutní pozici. Například použitím <xref:System.Windows.Media.TranslateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu, můžete přesunout element v rámci <xref:System.Windows.Controls.StackPanel> nebo <xref:System.Windows.Controls.DockPanel>.  
  
 Použití <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnost <xref:System.Windows.Media.TranslateTransform> k určení rozsahu jsou v pixelech, chcete-li přesunout element podél osy x. Použití <xref:System.Windows.Media.TranslateTransform.Y%2A> vlastnosti k určení rozsahu jsou v pixelech, chcete-li přesunout element podél osy y. Nakonec platí <xref:System.Windows.Media.TranslateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu.  
  
 Následující příklad používá <xref:System.Windows.Media.TranslateTransform> k dolů element 50 pixelů na vpravo a 50 pixelů.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Úplnou ukázku najdete v tématu [2D transformace ukázka](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Viz také:

- [Přehled transformace](transforms-overview.md)
