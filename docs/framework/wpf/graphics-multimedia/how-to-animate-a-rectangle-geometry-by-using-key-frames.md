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
ms.openlocfilehash: 30bd09ac61c855e0cda81261ca652f0574aa73e3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375932"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a><span data-ttu-id="7f676-102">Postupy: Animace obdélníkové geometrie použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="7f676-102">How to: Animate a Rectangle Geometry by Using Key Frames</span></span>
<span data-ttu-id="7f676-103">Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.RectangleGeometry.Rect%2A> vlastnost <xref:System.Windows.Media.RectangleGeometry> použitím klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="7f676-103">This example shows how to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f676-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f676-104">Example</span></span>  
 <span data-ttu-id="7f676-105">V následujícím příkladu <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Media.RectangleGeometry.Rect%2A> vlastnost <xref:System.Windows.Media.RectangleGeometry>.</span><span class="sxs-lookup"><span data-stu-id="7f676-105">The following example uses the <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>.</span></span> <span data-ttu-id="7f676-106">Tato animace používá tři klíčové snímky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7f676-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="7f676-107">Během prvních dvou sekund používá instanci <xref:System.Windows.Media.Animation.LinearRectKeyFrame> třídy pro animaci postupné změny v pozici, šířku a výšku obdélníku.</span><span class="sxs-lookup"><span data-stu-id="7f676-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearRectKeyFrame> class to animate a gradual change in the position, width, and height of a rectangle.</span></span> <span data-ttu-id="7f676-108">Lineární klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.LinearRectKeyFrame> Vytvoření hladkého lineárního přechodu mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="7f676-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearRectKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="7f676-109">Při ukončení na další půl sekundy, používá instanci <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> třídy se náhle výškou pravoúhelníku.</span><span class="sxs-lookup"><span data-stu-id="7f676-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> class to suddenly decrease the height of the rectangle.</span></span> <span data-ttu-id="7f676-110">Diskrétní klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> vytvořit náhlých změn mezi hodnotami, to znamená, snížení výšky proběhne rychle a není jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="7f676-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> create sudden changes between values, that is, the decrease in height occurs quickly and is not subtle.</span></span>  
  
3.  <span data-ttu-id="7f676-111">Během poslední dvě sekundy, používá instanci <xref:System.Windows.Media.Animation.SplineRectKeyFrame> třídy změnit obdélník zpět na původní velikost a umístění.</span><span class="sxs-lookup"><span data-stu-id="7f676-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame> class to change the rectangle back to its original size and position.</span></span> <span data-ttu-id="7f676-112">Klíčové snímky SpLine, jako jsou <xref:System.Windows.Media.Animation.SplineRectKeyFrame> vytvoříte proměnné přechod mezi hodnotami podle hodnoty <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7f676-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineRectKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="7f676-113">V tomto příkladu změnu začne pomalu a zrychluje exponenciálně na konci časového úseku.</span><span class="sxs-lookup"><span data-stu-id="7f676-113">In this example, the change begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="7f676-114">Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="7f676-114">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f676-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f676-115">See also</span></span>
- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [<span data-ttu-id="7f676-116">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="7f676-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="7f676-117">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="7f676-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
