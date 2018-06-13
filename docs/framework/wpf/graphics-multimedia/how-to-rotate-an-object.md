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
ms.openlocfilehash: 7eb562d81bdd8c9187672b31ed08ed6ac27da41c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561940"
---
# <a name="how-to-rotate-an-object"></a>Postupy: Otočení objektu
Tento příklad ukazuje, jak objektu. V příkladu se nejdřív vytvoří <xref:System.Windows.Media.RotateTransform> a pak specifikuje jeho <xref:System.Windows.Media.RotateTransform.Angle%2A> ve stupních.  
  
 Následující příklad otočí <xref:System.Windows.Shapes.Polyline> objektu 45 stupňů o jeho levého horního rohu.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti <xref:System.Windows.Media.RotateTransform> zadejte bod o tom, které se objekt otočen. Tento bod center je vyjádřeno v prostoru souřadnic elementu, který transformuje. Ve výchozím nastavení je oběh se použije k (0,0), který je levém horním rohu objektu k transformaci.  
  
 Další příklad otočí <xref:System.Windows.Shapes.Polyline> objektu 45 stupňů po směru hodinových ručiček kolem bodu (25,50).  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 Následující obrázek znázorňuje výsledky použití <xref:System.Windows.Media.Transform> na dva objekty.  
  
 ![Otočení o 45 stupňů s různými středy](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
Dva objekty, které otočit 45 stupňů z různých otáčení centra  
  
 <xref:System.Windows.Shapes.Polyline> v předchozích příkladech je <xref:System.Windows.UIElement>. Pokud použijete <xref:System.Windows.Media.Transform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost <xref:System.Windows.UIElement>, můžete použít <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnosti a určit tak pro počátek každých <xref:System.Windows.Media.Transform> , můžete použít k elementu. Protože <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost používá relativních souřadnicích, můžete použít transformaci k centru elementu i v případě, že neznáte jeho velikost. Další informace a příklady naleznete v tématu [zadejte počátek transformace pomocí relativní hodnoty](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).  
  
 Kompletní příklad, najdete v části [2-D transformací ukázka](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Transform>  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
