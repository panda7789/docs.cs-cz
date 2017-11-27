---
title: "Postupy: Vykreslení videa v oblasti"
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
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 362231bbd1f4e95c260370a99233b7e8c2617ca1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-paint-an-area-with-a-video"></a><span data-ttu-id="5c2ec-102">Postupy: Vykreslení videa v oblasti</span><span class="sxs-lookup"><span data-stu-id="5c2ec-102">How to: Paint an Area with a Video</span></span>
<span data-ttu-id="5c2ec-103">Tento příklad ukazuje, jak k vyplnění oblast s média.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-103">This example shows how to paint an area with media.</span></span> <span data-ttu-id="5c2ec-104">Jedním ze způsobů malovat oblast s média je používat <xref:System.Windows.Controls.MediaElement> společně s <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-104">One way to paint an area with media is to use a <xref:System.Windows.Controls.MediaElement> together with a <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="5c2ec-105">Použít <xref:System.Windows.Controls.MediaElement> k načtení a přehrávání média a použít jej nastavit <xref:System.Windows.Media.VisualBrush.Visual%2A> vlastnost <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-105">Use the <xref:System.Windows.Controls.MediaElement> to load and play the media, and then use it to set the <xref:System.Windows.Media.VisualBrush.Visual%2A> property of the <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="5c2ec-106">Pak můžete použít <xref:System.Windows.Media.VisualBrush> k vyplnění oblast s vložená média.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-106">You can then use the <xref:System.Windows.Media.VisualBrush> to paint an area with the loaded media.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c2ec-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c2ec-107">Example</span></span>  
 <span data-ttu-id="5c2ec-108">Následující příklad používá <xref:System.Windows.Controls.MediaElement> a <xref:System.Windows.Media.VisualBrush> k vyplnění <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> ovládacího prvku pomocí video.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-108">The following example uses a <xref:System.Windows.Controls.MediaElement> and a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Controls.TextBlock.Foreground%2A> of a <xref:System.Windows.Controls.TextBlock> control with video.</span></span> <span data-ttu-id="5c2ec-109">Tento příklad nastaví <xref:System.Windows.Controls.MediaElement.IsMuted%2A> vlastnost <xref:System.Windows.Controls.MediaElement> k `true` tak, aby vyvolá žádné zvuku.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-109">This example sets the <xref:System.Windows.Controls.MediaElement.IsMuted%2A> property of the <xref:System.Windows.Controls.MediaElement> to `true` so that it produces no sound.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a><span data-ttu-id="5c2ec-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c2ec-110">Example</span></span>  
 <span data-ttu-id="5c2ec-111">Protože <xref:System.Windows.Media.VisualBrush> dědí z <xref:System.Windows.Media.TileBrush> třída, poskytuje několik dlaždic režimy.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-111">Because <xref:System.Windows.Media.VisualBrush> inherits from the <xref:System.Windows.Media.TileBrush> class, it provides several tiling modes.</span></span> <span data-ttu-id="5c2ec-112">Nastavením <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost <xref:System.Windows.Media.VisualBrush> k <xref:System.Windows.Media.TileMode.Tile> a nastavením jeho <xref:System.Windows.Media.TileBrush.Viewport%2A> vlastnost na hodnotu menší než k oblasti, která jsou vykreslování, můžete vytvořit vzorek za sebou.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-112">By setting the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.VisualBrush> to <xref:System.Windows.Media.TileMode.Tile> and by setting its <xref:System.Windows.Media.TileBrush.Viewport%2A> property to a value smaller than the area that you are painting, you can create a tiled pattern.</span></span>  
  
 <span data-ttu-id="5c2ec-113">Následující příklad je stejný jako předchozí příklad, vyjma toho, že <xref:System.Windows.Media.VisualBrush> generuje vzorek z videa.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-113">The following example is identical to the previous example, except that the <xref:System.Windows.Media.VisualBrush> generates a pattern from the video.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 <span data-ttu-id="5c2ec-114">Informace o tom, jak přidat do vaší aplikace, soubor s obsahem, jako je například soubor média, najdete v článku [prostředek aplikace WPF, obsah a datové soubory](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="5c2ec-114">For information about how to add a content file, such as a media file, to your application, see [WPF Application Resource, Content, and Data Files](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span></span> <span data-ttu-id="5c2ec-115">Když přidáte soubor média, je třeba přidat ji jako soubor obsahu, nikoli jako soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="5c2ec-115">When you add a media file, you must add it as a content file, not as a resource file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c2ec-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c2ec-116">See Also</span></span>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="5c2ec-117">Malování s obrázky, kresby a vizuální prvky</span><span class="sxs-lookup"><span data-stu-id="5c2ec-117">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="5c2ec-118">Přehled TileBrush</span><span class="sxs-lookup"><span data-stu-id="5c2ec-118">TileBrush Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [<span data-ttu-id="5c2ec-119">Multimediální – přehled</span><span class="sxs-lookup"><span data-stu-id="5c2ec-119">Multimedia Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)
