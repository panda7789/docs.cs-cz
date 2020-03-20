---
title: 'Postupy: Transformace štětce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: b4484e2fc1ae3e969b02b1d8f3ae4ab2a035558e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187340"
---
# <a name="how-to-transform-a-brush"></a><span data-ttu-id="ef884-102">Postupy: Transformace štětce</span><span class="sxs-lookup"><span data-stu-id="ef884-102">How to: Transform a Brush</span></span>
<span data-ttu-id="ef884-103">Tento příklad ukazuje, <xref:System.Windows.Media.Brush> jak transformovat objekty <xref:System.Windows.Media.Brush.RelativeTransform%2A> pomocí <xref:System.Windows.Media.Brush.Transform%2A>jejich dvou vlastností transformace: a .</span><span class="sxs-lookup"><span data-stu-id="ef884-103">This example shows how to transform <xref:System.Windows.Media.Brush> objects by using their two transformation properties: <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A>.</span></span>  
  
 <span data-ttu-id="ef884-104">Následující příklady používají <xref:System.Windows.Media.RotateTransform> k otočení obsahu <xref:System.Windows.Media.ImageBrush> o 45 stupňů.</span><span class="sxs-lookup"><span data-stu-id="ef884-104">The following examples use a <xref:System.Windows.Media.RotateTransform> to rotate the content of an <xref:System.Windows.Media.ImageBrush> by 45 degrees.</span></span>  
  
 <span data-ttu-id="ef884-105">Následující obrázek <xref:System.Windows.Media.ImageBrush> znázorňuje <xref:System.Windows.Media.RotateTransform>bez <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.Brush.RelativeTransform%2A> , s aplikovanou vlastností a s <xref:System.Windows.Media.RotateTransform> aplikovanou vlastností. <xref:System.Windows.Media.Brush.Transform%2A></span><span class="sxs-lookup"><span data-stu-id="ef884-105">The following illustration shows the <xref:System.Windows.Media.ImageBrush> without a <xref:System.Windows.Media.RotateTransform>, with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property, and with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.Transform%2A> property.</span></span>  
  
 <span data-ttu-id="ef884-106">![Nastavení Relativní transformace stopy a transformace](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span><span class="sxs-lookup"><span data-stu-id="ef884-106">![Brush RelativeTransform and Transform settings](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef884-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef884-107">Example</span></span>  
 <span data-ttu-id="ef884-108">První příklad platí <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.Brush.RelativeTransform%2A> pro vlastnost <xref:System.Windows.Media.ImageBrush>.</span><span class="sxs-lookup"><span data-stu-id="ef884-108">The first example applies a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property of an <xref:System.Windows.Media.ImageBrush>.</span></span> <span data-ttu-id="ef884-109"><xref:System.Windows.Media.RotateTransform.CenterX%2A> Vlastnosti <xref:System.Windows.Media.RotateTransform.CenterY%2A> a <xref:System.Windows.Media.RotateTransform> objektu jsou nastaveny na 0,5, což je relativní souřadnice středového bodu tohoto obsahu.</span><span class="sxs-lookup"><span data-stu-id="ef884-109">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of a <xref:System.Windows.Media.RotateTransform> object are both set to 0.5, which is the relative coordinate of the center point of this content.</span></span> <span data-ttu-id="ef884-110">V důsledku toho <xref:System.Windows.Media.ImageBrush> se obsah otáčí kolem svého středu.</span><span class="sxs-lookup"><span data-stu-id="ef884-110">As a result, the <xref:System.Windows.Media.ImageBrush> content rotates about its center.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 <span data-ttu-id="ef884-111">Druhý příklad platí také <xref:System.Windows.Media.RotateTransform> pro <xref:System.Windows.Media.ImageBrush>; v tomto příkladu <xref:System.Windows.Media.Brush.Transform%2A> však <xref:System.Windows.Media.Brush.RelativeTransform%2A> používá vlastnost namísto vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ef884-111">The second example also applies a <xref:System.Windows.Media.RotateTransform> to an <xref:System.Windows.Media.ImageBrush>; however, this example uses the <xref:System.Windows.Media.Brush.Transform%2A> property instead of the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property.</span></span>  
  
 <span data-ttu-id="ef884-112">Chcete-li otočit stopu kolem jejího <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> středu, <xref:System.Windows.Media.RotateTransform> příklad nastaví vlastnosti a objektu na absolutní souřadnice.</span><span class="sxs-lookup"><span data-stu-id="ef884-112">To rotate the brush about its center, the example sets the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> object to absolute coordinates.</span></span> <span data-ttu-id="ef884-113">Vzhledem k tomu, že štětec maluje obdélník, který je 175 x 90 pixelů, středový bod obdélníku je (87.5, 45).</span><span class="sxs-lookup"><span data-stu-id="ef884-113">Because the brush paints a rectangle that is 175 by 90 pixels, the center point of the rectangle is (87.5, 45).</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <span data-ttu-id="ef884-114">Popis fungování <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastností <xref:System.Windows.Media.Brush.Transform%2A> a naleznete v tématu [Přehled transformace stopy](brush-transformation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ef884-114">For a description of how the <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A> properties work, see the [Brush Transformation Overview](brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="ef884-115">Úplný vzorek naleznete v tématu [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="ef884-115">For the complete sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="ef884-116">Další informace o stopách naleznete v [tématu Malování plnými barvami a přechody – přehled](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ef884-116">For more information about brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef884-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef884-117">See also</span></span>

- [<span data-ttu-id="ef884-118">Přehled transformace štětce</span><span class="sxs-lookup"><span data-stu-id="ef884-118">Brush Transformation Overview</span></span>](brush-transformation-overview.md)
- [<span data-ttu-id="ef884-119">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="ef884-119">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="ef884-120">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="ef884-120">Transforms Overview</span></span>](transforms-overview.md)
