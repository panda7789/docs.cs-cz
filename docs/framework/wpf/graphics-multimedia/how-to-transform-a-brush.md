---
title: "Postupy: Transformace štětce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ee517eb76877bb4e02c021061055b328597c517
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-transform-a-brush"></a><span data-ttu-id="f9f0a-102">Postupy: Transformace štětce</span><span class="sxs-lookup"><span data-stu-id="f9f0a-102">How to: Transform a Brush</span></span>
<span data-ttu-id="f9f0a-103">Tento příklad ukazuje, jak k transformaci <xref:System.Windows.Media.Brush> objekty pomocí jejich vlastnosti dvě transformace: <xref:System.Windows.Media.Brush.RelativeTransform%2A> a <xref:System.Windows.Media.Brush.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9f0a-103">This example shows how to transform <xref:System.Windows.Media.Brush> objects by using their two transformation properties: <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A>.</span></span>  
  
 <span data-ttu-id="f9f0a-104">Následující příklady použití <xref:System.Windows.Media.RotateTransform> otočení obsah <xref:System.Windows.Media.ImageBrush> o 45 stupňů.</span><span class="sxs-lookup"><span data-stu-id="f9f0a-104">The following examples use a <xref:System.Windows.Media.RotateTransform> to rotate the content of an <xref:System.Windows.Media.ImageBrush> by 45 degrees.</span></span>  
  
 <span data-ttu-id="f9f0a-105">Následující obrázek ukazuje <xref:System.Windows.Media.ImageBrush> bez <xref:System.Windows.Media.RotateTransform>, s <xref:System.Windows.Media.RotateTransform> u <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost a <xref:System.Windows.Media.RotateTransform> u <xref:System.Windows.Media.Brush.Transform%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f9f0a-105">The following illustration shows the <xref:System.Windows.Media.ImageBrush> without a <xref:System.Windows.Media.RotateTransform>, with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property, and with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.Transform%2A> property.</span></span>  
  
 <span data-ttu-id="f9f0a-106">![Zdokonalit RelativeTransform a transformace nastavení](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span><span class="sxs-lookup"><span data-stu-id="f9f0a-106">![Brush RelativeTransform and Transform settings](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9f0a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9f0a-107">Example</span></span>  
 <span data-ttu-id="f9f0a-108">V prvním příkladu se vztahuje <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost <xref:System.Windows.Media.ImageBrush>.</span><span class="sxs-lookup"><span data-stu-id="f9f0a-108">The first example applies a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property of an <xref:System.Windows.Media.ImageBrush>.</span></span> <span data-ttu-id="f9f0a-109"><xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti <xref:System.Windows.Media.RotateTransform> objekt, jsou nastaveny na 0,5, která je relativní souřadnice centrálního bodu tohoto obsahu.</span><span class="sxs-lookup"><span data-stu-id="f9f0a-109">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of a <xref:System.Windows.Media.RotateTransform> object are both set to 0.5, which is the relative coordinate of the center point of this content.</span></span> <span data-ttu-id="f9f0a-110">V důsledku toho <xref:System.Windows.Media.ImageBrush> obsah otočí o jeho center.</span><span class="sxs-lookup"><span data-stu-id="f9f0a-110">As a result, the <xref:System.Windows.Media.ImageBrush> content rotates about its center.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 <span data-ttu-id="f9f0a-111">V druhém příkladu platí také <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Media.ImageBrush>; však tento příklad používá <xref:System.Windows.Media.Brush.Transform%2A> vlastnost místo <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f9f0a-111">The second example also applies a <xref:System.Windows.Media.RotateTransform> to an <xref:System.Windows.Media.ImageBrush>; however, this example uses the <xref:System.Windows.Media.Brush.Transform%2A> property instead of the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property.</span></span>  
  
 <span data-ttu-id="f9f0a-112">Otočit štětce o jeho center, v příkladu je nastaven <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti <xref:System.Windows.Media.RotateTransform> objekt, který chcete absolutní souřadnice.</span><span class="sxs-lookup"><span data-stu-id="f9f0a-112">To rotate the brush about its center, the example sets the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> object to absolute coordinates.</span></span> <span data-ttu-id="f9f0a-113">Vzhledem k tomu stopy vybarví obdélníku, která je 175 o 90 pixelů, je středový bod obdélníku (87.5, 45).</span><span class="sxs-lookup"><span data-stu-id="f9f0a-113">Because the brush paints a rectangle that is 175 by 90 pixels, the center point of the rectangle is (87.5, 45).</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <span data-ttu-id="f9f0a-114">Popis toho, jak <xref:System.Windows.Media.Brush.RelativeTransform%2A> a <xref:System.Windows.Media.Brush.Transform%2A> vlastnosti naleznete v tématech [štětce transformace přehled](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f9f0a-114">For a description of how the <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A> properties work, see the [Brush Transformation Overview](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="f9f0a-115">Kompletní příklad, najdete v části [štětce ukázka](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="f9f0a-115">For the complete sample, see [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="f9f0a-116">Další informace o štětce najdete v tématu [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f9f0a-116">For more information about brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9f0a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9f0a-117">See Also</span></span>  
 [<span data-ttu-id="f9f0a-118">Přehled transformace štětce</span><span class="sxs-lookup"><span data-stu-id="f9f0a-118">Brush Transformation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [<span data-ttu-id="f9f0a-119">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="f9f0a-119">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="f9f0a-120">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="f9f0a-120">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
