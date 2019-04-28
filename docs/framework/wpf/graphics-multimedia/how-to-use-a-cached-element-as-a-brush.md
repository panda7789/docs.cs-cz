---
title: 'Postupy: Použití elementu uloženého v mezipaměti jako štětce'
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: 78df242c7f00b69e36ea4ab6751f51509d9e2220
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769249"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="87c4b-102">Postupy: Použití elementu uloženého v mezipaměti jako štětce</span><span class="sxs-lookup"><span data-stu-id="87c4b-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="87c4b-103">Použití <xref:System.Windows.Media.BitmapCacheBrush> třídy pro opětovné použití elementu uloženého v mezipaměti efektivně.</span><span class="sxs-lookup"><span data-stu-id="87c4b-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="87c4b-104">Pro ukládání do mezipaměti elementu, vytvořte novou instanci třídy <xref:System.Windows.Media.BitmapCache> třídy a přiřadit k elementu <xref:System.Windows.UIElement.CacheMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="87c4b-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87c4b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="87c4b-105">Example</span></span>  
 <span data-ttu-id="87c4b-106">Následující příklad kódu ukazuje, jak pro opětovné použití elementu uloženého v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="87c4b-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="87c4b-107">Je elementu uloženého v mezipaměti <xref:System.Windows.Controls.Image> ovládací prvek, který se zobrazuje velký obrázek.</span><span class="sxs-lookup"><span data-stu-id="87c4b-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="87c4b-108"><xref:System.Windows.Controls.Image> Ovládací prvek je do mezipaměti jako rastrový obrázek s použitím <xref:System.Windows.Media.BitmapCache> třídy a mezipaměti je znovu tak, že ji přiřadíte <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="87c4b-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="87c4b-109">Štětec přiřazená na pozadí 25 tlačítka zobrazit efektivní opakované použití.</span><span class="sxs-lookup"><span data-stu-id="87c4b-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="87c4b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87c4b-110">See also</span></span>

- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [<span data-ttu-id="87c4b-111">Postupy: Zvýšení výkonu vykreslování zachycením elementu</span><span class="sxs-lookup"><span data-stu-id="87c4b-111">How to: Improve Rendering Performance by Caching an Element</span></span>](how-to-improve-rendering-performance-by-caching-an-element.md)
