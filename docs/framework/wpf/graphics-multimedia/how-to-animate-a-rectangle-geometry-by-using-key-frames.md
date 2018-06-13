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
ms.openlocfilehash: 581dc89d21091ad0ce856d7a7ced84fd7bcea9d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559279"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a><span data-ttu-id="492c1-102">Postupy: Animace obdélníkové geometrie použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="492c1-102">How to: Animate a Rectangle Geometry by Using Key Frames</span></span>
<span data-ttu-id="492c1-103">Tento příklad ukazuje, jak animace <xref:System.Windows.Media.RectangleGeometry.Rect%2A> vlastnost <xref:System.Windows.Media.RectangleGeometry> pomocí klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="492c1-103">This example shows how to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="492c1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="492c1-104">Example</span></span>  
 <span data-ttu-id="492c1-105">Následující příklad používá <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Media.RectangleGeometry.Rect%2A> vlastnost <xref:System.Windows.Media.RectangleGeometry>.</span><span class="sxs-lookup"><span data-stu-id="492c1-105">The following example uses the <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>.</span></span> <span data-ttu-id="492c1-106">Tato animace používá tři klíčových snímků následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="492c1-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="492c1-107">Při první dvě sekundy používá instanci <xref:System.Windows.Media.Animation.LinearRectKeyFrame> třídy animace postupná změnu pozice, šířky a výšky obdélníku.</span><span class="sxs-lookup"><span data-stu-id="492c1-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearRectKeyFrame> class to animate a gradual change in the position, width, and height of a rectangle.</span></span> <span data-ttu-id="492c1-108">Lineární klíčových snímků jako <xref:System.Windows.Media.Animation.LinearRectKeyFrame> vytvořit hladký lineární přechod mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="492c1-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearRectKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="492c1-109">Během konec další půl sekundy používá instanci <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> třída najednou snížení výška rámečku.</span><span class="sxs-lookup"><span data-stu-id="492c1-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> class to suddenly decrease the height of the rectangle.</span></span> <span data-ttu-id="492c1-110">Diskrétní klíčových snímků jako <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> vytvořit nečekané změn mezi hodnotami, který je, poklesu výška probíhá rychle a není jemně.</span><span class="sxs-lookup"><span data-stu-id="492c1-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> create sudden changes between values, that is, the decrease in height occurs quickly and is not subtle.</span></span>  
  
3.  <span data-ttu-id="492c1-111">Během poslední dvou sekund, používá instanci <xref:System.Windows.Media.Animation.SplineRectKeyFrame> třída změnit rámeček zpět na původní velikost a umístění.</span><span class="sxs-lookup"><span data-stu-id="492c1-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame> class to change the rectangle back to its original size and position.</span></span> <span data-ttu-id="492c1-112">Křivkový klíčových snímků jako <xref:System.Windows.Media.Animation.SplineRectKeyFrame> vytvoření proměnné přechod mezi hodnotami podle hodnot <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="492c1-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineRectKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="492c1-113">V tomto příkladu změnu začne pomalu a urychluje exponenciálnímu ke konci čas segmentu.</span><span class="sxs-lookup"><span data-stu-id="492c1-113">In this example, the change begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="492c1-114">Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="492c1-114">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="492c1-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="492c1-115">See Also</span></span>  
 <xref:System.Windows.Media.RectangleGeometry>  
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>  
 <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>  
 [<span data-ttu-id="492c1-116">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="492c1-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="492c1-117">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="492c1-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
