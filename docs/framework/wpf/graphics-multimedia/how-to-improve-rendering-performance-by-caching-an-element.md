---
title: "Postupy: Zvýšení výkonu vykreslování zachycením elementu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d754d0ed2f3951c39b3eaeae097589adf3510f5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Postupy: použijte Element v mezipaměti jako štětce](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
