---
title: 'Postupy: Použití transformací na text'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
ms.openlocfilehash: fd86293c539bf58ac93894e0b879dddb984825e1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378941"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="c1c2b-102">Postupy: Použití transformací na text</span><span class="sxs-lookup"><span data-stu-id="c1c2b-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="c1c2b-103">Transformace můžete změnit zobrazení textu v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="c1c2b-104">Následující příklady používají různé druhy transformace vykreslování ovlivnit zobrazení textu v <xref:System.Windows.Controls.TextBlock> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1c2b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1c2b-105">Example</span></span>  
 <span data-ttu-id="c1c2b-106">Následující příklad ukazuje text otočený o určitému bodu v rovině dvojrozměrné x-y.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 <span data-ttu-id="c1c2b-107">![Text otočen pomocí RotateTransform](./media/transformedtext01.jpg "TransformedText01")</span><span class="sxs-lookup"><span data-stu-id="c1c2b-107">![Text rotated using a RotateTransform](./media/transformedtext01.jpg "TransformedText01")</span></span>  
<span data-ttu-id="c1c2b-108">Příklad textu otočenou o 90 stupňů</span><span class="sxs-lookup"><span data-stu-id="c1c2b-108">Example of text rotated 90 degrees</span></span>  
  
 <span data-ttu-id="c1c2b-109">Následující příklad kódu používá <xref:System.Windows.Media.RotateTransform> otočit text.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-109">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="c1c2b-110"><xref:System.Windows.Media.RotateTransform.Angle%2A> Hodnotu 90 otočí element 90 stupňů po směru hodinových ručiček.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-110">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="c1c2b-111">Následující příklad ukazuje, druhý řádek textu měřítkem řídit 150 % podél osy x a třetí řádek textu měřítkem řídit 150 % podél osy y.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-111">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 <span data-ttu-id="c1c2b-112">![Text, škálování, použití ScaleTransform –](./media/transformedtext02.jpg "TransformedText02")</span><span class="sxs-lookup"><span data-stu-id="c1c2b-112">![Text scaled using a ScaleTransform](./media/transformedtext02.jpg "TransformedText02")</span></span>  
<span data-ttu-id="c1c2b-113">Příklad text se změnou měřítka</span><span class="sxs-lookup"><span data-stu-id="c1c2b-113">Example of scaled text</span></span>  
  
 <span data-ttu-id="c1c2b-114">Následující příklad kódu používá <xref:System.Windows.Media.ScaleTransform> na škálování text z jeho původní velikost.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-114">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  <span data-ttu-id="c1c2b-115">Škálování text není stejný jako zvýšit velikost písma textu.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-115">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="c1c2b-116">Velikost písma se počítají nezávisle na sobě negace nejlepší řešení při různých velikostech.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-116">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="c1c2b-117">Text se změnou měřítka, na druhé straně zachová poměr stran původní velikost textu.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-117">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="c1c2b-118">Následující příklad ukazuje text zkosený podél osy x.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-118">The following example shows text skewed along the x-axis.</span></span>  
  
 <span data-ttu-id="c1c2b-119">![Text zkosený pomocí SkewTransform](./media/transformedtext03.jpg "TransformedText03")</span><span class="sxs-lookup"><span data-stu-id="c1c2b-119">![Text skewed using a SkewTransform](./media/transformedtext03.jpg "TransformedText03")</span></span>  
<span data-ttu-id="c1c2b-120">Příklad zkreslený text</span><span class="sxs-lookup"><span data-stu-id="c1c2b-120">Example of skewed text</span></span>  
  
 <span data-ttu-id="c1c2b-121">Následující příklad kódu používá <xref:System.Windows.Media.SkewTransform> zkosení text.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-121">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="c1c2b-122">Nerovnoměrná distribuce, označované také jako zkosení je transformace, která roztáhne souřadnicového prostoru nerovnoměrné způsobem.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-122">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="c1c2b-123">V tomto příkladu jsou dva textové řetězce výrazně nerovnoměrnou distribucí °-30 a 30 ° podél souřadnici x.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-123">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="c1c2b-124">Následující příklad ukazuje textové přeložit nebo přesunuty podél x a osy y.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-124">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 <span data-ttu-id="c1c2b-125">![Text odsazení pomocí TranslateTransform](./media/transformedtext04.jpg "TransformedText04")</span><span class="sxs-lookup"><span data-stu-id="c1c2b-125">![Text offset using a TranslateTransform](./media/transformedtext04.jpg "TransformedText04")</span></span>  
<span data-ttu-id="c1c2b-126">Příklad přeloženého textu</span><span class="sxs-lookup"><span data-stu-id="c1c2b-126">Example of translated text</span></span>  
  
 <span data-ttu-id="c1c2b-127">Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> odsazení textu.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-127">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="c1c2b-128">V tomto příkladu vytvoří kopii mírně posunu text pod primární text efektem stínování.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-128">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <span data-ttu-id="c1c2b-129"><xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Poskytuje bohatou sadu funkcí pro zajištění efekty stínování.</span><span class="sxs-lookup"><span data-stu-id="c1c2b-129">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="c1c2b-130">Další informace najdete v tématu [vytvoření textu se stínem](how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="c1c2b-130">For more information, see [Create Text with a Shadow](how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c2b-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1c2b-131">See also</span></span>
- [<span data-ttu-id="c1c2b-132">Použití animací na text</span><span class="sxs-lookup"><span data-stu-id="c1c2b-132">Apply Animations to Text</span></span>](how-to-apply-animations-to-text.md)
