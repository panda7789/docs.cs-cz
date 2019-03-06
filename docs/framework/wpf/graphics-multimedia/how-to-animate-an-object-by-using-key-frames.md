---
title: 'Postupy: Animace objektu použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 1e0e464adf70aeeaecb522d328d3087ca66a530c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368555"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="6f7e7-102">Postupy: Animace objektu použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="6f7e7-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="6f7e7-103">Tento příklad ukazuje, jak pro animaci objektu, který v tomto příkladu je <xref:System.Windows.Controls.Page.Background%2A> vlastnost <xref:System.Windows.Controls.Page> ovládacího prvku s použitím klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="6f7e7-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f7e7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6f7e7-104">Example</span></span>  
 <span data-ttu-id="6f7e7-105">V následujícím příkladu <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> třídy animace barev změní pro <xref:System.Windows.Controls.Page.Background%2A> vlastnost <xref:System.Windows.Controls.Page> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6f7e7-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="6f7e7-106">Příklad animace změní na štětec pozadí různých v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="6f7e7-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="6f7e7-107">Používá tato animace <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> třídy za účelem vytvoření tří různých klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="6f7e7-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="6f7e7-108">Animace pomocí klíčových snímků následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6f7e7-108">The animation uses key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="6f7e7-109">Na konci prvního druhé animuje instance <xref:System.Windows.Media.LinearGradientBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="6f7e7-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="6f7e7-110">Tato část. Příklad se týká lineárního přechodu na barvu pozadí tak, aby změní barvu z žlutá na oranžovou na červenou.</span><span class="sxs-lookup"><span data-stu-id="6f7e7-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2.  <span data-ttu-id="6f7e7-111">Na konci do příští sekundy animuje instance <xref:System.Windows.Media.RadialGradientBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="6f7e7-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="6f7e7-112">Tato část. Příklad se týká paprskového přechodu na barvu pozadí tak, aby změní barvu z prázdné na modrou na černou.</span><span class="sxs-lookup"><span data-stu-id="6f7e7-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3.  <span data-ttu-id="6f7e7-113">Na konci třetího druhé animuje instance <xref:System.Windows.Media.DrawingBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="6f7e7-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="6f7e7-114">Tato část příklad se týká šachovnicový vzor na pozadí.</span><span class="sxs-lookup"><span data-stu-id="6f7e7-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4.  <span data-ttu-id="6f7e7-115">Animace začne znovu a opakuje bez omezení.</span><span class="sxs-lookup"><span data-stu-id="6f7e7-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f7e7-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> je jediným typem klíčový snímek, který vám pomůže s <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> třídy.</span><span class="sxs-lookup"><span data-stu-id="6f7e7-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="6f7e7-117">Klíč snímků jako <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> vytvořit náhlých změn v hodnotách, to znamená, změny barev v tomto příkladu dojde k náhlému.</span><span class="sxs-lookup"><span data-stu-id="6f7e7-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="6f7e7-118">Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="6f7e7-118">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f7e7-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f7e7-119">See also</span></span>
- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [<span data-ttu-id="6f7e7-120">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="6f7e7-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="6f7e7-121">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="6f7e7-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
