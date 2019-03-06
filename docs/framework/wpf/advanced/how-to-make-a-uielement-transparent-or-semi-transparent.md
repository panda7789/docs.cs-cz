---
title: 'Postupy: Vytvoření průhledného nebo poloprůhledného elementu UIElement'
ms.date: 03/30/2017
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
ms.openlocfilehash: 1de9a7e11fee241ecb71242e9808e77b7e5e63b0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370524"
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a><span data-ttu-id="a4638-102">Postupy: Vytvoření průhledného nebo poloprůhledného elementu UIElement</span><span class="sxs-lookup"><span data-stu-id="a4638-102">How to: Make a UIElement Transparent or Semi-Transparent</span></span>
<span data-ttu-id="a4638-103">Tento příklad ukazuje, jak vytvořit <xref:System.Windows.UIElement> průhledného nebo poloprůhledného.</span><span class="sxs-lookup"><span data-stu-id="a4638-103">This example shows how to make a <xref:System.Windows.UIElement> transparent or semi-transparent.</span></span> <span data-ttu-id="a4638-104">Chcete-li prvek průhledného nebo poloprůhledného, nastavíte jeho <xref:System.Windows.UIElement.Opacity%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a4638-104">To make an element transparent or semi-transparent, you set its <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="a4638-105">Hodnota `0.0` nastaví prvek zcela transparentní, při hodnotu `1.0` nastaví prvek stane zcela neprůhledný.</span><span class="sxs-lookup"><span data-stu-id="a4638-105">A value of `0.0` makes the element completely transparent, while a value of `1.0` makes the element completely opaque.</span></span> <span data-ttu-id="a4638-106">Hodnota `0.5` nastaví prvek 50 % neprůhledných a tak dále.</span><span class="sxs-lookup"><span data-stu-id="a4638-106">A value of `0.5` makes the element 50% opaque, and so on.</span></span> <span data-ttu-id="a4638-107">Elementu <xref:System.Windows.UIElement.Opacity%2A> je nastavena na `1.0` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="a4638-107">An element's <xref:System.Windows.UIElement.Opacity%2A> is set to `1.0` by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4638-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4638-108">Example</span></span>  
 <span data-ttu-id="a4638-109">Následující příklad nastaví <xref:System.Windows.UIElement.Opacity%2A> tlačítka na `0.25`, provádění a její obsah (v tomto případě text tlačítka) 25 % neprůhledné.</span><span class="sxs-lookup"><span data-stu-id="a4638-109">The following example sets the <xref:System.Windows.UIElement.Opacity%2A> of a button to `0.25`, making it and its contents (in this case, the button's text) 25% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 <span data-ttu-id="a4638-110">Pokud obsah elementu má svoje vlastní <xref:System.Windows.UIElement.Opacity%2A> nastavení tyto hodnoty jsou vynásobené proti obsahující prvky <xref:System.Windows.UIElement.Opacity%2A>.</span><span class="sxs-lookup"><span data-stu-id="a4638-110">If an element's contents have their own <xref:System.Windows.UIElement.Opacity%2A> settings, those values are multiplied against the containing elements <xref:System.Windows.UIElement.Opacity%2A>.</span></span>  
  
 <span data-ttu-id="a4638-111">Následující příklad nastaví tlačítka <xref:System.Windows.UIElement.Opacity%2A> k `0.25`a <xref:System.Windows.UIElement.Opacity%2A> ze <xref:System.Windows.Controls.Image> ovládací prvek obsažený v tlačítka s `0.5`.</span><span class="sxs-lookup"><span data-stu-id="a4638-111">The following example sets a button's <xref:System.Windows.UIElement.Opacity%2A> to `0.25`, and the <xref:System.Windows.UIElement.Opacity%2A> of an <xref:System.Windows.Controls.Image> control contained with in the button to `0.5`.</span></span> <span data-ttu-id="a4638-112">Obrázek v důsledku toho se zobrazí 12,5 % neprůhledné: 0.25 \* 0.5 = 0.125.</span><span class="sxs-lookup"><span data-stu-id="a4638-112">As a result, the image appears 12.5% opaque: 0.25 \* 0.5 = 0.125.</span></span>  
  
 [!code-xaml[brushsamples_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 <span data-ttu-id="a4638-113">Dalším způsobem, jak řídit krytí elementu je nastavit neprůhlednost <xref:System.Windows.Media.Brush> , který vykreslí element.</span><span class="sxs-lookup"><span data-stu-id="a4638-113">Another way to control the opacity of an element is to set the opacity of the <xref:System.Windows.Media.Brush> that paints the element.</span></span> <span data-ttu-id="a4638-114">Tento přístup umožňuje selektivně alter krytí částí elementu a poskytuje výkonnostních výhod oproti použití prvku <xref:System.Windows.UIElement.Opacity%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a4638-114">This approach enables you to selectively alter the opacity of portions of an element, and provides performance benefits over using the element's <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="a4638-115">Následující příklad nastaví <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush> používá k malování tlačítka <xref:System.Windows.Controls.Control.Background%2A> je nastavena na `0.25`.</span><span class="sxs-lookup"><span data-stu-id="a4638-115">The following example sets the <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush> used to paint the button's <xref:System.Windows.Controls.Control.Background%2A> is set to `0.25`.</span></span> <span data-ttu-id="a4638-116">V důsledku toho štětec pozadí je neprůhledný 25 %, ale jeho obsah (text tlačítka) zůstávají neprůhledné 100 %.</span><span class="sxs-lookup"><span data-stu-id="a4638-116">As a result, the brush's background is 25% opaque, but its contents (the button's text) remain 100% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 <span data-ttu-id="a4638-117">Můžete také řídit krytí jednotlivé barvy v rámci štětce.</span><span class="sxs-lookup"><span data-stu-id="a4638-117">You may also control the opacity of individual colors within a brush.</span></span> <span data-ttu-id="a4638-118">Další informace o barvy a štětce naleznete v tématu [Malování plnými barvami a přechody přehled](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a4638-118">For more information about colors and brushes, see [Painting with Solid Colors and Gradients Overview](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span> <span data-ttu-id="a4638-119">Příklad ukazuje, jak animace krytí elementu, naleznete v tématu [animace krytí elementu nebo štětce](../graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).</span><span class="sxs-lookup"><span data-stu-id="a4638-119">For an example showing how to animate an element's opacity, see [Animate the Opacity of an Element or Brush](../graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).</span></span>
