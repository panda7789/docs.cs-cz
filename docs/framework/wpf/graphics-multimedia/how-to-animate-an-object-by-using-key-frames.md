---
title: 'Postupy: Animace objektu pomocí klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: ffbe1845b634c8f94eb6a10dfa44fcf9903e0cd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933910"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="f75ca-102">Postupy: Animace objektu pomocí klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="f75ca-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="f75ca-103">Tento příklad ukazuje, jak animovat objekt, který v tomto příkladu je <xref:System.Windows.Controls.Page.Background%2A> vlastností <xref:System.Windows.Controls.Page> ovládacího prvku pomocí klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="f75ca-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f75ca-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f75ca-104">Example</span></span>  
 <span data-ttu-id="f75ca-105">Následující příklad používá <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> třídu k animaci změn barvy <xref:System.Windows.Controls.Page.Background%2A> pro vlastnost <xref:System.Windows.Controls.Page> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f75ca-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="f75ca-106">Ukázková animace se v pravidelných intervalech mění na jiný štětec na pozadí.</span><span class="sxs-lookup"><span data-stu-id="f75ca-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="f75ca-107">Tato animace používá <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> třídu k vytvoření tří různých klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="f75ca-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="f75ca-108">Animace používá klíčové snímky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f75ca-108">The animation uses key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="f75ca-109">Na konci první sekundy animuje instanci <xref:System.Windows.Media.LinearGradientBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="f75ca-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="f75ca-110">Tato část příkladu aplikuje lineární přechod na barvu pozadí, aby se barvy od žlutého po oranžová do červené.</span><span class="sxs-lookup"><span data-stu-id="f75ca-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2. <span data-ttu-id="f75ca-111">Na konci další sekundy animuje instanci <xref:System.Windows.Media.RadialGradientBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="f75ca-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="f75ca-112">Tato část příkladu aplikuje paprskový přechod na barvu pozadí, aby se barvy přechází z bílé na modrou na černou.</span><span class="sxs-lookup"><span data-stu-id="f75ca-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3. <span data-ttu-id="f75ca-113">Na konci třetí sekundy animuje instanci <xref:System.Windows.Media.DrawingBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="f75ca-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="f75ca-114">Tato část příkladu aplikuje na pozadí šachovnicový vzor.</span><span class="sxs-lookup"><span data-stu-id="f75ca-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4. <span data-ttu-id="f75ca-115">Animace se znovu spustí a zopakuje se neomezeně.</span><span class="sxs-lookup"><span data-stu-id="f75ca-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f75ca-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>je jediným typem klíčového snímku, který lze použít s <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> třídou.</span><span class="sxs-lookup"><span data-stu-id="f75ca-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="f75ca-117">Klíčové snímky, <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> jako je vytváření náhlých změn v hodnotách, to znamená, že se změny barev v tomto příkladu vyskytují náhle.</span><span class="sxs-lookup"><span data-stu-id="f75ca-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="f75ca-118">Úplnou ukázku najdete v tématu [Ukázka animace klíčových snímků](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="f75ca-118">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f75ca-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f75ca-119">See also</span></span>

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [<span data-ttu-id="f75ca-120">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="f75ca-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="f75ca-121">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="f75ca-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
