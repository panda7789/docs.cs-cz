---
title: 'Postupy: Animace matice pomocí klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: ff5320fa5b4441ae3e0f414b274ab9118b77ec50
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336795"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="c71b3-102">Postupy: Animace matice pomocí klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="c71b3-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="c71b3-103">Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform> použitím klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="c71b3-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c71b3-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c71b3-104">Example</span></span>  
 <span data-ttu-id="c71b3-105">V následujícím příkladu <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Media.MatrixTransform.Matrix%2A> vlastnost <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="c71b3-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="c71b3-106">V příkladu se používá <xref:System.Windows.Media.MatrixTransform> objektu k transformaci vzhledu a umístění <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="c71b3-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="c71b3-107">Používá tato animace <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> třídy k vytvoření dvou klíčových snímků a provede následující s nimi:</span><span class="sxs-lookup"><span data-stu-id="c71b3-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1. <span data-ttu-id="c71b3-108">Animuje první <xref:System.Windows.Media.Matrix> během prvních 0,2 sekund.</span><span class="sxs-lookup"><span data-stu-id="c71b3-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="c71b3-109">Příklad změn <xref:System.Windows.Media.Matrix.M11%2A> a <xref:System.Windows.Media.Matrix.M12%2A> vlastnosti <xref:System.Windows.Media.Matrix>.</span><span class="sxs-lookup"><span data-stu-id="c71b3-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="c71b3-110">Tato změna způsobí, že tlačítko roztažení a stát zešikmená.</span><span class="sxs-lookup"><span data-stu-id="c71b3-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="c71b3-111">V příkladu se také změní <xref:System.Windows.Media.Matrix.OffsetX%2A> a <xref:System.Windows.Media.Matrix.OffsetY%2A> vlastnosti tak, aby se tlačítko změní pozice.</span><span class="sxs-lookup"><span data-stu-id="c71b3-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2. <span data-ttu-id="c71b3-112">Animuje druhý <xref:System.Windows.Media.Matrix> na 1.0 sekund.</span><span class="sxs-lookup"><span data-stu-id="c71b3-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="c71b3-113">Tlačítko pohybuje na jinou pracovní pozici, zatímco na tlačítko se už zkosený, nebo roztažená.</span><span class="sxs-lookup"><span data-stu-id="c71b3-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3. <span data-ttu-id="c71b3-114">Opakuje se animace po neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="c71b3-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c71b3-115">Klíčové snímky, které jsou odvozeny z <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> objekt vytvořit i s náhlými rozdíly mezi jednotlivými hodnotami, to znamená, je přehrávat nepravidelně přesun animace.</span><span class="sxs-lookup"><span data-stu-id="c71b3-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="c71b3-116">Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="c71b3-116">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c71b3-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c71b3-117">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [<span data-ttu-id="c71b3-118">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="c71b3-118">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="c71b3-119">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="c71b3-119">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
