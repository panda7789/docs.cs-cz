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
ms.openlocfilehash: 08b85935e0cb1ababd1fb63b9d02518ea3fcfa17
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452880"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a><span data-ttu-id="83093-102">Postupy: Animace barvy a krytí štětce SolidColorBrush</span><span class="sxs-lookup"><span data-stu-id="83093-102">How to: Animate the Color or Opacity of a SolidColorBrush</span></span>
<span data-ttu-id="83093-103">Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.Brush.Opacity%2A> <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="83093-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83093-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="83093-104">Example</span></span>  
 <span data-ttu-id="83093-105">Následující příklad používá tři animace k animaci <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.Brush.Opacity%2A> <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="83093-105">The following example uses three animations to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
- <span data-ttu-id="83093-106">První animace, <xref:System.Windows.Media.Animation.ColorAnimation>, změní barvu štětce na <xref:System.Windows.Media.Colors.Gray%2A>, když ukazatel myši vstoupí do obdélníku.</span><span class="sxs-lookup"><span data-stu-id="83093-106">The first animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Gray%2A> when the mouse enters the rectangle.</span></span>  
  
- <span data-ttu-id="83093-107">Další animace, jinou <xref:System.Windows.Media.Animation.ColorAnimation>, změní barvu štětce na <xref:System.Windows.Media.Colors.Orange%2A>, když myš opustí obdélník.</span><span class="sxs-lookup"><span data-stu-id="83093-107">The next animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Orange%2A> when the mouse leaves the rectangle.</span></span>  
  
- <span data-ttu-id="83093-108">Poslední animace, <xref:System.Windows.Media.Animation.DoubleAnimation>, změní krytí štětce na 0,0 při stisknutí levého tlačítka myši.</span><span class="sxs-lookup"><span data-stu-id="83093-108">The final animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, changes the brush's opacity to 0.0 when the left mouse button is pressed.</span></span>  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 <span data-ttu-id="83093-109">Úplnější ukázku, která ukazuje, jak animovat různé typy štětců, naleznete v [ukázce štětce](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="83093-109">For a more complete sample, which shows how to animate different types of brushes, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="83093-110">Další informace o animacích najdete v [přehledu animace](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="83093-110">For more information about animation, see the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="83093-111">Pro zajištění konzistence s dalšími příklady animací používají verze kódu v tomto příkladu objekt <xref:System.Windows.Media.Animation.Storyboard> k aplikování animací.</span><span class="sxs-lookup"><span data-stu-id="83093-111">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply their animations.</span></span> <span data-ttu-id="83093-112">Nicméně při použití jedné animace v kódu je jednodušší použít metodu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> namísto použití <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="83093-112">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="83093-113">Příklad naleznete v tématu [animace vlastnosti bez použití scénáře](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="83093-113">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83093-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="83093-114">See also</span></span>

- [<span data-ttu-id="83093-115">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="83093-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="83093-116">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="83093-116">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="83093-117">Ukázka štětců</span><span class="sxs-lookup"><span data-stu-id="83093-117">Brushes Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
