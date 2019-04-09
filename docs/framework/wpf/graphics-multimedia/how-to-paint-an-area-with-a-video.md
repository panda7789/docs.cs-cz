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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151174"
---
# <a name="how-to-paint-an-area-with-a-video"></a>Postupy: Vykreslení oblasti videem
Tento příklad ukazuje způsob vykreslení oblasti s médii. Vykreslení oblasti media jedním ze způsobů je použít <xref:System.Windows.Controls.MediaElement> spolu s <xref:System.Windows.Media.VisualBrush>. Použít <xref:System.Windows.Controls.MediaElement> načíst přehrání média a použít ji k nastavení <xref:System.Windows.Media.VisualBrush.Visual%2A> vlastnost <xref:System.Windows.Media.VisualBrush>. Pak můžete použít <xref:System.Windows.Media.VisualBrush> k vykreslení oblasti vložená média.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Controls.MediaElement> a <xref:System.Windows.Media.VisualBrush> k vykreslení <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> ovládacího prvku s videem. Tento příklad nastaví <xref:System.Windows.Controls.MediaElement.IsMuted%2A> vlastnost <xref:System.Windows.Controls.MediaElement> k `true` tak, aby vytváří žádný zvukový signál.  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a>Příklad  
 Protože <xref:System.Windows.Media.VisualBrush> dědí z <xref:System.Windows.Media.TileBrush> třída poskytuje několik režimů dělení do bloků. Tím, že nastavíte <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost <xref:System.Windows.Media.VisualBrush> k <xref:System.Windows.Media.TileMode.Tile> a nastavením jeho <xref:System.Windows.Media.TileBrush.Viewport%2A> vlastnost na hodnotu menší než oblasti, kterou vymalováváte, můžete vytvořit vzoru vedle sebe.  
  
 Následující příklad je stejný jako předchozí příklad s výjimkou, že <xref:System.Windows.Media.VisualBrush> generuje vzorek z videa.  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 Informace o tom, jak přidat soubor s obsahem, jako je například mediální soubor, do vaší aplikace, najdete v části [prostředek aplikace WPF, obsah a datové soubory](../app-development/wpf-application-resource-content-and-data-files.md). Když přidáte soubor média, je třeba přidat ji jako soubor s obsahem, nikoli jako soubor prostředků.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.VisualBrush>
- [Kreslení pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [TileBrush – přehled](tilebrush-overview.md)
- [Přehled multimédií](multimedia-overview.md)
