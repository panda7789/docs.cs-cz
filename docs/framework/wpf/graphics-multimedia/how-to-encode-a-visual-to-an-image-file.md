---
title: 'Postupy: Kódování vizuálního objektu na soubor obrázku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
ms.openlocfilehash: 872c19af0cfcf4fc980643c37e9a6028457c03b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947573"
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a><span data-ttu-id="d2ee2-102">Postupy: Kódování vizuálního objektu na soubor obrázku</span><span class="sxs-lookup"><span data-stu-id="d2ee2-102">How to: Encode a Visual to an Image File</span></span>
<span data-ttu-id="d2ee2-103">Tento příklad ukazuje, jak kódovat <xref:System.Windows.Media.Visual> do souboru image pomocí objektu <xref:System.Windows.Media.Imaging.RenderTargetBitmap> a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="d2ee2-103">This example demonstrates how to encode a <xref:System.Windows.Media.Visual> object into an image file using a <xref:System.Windows.Media.Imaging.RenderTargetBitmap> and a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2ee2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2ee2-104">Example</span></span>  
 <span data-ttu-id="d2ee2-105"><xref:System.Windows.Media.DrawingVisual> Je vytvořený pomocí <xref:System.Windows.Media.Imaging.BitmapImage> a <xref:System.Windows.Media.FormattedText> které je vykresleno do <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span><span class="sxs-lookup"><span data-stu-id="d2ee2-105">The <xref:System.Windows.Media.DrawingVisual> is created using a <xref:System.Windows.Media.Imaging.BitmapImage> and <xref:System.Windows.Media.FormattedText> which is rendered to a <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span></span> <span data-ttu-id="d2ee2-106">Vykreslený rastrového obrázku se pak použije k vytvoření <xref:System.Windows.Media.Imaging.BitmapFrame> která se přidá do <xref:System.Windows.Media.Imaging.PngBitmapEncoder> k vytvoření nového [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] souboru.</span><span class="sxs-lookup"><span data-stu-id="d2ee2-106">The rendered bitmap is then used to create a <xref:System.Windows.Media.Imaging.BitmapFrame> which is added to the <xref:System.Windows.Media.Imaging.PngBitmapEncoder> to create a new [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] file.</span></span>  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 <span data-ttu-id="d2ee2-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> byl použit v tomto příkladu, ale všechny odvozené <xref:System.Windows.Media.Imaging.BitmapEncoder> objektů by byla použita k vytvoření souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="d2ee2-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> was used in this example but any of the derived <xref:System.Windows.Media.Imaging.BitmapEncoder> objects could have been used to create the image file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ee2-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2ee2-108">See also</span></span>

- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="d2ee2-109">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="d2ee2-109">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="d2ee2-110">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="d2ee2-110">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="d2ee2-111">Použití objektů DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="d2ee2-111">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
