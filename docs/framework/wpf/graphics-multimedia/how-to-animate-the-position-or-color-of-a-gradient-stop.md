---
title: "Postupy: Animace umístění a barvy ukončení přechodu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c5a72d5df9d7ff9cdd90d6e09a7dab574e2caaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="558b9-102">Postupy: Animace umístění a barvy ukončení přechodu</span><span class="sxs-lookup"><span data-stu-id="558b9-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="558b9-103">Tento příklad ukazuje, jak animace <xref:System.Windows.Media.GradientStop.Color%2A> a <xref:System.Windows.Media.GradientStop.Offset%2A> z <xref:System.Windows.Media.GradientStop> objekty.</span><span class="sxs-lookup"><span data-stu-id="558b9-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="558b9-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="558b9-104">Example</span></span>  
 <span data-ttu-id="558b9-105">Následující příklad animuje tři ukončení přechodu uvnitř <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="558b9-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="558b9-106">Tento příklad používá tři animací, z nichž každý animuje různé Přechodové zarážky:</span><span class="sxs-lookup"><span data-stu-id="558b9-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
-   <span data-ttu-id="558b9-107">První animace <xref:System.Windows.Media.Animation.DoubleAnimation>, animuje první Přechodové zarážky <xref:System.Windows.Media.GradientStop.Offset%2A> od 0,0 do 1,0 a pak zpátky na 0,0.</span><span class="sxs-lookup"><span data-stu-id="558b9-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="558b9-108">V důsledku toho první barvu v přechodu posuny z levé strany na pravé straně obdélníku a pak zpátky na levé straně.</span><span class="sxs-lookup"><span data-stu-id="558b9-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
-   <span data-ttu-id="558b9-109">Druhý animace <xref:System.Windows.Media.Animation.ColorAnimation>, animuje druhý Přechodové zarážky <xref:System.Windows.Media.GradientStop.Color%2A> z <xref:System.Windows.Media.Colors.Purple%2A> k <xref:System.Windows.Media.Colors.Yellow%2A> a pak zpátky na <xref:System.Windows.Media.Colors.Purple%2A>.</span><span class="sxs-lookup"><span data-stu-id="558b9-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="558b9-110">V důsledku toho změní střední barvu v přechodu z Fialová žlutý a zpět na fialový.</span><span class="sxs-lookup"><span data-stu-id="558b9-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
-   <span data-ttu-id="558b9-111">Třetí animace jiné <xref:System.Windows.Media.Animation.ColorAnimation>, animuje krytí třetí Přechodové zarážky <xref:System.Windows.Media.GradientStop.Color%2A> podle -1 a pak zpátky.</span><span class="sxs-lookup"><span data-stu-id="558b9-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="558b9-112">V důsledku toho třetí barvu v přechodu zmizí a pak stane neprůhledné.</span><span class="sxs-lookup"><span data-stu-id="558b9-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="558b9-113">I když tento příklad používá <xref:System.Windows.Media.LinearGradientBrush>, proces je stejný pro animace <xref:System.Windows.Media.GradientStop> objekty uvnitř <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="558b9-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="558b9-114">Další příklady najdete v tématu [štětce ukázka](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="558b9-114">For additional examples, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="558b9-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="558b9-115">See Also</span></span>  
 <xref:System.Windows.Media.GradientStop>  
 [<span data-ttu-id="558b9-116">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="558b9-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="558b9-117">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="558b9-117">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
