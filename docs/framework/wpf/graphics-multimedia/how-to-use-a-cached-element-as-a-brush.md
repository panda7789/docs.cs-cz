---
title: 'Postupy: Použití elementu uloženého v mezipaměti jako štětce'
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: 7ff0e9eb131faaed3874995ee137126eac31f43d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597928"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a>Postupy: Použití elementu uloženého v mezipaměti jako štětce
Použití <xref:System.Windows.Media.BitmapCacheBrush> třídy pro opětovné použití elementu uloženého v mezipaměti efektivně. Pro ukládání do mezipaměti elementu, vytvořte novou instanci třídy <xref:System.Windows.Media.BitmapCache> třídy a přiřadit k elementu <xref:System.Windows.UIElement.CacheMode%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak pro opětovné použití elementu uloženého v mezipaměti. Je elementu uloženého v mezipaměti <xref:System.Windows.Controls.Image> ovládací prvek, který se zobrazuje velký obrázek. <xref:System.Windows.Controls.Image> Ovládací prvek je do mezipaměti jako rastrový obrázek s použitím <xref:System.Windows.Media.BitmapCache> třídy a mezipaměti je znovu tak, že ji přiřadíte <xref:System.Windows.Media.BitmapCacheBrush>. Štětec přiřazená na pozadí 25 tlačítka zobrazit efektivní opakované použití.  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [Postupy: Zvýšení výkonu vykreslování zachycením elementu](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
