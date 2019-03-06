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
ms.openlocfilehash: d18e4a9fe4f99c1947402c252082e1580a0b22cc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352552"
---
# <a name="how-to-set-the-horizontal-and-vertical-alignment-of-a-tilebrush"></a>Postupy: Nastavení vodorovného a svislého zarovnání TileBrush
Tento příklad ukazuje, jak ovládací prvek vodorovné a svislé zarovnání obsahu v bloku. K řízení vodorovného a svislého zarovnání <xref:System.Windows.Media.TileBrush>, použijte jeho <xref:System.Windows.Media.TileBrush.AlignmentX%2A> a <xref:System.Windows.Media.TileBrush.AlignmentY%2A> vlastnosti.  
  
 <xref:System.Windows.Media.TileBrush.AlignmentX%2A> a <xref:System.Windows.Media.TileBrush.AlignmentY%2A> vlastnosti <xref:System.Windows.Media.TileBrush> se používají Pokud je splněna jedna z následujících podmínek:  
  
-   <xref:System.Windows.Media.TileBrush.Stretch%2A> Vlastnost <xref:System.Windows.Media.Stretch.Uniform> nebo <xref:System.Windows.Media.Stretch.UniformToFill> a <xref:System.Windows.Media.TileBrush.Viewbox%2A> a <xref:System.Windows.Media.TileBrush.Viewport%2A> mají různé poměry stran.  
  
-   <xref:System.Windows.Media.TileBrush.Stretch%2A> Vlastnost <xref:System.Windows.Media.Stretch.None> a <xref:System.Windows.Media.TileBrush.Viewbox%2A> a <xref:System.Windows.Media.TileBrush.Viewport%2A> jsou různých velikostí.  
  
## <a name="example"></a>Příklad  
 Následující příklad Zarovná obsah <xref:System.Windows.Media.DrawingBrush>, což je typ <xref:System.Windows.Media.TileBrush>, do levého horního rohu jeho dlaždice. Zarovnání obsahu v příkladu je nastavena <xref:System.Windows.Media.TileBrush.AlignmentX%2A> vlastnost <xref:System.Windows.Media.DrawingBrush> k <xref:System.Windows.Media.AlignmentX.Left> a <xref:System.Windows.Media.TileBrush.AlignmentY%2A> vlastnost <xref:System.Windows.Media.AlignmentY.Top>. Tento příklad vytvoří následující výstup.  
  
 ![TileBrush s horní&#45;zarovnání vlevo](./media/graphicsmm-tilebrushalignmentexampletopleft.png "graphicsmm_TileBrushAlignmentExampleTopLeft")  
Zarovnání TileBrush se obsah do levého horního rohu  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmentinline)]  
  
## <a name="example"></a>Příklad  
 Následující příklad Zarovná obsah <xref:System.Windows.Media.DrawingBrush> do pravého dolního rohu jeho dlaždici tak, že nastavíte <xref:System.Windows.Media.TileBrush.AlignmentX%2A> vlastnost <xref:System.Windows.Media.AlignmentX.Right> a <xref:System.Windows.Media.TileBrush.AlignmentY%2A> vlastnost <xref:System.Windows.Media.AlignmentY.Bottom>. Tento příklad vytvoří následující výstup.  
  
 ![TileBrush s dolní&#45;klikněte pravým tlačítkem myši zarovnání](./media/graphicsmm-tilebrushalignmentexamplebottomright.png "graphicsmm_TileBrushAlignmentExampleBottomRight")  
Zarovnání TileBrush se obsah do pravého dolního rohu  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
## <a name="example"></a>Příklad  
 Následující příklad Zarovná obsah <xref:System.Windows.Media.DrawingBrush> do levého horního rohu jeho dlaždici tak, že nastavíte <xref:System.Windows.Media.TileBrush.AlignmentX%2A> vlastnost <xref:System.Windows.Media.AlignmentX.Left> a <xref:System.Windows.Media.TileBrush.AlignmentY%2A> vlastnost <xref:System.Windows.Media.AlignmentY.Top>. Také nastaví <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.TileMode%2A> z <xref:System.Windows.Media.DrawingBrush> k vytvoření vzorku dlaždice. Tento příklad vytvoří následující výstup.  
  
 ![A tiled horní TileBrush&#45;zarovnání vlevo](./media/graphicsmm-tilebrushalignmentexampletoplefttiled.png "graphicsmm_TileBrushAlignmentExampleTopLeftTiled")  
Dlaždice vzoru se obsahu zarovnána na levou horní v základní dlaždice  
  
 Nejdůležitější funkce obsahuje obrázek abase dlaždice tak, abyste viděli, jak se jeho obsah je zarovnán. Všimněte si, že <xref:System.Windows.Media.TileBrush.AlignmentX%2A> nastavení nemá žádný vliv, protože obsah <xref:System.Windows.Media.DrawingBrush> nesplňuje kompletně základní dlaždice vodorovně.  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmenttiledinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmenttiledinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmenttiledinline)]  
  
## <a name="example"></a>Příklad  
 V posledním příkladu Zarovná obsah dlaždicového <xref:System.Windows.Media.DrawingBrush> na pravém dolním rohu jeho základní dlaždice tak, že nastavíte <xref:System.Windows.Media.TileBrush.AlignmentX%2A> vlastnost <xref:System.Windows.Media.AlignmentX.Right> a <xref:System.Windows.Media.TileBrush.AlignmentY%2A> vlastnost <xref:System.Windows.Media.AlignmentY.Bottom>. Tento příklad vytvoří následující výstup.  
  
 ![A tiled dolní TileBrush&#45;klikněte pravým tlačítkem myši zarovnání](./media/graphicsmm-tilebrushalignmentexamplebottomrighttiled.png "graphicsmm_TileBrushAlignmentExampleBottomRightTiled")  
Dlaždice vzoru se obsahu zarovnána na pravém v základní dlaždice  
  
 Znovu <xref:System.Windows.Media.TileBrush.AlignmentX%2A> nastavení nemá žádný vliv, protože obsah <xref:System.Windows.Media.DrawingBrush> nesplňuje kompletně základní dlaždice vodorovně.  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
 V příkladech se používá <xref:System.Windows.Media.DrawingBrush> objekty k předvedení jak <xref:System.Windows.Media.TileBrush.AlignmentX%2A> a <xref:System.Windows.Media.TileBrush.AlignmentY%2A> vlastnosti jsou používány. Tyto vlastnosti se chovají stejně jako pro všechny dlaždice štětce: <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.ImageBrush>, a <xref:System.Windows.Media.VisualBrush>. Další informace o štětcích dlaždice najdete v tématu [Malování pomocí obrázků, kreseb a vizuálních](painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.DrawingBrush>
- <xref:System.Windows.Media.ImageBrush>
- <xref:System.Windows.Media.VisualBrush>
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
