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
ms.openlocfilehash: b5e39541fdf031b19e9e74483c0de94295e788d7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375216"
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a>Postupy: Zvýšení výkonu vykreslování zachycením elementu
Použití <xref:System.Windows.Media.BitmapCache> třídy ke zvýšení výkonu vykreslování komplexní <xref:System.Windows.UIElement>. Pro ukládání do mezipaměti elementu, vytvořte novou instanci třídy <xref:System.Windows.Media.BitmapCache> třídy a přiřadit k elementu <xref:System.Windows.UIElement.CacheMode%2A> vlastnost. Můžete opakovaně použít <xref:System.Windows.Media.BitmapCache> efektivně v <xref:System.Windows.Media.BitmapCacheBrush>.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit komplexních prvků a uložení do mezipaměti jako rastrový obrázek, což zvyšuje výkon, když je animovaný elementu. Element je plátno, která obsahuje obrazec geometrie s mnoha vrcholy. A <xref:System.Windows.Media.BitmapCache> s výchozí hodnoty přiřazeny k <xref:System.Windows.UIElement.CacheMode%2A> plátna, a zobrazí animace smooth škálování v mezipaměti rastrový obrázek.  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [Postupy: Použití elementu uloženého v mezipaměti jako štětce](how-to-use-a-cached-element-as-a-brush.md)
