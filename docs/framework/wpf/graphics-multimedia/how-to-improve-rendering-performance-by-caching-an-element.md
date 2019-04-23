---
title: 'Postupy: Zvýšení výkonu vykreslování uložením elementu do mezipaměti'
ms.date: 03/30/2017
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
ms.openlocfilehash: 118e8b0cca52c44788c9d5b291d710f765e7af2a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153371"
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a><span data-ttu-id="e6b13-102">Postupy: Zvýšení výkonu vykreslování uložením elementu do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="e6b13-102">How to: Improve Rendering Performance by Caching an Element</span></span>
<span data-ttu-id="e6b13-103">Použití <xref:System.Windows.Media.BitmapCache> třídy ke zvýšení výkonu vykreslování komplexní <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="e6b13-103">Use the <xref:System.Windows.Media.BitmapCache> class to improve rendering performance of a complex <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="e6b13-104">Pro ukládání do mezipaměti elementu, vytvořte novou instanci třídy <xref:System.Windows.Media.BitmapCache> třídy a přiřadit k elementu <xref:System.Windows.UIElement.CacheMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e6b13-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span> <span data-ttu-id="e6b13-105">Můžete opakovaně použít <xref:System.Windows.Media.BitmapCache> efektivně v <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="e6b13-105">You can reuse a <xref:System.Windows.Media.BitmapCache> efficiently in a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6b13-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6b13-106">Example</span></span>  
 <span data-ttu-id="e6b13-107">Následující příklad kódu ukazuje, jak vytvořit komplexních prvků a uložení do mezipaměti jako rastrový obrázek, což zvyšuje výkon, když je animovaný elementu.</span><span class="sxs-lookup"><span data-stu-id="e6b13-107">The following code example shows how to create a complex element and cache it as a bitmap, which improves performance when the element is animated.</span></span> <span data-ttu-id="e6b13-108">Element je plátno, která obsahuje obrazec geometrie s mnoha vrcholy.</span><span class="sxs-lookup"><span data-stu-id="e6b13-108">The element is a canvas that holds shape geometries with many vertices.</span></span> <span data-ttu-id="e6b13-109">A <xref:System.Windows.Media.BitmapCache> s výchozí hodnoty přiřazeny k <xref:System.Windows.UIElement.CacheMode%2A> plátna, a zobrazí animace smooth škálování v mezipaměti rastrový obrázek.</span><span class="sxs-lookup"><span data-stu-id="e6b13-109">A <xref:System.Windows.Media.BitmapCache> with default values is assigned to the <xref:System.Windows.UIElement.CacheMode%2A> of the canvas, and an animation shows the smooth scaling of the cached bitmap.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a><span data-ttu-id="e6b13-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6b13-110">See also</span></span>

- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [<span data-ttu-id="e6b13-111">Postupy: Použití elementu uloženého v mezipaměti jako štětce</span><span class="sxs-lookup"><span data-stu-id="e6b13-111">How to: Use a Cached Element as a Brush</span></span>](how-to-use-a-cached-element-as-a-brush.md)
