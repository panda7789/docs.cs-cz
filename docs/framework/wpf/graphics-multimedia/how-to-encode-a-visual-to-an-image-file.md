---
title: "Postupy: Kódování vizuálního souboru na obrázek"
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
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88a5d93c9c4726d1f6493df28d0a2a559394ef74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a><span data-ttu-id="d979f-102">Postupy: Kódování vizuálního souboru na obrázek</span><span class="sxs-lookup"><span data-stu-id="d979f-102">How to: Encode a Visual to an Image File</span></span>
<span data-ttu-id="d979f-103">Tento příklad ukazuje, jak ke kódování <xref:System.Windows.Media.Visual> objektu do souboru bitové kopie pomocí <xref:System.Windows.Media.Imaging.RenderTargetBitmap> a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="d979f-103">This example demonstrates how to encode a <xref:System.Windows.Media.Visual> object into an image file using a <xref:System.Windows.Media.Imaging.RenderTargetBitmap> and a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d979f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d979f-104">Example</span></span>  
 <span data-ttu-id="d979f-105"><xref:System.Windows.Media.DrawingVisual> Je vytvořený pomocí <xref:System.Windows.Media.Imaging.BitmapImage> a <xref:System.Windows.Media.FormattedText> které je vykresleno do <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span><span class="sxs-lookup"><span data-stu-id="d979f-105">The <xref:System.Windows.Media.DrawingVisual> is created using a <xref:System.Windows.Media.Imaging.BitmapImage> and <xref:System.Windows.Media.FormattedText> which is rendered to a <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span></span> <span data-ttu-id="d979f-106">Vykreslené rastrového obrázku se pak použije k vytvoření <xref:System.Windows.Media.Imaging.BitmapFrame> která se přidá do <xref:System.Windows.Media.Imaging.PngBitmapEncoder> pro vytvoření nového [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] souboru.</span><span class="sxs-lookup"><span data-stu-id="d979f-106">The rendered bitmap is then used to create a <xref:System.Windows.Media.Imaging.BitmapFrame> which is added to the <xref:System.Windows.Media.Imaging.PngBitmapEncoder> to create a new [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] file.</span></span>  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 <span data-ttu-id="d979f-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> byl použit v tomto příkladu, ale některé z odvozené <xref:System.Windows.Media.Imaging.BitmapEncoder> objekty může byl použit pro vytvoření souboru bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="d979f-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> was used in this example but any of the derived <xref:System.Windows.Media.Imaging.BitmapEncoder> objects could have been used to create the image file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d979f-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="d979f-108">See Also</span></span>  
 <xref:System.Windows.Media.DrawingContext>  
 [<span data-ttu-id="d979f-109">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="d979f-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [<span data-ttu-id="d979f-110">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="d979f-110">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="d979f-111">Použití objektů DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="d979f-111">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
