---
title: 'Postupy: Animace matice použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: eb596cf728f8a7cc1964963b8509f42bdd7a392a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344922"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="d5961-102">Postupy: Animace matice použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="d5961-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="d5961-103">Tento příklad ukazuje, jak <xref:System.Windows.Media.MatrixTransform.Matrix%2A> animovat vlastnost a <xref:System.Windows.Media.MatrixTransform> pomocí klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="d5961-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5961-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d5961-104">Example</span></span>  
 <span data-ttu-id="d5961-105">Následující příklad používá <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> třídu k <xref:System.Windows.Media.MatrixTransform.Matrix%2A> animaci vlastnosti <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="d5961-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="d5961-106">Příklad používá <xref:System.Windows.Media.MatrixTransform> objekt k transformaci vzhledu <xref:System.Windows.Controls.Button>a polohy .</span><span class="sxs-lookup"><span data-stu-id="d5961-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="d5961-107">Tato animace <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> používá třídu k vytvoření dvou klíčových snímků a provádí s nimi následující:</span><span class="sxs-lookup"><span data-stu-id="d5961-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1. <span data-ttu-id="d5961-108">Animuje <xref:System.Windows.Media.Matrix> první během prvních 0,2 sekundy.</span><span class="sxs-lookup"><span data-stu-id="d5961-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="d5961-109">Příklad změní <xref:System.Windows.Media.Matrix.M11%2A> vlastnosti <xref:System.Windows.Media.Matrix.M12%2A> a <xref:System.Windows.Media.Matrix>.</span><span class="sxs-lookup"><span data-stu-id="d5961-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="d5961-110">Tato změna způsobí, že tlačítko roztáhnout a stát se zkosený.</span><span class="sxs-lookup"><span data-stu-id="d5961-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="d5961-111">Příklad také změní <xref:System.Windows.Media.Matrix.OffsetX%2A> <xref:System.Windows.Media.Matrix.OffsetY%2A> vlastnosti a tak, aby tlačítko změnilo polohu.</span><span class="sxs-lookup"><span data-stu-id="d5961-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2. <span data-ttu-id="d5961-112">Animuje <xref:System.Windows.Media.Matrix> druhou po 1,0 sekundě.</span><span class="sxs-lookup"><span data-stu-id="d5961-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="d5961-113">Tlačítko se přesune do jiné polohy, zatímco tlačítko již není zkosené nebo roztažené.</span><span class="sxs-lookup"><span data-stu-id="d5961-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3. <span data-ttu-id="d5961-114">Opakuje animaci neomezeně dlouho.</span><span class="sxs-lookup"><span data-stu-id="d5961-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5961-115">Klíčové snímky, které <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> jsou odvozeny z objektu, vytvářejí náhlé skoky mezi hodnotami, to znamená, že pohyb animace je trhaný.</span><span class="sxs-lookup"><span data-stu-id="d5961-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="d5961-116">Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="d5961-116">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5961-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5961-117">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [<span data-ttu-id="d5961-118">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="d5961-118">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="d5961-119">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="d5961-119">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
