---
title: 'Postupy: Animace obdélníkové geometrie použitím klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: bcc9e7f198b8a20ffe13daf6508fb8a735937652
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344683"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a><span data-ttu-id="d3e96-102">Postupy: Animace obdélníkové geometrie použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="d3e96-102">How to: Animate a Rectangle Geometry by Using Key Frames</span></span>
<span data-ttu-id="d3e96-103">Tento příklad ukazuje, jak <xref:System.Windows.Media.RectangleGeometry.Rect%2A> animovat vlastnost a <xref:System.Windows.Media.RectangleGeometry> pomocí klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="d3e96-103">This example shows how to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3e96-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3e96-104">Example</span></span>  
 <span data-ttu-id="d3e96-105">Následující příklad používá <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> třídu k <xref:System.Windows.Media.RectangleGeometry.Rect%2A> animaci vlastnosti <xref:System.Windows.Media.RectangleGeometry>.</span><span class="sxs-lookup"><span data-stu-id="d3e96-105">The following example uses the <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>.</span></span> <span data-ttu-id="d3e96-106">Tato animace používá tři klíčové snímky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d3e96-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="d3e96-107">Během prvních dvou sekund použije instanci <xref:System.Windows.Media.Animation.LinearRectKeyFrame> třídy k animaci postupné změny polohy, šířky a výšky obdélníku.</span><span class="sxs-lookup"><span data-stu-id="d3e96-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearRectKeyFrame> class to animate a gradual change in the position, width, and height of a rectangle.</span></span> <span data-ttu-id="d3e96-108">Lineární klíčové <xref:System.Windows.Media.Animation.LinearRectKeyFrame> snímky, jako je vytvoření hladkého lineárního přechodu mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="d3e96-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearRectKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="d3e96-109">Během konce další poloviny sekundy, používá <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> instance třídy náhle snížit výšku obdélníku.</span><span class="sxs-lookup"><span data-stu-id="d3e96-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> class to suddenly decrease the height of the rectangle.</span></span> <span data-ttu-id="d3e96-110">Diskrétní klíčové snímky, <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> jako je vytvoření náhlých změn mezi hodnotami, to znamená, že snížení výšky dochází rychle a není jemné.</span><span class="sxs-lookup"><span data-stu-id="d3e96-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> create sudden changes between values, that is, the decrease in height occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="d3e96-111">Během posledních dvou sekund, používá <xref:System.Windows.Media.Animation.SplineRectKeyFrame> instance třídy změnit obdélník zpět na původní velikost a umístění.</span><span class="sxs-lookup"><span data-stu-id="d3e96-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame> class to change the rectangle back to its original size and position.</span></span> <span data-ttu-id="d3e96-112">Klíčové snímky spline, jako je <xref:System.Windows.Media.Animation.SplineRectKeyFrame> vytvoření proměnné přechodu mezi hodnotami podle hodnot vlastnosti. <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A></span><span class="sxs-lookup"><span data-stu-id="d3e96-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineRectKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="d3e96-113">V tomto příkladu změna začíná pomalu a exponenciálně urychluje ke konci časového segmentu.</span><span class="sxs-lookup"><span data-stu-id="d3e96-113">In this example, the change begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="d3e96-114">Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="d3e96-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e96-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3e96-115">See also</span></span>

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [<span data-ttu-id="d3e96-116">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="d3e96-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="d3e96-117">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="d3e96-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
