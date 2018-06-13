---
title: 'Postupy: Použití elementu uloženého v mezipaměti jako štětce'
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: c43c4ecbefe99d6e38766705378d85d92ecc5729
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561521"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a>Postupy: Použití elementu uloženého v mezipaměti jako štětce
Použití <xref:System.Windows.Media.BitmapCacheBrush> třída efektivně znovu použít element v mezipaměti. Pro ukládání do mezipaměti element, vytvořte novou instanci třídy <xref:System.Windows.Media.BitmapCache> třídy a přiřadit k elementu <xref:System.Windows.UIElement.CacheMode%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak znovu použít element v mezipaměti. Element v mezipaměti je <xref:System.Windows.Controls.Image> ovládací prvek, který zobrazí velký obrázek. <xref:System.Windows.Controls.Image> Ovládací prvek je do mezipaměti jako rastrový obrázek pomocí <xref:System.Windows.Media.BitmapCache> třídy a mezipaměti je znovu jeho k přiřazení <xref:System.Windows.Media.BitmapCacheBrush>. Štětec se přiřadí ke na pozadí 25 tlačítek a zobrazit efektivní opakované použití.  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [Postupy: Zvýšení výkonu vykreslování uložením elementu do mezipaměti](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
