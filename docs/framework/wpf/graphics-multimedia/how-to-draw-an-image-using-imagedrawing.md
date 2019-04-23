---
title: 'Postupy: Vykreslení obrázku pomocí ImageDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: f9459185bf81160b45222e7d6821e0f945ada381
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100155"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a><span data-ttu-id="fc832-102">Postupy: Vykreslení obrázku pomocí ImageDrawing</span><span class="sxs-lookup"><span data-stu-id="fc832-102">How to: Draw an Image Using ImageDrawing</span></span>
<span data-ttu-id="fc832-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.ImageDrawing> nakreslete obrázek.</span><span class="sxs-lookup"><span data-stu-id="fc832-103">This example shows how to use an <xref:System.Windows.Media.ImageDrawing> to draw an image.</span></span> <span data-ttu-id="fc832-104"><xref:System.Windows.Media.ImageDrawing> Umožňuje zobrazení <xref:System.Windows.Media.ImageSource> s <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, nebo <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="fc832-104">An <xref:System.Windows.Media.ImageDrawing> enables you display an <xref:System.Windows.Media.ImageSource> with a <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, or <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="fc832-105">Chcete-li nakreslit obrázek, vytvoříte <xref:System.Windows.Media.ImageDrawing> a nastavte jeho <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> a <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fc832-105">To draw an image, you create an <xref:System.Windows.Media.ImageDrawing> and set its <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> and <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="fc832-106"><xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> Vlastnost určuje obrázek, chcete-li nakreslit a <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> vlastnost určuje umístění a velikost jednotlivých obrázků.</span><span class="sxs-lookup"><span data-stu-id="fc832-106">The <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> property specifies the image to draw, and the <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> property specifies the position and size of each image.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc832-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc832-107">Example</span></span>  
 <span data-ttu-id="fc832-108">Následující příklad vytvoří pomocí čtyř kompozitní kresby <xref:System.Windows.Media.ImageDrawing> objekty.</span><span class="sxs-lookup"><span data-stu-id="fc832-108">The following example creates a composite drawing using four <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="fc832-109">Tento příklad vytvoří na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="fc832-109">This example produces the following image:</span></span>  
  
 <span data-ttu-id="fc832-110">![Několik objektů DrawingImage](./media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span><span class="sxs-lookup"><span data-stu-id="fc832-110">![Several DrawingImage objects](./media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span></span>  
<span data-ttu-id="fc832-111">Čtyři ImageDrawing – objekty</span><span class="sxs-lookup"><span data-stu-id="fc832-111">Four ImageDrawing objects</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 <span data-ttu-id="fc832-112">Příklad znázorňující jednoduchý způsob, jak zobrazit obrázek bez použití <xref:System.Windows.Media.ImageDrawing>, naleznete v tématu [použití elementu obrázku](../controls/how-to-use-the-image-element.md).</span><span class="sxs-lookup"><span data-stu-id="fc832-112">For an example showing a simple way to display an image without using <xref:System.Windows.Media.ImageDrawing>, see [Use the Image Element](../controls/how-to-use-the-image-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc832-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc832-113">See also</span></span>

- <xref:System.Windows.Freezable.Freeze%2A>
- <xref:System.Windows.Controls.Image>
- [<span data-ttu-id="fc832-114">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="fc832-114">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="fc832-115">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="fc832-115">Freezable Objects Overview</span></span>](../advanced/freezable-objects-overview.md)
- [<span data-ttu-id="fc832-116">PresentationOptions:Freeze – atribut</span><span class="sxs-lookup"><span data-stu-id="fc832-116">PresentationOptions:Freeze Attribute</span></span>](../advanced/presentationoptions-freeze-attribute.md)
