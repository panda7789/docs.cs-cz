---
title: 'Postupy: Animace barvy a krytí štětce SolidColorBrush'
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: 194f01d3d5aa4c2b5a08a6c3fdb3dc195b0e9e3e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392224"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a><span data-ttu-id="d0c07-102">Postupy: Animace barvy a krytí štětce SolidColorBrush</span><span class="sxs-lookup"><span data-stu-id="d0c07-102">How to: Animate the Color or Opacity of a SolidColorBrush</span></span>
<span data-ttu-id="d0c07-103">Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="d0c07-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0c07-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0c07-104">Example</span></span>  
 <span data-ttu-id="d0c07-105">Následující příklad používá tři animace pro animaci <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="d0c07-105">The following example uses three animations to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
-   <span data-ttu-id="d0c07-106">První animace <xref:System.Windows.Media.Animation.ColorAnimation>, se změní barva stopy <xref:System.Windows.Media.Colors.Gray%2A> vstupu myší v obdélníku.</span><span class="sxs-lookup"><span data-stu-id="d0c07-106">The first animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Gray%2A> when the mouse enters the rectangle.</span></span>  
  
-   <span data-ttu-id="d0c07-107">Další animace jiného <xref:System.Windows.Media.Animation.ColorAnimation>, se změní barva stopy <xref:System.Windows.Media.Colors.Orange%2A> když ukazatel myši opustí obdélníku.</span><span class="sxs-lookup"><span data-stu-id="d0c07-107">The next animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Orange%2A> when the mouse leaves the rectangle.</span></span>  
  
-   <span data-ttu-id="d0c07-108">Poslední animace <xref:System.Windows.Media.Animation.DoubleAnimation>, mění neprůhlednost štětce rovnou 0,0, když se stiskne levé tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="d0c07-108">The final animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, changes the brush's opacity to 0.0 when the left mouse button is pressed.</span></span>  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 <span data-ttu-id="d0c07-109">Ucelenější ukázku, která ukazuje, jak animovat různé druhy štětce, najdete v článku [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="d0c07-109">For a more complete sample, which shows how to animate different types of brushes, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="d0c07-110">Další informace o animace, najdete v článku [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d0c07-110">For more information about animation, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
 <span data-ttu-id="d0c07-111">Pro zajištění konzistence s další příklady animace, kód verze tohoto příkladu použijte <xref:System.Windows.Media.Animation.Storyboard> objekt jejich animace.</span><span class="sxs-lookup"><span data-stu-id="d0c07-111">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply their animations.</span></span> <span data-ttu-id="d0c07-112">Při použití jedné animace v kódu, je ale jednodušší použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda namísto použití <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="d0c07-112">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="d0c07-113">Příklad najdete v tématu [animace vlastnosti bez pomoci scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="d0c07-113">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0c07-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0c07-114">See Also</span></span>  
 [<span data-ttu-id="d0c07-115">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="d0c07-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="d0c07-116">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="d0c07-116">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="d0c07-117">Ukázka štětců</span><span class="sxs-lookup"><span data-stu-id="d0c07-117">Brushes Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159973)
