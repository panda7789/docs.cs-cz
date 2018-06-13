---
title: 'Postupy: Nastavení vodorovného a svislého zarovnání TileBrush'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], alignment of
- vertical alignment of TileBrushes [WPF]
- aligning [WPF], TileBrushes
- horizontal alignment of Tilebrushes [WPF]
ms.assetid: 65ae89bd-9246-4c9e-bde4-2fb991d4060d
ms.openlocfilehash: 4352067f149a1af25cd0a04a12596693188445fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563594"
---
# <a name="how-to-set-the-horizontal-and-vertical-alignment-of-a-tilebrush"></a>Postupy: Nastavení vodorovného a svislého zarovnání TileBrush
Tento příklad ukazuje, jak řídit vodorovného a svislého zarovnání obsahu v dlaždici. K řízení zarovnání vodorovného a svislého <xref:System.Windows.Media.TileBrush>, použijte jeho <xref:System.Windows.Media.TileBrush.AlignmentX%2A> a <xref:System.Windows.Media.TileBrush.AlignmentY%2A> vlastnosti.  
  
 <xref:System.Windows.Media.TileBrush.AlignmentX%2A> a <xref:System.Windows.Media.TileBrush.AlignmentY%2A> vlastnosti <xref:System.Windows.Media.TileBrush> se používají při je splněna jedna z následujících podmínek:  
  
-   <xref:System.Windows.Media.TileBrush.Stretch%2A> Vlastnost je <xref:System.Windows.Media.Stretch.Uniform> nebo <xref:System.Windows.Media.Stretch.UniformToFill> a <xref:System.Windows.Media.TileBrush.Viewbox%2A> a <xref:System.Windows.Media.TileBrush.Viewport%2A> mají různé poměrům stran.  
  
-   <xref:System.Windows.Media.TileBrush.Stretch%2A> Vlastnost je <xref:System.Windows.Media.Stretch.None> a <xref:System.Windows.Media.TileBrush.Viewbox%2A> a <xref:System.Windows.Media.TileBrush.Viewport%2A> mají různé velikosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad zarovnává obsah <xref:System.Windows.Media.DrawingBrush>, který je typem <xref:System.Windows.Media.TileBrush>, do levého horního rohu jeho dlaždici. Chcete-li zarovnat obsah v příkladu je nastavena <xref:System.Windows.Media.TileBrush.AlignmentX%2A> vlastnost <xref:System.Windows.Media.DrawingBrush> k <xref:System.Windows.Media.AlignmentX.Left> a <xref:System.Windows.Media.TileBrush.AlignmentY%2A> vlastnost, která má <xref:System.Windows.Media.AlignmentY.Top>. Tento příklad vytvoří následující výstup.  
  
 ![Objekt TileBrush s horní&#45;zarovnání vlevo](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletopleft.png "graphicsmm_TileBrushAlignmentExampleTopLeft")  
Levém horním rohu zarovnán TileBrush s obsahem  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmentinline)]  
  
## <a name="example"></a>Příklad  
 Další příklad zarovnává obsah <xref:System.Windows.Media.DrawingBrush> do pravého dolního rohu jeho dlaždici nastavením <xref:System.Windows.Media.TileBrush.AlignmentX%2A> vlastnost <xref:System.Windows.Media.AlignmentX.Right> a <xref:System.Windows.Media.TileBrush.AlignmentY%2A> vlastnost <xref:System.Windows.Media.AlignmentY.Bottom>. Tento příklad vytvoří následující výstup.  
  
 ![Objekt TileBrush se dolní&#45;pravým zarovnání](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomright.png "graphicsmm_TileBrushAlignmentExampleBottomRight")  
Pravém dolním rohu, zarovnán TileBrush s obsahem  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
## <a name="example"></a>Příklad  
 Další příklad zarovnává obsah <xref:System.Windows.Media.DrawingBrush> do levého horního rohu jeho dlaždici nastavením <xref:System.Windows.Media.TileBrush.AlignmentX%2A> vlastnost <xref:System.Windows.Media.AlignmentX.Left> a <xref:System.Windows.Media.TileBrush.AlignmentY%2A> vlastnost <xref:System.Windows.Media.AlignmentY.Top>. Nastaví taky <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.TileMode%2A> z <xref:System.Windows.Media.DrawingBrush> k vytvoření vzoru dlaždice. Tento příklad vytvoří následující výstup.  
  
 ![A TileBrush rozložen formou dlaždic s horní&#45;zarovnání vlevo](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletoplefttiled.png "graphicsmm_TileBrushAlignmentExampleTopLeftTiled")  
Vzor dlaždice s obsahem zarovnán levém základní dlaždice  
  
 Označuje obrázek abase dlaždice, aby mohli zobrazit, jakým způsobem je zarovnán jeho obsah. Všimněte si, že <xref:System.Windows.Media.TileBrush.AlignmentX%2A> nastavení nemá žádný vliv, protože obsah <xref:System.Windows.Media.DrawingBrush> úplně vodorovně vyplní celé základní dlaždice.  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmenttiledinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmenttiledinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmenttiledinline)]  
  
## <a name="example"></a>Příklad  
 Poslední příklad zarovnává obsah vedle sebe <xref:System.Windows.Media.DrawingBrush> do dolní části jeho základní dlaždice nastavením <xref:System.Windows.Media.TileBrush.AlignmentX%2A> vlastnost <xref:System.Windows.Media.AlignmentX.Right> a <xref:System.Windows.Media.TileBrush.AlignmentY%2A> vlastnost <xref:System.Windows.Media.AlignmentY.Bottom>. Tento příklad vytvoří následující výstup.  
  
 ![A TileBrush rozložen formou dlaždic s dolní&#45;pravým zarovnání](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomrighttiled.png "graphicsmm_TileBrushAlignmentExampleBottomRightTiled")  
Vzor dlaždice s obsahem zarovnán pravém základní dlaždici  
  
 Znovu <xref:System.Windows.Media.TileBrush.AlignmentX%2A> nastavení nemá žádný vliv, protože obsah <xref:System.Windows.Media.DrawingBrush> úplně vodorovně vyplní celé základní dlaždice.  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
 Příklady používají <xref:System.Windows.Media.DrawingBrush> objekty, které se ukazují, jak <xref:System.Windows.Media.TileBrush.AlignmentX%2A> a <xref:System.Windows.Media.TileBrush.AlignmentY%2A> vlastnosti se používají. Tyto vlastnosti chovají stejně jako pro všechny dlaždice štětce: <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.ImageBrush>, a <xref:System.Windows.Media.VisualBrush>. Další informace o dlaždici štětce najdete v tématu [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 [Malování pomocí obrázků, kreseb a vizuálních objektů](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
