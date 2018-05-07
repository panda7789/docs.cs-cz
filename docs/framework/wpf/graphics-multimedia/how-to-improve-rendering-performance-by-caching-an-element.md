---
title: 'Postupy: Zvýšení výkonu vykreslování zachycením elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
ms.openlocfilehash: a92909c623db0c10e3434677b4275fa82b787fa7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a>Postupy: Zvýšení výkonu vykreslování zachycením elementu
Použití <xref:System.Windows.Media.BitmapCache> třída pro zlepšení výkonu vykreslování komplexní <xref:System.Windows.UIElement>. Pro ukládání do mezipaměti element, vytvořte novou instanci třídy <xref:System.Windows.Media.BitmapCache> třídy a přiřadit k elementu <xref:System.Windows.UIElement.CacheMode%2A> vlastnost. Můžete opakovaně použít <xref:System.Windows.Media.BitmapCache> efektivně v <xref:System.Windows.Media.BitmapCacheBrush>.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit komplexní prvek a uložení do mezipaměti jako bitmapu, což zvyšuje výkon, když je animace elementu. Element nachází na plátně, který obsahuje geometrie obrazce s mnoha vrcholy. A <xref:System.Windows.Media.BitmapCache> výchozí hodnoty přiřazeny k <xref:System.Windows.UIElement.CacheMode%2A> plátna, a zobrazuje animace smooth škálování v mezipaměti rastrového obrázku.  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [Postupy: Použití elementu uloženého v mezipaměti jako štětce](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
