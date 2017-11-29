---
title: "Postupy: Použití elementu uloženého v mezipaměti jako štětce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d0f0c60e9df6a1ec816b1f9cf5769c93b382ae5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Postupy: zlepšení výkonu vykreslování pomocí ukládání do mezipaměti Element](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
