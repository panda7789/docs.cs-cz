---
title: 'Postupy: Vytvoření průhledného nebo poloprůhledného elementu UIElement'
ms.date: 03/30/2017
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
ms.openlocfilehash: 7bf79848edb84a5bd93d1196fbe0b3196d159ff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545308"
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a><span data-ttu-id="a8a97-102">Postupy: Vytvoření průhledného nebo poloprůhledného elementu UIElement</span><span class="sxs-lookup"><span data-stu-id="a8a97-102">How to: Make a UIElement Transparent or Semi-Transparent</span></span>
<span data-ttu-id="a8a97-103">Tento příklad ukazuje, jak provádět <xref:System.Windows.UIElement> průhledných nebo poloprůhlednost.</span><span class="sxs-lookup"><span data-stu-id="a8a97-103">This example shows how to make a <xref:System.Windows.UIElement> transparent or semi-transparent.</span></span> <span data-ttu-id="a8a97-104">K nastavení vzhledu elementu průhledných nebo poloprůhledné, nastavte jeho <xref:System.Windows.UIElement.Opacity%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a8a97-104">To make an element transparent or semi-transparent, you set its <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="a8a97-105">Hodnota `0.0` nastaví prvek zcela transparentní, při hodnotu `1.0` bude zcela neprůhledná elementu.</span><span class="sxs-lookup"><span data-stu-id="a8a97-105">A value of `0.0` makes the element completely transparent, while a value of `1.0` makes the element completely opaque.</span></span> <span data-ttu-id="a8a97-106">Hodnota `0.5` nastaví prvek 50 % neprůhledných a tak dále.</span><span class="sxs-lookup"><span data-stu-id="a8a97-106">A value of `0.5` makes the element 50% opaque, and so on.</span></span> <span data-ttu-id="a8a97-107">Elementu <xref:System.Windows.UIElement.Opacity%2A> je nastaven na `1.0` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="a8a97-107">An element's <xref:System.Windows.UIElement.Opacity%2A> is set to `1.0` by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8a97-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8a97-108">Example</span></span>  
 <span data-ttu-id="a8a97-109">Následující příklad nastavuje <xref:System.Windows.UIElement.Opacity%2A> tlačítka na `0.25`, nastavení jako ho a její obsah (v tomto případě na tlačítko text) 25 % neprůhledné.</span><span class="sxs-lookup"><span data-stu-id="a8a97-109">The following example sets the <xref:System.Windows.UIElement.Opacity%2A> of a button to `0.25`, making it and its contents (in this case, the button's text) 25% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 <span data-ttu-id="a8a97-110">Pokud obsah elementu mají svůj vlastní <xref:System.Windows.UIElement.Opacity%2A> nastavení, tyto hodnoty se násobí proti obsahující elementy <xref:System.Windows.UIElement.Opacity%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8a97-110">If an element's contents have their own <xref:System.Windows.UIElement.Opacity%2A> settings, those values are multiplied against the containing elements <xref:System.Windows.UIElement.Opacity%2A>.</span></span>  
  
 <span data-ttu-id="a8a97-111">Následující příklad ilustruje tlačítko <xref:System.Windows.UIElement.Opacity%2A> k `0.25`a <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Image> řízení, které jsou součástí na tlačítko s `0.5`.</span><span class="sxs-lookup"><span data-stu-id="a8a97-111">The following example sets a button's <xref:System.Windows.UIElement.Opacity%2A> to `0.25`, and the <xref:System.Windows.UIElement.Opacity%2A> of an <xref:System.Windows.Controls.Image> control contained with in the button to `0.5`.</span></span> <span data-ttu-id="a8a97-112">V důsledku toho obrázek vypadá jako neprůhledností 12,5 %: 0,25 \* 0,5 = 0,125.</span><span class="sxs-lookup"><span data-stu-id="a8a97-112">As a result, the image appears 12.5% opaque: 0.25 \* 0.5 = 0.125.</span></span>  
  
 [!code-xaml[brushsamples_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 <span data-ttu-id="a8a97-113">Jiný způsob, jak řídit krytí elementu je nastavit krytí <xref:System.Windows.Media.Brush> který vybarví elementu.</span><span class="sxs-lookup"><span data-stu-id="a8a97-113">Another way to control the opacity of an element is to set the opacity of the <xref:System.Windows.Media.Brush> that paints the element.</span></span> <span data-ttu-id="a8a97-114">Tento přístup umožňuje selektivně alter krytí části elementu a poskytuje výkonnostních výhod oproti použití elementu <xref:System.Windows.UIElement.Opacity%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a8a97-114">This approach enables you to selectively alter the opacity of portions of an element, and provides performance benefits over using the element's <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="a8a97-115">Následující příklad nastavuje <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush> použita k vyplnění na tlačítko <xref:System.Windows.Controls.Control.Background%2A> je nastaven na `0.25`.</span><span class="sxs-lookup"><span data-stu-id="a8a97-115">The following example sets the <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush> used to paint the button's <xref:System.Windows.Controls.Control.Background%2A> is set to `0.25`.</span></span> <span data-ttu-id="a8a97-116">V důsledku toho je nástroj štětec pozadí 25 % neprůhledné, ale její obsah (text tlačítka) zůstanou neprůhledností 100 %.</span><span class="sxs-lookup"><span data-stu-id="a8a97-116">As a result, the brush's background is 25% opaque, but its contents (the button's text) remain 100% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 <span data-ttu-id="a8a97-117">Může také řídit krytí jednotlivé barvy v rámci štětce.</span><span class="sxs-lookup"><span data-stu-id="a8a97-117">You may also control the opacity of individual colors within a brush.</span></span> <span data-ttu-id="a8a97-118">Další informace o barvy a štětce najdete v tématu [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a8a97-118">For more information about colors and brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span> <span data-ttu-id="a8a97-119">Příkladem zobrazujícím postup animace elementu krytí, najdete v části [animace krytí Element nebo štětce](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).</span><span class="sxs-lookup"><span data-stu-id="a8a97-119">For an example showing how to animate an element's opacity, see [Animate the Opacity of an Element or Brush](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).</span></span>
