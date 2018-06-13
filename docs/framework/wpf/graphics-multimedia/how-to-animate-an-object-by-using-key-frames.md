---
title: 'Postupy: Animace objektu použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 7dc49bc6b3f9156507cb821bfc32b269365b206c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558537"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="04cdb-102">Postupy: Animace objektu použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="04cdb-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="04cdb-103">Tento příklad ukazuje, jak animace objekt, který je v tomto příkladu <xref:System.Windows.Controls.Page.Background%2A> vlastnost <xref:System.Windows.Controls.Page> ovládacího prvku pomocí klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="04cdb-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04cdb-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="04cdb-104">Example</span></span>  
 <span data-ttu-id="04cdb-105">Následující příklad používá <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> třídy animace barva změny pro <xref:System.Windows.Controls.Page.Background%2A> vlastnost <xref:System.Windows.Controls.Page> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="04cdb-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="04cdb-106">Příklad animace se změní na různých pozadí štětce v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="04cdb-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="04cdb-107">Používá tento animace <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> třídy za účelem vytvoření tři různé klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="04cdb-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="04cdb-108">Animace používá klíčových snímků následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="04cdb-108">The animation uses key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="04cdb-109">Na konci prvního druhý animuje instanci <xref:System.Windows.Media.LinearGradientBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="04cdb-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="04cdb-110">Tato část v příkladu se týká lineárního přechodu na barvu pozadí tak, aby barva přechází z žlutý do oranžová na červený.</span><span class="sxs-lookup"><span data-stu-id="04cdb-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2.  <span data-ttu-id="04cdb-111">Na konci do příští sekundy animuje instanci <xref:System.Windows.Media.RadialGradientBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="04cdb-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="04cdb-112">Tato část v příkladu se týká kruhového přechodu na barvu pozadí tak, aby barva přechází z prázdné na modrou do černé.</span><span class="sxs-lookup"><span data-stu-id="04cdb-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3.  <span data-ttu-id="04cdb-113">Na konci třetí druhý animuje instanci <xref:System.Windows.Media.DrawingBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="04cdb-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="04cdb-114">Tato část příklad se týká pouze šachovnicový vzorek na pozadí.</span><span class="sxs-lookup"><span data-stu-id="04cdb-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4.  <span data-ttu-id="04cdb-115">Animace začne počítat od začátku a opakuje bez omezení.</span><span class="sxs-lookup"><span data-stu-id="04cdb-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04cdb-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> je jediným typem klíče rámce, který můžete použít s <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> třídy.</span><span class="sxs-lookup"><span data-stu-id="04cdb-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="04cdb-117">Klíč rámců jako <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> vytvořit nečekané změn v hodnoty, který je, změny barev v tomto příkladu dojde k najednou.</span><span class="sxs-lookup"><span data-stu-id="04cdb-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="04cdb-118">Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="04cdb-118">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04cdb-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="04cdb-119">See Also</span></span>  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [<span data-ttu-id="04cdb-120">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="04cdb-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="04cdb-121">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="04cdb-121">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
