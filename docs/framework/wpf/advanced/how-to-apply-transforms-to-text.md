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
ms.openlocfilehash: b749d21c1b5940d216e244393eeb3c133dc153b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956473"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="84928-102">Postupy: Použití transformací na text</span><span class="sxs-lookup"><span data-stu-id="84928-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="84928-103">Transformace mohou změnit zobrazení textu v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="84928-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="84928-104">Následující příklady používají různé typy transformací vykreslování pro vliv zobrazení textu v <xref:System.Windows.Controls.TextBlock> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="84928-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84928-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="84928-105">Example</span></span>  
 <span data-ttu-id="84928-106">Následující příklad ukazuje text otočený o zadaný bod v dvojrozměrné rovině x-y.</span><span class="sxs-lookup"><span data-stu-id="84928-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 ![Text otočený pomocí RotateTransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 <span data-ttu-id="84928-108">Následující příklad kódu používá <xref:System.Windows.Media.RotateTransform> pro otočení textu.</span><span class="sxs-lookup"><span data-stu-id="84928-108">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="84928-109"><xref:System.Windows.Media.RotateTransform.Angle%2A> Hodnota 90 otočí prvek 90 stupňů po směru hodinových ručiček.</span><span class="sxs-lookup"><span data-stu-id="84928-109">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="84928-110">Následující příklad ukazuje druhý řádek textu škálované o 150% podél osy x a třetí řádek textu se škáluje o 150% podél osy y.</span><span class="sxs-lookup"><span data-stu-id="84928-110">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 ![Zvětšený text pomocí ScaleTransform](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg) 
  
 <span data-ttu-id="84928-112">Následující příklad kódu používá <xref:System.Windows.Media.ScaleTransform> pro horizontální navýšení kapacity textu z jeho původní velikosti.</span><span class="sxs-lookup"><span data-stu-id="84928-112">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> <span data-ttu-id="84928-113">Škálování textu není stejné jako zvětšení velikosti písma textu.</span><span class="sxs-lookup"><span data-stu-id="84928-113">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="84928-114">Velikosti písem jsou počítány nezávisle na sobě, aby bylo možné zajistit optimální rozlišení v různých velikostech.</span><span class="sxs-lookup"><span data-stu-id="84928-114">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="84928-115">Na druhé straně škálované textu zachovává proporce textu původní velikosti.</span><span class="sxs-lookup"><span data-stu-id="84928-115">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="84928-116">Následující příklad ukazuje text zkosený podél osy x.</span><span class="sxs-lookup"><span data-stu-id="84928-116">The following example shows text skewed along the x-axis.</span></span>  
  
 ![Text zkosený pomocí SkewTransform](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)
   
 <span data-ttu-id="84928-118">Následující příklad kódu používá <xref:System.Windows.Media.SkewTransform> pro zkosení textu.</span><span class="sxs-lookup"><span data-stu-id="84928-118">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="84928-119">Zkosení, označované také jako zkosit, je transformace, která roztáhne prostor souřadnic nejednotným způsobem.</span><span class="sxs-lookup"><span data-stu-id="84928-119">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="84928-120">V tomto příkladu jsou dva textové řetězce zkosených – 30 ° a 30 ° podél souřadnice x.</span><span class="sxs-lookup"><span data-stu-id="84928-120">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="84928-121">Následující příklad zobrazuje přeložený nebo přesunutý text podél osy x a y.</span><span class="sxs-lookup"><span data-stu-id="84928-121">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 ![Posun textu pomocí TranslateTransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 <span data-ttu-id="84928-123">Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> k posunu textu.</span><span class="sxs-lookup"><span data-stu-id="84928-123">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="84928-124">V tomto příkladu mírně posunutí kopie textu pod primárním textem vytvoří stínový efekt.</span><span class="sxs-lookup"><span data-stu-id="84928-124">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> <span data-ttu-id="84928-125"><xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Poskytuje bohatou sadu funkcí pro zajištění stínových efektů.</span><span class="sxs-lookup"><span data-stu-id="84928-125">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="84928-126">Další informace najdete v tématu [Vytvoření textu se stínem](how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="84928-126">For more information, see [Create Text with a Shadow](how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84928-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84928-127">See also</span></span>

- [<span data-ttu-id="84928-128">Použití animací na text</span><span class="sxs-lookup"><span data-stu-id="84928-128">Apply Animations to Text</span></span>](how-to-apply-animations-to-text.md)
