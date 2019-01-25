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
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="160c2-102">Postupy: Použití elementu uloženého v mezipaměti jako štětce</span><span class="sxs-lookup"><span data-stu-id="160c2-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="160c2-103">Použití <xref:System.Windows.Media.BitmapCacheBrush> třídy pro opětovné použití elementu uloženého v mezipaměti efektivně.</span><span class="sxs-lookup"><span data-stu-id="160c2-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="160c2-104">Pro ukládání do mezipaměti elementu, vytvořte novou instanci třídy <xref:System.Windows.Media.BitmapCache> třídy a přiřadit k elementu <xref:System.Windows.UIElement.CacheMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="160c2-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="160c2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="160c2-105">Example</span></span>  
 <span data-ttu-id="160c2-106">Následující příklad kódu ukazuje, jak pro opětovné použití elementu uloženého v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="160c2-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="160c2-107">Je elementu uloženého v mezipaměti <xref:System.Windows.Controls.Image> ovládací prvek, který se zobrazuje velký obrázek.</span><span class="sxs-lookup"><span data-stu-id="160c2-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="160c2-108"><xref:System.Windows.Controls.Image> Ovládací prvek je do mezipaměti jako rastrový obrázek s použitím <xref:System.Windows.Media.BitmapCache> třídy a mezipaměti je znovu tak, že ji přiřadíte <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="160c2-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="160c2-109">Štětec přiřazená na pozadí 25 tlačítka zobrazit efektivní opakované použití.</span><span class="sxs-lookup"><span data-stu-id="160c2-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="160c2-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="160c2-110">See also</span></span>
- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [<span data-ttu-id="160c2-111">Postupy: Zvýšení výkonu vykreslování zachycením elementu</span><span class="sxs-lookup"><span data-stu-id="160c2-111">How to: Improve Rendering Performance by Caching an Element</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
