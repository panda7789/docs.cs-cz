---
title: 'Postupy: Vytvoření bitmapy z prostředí Visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: 429aacc99d8ead5a18e9be7602b19a74773b419a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362861"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="cb8a3-102">Postupy: Vytvoření bitmapy z prostředí Visual</span><span class="sxs-lookup"><span data-stu-id="cb8a3-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="cb8a3-103">Tento příklad ukazuje, jak můžete vytvořit rastrový obrázek z <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="cb8a3-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="cb8a3-104">A <xref:System.Windows.Media.DrawingVisual> je vykreslen pomocí <xref:System.Windows.Media.FormattedText>.</span><span class="sxs-lookup"><span data-stu-id="cb8a3-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="cb8a3-105"><xref:System.Windows.Media.Visual> Se pak vykreslí na <xref:System.Windows.Media.Imaging.RenderTargetBitmap> vytvoření bitmapy z daného textu.</span><span class="sxs-lookup"><span data-stu-id="cb8a3-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb8a3-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb8a3-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="cb8a3-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb8a3-107">See also</span></span>
- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="cb8a3-108">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="cb8a3-108">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="cb8a3-109">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="cb8a3-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="cb8a3-110">Použití objektů DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="cb8a3-110">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
