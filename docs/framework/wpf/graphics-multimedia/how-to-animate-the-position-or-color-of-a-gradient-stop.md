---
title: 'Postupy: Animace umístění a barvy ukončení přechodu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: aeae33f5f3c8016808988f58d61969e9b6f05039
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452841"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="bc304-102">Postupy: Animace umístění a barvy ukončení přechodu</span><span class="sxs-lookup"><span data-stu-id="bc304-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="bc304-103">Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.GradientStop.Color%2A> a <xref:System.Windows.Media.GradientStop.Offset%2A> objektů <xref:System.Windows.Media.GradientStop>.</span><span class="sxs-lookup"><span data-stu-id="bc304-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc304-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc304-104">Example</span></span>  
 <span data-ttu-id="bc304-105">Následující příklad animuje tři zarážky přechodu v rámci <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="bc304-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="bc304-106">V tomto příkladu se používají tři animace, z nichž každá animuje jiné zarážky přechodu:</span><span class="sxs-lookup"><span data-stu-id="bc304-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
- <span data-ttu-id="bc304-107">První animace, <xref:System.Windows.Media.Animation.DoubleAnimation>, animuje první <xref:System.Windows.Media.GradientStop.Offset%2A> zastavení přechodu z 0,0 na 1,0 a pak zpět na 0,0.</span><span class="sxs-lookup"><span data-stu-id="bc304-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="bc304-108">V důsledku toho se první barva v přechodu posouvá od levé strany obdélníku k pravé straně obdélníku a pak se vrátí na levou stranu.</span><span class="sxs-lookup"><span data-stu-id="bc304-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
- <span data-ttu-id="bc304-109">Druhá animace, <xref:System.Windows.Media.Animation.ColorAnimation>, animuje druhé <xref:System.Windows.Media.GradientStop.Color%2A> zastavení přechodu z <xref:System.Windows.Media.Colors.Purple%2A> na <xref:System.Windows.Media.Colors.Yellow%2A> a následně zpět na <xref:System.Windows.Media.Colors.Purple%2A>.</span><span class="sxs-lookup"><span data-stu-id="bc304-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="bc304-110">V důsledku toho se Prostřední barva v přechodu změní ze fialová na žlutou a zpátky na fialovou.</span><span class="sxs-lookup"><span data-stu-id="bc304-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
- <span data-ttu-id="bc304-111">Třetí animace, další <xref:System.Windows.Media.Animation.ColorAnimation>, animuje neprůhlednost třetí <xref:System.Windows.Media.GradientStop.Color%2A> zastavení přechodu na-1 a pak zpět.</span><span class="sxs-lookup"><span data-stu-id="bc304-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="bc304-112">V důsledku toho se třetí barva v přechodu zmizí a pak se znovu neprůhledná.</span><span class="sxs-lookup"><span data-stu-id="bc304-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="bc304-113">I když tento příklad používá <xref:System.Windows.Media.LinearGradientBrush>, proces je stejný pro animování <xref:System.Windows.Media.GradientStop> objektů uvnitř <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="bc304-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="bc304-114">Další příklady naleznete v [ukázce štětce](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="bc304-114">For additional examples, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc304-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc304-115">See also</span></span>

- <xref:System.Windows.Media.GradientStop>
- [<span data-ttu-id="bc304-116">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="bc304-116">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="bc304-117">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="bc304-117">Storyboards Overview</span></span>](storyboards-overview.md)
