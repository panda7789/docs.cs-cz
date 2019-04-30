---
title: 'Postupy: Vytvoření bitmapy z vizuálního objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: a622d99f7c477f8654526ed399f1eb37288682fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910257"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="f2989-102">Postupy: Vytvoření bitmapy z vizuálního objektu</span><span class="sxs-lookup"><span data-stu-id="f2989-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="f2989-103">Tento příklad ukazuje, jak můžete vytvořit rastrový obrázek z <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="f2989-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="f2989-104">A <xref:System.Windows.Media.DrawingVisual> je vykreslen pomocí <xref:System.Windows.Media.FormattedText>.</span><span class="sxs-lookup"><span data-stu-id="f2989-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="f2989-105"><xref:System.Windows.Media.Visual> Se pak vykreslí na <xref:System.Windows.Media.Imaging.RenderTargetBitmap> vytvoření bitmapy z daného textu.</span><span class="sxs-lookup"><span data-stu-id="f2989-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2989-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2989-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="f2989-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2989-107">See also</span></span>

- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="f2989-108">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="f2989-108">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="f2989-109">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="f2989-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="f2989-110">Použití objektů DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="f2989-110">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
