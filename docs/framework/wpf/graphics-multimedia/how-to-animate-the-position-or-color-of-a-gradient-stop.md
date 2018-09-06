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
ms.openlocfilehash: fcbb546b64810416d3f7dbe052da77b7bc941e7a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43867424"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="c834f-102">Postupy: Animace umístění a barvy ukončení přechodu</span><span class="sxs-lookup"><span data-stu-id="c834f-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="c834f-103">Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.GradientStop.Color%2A> a <xref:System.Windows.Media.GradientStop.Offset%2A> z <xref:System.Windows.Media.GradientStop> objekty.</span><span class="sxs-lookup"><span data-stu-id="c834f-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c834f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c834f-104">Example</span></span>  
 <span data-ttu-id="c834f-105">Následující příklad animuje tři Přechodové zarážky dovnitř <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="c834f-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="c834f-106">V příkladu tři animace, z nichž každý animuje různé Přechodové zarážky:</span><span class="sxs-lookup"><span data-stu-id="c834f-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
-   <span data-ttu-id="c834f-107">První animace <xref:System.Windows.Media.Animation.DoubleAnimation>, animuje první ukončení přechodu <xref:System.Windows.Media.GradientStop.Offset%2A> od 0.0 do 1.0 a pak zpátky 0,0.</span><span class="sxs-lookup"><span data-stu-id="c834f-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="c834f-108">V důsledku toho první barvy v přechodu staffhubu od levého okraje pravé části obdélníku a pak zpátky na levé straně.</span><span class="sxs-lookup"><span data-stu-id="c834f-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
-   <span data-ttu-id="c834f-109">Druhé animace <xref:System.Windows.Media.Animation.ColorAnimation>, animuje druhý ukončení přechodu <xref:System.Windows.Media.GradientStop.Color%2A> z <xref:System.Windows.Media.Colors.Purple%2A> k <xref:System.Windows.Media.Colors.Yellow%2A> a pak zpátky <xref:System.Windows.Media.Colors.Purple%2A>.</span><span class="sxs-lookup"><span data-stu-id="c834f-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="c834f-110">Prostřední barva přechodu v důsledku toho změní z nachová na žlutou a zpět na fialový.</span><span class="sxs-lookup"><span data-stu-id="c834f-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
-   <span data-ttu-id="c834f-111">Třetí animace jiného <xref:System.Windows.Media.Animation.ColorAnimation>, animuje krytí třetí ukončení přechodu <xref:System.Windows.Media.GradientStop.Color%2A> podle -1 a pak zpátky.</span><span class="sxs-lookup"><span data-stu-id="c834f-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="c834f-112">V důsledku toho třetí barev v gradientu zmizí a pak stane neprůhledné.</span><span class="sxs-lookup"><span data-stu-id="c834f-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="c834f-113">Přestože tento příklad používá <xref:System.Windows.Media.LinearGradientBrush>, proces je stejný pro animaci <xref:System.Windows.Media.GradientStop> objektů uvnitř <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="c834f-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="c834f-114">Další příklady najdete v článku [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="c834f-114">For additional examples, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c834f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c834f-115">See Also</span></span>  
 <xref:System.Windows.Media.GradientStop>  
 [<span data-ttu-id="c834f-116">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="c834f-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="c834f-117">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="c834f-117">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
