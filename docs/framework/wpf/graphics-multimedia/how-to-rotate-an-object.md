---
title: 'Postupy: Otočení objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: e17d3b7b9986b477df198480129edaf4c139c6bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112060"
---
# <a name="how-to-rotate-an-object"></a>Postupy: Otočení objektu
Tento příklad ukazuje, jak otočit objekt. Příklad nejprve <xref:System.Windows.Media.RotateTransform> vytvoří a pak <xref:System.Windows.Media.RotateTransform.Angle%2A> určuje jeho ve stupních.  
  
 Následující příklad otočí <xref:System.Windows.Shapes.Polyline> objekt o 45 stupňů kolem levého horního rohu.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <xref:System.Windows.Media.RotateTransform.CenterX%2A> Vlastnosti <xref:System.Windows.Media.RotateTransform.CenterY%2A> a <xref:System.Windows.Media.RotateTransform> určete bod, ve kterém je objekt otočen. Tento středový bod je vyjádřen v souřadnicovém prostoru prvku, který je transformován. Ve výchozím nastavení je otočení aplikováno na (0,0), což je levý horní roh objektu, který má být transformován.  
  
 Další příklad otočí <xref:System.Windows.Shapes.Polyline> objekt ve směru hodinových ručiček o 45 stupňů kolem bodu (25,50).  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 Následující obrázek znázorňuje <xref:System.Windows.Media.Transform> výsledky použití a na dva objekty.  
  
 ![Otočení o 45 stupňů s různými středovými body](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
Dva objekty, které se otáčejí o 45 stupňů od různých rotačních středů  
  
 V <xref:System.Windows.Shapes.Polyline> předchozích příkladech <xref:System.Windows.UIElement>je . Při použití <xref:System.Windows.Media.Transform> <xref:System.Windows.UIElement.RenderTransform%2A> vlastnosti <xref:System.Windows.UIElement>, můžete použít <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost k určení původu <xref:System.Windows.Media.Transform> pro každý, který použijete na prvek. Vzhledem <xref:System.Windows.UIElement.RenderTransformOrigin%2A> k tomu, že vlastnost používá relativní souřadnice, můžete použít transformaci na střed prvku i v případě, že neznáte jeho velikost. Další informace a příklad [najdete v tématu Určení počátku transformace pomocí relativních hodnot](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).  
  
 Kompletní ukázku naleznete v tématu [2D transformace Ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Transform>
- [Přehled transformace](transforms-overview.md)
- [Témata s postupy](transformations-how-to-topics.md)
