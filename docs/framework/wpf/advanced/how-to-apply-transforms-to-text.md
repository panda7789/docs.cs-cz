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
ms.openlocfilehash: 867f39e3df8493014d8601530e91310c3bbbeeb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141611"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="cf520-102">Postupy: Použití transformací na text</span><span class="sxs-lookup"><span data-stu-id="cf520-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="cf520-103">Transformace může změnit zobrazení textu v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cf520-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="cf520-104">Následující příklady používají různé typy vykreslování <xref:System.Windows.Controls.TextBlock> transformace ovlivnit zobrazení textu v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="cf520-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf520-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="cf520-105">Example</span></span>  
 <span data-ttu-id="cf520-106">Následující příklad ukazuje text otočený kolem zadaného bodu v dvojrozměrné rovině x-y.</span><span class="sxs-lookup"><span data-stu-id="cf520-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 ![Text otočený pomocí rotatetransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 <span data-ttu-id="cf520-108">Následující příklad kódu <xref:System.Windows.Media.RotateTransform> používá k otočení textu.</span><span class="sxs-lookup"><span data-stu-id="cf520-108">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="cf520-109">Hodnota <xref:System.Windows.Media.RotateTransform.Angle%2A> 90 otočí prvek o 90 stupňů ve směru hodinových ručiček.</span><span class="sxs-lookup"><span data-stu-id="cf520-109">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="cf520-110">Následující příklad ukazuje druhý řádek textu se 150 % podél osy x a třetí řádek textu o 150 % podél osy y.</span><span class="sxs-lookup"><span data-stu-id="cf520-110">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 ![Velikost textu s měřítkem pomocí scaletransform](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg)
  
 <span data-ttu-id="cf520-112">Následující příklad kódu <xref:System.Windows.Media.ScaleTransform> používá měřítko textu z původní velikosti.</span><span class="sxs-lookup"><span data-stu-id="cf520-112">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> <span data-ttu-id="cf520-113">Změna velikosti textu není stejná jako zvětšení velikosti písma textu.</span><span class="sxs-lookup"><span data-stu-id="cf520-113">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="cf520-114">Velikosti písma jsou vypočteny nezávisle na sobě, aby bylo zajištěno nejlepší rozlišení při různých velikostech.</span><span class="sxs-lookup"><span data-stu-id="cf520-114">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="cf520-115">Velikost textu s měřítkem naopak zachová proporce textu původní velikosti.</span><span class="sxs-lookup"><span data-stu-id="cf520-115">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="cf520-116">Následující příklad ukazuje text zkosený podél osy x.</span><span class="sxs-lookup"><span data-stu-id="cf520-116">The following example shows text skewed along the x-axis.</span></span>  
  
 ![Text zkosený pomocí skewtransformu](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)

 <span data-ttu-id="cf520-118">Následující příklad kódu <xref:System.Windows.Media.SkewTransform> používá k zkosení textu.</span><span class="sxs-lookup"><span data-stu-id="cf520-118">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="cf520-119">Zkosení, známé také jako zkosení, je transformace, která roztáhne souřadnicový prostor nerovnoměrným způsobem.</span><span class="sxs-lookup"><span data-stu-id="cf520-119">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="cf520-120">V tomto příkladu jsou dva textové řetězce zkosené -30° a 30° podél souřadnice x.</span><span class="sxs-lookup"><span data-stu-id="cf520-120">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="cf520-121">Následující příklad ukazuje text přeložený nebo přesunutý podél osy x a y.</span><span class="sxs-lookup"><span data-stu-id="cf520-121">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 ![Posun textu pomocí TranslateTransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 <span data-ttu-id="cf520-123">Následující příklad kódu <xref:System.Windows.Media.TranslateTransform> používá k odsazení textu.</span><span class="sxs-lookup"><span data-stu-id="cf520-123">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="cf520-124">V tomto příkladu vytvoří mírně odsazená kopie textu pod primárním textem stínový efekt.</span><span class="sxs-lookup"><span data-stu-id="cf520-124">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> <span data-ttu-id="cf520-125">Poskytuje <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> bohatou sadu funkcí pro poskytování stínových efektů.</span><span class="sxs-lookup"><span data-stu-id="cf520-125">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="cf520-126">Další informace naleznete v [tématu Vytvoření textu se stínem](how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="cf520-126">For more information, see [Create Text with a Shadow](how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf520-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf520-127">See also</span></span>

- [<span data-ttu-id="cf520-128">Použití animací na text</span><span class="sxs-lookup"><span data-stu-id="cf520-128">Apply Animations to Text</span></span>](how-to-apply-animations-to-text.md)
