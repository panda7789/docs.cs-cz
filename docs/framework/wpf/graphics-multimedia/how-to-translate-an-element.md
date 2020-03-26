---
title: 'Postupy: Překlad elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: addff0e22fb3f27ea924887809c0635aeb3ad67d
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111969"
---
# <a name="how-to-translate-an-element"></a>Postupy: Překlad elementu
Tento příklad ukazuje, jak přeložit (přesunout) prvek pomocí <xref:System.Windows.Media.TranslateTransform>.  
  
 Třída <xref:System.Windows.Media.TranslateTransform> je zvláště užitečná pro pohyblivé prvky uvnitř panelů, které nepodporují absolutní umístění. Například <xref:System.Windows.Media.TranslateTransform> použitím <xref:System.Windows.UIElement.RenderTransform%2A> a na vlastnost prvku můžete přesunout prvek <xref:System.Windows.Controls.StackPanel> v <xref:System.Windows.Controls.DockPanel>rámci nebo .  
  
 Pomocí <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnosti <xref:System.Windows.Media.TranslateTransform> funkce určete částku v obrazových bodech k přesunutí prvku podél osy x. Pomocí <xref:System.Windows.Media.TranslateTransform.Y%2A> vlastnosti určete částku v obrazových bodech pro přesunutí prvku podél osy y. Nakonec použít <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost prvku.  
  
 Následující příklad používá <xref:System.Windows.Media.TranslateTransform> prvek 50 pixelů doprava a 50 pixelů dolů.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Kompletní ukázku naleznete v tématu [2D transformace Ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Viz také

- [Přehled transformace](transforms-overview.md)
