---
title: 'Postupy: Překlad elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: addff0e22fb3f27ea924887809c0635aeb3ad67d
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111969"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="1d121-102">Postupy: Překlad elementu</span><span class="sxs-lookup"><span data-stu-id="1d121-102">How to: Translate an Element</span></span>
<span data-ttu-id="1d121-103">Tento příklad ukazuje, jak přeložit (přesunout) prvek pomocí <xref:System.Windows.Media.TranslateTransform>.</span><span class="sxs-lookup"><span data-stu-id="1d121-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="1d121-104">Třída <xref:System.Windows.Media.TranslateTransform> je zvláště užitečná pro pohyblivé prvky uvnitř panelů, které nepodporují absolutní umístění.</span><span class="sxs-lookup"><span data-stu-id="1d121-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="1d121-105">Například <xref:System.Windows.Media.TranslateTransform> použitím <xref:System.Windows.UIElement.RenderTransform%2A> a na vlastnost prvku můžete přesunout prvek <xref:System.Windows.Controls.StackPanel> v <xref:System.Windows.Controls.DockPanel>rámci nebo .</span><span class="sxs-lookup"><span data-stu-id="1d121-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="1d121-106">Pomocí <xref:System.Windows.Media.TranslateTransform.X%2A> vlastnosti <xref:System.Windows.Media.TranslateTransform> funkce určete částku v obrazových bodech k přesunutí prvku podél osy x.</span><span class="sxs-lookup"><span data-stu-id="1d121-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="1d121-107">Pomocí <xref:System.Windows.Media.TranslateTransform.Y%2A> vlastnosti určete částku v obrazových bodech pro přesunutí prvku podél osy y.</span><span class="sxs-lookup"><span data-stu-id="1d121-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="1d121-108">Nakonec použít <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost prvku.</span><span class="sxs-lookup"><span data-stu-id="1d121-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="1d121-109">Následující příklad používá <xref:System.Windows.Media.TranslateTransform> prvek 50 pixelů doprava a 50 pixelů dolů.</span><span class="sxs-lookup"><span data-stu-id="1d121-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d121-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d121-110">Example</span></span>  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="1d121-111">Kompletní ukázku naleznete v tématu [2D transformace Ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="1d121-111">For the complete sample, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d121-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d121-112">See also</span></span>

- [<span data-ttu-id="1d121-113">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="1d121-113">Transforms Overview</span></span>](transforms-overview.md)
