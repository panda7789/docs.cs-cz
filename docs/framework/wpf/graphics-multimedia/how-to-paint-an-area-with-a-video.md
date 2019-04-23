---
title: 'Postupy: Vykreslení oblasti videem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
ms.openlocfilehash: be09d1310847cd7214ea795a704c25d994f07b7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151174"
---
# <a name="how-to-paint-an-area-with-a-video"></a><span data-ttu-id="ad490-102">Postupy: Vykreslení oblasti videem</span><span class="sxs-lookup"><span data-stu-id="ad490-102">How to: Paint an Area with a Video</span></span>
<span data-ttu-id="ad490-103">Tento příklad ukazuje způsob vykreslení oblasti s médii.</span><span class="sxs-lookup"><span data-stu-id="ad490-103">This example shows how to paint an area with media.</span></span> <span data-ttu-id="ad490-104">Vykreslení oblasti media jedním ze způsobů je použít <xref:System.Windows.Controls.MediaElement> spolu s <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="ad490-104">One way to paint an area with media is to use a <xref:System.Windows.Controls.MediaElement> together with a <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="ad490-105">Použít <xref:System.Windows.Controls.MediaElement> načíst přehrání média a použít ji k nastavení <xref:System.Windows.Media.VisualBrush.Visual%2A> vlastnost <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="ad490-105">Use the <xref:System.Windows.Controls.MediaElement> to load and play the media, and then use it to set the <xref:System.Windows.Media.VisualBrush.Visual%2A> property of the <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="ad490-106">Pak můžete použít <xref:System.Windows.Media.VisualBrush> k vykreslení oblasti vložená média.</span><span class="sxs-lookup"><span data-stu-id="ad490-106">You can then use the <xref:System.Windows.Media.VisualBrush> to paint an area with the loaded media.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad490-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad490-107">Example</span></span>  
 <span data-ttu-id="ad490-108">Následující příklad používá <xref:System.Windows.Controls.MediaElement> a <xref:System.Windows.Media.VisualBrush> k vykreslení <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> ovládacího prvku s videem.</span><span class="sxs-lookup"><span data-stu-id="ad490-108">The following example uses a <xref:System.Windows.Controls.MediaElement> and a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Controls.TextBlock.Foreground%2A> of a <xref:System.Windows.Controls.TextBlock> control with video.</span></span> <span data-ttu-id="ad490-109">Tento příklad nastaví <xref:System.Windows.Controls.MediaElement.IsMuted%2A> vlastnost <xref:System.Windows.Controls.MediaElement> k `true` tak, aby vytváří žádný zvukový signál.</span><span class="sxs-lookup"><span data-stu-id="ad490-109">This example sets the <xref:System.Windows.Controls.MediaElement.IsMuted%2A> property of the <xref:System.Windows.Controls.MediaElement> to `true` so that it produces no sound.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a><span data-ttu-id="ad490-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad490-110">Example</span></span>  
 <span data-ttu-id="ad490-111">Protože <xref:System.Windows.Media.VisualBrush> dědí z <xref:System.Windows.Media.TileBrush> třída poskytuje několik režimů dělení do bloků.</span><span class="sxs-lookup"><span data-stu-id="ad490-111">Because <xref:System.Windows.Media.VisualBrush> inherits from the <xref:System.Windows.Media.TileBrush> class, it provides several tiling modes.</span></span> <span data-ttu-id="ad490-112">Tím, že nastavíte <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost <xref:System.Windows.Media.VisualBrush> k <xref:System.Windows.Media.TileMode.Tile> a nastavením jeho <xref:System.Windows.Media.TileBrush.Viewport%2A> vlastnost na hodnotu menší než oblasti, kterou vymalováváte, můžete vytvořit vzoru vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="ad490-112">By setting the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.VisualBrush> to <xref:System.Windows.Media.TileMode.Tile> and by setting its <xref:System.Windows.Media.TileBrush.Viewport%2A> property to a value smaller than the area that you are painting, you can create a tiled pattern.</span></span>  
  
 <span data-ttu-id="ad490-113">Následující příklad je stejný jako předchozí příklad s výjimkou, že <xref:System.Windows.Media.VisualBrush> generuje vzorek z videa.</span><span class="sxs-lookup"><span data-stu-id="ad490-113">The following example is identical to the previous example, except that the <xref:System.Windows.Media.VisualBrush> generates a pattern from the video.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 <span data-ttu-id="ad490-114">Informace o tom, jak přidat soubor s obsahem, jako je například mediální soubor, do vaší aplikace, najdete v části [prostředek aplikace WPF, obsah a datové soubory](../app-development/wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="ad490-114">For information about how to add a content file, such as a media file, to your application, see [WPF Application Resource, Content, and Data Files](../app-development/wpf-application-resource-content-and-data-files.md).</span></span> <span data-ttu-id="ad490-115">Když přidáte soubor média, je třeba přidat ji jako soubor s obsahem, nikoli jako soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="ad490-115">When you add a media file, you must add it as a content file, not as a resource file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad490-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad490-116">See also</span></span>

- <xref:System.Windows.Media.VisualBrush>
- [<span data-ttu-id="ad490-117">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="ad490-117">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="ad490-118">TileBrush – přehled</span><span class="sxs-lookup"><span data-stu-id="ad490-118">TileBrush Overview</span></span>](tilebrush-overview.md)
- [<span data-ttu-id="ad490-119">Přehled multimédií</span><span class="sxs-lookup"><span data-stu-id="ad490-119">Multimedia Overview</span></span>](multimedia-overview.md)
