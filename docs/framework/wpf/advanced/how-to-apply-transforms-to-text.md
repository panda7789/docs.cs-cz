---
title: "Postupy: Použití transformací na text"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ed10a00d3d62f7eae91e5932a917be692de868b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="4c42e-102">Postupy: Použití transformací na text</span><span class="sxs-lookup"><span data-stu-id="4c42e-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="4c42e-103">Transformace můžete změnit zobrazení textu v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4c42e-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="4c42e-104">Následující příklady používají různé typy transformací vykreslování ovlivnit zobrazení textu v <xref:System.Windows.Controls.TextBlock> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4c42e-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c42e-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c42e-105">Example</span></span>  
 <span data-ttu-id="4c42e-106">Následující příklad ukazuje text otočený o zadaný bod v rovině dvourozměrná x-y.</span><span class="sxs-lookup"><span data-stu-id="4c42e-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 <span data-ttu-id="4c42e-107">![Text otočen pomocí RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")</span><span class="sxs-lookup"><span data-stu-id="4c42e-107">![Text rotated using a RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")</span></span>  
<span data-ttu-id="4c42e-108">Příklad textu otočený o 90 stupňů</span><span class="sxs-lookup"><span data-stu-id="4c42e-108">Example of text rotated 90 degrees</span></span>  
  
 <span data-ttu-id="4c42e-109">Následující příklad kódu používá <xref:System.Windows.Media.RotateTransform> otočení textu.</span><span class="sxs-lookup"><span data-stu-id="4c42e-109">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="4c42e-110"><xref:System.Windows.Media.RotateTransform.Angle%2A> Hodnotu 90 otočí element 90 stupňů po směru hodinových ručiček.</span><span class="sxs-lookup"><span data-stu-id="4c42e-110">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="4c42e-111">Následující příklad ukazuje na druhém řádku textu škálovat 150 % podél osy x a ve třetím řádku textu škálovat 150 % podél osy y.</span><span class="sxs-lookup"><span data-stu-id="4c42e-111">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 <span data-ttu-id="4c42e-112">![Text škálovat pomocí metody ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")</span><span class="sxs-lookup"><span data-stu-id="4c42e-112">![Text scaled using a ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")</span></span>  
<span data-ttu-id="4c42e-113">Příklad škálovat textu</span><span class="sxs-lookup"><span data-stu-id="4c42e-113">Example of scaled text</span></span>  
  
 <span data-ttu-id="4c42e-114">Následující příklad kódu používá <xref:System.Windows.Media.ScaleTransform> na škálování text z jeho původní velikost.</span><span class="sxs-lookup"><span data-stu-id="4c42e-114">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  <span data-ttu-id="4c42e-115">Škálování text není stejný jako zvýšit velikost písma v textu.</span><span class="sxs-lookup"><span data-stu-id="4c42e-115">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="4c42e-116">Velikosti písem jsou vypočítávány nezávisle na sobě navzájem, chcete-li poskytovat nejlepší řešení při různých velikostech.</span><span class="sxs-lookup"><span data-stu-id="4c42e-116">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="4c42e-117">Škálovat text, na druhé straně zachová poměr stran původní velikost textu.</span><span class="sxs-lookup"><span data-stu-id="4c42e-117">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="4c42e-118">Následující příklad ukazuje text nesouměrně rozdělí podél osy x.</span><span class="sxs-lookup"><span data-stu-id="4c42e-118">The following example shows text skewed along the x-axis.</span></span>  
  
 <span data-ttu-id="4c42e-119">![Text nesouměrně rozdělí pomocí metody SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")</span><span class="sxs-lookup"><span data-stu-id="4c42e-119">![Text skewed using a SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")</span></span>  
<span data-ttu-id="4c42e-120">Příklad zkreslilo textu</span><span class="sxs-lookup"><span data-stu-id="4c42e-120">Example of skewed text</span></span>  
  
 <span data-ttu-id="4c42e-121">Následující příklad kódu používá <xref:System.Windows.Media.SkewTransform> zkosení textu.</span><span class="sxs-lookup"><span data-stu-id="4c42e-121">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="4c42e-122">Zkosení, také známé jako zkosení je transformaci, která roztahovány souřadnicového prostoru neuniformní způsobem.</span><span class="sxs-lookup"><span data-stu-id="4c42e-122">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="4c42e-123">V tomto příkladu jsou dva textové řetězce zkreslilo °-30 a 30 ° podél souřadnici x.</span><span class="sxs-lookup"><span data-stu-id="4c42e-123">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="4c42e-124">Následující příklad ukazuje text přeložit, nebo se vyjme podél x - a osy y.</span><span class="sxs-lookup"><span data-stu-id="4c42e-124">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 <span data-ttu-id="4c42e-125">![Text posun pomocí TranslateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")</span><span class="sxs-lookup"><span data-stu-id="4c42e-125">![Text offset using a TranslateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")</span></span>  
<span data-ttu-id="4c42e-126">Příklad přeložený text</span><span class="sxs-lookup"><span data-stu-id="4c42e-126">Example of translated text</span></span>  
  
 <span data-ttu-id="4c42e-127">Následující příklad kódu používá <xref:System.Windows.Media.TranslateTransform> k posunutí textu.</span><span class="sxs-lookup"><span data-stu-id="4c42e-127">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="4c42e-128">V tomto příkladu se vytvoří kopii text pod primární text mírně posunutí efekt stínu.</span><span class="sxs-lookup"><span data-stu-id="4c42e-128">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <span data-ttu-id="4c42e-129"><xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Poskytuje bohatou sadu funkcí pro zajištění stínové účinky.</span><span class="sxs-lookup"><span data-stu-id="4c42e-129">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="4c42e-130">Další informace najdete v tématu [vytvoření textu pomocí stín](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="4c42e-130">For more information, see [Create Text with a Shadow](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c42e-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c42e-131">See Also</span></span>  
 [<span data-ttu-id="4c42e-132">Použít animací na Text</span><span class="sxs-lookup"><span data-stu-id="4c42e-132">Apply Animations to Text</span></span>](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)
