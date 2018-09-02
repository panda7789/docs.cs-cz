---
title: 'Postupy: Zkreslení elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: f828e4d4e59fa5ed31f81f3e83570a25add19e01
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43424291"
---
# <a name="how-to-skew-an-element"></a>Postupy: Zkreslení elementu
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.SkewTransform> zkosení elementu. Nerovnoměrná distribuce, které se taky říká zkosení je transformace, která roztáhne souřadnicového prostoru nerovnoměrné způsobem. Jeden typické použití <xref:System.Windows.Media.SkewTransform> je pro simulaci [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] hloubka v [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objekty.  
  
 Použití <xref:System.Windows.Media.SkewTransform.CenterX%2A> a <xref:System.Windows.Media.SkewTransform.CenterY%2A> vlastnosti k určení centru bod <xref:System.Windows.Media.SkewTransform>.  
  
 Použití <xref:System.Windows.Media.SkewTransform.AngleX%2A> a <xref:System.Windows.Media.SkewTransform.AngleY%2A> vlastnosti k určení nerovnoměrné rozdělení úhlu z osy x a y a zkosení aktuální systém souřadnic spolu tyto osy.  
  
 Chcete-li odhadnout účinky transformaci zkosení, zvažte, který <xref:System.Windows.Media.SkewTransform.AngleX%2A> zkosí hodnoty na ose x vzhledem k původní systém souřadnic. Proto se pro <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30, osy y otočí 30 stupňů prostřednictvím původ a zkosí hodnoty x – o 30 stupňů z tohoto počátku. Podobně <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 zkosí hodnot y tvaru o 30 stupňů z původního zdroje. Všimněte si, že to není stejný účinek jako překladu (přesun) souřadnicový systém o 30 stupňů x nebo y.  
  
 Následující příklad použije vodorovné zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> od středu (0; 0).  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 Následující příklad použije vodorovné zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> od středu (25,25).  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 Následující příklad použije svislé zkosení 45 stupňů <xref:System.Windows.Shapes.Rectangle> od středu (25,25).  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 Následující obrázek znázorňuje různé nerovnoměrné distribuce, které se používají v tomto příkladu.  
  
 ![SkewTransform – příklady](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
Tři SkewTransform – příklady jsou znázorněné  
  
 Úplnou ukázku najdete v tématu [2D transformace ukázka](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
