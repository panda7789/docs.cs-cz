---
title: 'Postupy: Animace řetězce pomocí klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 4a37408ad90fda12a95e66c1b44018967b376837
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204169"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a><span data-ttu-id="8d59e-102">Postupy: Animace řetězce pomocí klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="8d59e-102">How to: Animate a String by Using Key Frames</span></span>
<span data-ttu-id="8d59e-103">Tento příklad ukazuje, jak animovat řetězec, který v tomto příkladu je <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.Button> ovládacího prvku s použitím klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="8d59e-103">This example shows how to animate a string, which in this example is the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d59e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d59e-104">Example</span></span>  
 <span data-ttu-id="8d59e-105">V následujícím příkladu <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="8d59e-105">The following example uses the <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="8d59e-106">Instance pomocí klíčových snímků v tomto příkladu <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> třídy, protože řetězec animace, která je vytvořena s použitím klíčových snímků lze použít pouze diskrétní klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="8d59e-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> class because a string animation that is created with key frames can only use discrete key frames.</span></span> <span data-ttu-id="8d59e-107">Diskrétní klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> vytvoření i s náhlými přechodů mezi hodnotami, to znamená, změny animace dojde k rychlému a nejsou malý.</span><span class="sxs-lookup"><span data-stu-id="8d59e-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> create sudden jumps between values, that is, changes to the animation occur quickly and are not subtle.</span></span>  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="8d59e-108">Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="8d59e-108">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d59e-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d59e-109">See also</span></span>

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [<span data-ttu-id="8d59e-110">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="8d59e-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="8d59e-111">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="8d59e-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
