---
title: "Postupy: Vykreslení obrázku pomocí ImageDrawing"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d975d33bb3c102e5294d78dc76d8136ab521953
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a><span data-ttu-id="85d0e-102">Postupy: Vykreslení obrázku pomocí ImageDrawing</span><span class="sxs-lookup"><span data-stu-id="85d0e-102">How to: Draw an Image Using ImageDrawing</span></span>
<span data-ttu-id="85d0e-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Media.ImageDrawing> kreslení obrázku.</span><span class="sxs-lookup"><span data-stu-id="85d0e-103">This example shows how to use an <xref:System.Windows.Media.ImageDrawing> to draw an image.</span></span> <span data-ttu-id="85d0e-104"><xref:System.Windows.Media.ImageDrawing> Umožňuje můžete zobrazit <xref:System.Windows.Media.ImageSource> s <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, nebo <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="85d0e-104">An <xref:System.Windows.Media.ImageDrawing> enables you display an <xref:System.Windows.Media.ImageSource> with a <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, or <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="85d0e-105">Kreslení obrázku, vytvoříte <xref:System.Windows.Media.ImageDrawing> a nastavit jeho <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> a <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="85d0e-105">To draw an image, you create an <xref:System.Windows.Media.ImageDrawing> and set its <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> and <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="85d0e-106"><xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> Vlastnost určuje bitovou kopii k vykreslení a <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> vlastnost určuje umístění a velikost každé bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="85d0e-106">The <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> property specifies the image to draw, and the <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> property specifies the position and size of each image.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85d0e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="85d0e-107">Example</span></span>  
 <span data-ttu-id="85d0e-108">Následující příklad vytvoří složené kreslení pomocí čtyři <xref:System.Windows.Media.ImageDrawing> objekty.</span><span class="sxs-lookup"><span data-stu-id="85d0e-108">The following example creates a composite drawing using four <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="85d0e-109">Tento příklad vytvoří na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="85d0e-109">This example produces the following image:</span></span>  
  
 <span data-ttu-id="85d0e-110">![Několik objektů DrawingImage](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span><span class="sxs-lookup"><span data-stu-id="85d0e-110">![Several DrawingImage objects](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span></span>  
<span data-ttu-id="85d0e-111">Čtyři ImageDrawing objekty</span><span class="sxs-lookup"><span data-stu-id="85d0e-111">Four ImageDrawing objects</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 <span data-ttu-id="85d0e-112">Příklad zobrazuje jednoduchý způsob, jak zobrazit obrázek bez použití <xref:System.Windows.Media.ImageDrawing>, najdete v části [pomocí bitové kopie elementu](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).</span><span class="sxs-lookup"><span data-stu-id="85d0e-112">For an example showing a simple way to display an image without using <xref:System.Windows.Media.ImageDrawing>, see [Use the Image Element](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d0e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="85d0e-113">See Also</span></span>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 <xref:System.Windows.Controls.Image>  
 [<span data-ttu-id="85d0e-114">Kreslení objekty – přehled</span><span class="sxs-lookup"><span data-stu-id="85d0e-114">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="85d0e-115">Zmrazitelné objekty – přehled</span><span class="sxs-lookup"><span data-stu-id="85d0e-115">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="85d0e-116">Atribut PresentationOptions:Freeze</span><span class="sxs-lookup"><span data-stu-id="85d0e-116">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
