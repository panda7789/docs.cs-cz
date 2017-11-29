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
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="31d09-102">Postupy: Použití elementu uloženého v mezipaměti jako štětce</span><span class="sxs-lookup"><span data-stu-id="31d09-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="31d09-103">Použití <xref:System.Windows.Media.BitmapCacheBrush> třída efektivně znovu použít element v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="31d09-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="31d09-104">Pro ukládání do mezipaměti element, vytvořte novou instanci třídy <xref:System.Windows.Media.BitmapCache> třídy a přiřadit k elementu <xref:System.Windows.UIElement.CacheMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="31d09-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31d09-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="31d09-105">Example</span></span>  
 <span data-ttu-id="31d09-106">Následující příklad kódu ukazuje, jak znovu použít element v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="31d09-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="31d09-107">Element v mezipaměti je <xref:System.Windows.Controls.Image> ovládací prvek, který zobrazí velký obrázek.</span><span class="sxs-lookup"><span data-stu-id="31d09-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="31d09-108"><xref:System.Windows.Controls.Image> Ovládací prvek je do mezipaměti jako rastrový obrázek pomocí <xref:System.Windows.Media.BitmapCache> třídy a mezipaměti je znovu jeho k přiřazení <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="31d09-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="31d09-109">Štětec se přiřadí ke na pozadí 25 tlačítek a zobrazit efektivní opakované použití.</span><span class="sxs-lookup"><span data-stu-id="31d09-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="31d09-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="31d09-110">See Also</span></span>  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [<span data-ttu-id="31d09-111">Postupy: zlepšení výkonu vykreslování pomocí ukládání do mezipaměti Element</span><span class="sxs-lookup"><span data-stu-id="31d09-111">How to: Improve Rendering Performance by Caching an Element</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
