---
title: 'Postupy: Animace změn velikosti pomocí klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 0629b6600444bd172af451fd7e970bff894d8047
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342359"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="8e20a-102">Postupy: Animace změn velikosti pomocí klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="8e20a-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="8e20a-103">Tento příklad ukazuje, jak animace změn velikosti použitím klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="8e20a-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e20a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e20a-104">Example</span></span>  
 <span data-ttu-id="8e20a-105">V následujícím příkladu <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Media.ArcSegment.Size%2A> vlastnost <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="8e20a-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="8e20a-106">Tato animace používá tři klíčové snímky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="8e20a-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="8e20a-107">Během prvního půl sekundy animace používá instanci <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> třídy postupně zvyšovat velikost oblouk. Lineární klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> Vytvoření hladkého lineárního přechodu mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="8e20a-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="8e20a-108">Na konci další půl sekundy, používá instanci <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> třídy prudce zvýšit velikost oblouku. Diskrétní klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> vytvoření i s náhlými přechodů mezi hodnotami, to znamená, dojde k náhlému změny velikosti a nejsou drobným.</span><span class="sxs-lookup"><span data-stu-id="8e20a-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3. <span data-ttu-id="8e20a-109">Za poslední 2 sekundy, používá instanci <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> třídy zvýšit velikost oblouk. Klíčové snímky SpLine, jako jsou <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> vytvoříte proměnné přechod mezi hodnotami podle hodnoty <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8e20a-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="8e20a-110">V tomto příkladu velikost oblouk zvyšuje pomalu zpočátku a pak exponenciálně zvyšuje na konci časového úseku.</span><span class="sxs-lookup"><span data-stu-id="8e20a-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="8e20a-111">Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="8e20a-111">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e20a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e20a-112">See also</span></span>

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [<span data-ttu-id="8e20a-113">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="8e20a-113">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="8e20a-114">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="8e20a-114">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
